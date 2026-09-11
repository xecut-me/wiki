# Snapmaker U1

IP: 192.168.10.21
[[WebUI|http://192.168.10.21]]
[[Filament Configuration|http://192.168.10.21/filament]]

# [[Характеристики|https://eu.snapmaker.com/products/snapmaker-u1-3d-printer]]

* Максимальный размер печати: 270 x 270 x 270 mm³
* Максимальная температура сопла: 300 ℃
* Максимальная температура кроватки: 100 ℃
* Печать через wi-fi / USB

# Текущая конфигурация
* 4 сопла 0.4mm
* Textured PEI Plate
* [[Extended Firmware|https://github.com/paxx12-snapmaker-u1/SnapmakerU1-Extended-Firmware]]

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
* Хорошо: PLA, PETG, [[TPU|https://www.youtube.com/watch?v=McCOm5IerC4]] (>90A), PVA, PCTG
* Желательно с крышкой: PLA, PETG, TPU, PVA, PET, ABS, ASA, PA, PC
* С крышкой и закалённым соплом: Carbon-fiber-reinforced Polymer, Glass-fiber-reinforced Polymer

# Слайсер
На текущий момент U1 поддерживается только в Snapmaker Orca ([[Win, Mac|https://www.snapmaker.com/snapmaker-orca]],[[Linux|https://github.com/Snapmaker/OrcaSlicer/releases]].

Официальный гайд по настройке: [[[https://wiki.snapmaker.com/en/snapmaker_orca/qsg]]

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
5. [[Filament Configuration|http://192.168.10.21/filament]](рекомедуется) или вручную в интерфейсе принтера 
6. ![](./image-1789157101995.png)
7. В поиске ввести номер катушки, цвет, название или тип пластика
8. Выбрать правильную катушку
9. ![](./image-1789157270297.png)
10. В интерфейсе отбразится тип и цвет пластика 
11. ![](./image-1789157344085.png)
12. ![](./image-1789157530373.png) 
13. ![](./image-1789157542243.png)

## [[Spoolman|http://192.168.10.5:7912]]
Все катушки занесены в Spoolman и пронумерованы, при правильном использовании долно отслеживаться количество оставшегося пластика.

Также планируется наклеить на катушки QR или RFID, для автоматизации выбора катушки.
