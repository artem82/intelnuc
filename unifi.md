## UNIFI

Логин пароль - `ubnt/ubnt ....`    

:ballot_box_with_check: Команда сбросить текущее UNIFI устройство
```yaml
syswrapper.sh restore-default
```
:ballot_box_with_check: Команда привязать текущее UNIFI устройство к серверу
```yaml
set-inform http://192.168.1.10:8080/inform
```
### Ссылки на прошивки устройств
:ballot_box_with_check: U6 pro
```yaml
https://ui.com/download/software/u6-pro
```
:ballot_box_with_check: U7 pro
```yaml
https://ui.com/download/software/u7-pro
```
:ballot_box_with_check: [UniFi OS - Dream Machine Pro Max 4.3.6](https://ui.com/download/software/udm-pro-max)
```yaml
https://fw-download.ubnt.com/data/unifi-dream/4092-UDMPROMAX-4.3.6-04d08e37-0365-4e68-a217-207667f27c39.bin
```
:ballot_box_with_check: U7 pro обновление прошивки
```yaml
upgrade https://dl.ui.com/unifi/firmware/U7PRO/8.4.6.18068/BZ.ipq53xx_8.4.6+18068.260111.0707.bin
```
:ballot_box_with_check: U6/U7 pro обновление прошивки локально
```yaml
http://kedriza.ru/U7PRO8611.bin
```
```yaml
http://kedriza.ru/U6PRO682.bin
```
:ballot_box_with_check: Команда скачать прямо на AP через SSH
```yaml
curl -o /tmp/fwupdate.bin http://kedriza.ru/U7PRO8611.bin

```
```yaml
syswrapper.sh upgrade2 &
```

### UniFi Network Application
[UniFi Network Application 9.5.21 for UniFi OS](https://dl.ui.com/unifi/9.5.21/unifi-uos_sysvinit.deb)


