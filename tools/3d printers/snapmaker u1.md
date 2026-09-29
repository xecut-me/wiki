# Snapmaker U1

IP: 192.168.10.21
[WebUI](http://192.168.10.21)
[Filament Configuration](http://192.168.10.21/filament)

# [Характеристики](https://eu.snapmaker.com/products/snapmaker-u1-3d-printer)

* Максимальный размер печати: 270 x 270 x 270 mm³
* Максимальная температура сопла: 300 ℃
* Максимальная температура кроватки: 100 ℃
* Печать через wi-fi / USB

# Текущая конфигурация
* 4 сопла 0.4mm
* Textured PEI Plate
* [Extended Firmware](https://github.com/paxx12-snapmaker-u1/SnapmakerU1-Extended-Firmware)

Также имеется:
 * Carbon-Fiber Textured PEI
 * Graphic PEI
 * "Cold Plate"
 * 4 сопла 0.2mm Noname
 * 4 сопла 0.4mm Noname
 * 4 сопла 0.6mm Noname
 * 4 сопла 0.8mm Noname
 * 2 сопла 0.4mm Orig
 * Запасная левая голова (0.4mm)
 * Запасная правая голова (0.6mm)
 * Прочие запасные части

# Филаменты
* Хорошо: PLA, PETG, [TPU](https://www.youtube.com/watch?v=McCOm5IerC4) (>90A), PVA, PCTG
* Желательно с крышкой: PLA, PETG, TPU, PVA, PET, ABS, ASA, PA, PC
* С крышкой и закалённым соплом: Carbon-fiber-reinforced Polymer, Glass-fiber-reinforced Polymer

# Слайсер
На текущий момент U1 поддерживается только в Snapmaker Orca ([Win, Mac](https://www.snapmaker.com/snapmaker-orca),[Linux](https://github.com/Snapmaker/OrcaSlicer/releases)).

Официальный гайд по настройке: [[https://wiki.snapmaker.com/en/snapmaker_orca/qsg]]

В большинстве случаев можно использовать стандартные настройки для печати.

## Color Mixing
   TODO

# Смена филамента
## Unload

Процесс полностью автоматический

![](./image-1789156145260.png)
![](./image-1789156269969.png)
![](./image-1789156418051.png)
![](./image-1789156399027.png)

После этого смотать катушку вручную

## Load
1. Просунуть филамент в фидер
2. Его автоматически затянет почти до экструдера
3. ![](./image-1789156907463.png)
4. ![](./image-1789156970621.png)

>| # Ручной выбор филамента 
>| 5. [Filament Configuration](http://192.168.10.21/filament) (рекомедуется) или вручную в интерфейсе принтера 
>| 6. ![](./image-1789157101995.png)
>| 7. В поиске ввести номер катушки, цвет, название или тип пластика
>| 8. Выбрать правильную катушку
>| 9. ![](./image-1789157270297.png)

9. Филамент определяется автоматически по NFC меткам наклееным на катушки
10. В интерфейсе отбразится тип и цвет пластика 
11. ![](./image-1789157344085.png)
12. ![](./image-1789157530373.png) 
13. ![](./image-1789157542243.png)

## [Spoolman](http://192.168.10.5:7912)
Все катушки занесены в Spoolman и пронумерованы, при правильном использовании должно отслеживаться количество оставшегося пластика.
На всех катушках наклеены NFC метки, с информацией о филаменте в формате OpenSpool. При установке катушки принтер определяет филамент самостоятельно.


### Для автоматического "перемещения" катушек на принтер
#### [/extended/moonraker/99_move_spool.cfg](http://192.168.10.21/#/configure)
```ini
[move_spool]
location: Snapmaker U1
```

#### ~lava/moonraker/moonraker/components/move_spool.py
```python
import asyncio
import json
import logging

class MoveSpool:
	def __init__(self,config):
		logging.error("Hello")
		self.server = config.get_server()
		self.server.register_event_handler("spoolman:active_spool_set",self._spool_set)
		self.klippy_apis = self.server.lookup_component("klippy_apis")
		self.server.register_event_handler("server:klippy_ready", self._handle_klippy_ready)
		self.active_spool_ids = [0,0,0,0]
		self.location_name = config.get("location","Snapmaker U1")
		self.spoolman_url= None
	
	
	async def _handle_klippy_ready(self) -> None:
        	logging.info("[spoollink] Klippy ready, subscribing to objects")
	        status = await self.klippy_apis.subscribe_objects({
	            "print_task_config": ["filament_spool_id"],
	        }, self._handle_status_update, {})
        	self._handle_status_update(status, 0.)

	async def update_spool_locs(self,old,new):
			removed = [i for i in old if i not in new]
			added = [i for i in new if i not in old]
			await self.set_spool_location(removed,"")
			await self.set_spool_location(added,self.location_name)
			self.active_spool_ids = new
		
	async def set_spool_location(self, ids, loc):
		logging.info(f"{self.spoolman_url} {ids} {loc}")
		if self.spoolman_url is None:
			spoolman = self.server.lookup_component("spoolman", None)
			if spoolman is not None:
				logging.info(f"Spoolman url is: {spoolman.spoolman_url}")
				self.spoolman_url = spoolman.spoolman_url
		if self.spoolman_url is None:
			return
		for i in ids:
			if i==0:
				continue
			url = f"{self.spoolman_url}/v1/spool/{i}"
			method = "PATCH"
			#body = '{"location": "'+loc+'"}'
			body = {"location": loc}
			http = self.server.lookup_component("http_client")
			logging.info(f"{url} {method} {body}")
			response = await http.request(method=method,url=url,body=body,)
			logging.info(f"{response}")

	def _fire(self, coro) :
		task = asyncio.ensure_future(coro)
		task.add_done_callback(self._task_done)
		return task

	@staticmethod
	def _task_done(task):
		if not task.cancelled() and task.exception() is not None:
			logging.error("[spoollink] background task failed: %s",task.exception(), exc_info=task.exception())

	def _handle_status_update(self, status, eventtime):
		ptc = status.get("print_task_config")
		if ptc is not None:
			spool_ids = ptc.get("filament_spool_id")
			logging.info(f"Current filaments: {spool_ids}")
			self._fire(self.update_spool_locs(self.active_spool_ids,spool_ids))

	def _spool_set(self,spool_id):
		logging.info(f"Spool ID set to {spool_id} ")
		spoolman = self.server.lookup_component("spoolman", None)
		if spoolman is not None:
			logging.info(f"Spoolman url is: {spoolman.spoolman_url}")
		

def load_component(config):
	return MoveSpool(config)

```
