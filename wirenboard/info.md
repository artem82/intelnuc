## WIRENBOARD


###  Шаблоны хранятся на контроллере в директории

:white_check_mark: /usr/share/wb-mqtt-serial/templates  — папка с предустановленными шаблонами;

:white_check_mark: /etc/wb-mqtt-serial.conf.d/templates — папка для пользовательских шаблонов, которые имеют приоритет над предустановленными.

:ballot_box_with_check: Если вы добавили свой шаблон или изменили существующий, подождите 20 секунд, а потом перезагрузите страницу конфигуратора в веб-интерфейсе клавишами Ctrl+F5 или перезапустите сервис:
```yaml
systemctl restart wb-mqtt-confed
```

### MODBUS ID замена

`Остановить` службу 
```yaml
systemctl stop wb-mqtt-serial 
```
`Запустить` службу 
```yaml
systemctl start wb-mqtt-serial 
```

Чтобы назначить новый адрес `12` устройству с адресом `1` и подключенное к порту `/dev/ttyRS485-1` выполните команду:
```yaml
modbus_client --debug -mrtu -b9600 -pnone -s2 /dev/ttyRS485-1 -a1 -t0x06 -r128 12  
```
128->51
```yaml
modbus_client --debug -mrtu -b9600 -pnone -s2 /dev/ttyMOD2 -a128 -t0x06 -r128 51  
```
12->55
```yaml
modbus_client --debug -mrtu -b9600 -pnone -s2 /dev/ttyRS485-2 -a12 -t0x06 -r128 55  
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
### Определение адреса методом перебора
```yaml
for i in {1..247}; do echo -n "$i - "; D=`modbus_client -mrtu /dev/ttyRS485-1 --debug -b9600 -pnone -s2 -a$i -t3 -o100 -r200 -c6 2>/dev/null | grep Data: | awk 'gsub("Data:","")' | sed -e 's/0x00/\\\x/g' -e 's/\s//g'`; echo -e $D; done
```

### WIRENBOARD CLOUD

```yaml
apt update
```
```yaml
apt install wb-cloud-agent
```
### WIRENBOARD ПРОШИВКА

```yaml
https://fw-releases.wirenboard.com/?prefix=fit_image/stable/8x/
```
