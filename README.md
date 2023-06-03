### [Beelink GK Mini часть 2 - Autoboot, Debian 11, Supervised Home Assistant](https://youtu.be/RqW5q-0RYio)

<a href="https://www.youtube.com/channel/UCcq9onYHbs6go3kDpfBoqhg?sub_confirmation=1" target="_blank"><img src="https://raw.githubusercontent.com/kvazis/training/master/lessons/img/subscribe.png" alt="Subscribe" style="height: 71px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

### [Beelink GK Mini на Celeron J4125 - обзор, легкая установка Home Assistant OS - пошаговая инструкция](https://youtu.be/i4bp-s20Dm8)
### [Установка Ubuntu 20.04 LTS и Home Assistant Supervised на мини пк GK3V. Проще, удобнее, красивее](https://www.youtube.com/watch?v=6l8swO5H-9s)


#### Команды и ссылки из урока:    

:white_check_mark: **Оригинальная инструкция** - [Community Home Assistant Forum](https://community.home-assistant.io/t/installing-home-assistant-supervised-on-debian-11/200253#installing-home-assistant-supervised-on-debian-11-1)    

:white_check_mark: **Официальный репозиторий Debian 11** - [Загрузка образа](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/)    
:white_check_mark: **Неофициальный репозиторий Debian 11 non-free с драйверами** - [Загрузка образа](https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/11.5.0+nonfree/amd64/iso-dvd/)    

:white_check_mark: **Удобный SSH клиент** - [Putty](https://www.putty.org/)    

### Home Assistant:    

:ballot_box_with_check: Переход в режим root    
```yaml
su
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

:ballot_box_with_check: Установка зависимостей
```yaml
apt-get install jq wget curl udisks2 libglib2.0-bin network-manager dbus -y
```

:ballot_box_with_check: Установка Docker    
```yaml
curl -fsSL get.docker.com | sh
```

:ballot_box_with_check: Установка OS-Agent    
:white_check_mark: [Последний релиз](https://github.com/home-assistant/os-agent/releases/latest)    
Загружаем - `wget https://github.com/home-assistant/os-agent/releases/download/1.5.1/os-agent_1.5.1_linux_x86_64.deb` (номер меняем на актуальный)    
Установка - `dpkg -i os-agent_1.5.1_linux_x86_64.deb`  

:ballot_box_with_check: Установка Home Assisistant Supervised    
Загружаем - `wget https://github.com/home-assistant/supervised-installer/releases/latest/download/homeassistant-supervised.deb`    
Установка - `dpkg -i homeassistant-supervised.deb`  

:ballot_box_with_check: Исправление поврежденных пакетов
```yaml
apt --fix-broken install
```

:ballot_box_with_check: Перечень контейнеров
`docker ps --format "table {{.ID}}\t{{.Image}}\t{{.Status}}\t{{.Names}}"` 


:ballot_box_with_check: Установка Bluetooth
`apt install bluez`

:ballot_box_with_check: Перечень Bluetooth адаптеров
`hciconfig`

:ballot_box_with_check: Иногда необходимо вовсе отключить на Debian любые энергосберегающие функции (сон, гибернация, гибридный сон и т.п.), тогда пригодится следующая команда.
```yaml
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
:ballot_box_with_check: Hacs
```yaml
wget -O - https://get.hacs.xyz | bash -
```
## ZIGBE2MQTT
:ballot_box_with_check: Команда показать текущие USB устройства
```yaml
lsusb
```

### [ZIGBEE2MQTT инструкция](https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)
### [HYPERION install](https://docs.hyperion-project.org/en/user/Installation.html#rpi-debian-ubuntu)
#### WIREGUARD
:ballot_box_with_check: wireguard-install
```yaml
wget https://git.io/wireguard -O wireguard-install.sh && bash wireguard-install.sh
```

____

