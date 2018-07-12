# Администрирование ROS

## SSH подключение к RaspberryPi

{% hint style="info" %}
ip: 192.168.1.10 или 10.42.0.1  
login: pi  
password: brobro
{% endhint %}

## Сервис navibro

`sudo systemctl status navibro` Получить статус  
`sudo systemctl stop navibro` Остановить сервис`sudo systemctl start navibro` Запустить сервис

Логирование работы сервиса происходит `/home/pi/.ros/log/latest`

## Настройка камеры

Изменить настройки работы камеры возможно в файле `/opt/ros/kinetic/share/navibro/camera/camerav1_320x240.launch`

```text
<launch>
  <node type="raspicam_node" pkg="raspicam_node" name="raspicam_node" output="screen">

    <param name="camera_info_url" value="package://navibro/camera/camera_info/camerav1_320x240.yaml"/>
    <param name="width" value="320"/>
    <param name="height" value="240"/>
    <!-- We are running at 90fps to reduce motion blur -->
    <param name="framerate" value="20"/>
    <param name="contrast" value="50"/>
    <param name="brightness" value="50"/>
    <param name="hFlip" value="true"/>
    <param name="vFlip" value="true"/>

    <param name="camera_frame_id" value="raspicam"/>

  </node>

</launch>
```

После изменения параметров, необходимо перезапустить сервис navibro

## NetworkManager

**Подключение к новой WiFi сети**

```bash
nmcli dev wifi connect NavibroWiFi password navibro2018
```

**Отображение текущего подключения WiFi**

```text
nmcli connection show --active
```

**Список доступных сетей**

```text
nmcli dev wifi list
```

**Добавить статический IP в connection**. Для этого необходимо отредактировать файл /etc/NetworkManager/system-connections/НазваниеСоединения

```text
[ipv4]
address1=192.168.1.10/24,192.168.1.1
```
