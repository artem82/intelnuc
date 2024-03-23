### [Beelink GK Mini часть 2 - Autoboot, Debian 11, Supervised Home Assistant](https://youtu.be/RqW5q-0RYio)

<a href="https://www.youtube.com/channel/UCcq9onYHbs6go3kDpfBoqhg?sub_confirmation=1" target="_blank"><img src="https://raw.githubusercontent.com/kvazis/training/master/lessons/img/subscribe.png" alt="Subscribe" style="height: 71px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

### [Beelink GK Mini на Celeron J4125 - обзор, легкая установка Home Assistant OS - пошаговая инструкция](https://youtu.be/i4bp-s20Dm8)
### [Установка Ubuntu 20.04 LTS и Home Assistant Supervised на мини пк GK3V. Проще, удобнее, красивее](https://www.youtube.com/watch?v=6l8swO5H-9s)


#### Команды и ссылки из урока:    

:white_check_mark: **Оригинальная инструкция** - [Community Home Assistant Forum](https://community.home-assistant.io/t/installing-home-assistant-supervised-on-debian-11/200253#installing-home-assistant-supervised-on-debian-11-1)   
:white_check_mark: **Официальный репозиторий Debian 12** - [Загрузка образа](https://cdimage.debian.org/cdimage/unofficial/non-free/firmware/bookworm/12.0.0/)   
:white_check_mark: **Официальный репозиторий Debian 11** - [Загрузка образа](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/)      

:white_check_mark: **Удобный SSH клиент** - [Putty](https://www.putty.org/)    

## LINUX:    
/usr/share/hassio/homeassistant

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

