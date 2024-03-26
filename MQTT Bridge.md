## Home Assistant. MQTT Bridge - синхронизация работы Mosquitto broker

###  Установка mqtt Mosquitto broker

:white_check_mark: **Wirenboard** [ссылка](https://wirenboard.com/wiki/index.php/MQTT#%D0%A0%D0%B0%D0%B1%D0%BE%D1%82%D0%B0_%D1%81_%D1%81%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D0%BD%D0%B8%D1%8F%D0%BC%D0%B8_MQTT_%D1%81_%D0%B2%D0%BD%D0%B5%D1%88%D0%BD%D0%B5%D0%B3%D0%BE_%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0)  
:white_check_mark: **Статья 1** - [ссылка](https://www.8host.com/blog/ustanovka-brokera-soobshhenij-mosquitto-v-debian-10/?ysclid=lu8cn6mvyd128775825)  


:ballot_box_with_check: Обновление списка пакетов и установка обновлений
```yaml
apt update && sudo apt upgrade -y && sudo apt autoremove -y
```
:ballot_box_with_check: Чтобы установить Mosquitto, введите:
```yaml
sudo apt install mosquitto mosquitto-clients
```
:ballot_box_with_check: Mosquitto предоставляет утилиту `mosquitto_passwd` для создания файла паролей. Эта команда предложит ввести пароль для указанного пользователя и поместит его в файл `/etc/mosquitto/passwd`
```yaml
sudo mosquitto_passwd -c /etc/mosquitto/passwd artem
```
пользователю `artem` нужно будет ввести пароль

:ballot_box_with_check: Откройте конфигурации Mosquitto и добавьте в них информацию о новом файле
```yaml
sudo nano /etc/mosquitto/conf.d/default.conf
```
:ballot_box_with_check: На экране появится пустой файл `default.conf`. Введите в него:
```yaml
allow_anonymous false
password_file /etc/mosquitto/passwd
listener 1883

```
:ballot_box_with_check: Теперь нужно перезапустить Mosquitto и проверить новые настройки:
```yaml
sudo systemctl restart mosquitto
```
Статус сервера 
```yaml
sudo systemctl status mosquitto
```

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
:ballot_box_with_check: В настройка брокера обязательно
`active: true`
