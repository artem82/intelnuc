  
# HOME ASSISTANT Amlogic S912
:white_check_mark: **Инструкция 1** - [Community Home Assistant Forum](https://gist.github.com/saper-2/544928b61060d4847cf5617641d876ab)    
:white_check_mark: **Инструкция 2** - [Community Home Assistant Forum](https://community.home-assistant.io/t/installing-home-assistant-supervised-on-a-raspberry-pi-with-debian-11/247116)


:white_check_mark: **Официальный репозиторий Debian 11** - [Загрузка образа](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/)    
:white_check_mark: **Неофициальный репозиторий ARMBIAN S912 ophub** - [Загрузка образа bullseye](https://github.com/ophub/amlogic-s9xxx-armbian)

`https://github.com/ophub/amlogic-s9xxx-armbian/releases/download/Armbian_bullseye_save_2023.05/Armbian_23.05.0_amlogic_s912_bullseye_6.1.30_server_2023.05.26.img.gz`

:white_check_mark: **Удобный SSH клиент** - [Putty](https://www.putty.org/)    
### ARMBIAN
:ballot_box_with_check: репозиторий ARMBIAN amlogic ophub
```yaml
https://github.com/ophub/amlogic-s9xxx-armbian
```

## Home Assistant:    

Путь - `/usr/share/hassio/homeassistant ....`    

:ballot_box_with_check: Установка sudo       
```yaml
apt install sudo
```

:ballot_box_with_check: Добавление пользователя в sudo   
```yaml
sudo usermod -aG sudo username
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
```yaml
sudo apt search apparmor | grep apparmor
```

#### Docker :
:ballot_box_with_check: Установка Docker    
```yaml
curl -fsSL get.docker.com | sh
```
:ballot_box_with_check: Добавление пользователя в DOCKER  
Чтобы не было ошибки permission denied unix:///var/run/docker.sock необходимо добавить текущего пользователя в группу и назначить права на docker.sock: 
```yaml
sudo usermod -aG docker root
```
```yaml
sudo chmod 666 /var/run/docker.sock
```
#### Home Assistant OS-Agent : 
:ballot_box_with_check: Установка OS-Agent    
:white_check_mark: [Последний релиз](https://github.com/home-assistant/os-agent/releases/latest)  

:ballot_box_with_check: Загружаем агента
```yaml
wget https://github.com/home-assistant/os-agent/releases/download/1.6.0/os-agent_1.6.0_linux_aarch64.deb
```
(номер меняем на актуальный)  
 
Установка - `dpkg -i os-agent_1.6.0_linux_aarch64.deb`  

#### Home Assistant Supervised : 
:ballot_box_with_check: Загружаем Home Assisistant Supervised 
```yaml
wget https://github.com/home-assistant/supervised-installer/releases/latest/download/homeassistant-supervised.deb
```
:ballot_box_with_check: Установка Home Assisistant Supervised 
```yaml
dpkg -i homeassistant-supervised.deb
```

:ballot_box_with_check: Исправление поврежденных пакетов
```yaml
apt --fix-broken install
```
ВЫБИРАЕМ - `odroid c2`

#### Home Assistant Разное : 

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



____


