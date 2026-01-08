
## supervisor
:ballot_box_with_check: Если глючит supervisor
```yaml
sudo docker restart hassio_supervisor
```

## HACS
#### После настройки HA (192.168.1.X:8123)
:ballot_box_with_check: Hacs
```yaml
wget -O - https://get.hacs.xyz | bash -
```

:ballot_box_with_check: Если глючит путь
```yaml
find / -name "configuration.yaml"
```
/var/lib/homeassistant/homeassistant/configuration.yaml
```yaml
cd /var/lib/homeassistant/homeassistant/
```
## Репозитории дополнений
:ballot_box_with_check: Ссылки
```yaml
https://github.com/hacs/addons
```
```yaml
https://github.com/zigbee2mqtt/hassio-zigbee2mqtt
```
```yaml
https://github.com/blakeblackshear/frigate-hass-addons
```
```yaml
https://github.com/AlexxIT/hassio-addons
```
```yaml
https://github.com/faserf/hassio-addons
```
```yaml
https://github.com/pergolafabio/Hikvision-Addons
```
____
#### [Beelink GK Mini часть 2 - Autoboot, Debian 11, Supervised Home Assistant](https://youtu.be/RqW5q-0RYio)

<a href="https://www.youtube.com/channel/UCcq9onYHbs6go3kDpfBoqhg?sub_confirmation=1" target="_blank"><img src="https://raw.githubusercontent.com/kvazis/training/master/lessons/img/subscribe.png" alt="Subscribe" style="height: 71px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

#### [Beelink GK Mini на Celeron J4125 - обзор, легкая установка Home Assistant OS - пошаговая инструкция](https://youtu.be/i4bp-s20Dm8)
