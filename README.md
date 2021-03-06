# Система навигации NaviBro

## Краткое описание

Система навигации NaviBro, позволяет определить положение объекта расположенного на полигоне в системе координат XYZ, углам тангажа, рысканья и крена.

Определение расположение объекта происходит относительно координатной карты,состоящей из графических меток \(Aruco Marker\) расположенных на потолке полигона.

Камера, снимает графические метки и передает на микрокомпьютер RaspberryPi. Далее происходит анализ изображения, при котором определяется положение камеры в пространстве, согласно созданной карты меток и полученного изображения.

Для определения расположения, необходимо чтобы камера “видела” минимум одну графическую метку, для более точного определения, необходимо три метки. Чем больше меток может обработать микрокомпьютер, тем меньше разброс значений при определении координат.

Точность работы системы зависит от точности созданной координатной карты, размеров меток и расстояния до них относительно камеры, условий освещения.  
При нормальной работе системы, точность определения координат составляет +-5см \(при округлении нескольких измерений\).

В зависимости от кол-ва видимых меток, системы выдает от 3 до 10 значений координат объекта в секунду.

Значений координат объекта можно получить через Serial порт микрокомпьютера как обычную строчку, websocket или ROS topic.

