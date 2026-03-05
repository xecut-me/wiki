# Bamboo A1 3d printer
![](./image-1772735623990.png?thumbnail=400)
# Параметры
Этого должно быть достаточно, чтобы настроить слайсер на принтер:
- Bambu Lab A1
- 0.4 nozzle
- Textured PEI Plate
Остальное - https://bambulab.com/en/a1/tech-specs
- Максимальный размер печати: 256 x 256 x 256 mm³
- Максимальная температура сопла: 300 ℃
- Максимальная температура кроватки: 	100 ℃
- Печать через Micro SD Card / wi-fi
# Филамент
Хорошо: PLA, PETG, TPU, PVA

Не рекомендуется: ABS, ASA, PC, PA, PET, Carbon/Glass Fiber Reinforced Polymer

# Orca
## Как выбрать принтер в орке:
1. Prepare -> Printer -> Select/Remove printers (system presets)
![](./image-1772574719583.png?thumbnail=400)

2. Во всплывающем окошке дождаться загрузки и выбрать Bambu Lab A1 c 0.4mm nozzle
![](./image-1772574966096.png?thumbnail=400)


3. Выбрать подложку: Bed type -> Textured PEI Plate
![](./image-1772574731356.png?thumbnail=400)

4. Выбрать филамент - вероятно это будет PLA
5. Process  хорошо печатает со стандартными значениями и изменений не требует.
## Как подключить принтер к орке:
Это опциональный шаг для возможности отправлять файлы на печать по сети минуя перенос флешки от компа к принтеру.
1. Device -> "No printer +" -> Other device -> 3DP-XXX-XXX
![](./image-1772574738017.png?thumbnail=400)

2.  Взять код из принтера из Settings -> Lan Only Mode -> Access code
## Как печатать в орке:
### Через флешку
1. Заслайсить

![](./image-1772574746545.png?thumbnail=400)

2. Экспортировать файл для печати и отправить на флешку.
Export plate sliced file для .3mf или Export G-code для .gcode.

![](./image-1772574760330.png?thumbnail=400)

3. Из меню принтера выбрать файл и начать печать.
### Через сеть
1. Slice
2. Print
3. Во всплывающем окошке оставить bed leveling и убрать Flow Dynamic Calibration. Последний нужен после замены филамента.

![](./image-1772574769366.png?thumbnail=400)
