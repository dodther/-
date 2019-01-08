# Энергомонитор

Устройство для учёта потреблённой энергии основанное на Arduino nano, PZEM-004t и Blynk.

Содержание:  
1. [Возможности](#id1)
2. [Вид приложениия](#id2)
3. [Необходимые компоненты](#id3)
3. [Необходимые библиотеки](#id4)
4. [Схема включения](#id5)


Возможности <a name="id1"></a>
-----------------------------------
1. Отслеживание напряжения и потребления ЭЭ в трёх фазных сетях.
2. Учёт потреблённой энергии с разбивкой на два тарифа (день, ночь).
3. Расчёт количества денег необходымых для оплаты потреблённого ЭЭ.
4. Возможность указать стоимость тарифа (день, ночь).
5. Возможность указать время перехода на дневной и ночной тариф.
6. Показывает активную и реактивную мощность


Вид приложениия<a name="id2"></a>
--------------------
![Программа](https://github.com/dodther/-/blob/master/Energy.JPG)
![График](https://github.com/dodther/-/blob/master/%D0%93%D1%80%D0%B0%D1%84%D0%B8%D0%BA.JPG)
![Настройки](https://github.com/dodther/-/blob/master/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8.jpg)


Необходимые компоненты<a name="id3"></a>
------------------

Наименование    | Количество  | Назначение 
----------------|-------------|------------
Arduino Nano    | 1шт         |
PZEM-004t       | 3шт         | Датчик напряжения и тока
W5100           | 1шт         | Сеть
Оптрон          | 3шт         | Програмный сброс показаний у PZEM-004t
Сопротивление   | 1шт         | для ограничения тока при работе оптрона от 5В логики Arduino

Ну и ещё всякие провода, фишки и т.д коих у любителей заниматься микроконтролерами должно быть навалом.

Необходимые библиотеки<a name="id4"></a>
-----------------------
[PZEM004T](https://github.com/olehs/PZEM004T)  
[Blynk](https://github.com/blynkkk/blynk-library)  
[Time](https://github.com/PaulStoffregen/Time)  




Схема включения<a name="id5"></a>
--------------

Все 3 PZEM-004t подключаются на 2 вывода Arduino. Для этого их надо подключить по одному и задать уникальный адресс. Адресс после выключения питания не сбрасывается и останется в датчике до тех пор пока не будет задан другой адресс. Для это можно воспользоваться библиотекой [PZEM004T](https://github.com/olehs/PZEM004T). Она же необходима для работы проекта. В моём проекте используются адреса 192,168,1,1, ...1,2, ...1,3.   Для корректной работы необходимо [удалить](https://github.com/zbx-sadman/zabbuino/issues/8#issuecomment-293243993) сопротивление R15 на двух датчиках из трёх.  
GND - GND  
А VCC подключается через инвертор на полевых транзисторах. Это сделано для возможности отключать питания порта передачи данных. Так как сброс показаний возможен только когда прерван обмен данными. А при питании напрямую от ноги ардуины слишком поздно появляется высокий уровень и датчик не успевает инициализороватся.  

![Схема подключения](https://github.com/dodther/Energomonitor/blob/master/%D0%A1%D1%85%D0%B5%D0%BC%D0%B0.png)


