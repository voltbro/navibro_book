# Панель управления

## Обзор

Панель управления расположенна по адрессу [http://192.168.1.10:8000](http://192.168.1.10:8000) в случае поставки с роутером, или [http://10.42.0.1:8000](http://10.42.0.1:8000) в случае прямого подключения к RaspberryPi

Экран общей информации о модуле. Если камера видит метки, то обновляються данные с координатам. Также выводиться информация о текущем подключенни к сети, и информация мониторинга.

![&#x421;&#x442;&#x440;&#x430;&#x43D;&#x438;&#x446;&#x430; &#x41E;&#x431;&#x437;&#x43E;&#x440;, &#x441; &#x438;&#x43D;&#x444;&#x43E;&#x440;&#x43C;&#x430;&#x446;&#x438;&#x435;&#x439; &#x43E; &#x441;&#x438;&#x441;&#x442;&#x435;&#x43C;&#x435;](.gitbook/assets/snimok-ekrana-2018-07-12-v-15.12.39.png)

### Раздел WiFI

На этой странице возможно изменить и настроить тип подключения к WiFi \(Режим точки доступа, или работа с внешней wifi сетью\)

![&#x412;&#x44B;&#x431;&#x43E;&#x440; WiFi &#x43D;&#x430;&#x441;&#x442;&#x440;&#x43E;&#x435;&#x43A;](.gitbook/assets/snimok-ekrana-2018-07-12-v-16.30.42.png)

{% hint style="info" %}
При подключении к внешней WiFi сети, IP адрес утсройства выдаст "внешний" DCHP сервер. Он может отличаться от предустановленного. Подключаться необходимо по новому IP
{% endhint %}

### Настройка рабочих сервисов 

Работа с Serial портом возможна в режиме `SimpleSerial` \(режим по умолчанию\) в котором данные о местоположении передаються простой строкой вида КоординатаX;КоординатаY;КоординатаZ;УголTheta. Например:

```text
"0.21;-0.21;2.1;110.21\n"
```

Также возможен режим работы `RosSerial`. Тогда на порту Serial запускаеться процесс RosSerial, который позволяет работать стандартными средствами. Документация по пакету доступна [http://wiki.ros.org/rosserial](http://wiki.ros.org/rosserial).

Передача данных с происходит в топиках `navibro/pose2d (Pose2D)`для двухмерных координат и `/fiducial_pose (PoseWithCovarianceStamped)` для трехмерных координат

Библиотека [ros\_lib.zip](https://github.com/voltbro/navibro_book/raw/master/assets/ros_lib.zip) для Arduino

### Метки

В разделе можно загрузить обновленную карту поля с метками.

![](.gitbook/assets/snimok-ekrana-2018-07-12-v-16.48.53.png)

Формат данных с данными о расположении меток  
`ID метки  
Координата X  
Координата Y  
Координата Z (Высота)  
Угол pan  
Угол tilt  
Угол roll   
0 (коэффициент variance)  
0 (коэффициент numObservations)`

По умолчанию загруженна карта для 1U стола \(см. [Установка маркерного поля](ustanovka-merkernogo-polya.md)\)

### Видео

![&#x41E;&#x442;&#x43E;&#x431;&#x440;&#x430;&#x436;&#x435;&#x43D;&#x438;&#x435; &#x437;&#x430;&#x445;&#x432;&#x430;&#x442;&#x430; &#x43A;&#x430;&#x43C;&#x435;&#x440;&#x44B;, &#x441; &#x432;&#x44B;&#x434;&#x435;&#x43B;&#x435;&#x43D;&#x438;&#x435;&#x43C; &#x440;&#x430;&#x441;&#x43F;&#x43E;&#x437;&#x43D;&#x430;&#x43D;&#x43D;&#x44B;&#x445; &#x43C;&#x435;&#x442;&#x43E;&#x43A;](.gitbook/assets/snimok-ekrana-2018-07-12-v-17.10.28.png)

Если изображение получилось не качественным, возможно настроить его параметры \(яркость, контрастность\) см. раздел \([Администрирование](administrirovanie-ros.md#nastroika-kamery)\)

