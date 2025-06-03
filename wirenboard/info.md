## WIRENBOARD


###  Шаблоны хранятся на контроллере в директории

:white_check_mark: /usr/share/wb-mqtt-serial/templates  — папка с предустановленными шаблонами;

:white_check_mark: /etc/wb-mqtt-serial.conf.d/templates — папка для пользовательских шаблонов, которые имеют приоритет над предустановленными.

:ballot_box_with_check: Если вы добавили свой шаблон или изменили существующий, подождите 20 секунд, а потом перезагрузите страницу конфигуратора в веб-интерфейсе клавишами Ctrl+F5 или перезапустите сервис:
```yaml
systemctl restart wb-mqtt-confed
```

### MODBUS ID замена

Остановить службу 
```yaml
systemctl stop wb-mqtt-serial 
```
Чтобы назначить новый адрес 12 устройству с адресом 1 и подключенное к порту /dev/ttyRS485-1 выполните команду:
```yaml
modbus_client --debug -mrtu -b9600 -pnone -s2 /dev/ttyRS485-1 -a1 -t0x06 -r128 12  
```
128->51
```yaml
modbus_client --debug -mrtu -b9600 -pnone -s2 /dev/ttyMOD2 -a128 -t0x06 -r128 51  
```
125->11
```yaml
modbus_client --debug -mrtu -b9600 -pnone -s2 /dev/ttyMOD1 -a125 -t0x06 -r128 11  
```

### WB RULES
:ballot_box_with_check: https://wirenboard.com/wiki/Wb-rules
Файлы с правилами хранятся в контроллере в папке /etc/wb-rules/ с расширением .js
```yaml
systemctl restart wb-rules
```

### Обновление всех устройств на шине

```yaml
wb-mcu-fw-updater update-all
```

### WIRENBOARD CLOUD

```yaml
apt update
```
```yaml
apt install wb-cloud-agent
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

- `out = publish from the broker`
- `in = receive from remote broker` получить от удаленного брокера
- `both = publish and receive`

  ***ПРИМЕР***
  при такой конфигурации на удаленный сервер приходят все топики с текущего клиента `topic # out 0` OUT - с клиента топики уходят с префиксом `ha_home/`
```yaml
connection bridge-home
address 195.201.xxx.xx:1883
notifications true
notification_topic status/HA_Home/bridge_status
topic # out 0 "" ha_home/
remote_username artem
remote_password artem
```
### WIRENBOARD

:ballot_box_with_check: Путь к конфигурации - `/etc/mosquitto/conf.d/20bridges.conf`     

```yaml
connection WB8IP20
address 192.168.100.10:1883
remote_username artem
remote_password artem
try_private false
allow_anonymous true
notifications true
notification_topic /client/WB8IP20/bridge_status
start_type automatic
topic /# both 0 ""
```
:ballot_box_with_check: Перезапустите mosquitto, выполнив в консоли:
```yaml
service mosquitto restart
```

