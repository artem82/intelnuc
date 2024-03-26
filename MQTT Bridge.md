## Home Assistant. MQTT Bridge - синхронизация работы Mosquitto broker

###  Установка mqtt

:white_check_mark: 
:white_check_mark: **Официальный репозиторий Debian 11** - [Загрузка образа](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/)  

<a href="https://www.youtube.com/channel/UCcq9onYHbs6go3kDpfBoqhg?sub_confirmation=1" target="_blank"><img src="https://raw.githubusercontent.com/kvazis/training/master/lessons/img/subscribe.png" alt="Subscribe" style="height: 71px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

### Home Assistant
Заходим в file editor

:ballot_box_with_check: Путь к конфигурации - `/share/mosquitto/20bridges.conf`     

:ballot_box_with_check: Конфиг показанный в уроке. Адрес, логин и пароль - ставим свои    

```yaml
connection bridge-01
address 192.168.1.55:1883
notifications true
notification_topic status/HA_Home/bridge_status
topic # out 0
topic # in 0
remote_username mqtt
remote_password mqtt
```
