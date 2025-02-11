## УСТАНОВКА Home Assistant Debian 12:   
<a href="https://www.home-assistant.io" target="_blank"><img src="https://github.com/home-assistant/assets/blob/master/misc/logo-icon_template.png" alt="Subscribe" style="height: 71px !important;width: 71px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>
 

:white_check_mark: **Оригинальная инструкция** - [Community Home Assistant Forum](https://community.home-assistant.io/t/installing-home-assistant-supervised-on-debian-11/200253#installing-home-assistant-supervised-on-debian-11-1)   
:white_check_mark: **Официальный образ DVD Debian 12.9** - [Загрузка образа](https://cdimage.debian.org/debian-cd/12.9.0/amd64/iso-dvd/) 
:white_check_mark: **Официальный репозиторий Debian 12.6** - [Загрузка образа](https://cdimage.debian.org/cdimage/unofficial/non-free/firmware/bookworm/12.6.0/)  

:white_check_mark: ***RUFUS*** - [Загрузка](https://rufus.ie/ru/)  
:white_check_mark: **Удобный SSH клиент** - [Putty](https://www.putty.org/)    

## LINUX:    
/usr/share/hassio/homeassistant

:ballot_box_with_check: Переход в режим root    
```yaml
su
```
:ballot_box_with_check: Connect to your Debian 12 server using an SSH client such as PuTTY or the terminal.
:ballot_box: Включаем ROOT

Должно быть без # 
`PermitRootLogin yes`
```yaml
sudo nano /etc/ssh/sshd_config
```
`Ctrl X` - для выхода    
`Y` для сохранения   

:ballot_box_with_check: Иногда необходимо вовсе отключить на Debian любые энергосберегающие функции (сон, гибернация, гибридный сон и т.п.), тогда пригодится следующая команда.
```yaml
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

:ballot_box_with_check: Редактирование источников    
```yaml
nano /etc/apt/sources.list
```
Комментируем строку ` deb cdrom:[Debian GNU/Linux ....`    

`Ctrl X` - для выхода    
`Y` для сохранения    

:ballot_box_with_check: Установка sudo       
```yaml
apt install sudo
```

:ballot_box_with_check: Добавление пользователя в sudo   
```yaml
sudo usermod -aG sudo username
```
```yaml
sudo usermod -aG sudo artem
```
:point_up: Выход из учетной записи root (не нужно) 
```yaml
exit
```

:ballot_box_with_check: Выполнение команд с правами root
```yaml
sudo -i
```
:ballot_box_with_check: Обновление списка пакетов и установка обновлений
```yaml
apt update && sudo apt upgrade -y && sudo apt autoremove -y
```

:ballot_box_with_check: Исправление поврежденных пакетов
```yaml
apt --fix-broken install
```

:ballot_box_with_check: Установка зависимостей №1
```yaml
apt-get install jq wget curl udisks2 libglib2.0-bin network-manager dbus -y
```
:ballot_box_with_check: Установка зависимостей №2
```yaml
apt install \
apparmor \
jq \
wget \
curl \
udisks2 \
libglib2.0-bin \
network-manager \
dbus \
lsb-release \
systemd-journal-remote \
systemd-resolved -y
```
После этого шага необходимо перезагрузить систему. Иначе у вас, скорее всего, возникнет ошибка "#Could not resolve host: get.docker.com" 

:ballot_box_with_check: Перезагрузка
```yaml
systemctl reboot
```
## Home Assistant:  

:ballot_box_with_check: Установка Docker    
```yaml
curl -fsSL get.docker.com | sh
```

#### Home Assistant OS-Agent  : 

:white_check_mark: [Последний релиз](https://github.com/home-assistant/os-agent/releases/latest)  

:ballot_box_with_check: Загружаем агента
```yaml
wget https://github.com/home-assistant/os-agent/releases/download/1.6.0/os-agent_1.6.0_linux_x86_64.deb
```
(номер меняем на актуальный)  
Загружаем - `wget https://github.com/home-assistant/os-agent/releases/download/1.6.0/os-agent_1.6.0_linux_x86_64.deb` (номер меняем на актуальный)    

Установка `dpkg -i os-agent_1.6.0_linux_x86_64.deb`
sudo - i должно работать
```yaml
dpkg -i os-agent_1.6.0_linux_x86_64.deb
```

#### Home Assistant Supervised : 

:ballot_box_with_check: Загружаем Home Assisistant Supervised 
```yaml
wget https://github.com/home-assistant/supervised-installer/releases/latest/download/homeassistant-supervised.deb
```
:ballot_box_with_check: Установка Home Assisistant Supervised 
```yaml
dpkg -i homeassistant-supervised.deb
```
```yaml
apt install ./homeassistant-supervised.deb
```
Возможно:
https://geekrepos.com/home-assistant/supervised-installer/issues/304

:ballot_box_with_check: Исправление поврежденных пакетов
```yaml
apt --fix-broken install
```
#### Home Assistant Разное : 

:ballot_box_with_check: Перечень контейнеров
`docker ps --format "table {{.ID}}\t{{.Image}}\t{{.Status}}\t{{.Names}}"` 

:ballot_box_with_check: Установка Bluetooth
```yaml
apt install bluez
```

:ballot_box_with_check: Перечень Bluetooth адаптеров
`hciconfig`


:ballot_box_with_check: Connect to your Debian 12 server using an SSH client such as PuTTY or the terminal. Включаем ROOT

Должно быть без # 
`PermitRootLogin yes`
```yaml
sudo nano /etc/ssh/sshd_config
```


#### После настройки HA (192.168.1.X:8123)
:ballot_box_with_check: Hacs
```yaml
wget -O - https://get.hacs.xyz | bash -
```

## SSL
:ballot_box_with_check: Файлы должны распологаться в директории SSL выше config home assistant
```yaml
privkey.pem
fullchain.pem
```
## supervisor
:ballot_box_with_check: Если глючит supervisor
```yaml
sudo docker restart hassio_supervisor
```


____
#### [Beelink GK Mini часть 2 - Autoboot, Debian 11, Supervised Home Assistant](https://youtu.be/RqW5q-0RYio)

<a href="https://www.youtube.com/channel/UCcq9onYHbs6go3kDpfBoqhg?sub_confirmation=1" target="_blank"><img src="https://raw.githubusercontent.com/kvazis/training/master/lessons/img/subscribe.png" alt="Subscribe" style="height: 71px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

#### [Beelink GK Mini на Celeron J4125 - обзор, легкая установка Home Assistant OS - пошаговая инструкция](https://youtu.be/i4bp-s20Dm8)
