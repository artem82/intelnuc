## Home Assistant. MQTT Bridge - синхронизация работы Mosquitto broker

###  Установка mqtt

[Wirenboard] (https://wirenboard.com/wiki/index.php/MQTT#%D0%A0%D0%B0%D0%B1%D0%BE%D1%82%D0%B0_%D1%81_%D1%81%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D0%BD%D0%B8%D1%8F%D0%BC%D0%B8_MQTT_%D1%81_%D0%B2%D0%BD%D0%B5%D1%88%D0%BD%D0%B5%D0%B3%D0%BE_%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0ХЪ)

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