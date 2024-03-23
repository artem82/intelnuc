
## LINUX подготовка и красота


#### Команды и ссылки из урока:    

:white_check_mark: **Оригинальная инструкция** - [Community Home Assistant Forum](https://community.home-assistant.io/t/installing-home-assistant-supervised-on-debian-11/200253#installing-home-assistant-supervised-on-debian-11-1)   
:white_check_mark: **Официальный репозиторий Debian 12** - [Загрузка образа](https://cdimage.debian.org/cdimage/unofficial/non-free/firmware/bookworm/12.0.0/)   
:white_check_mark: **Официальный репозиторий Debian 11** - [Загрузка образа](https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/)      

:white_check_mark: **Удобный SSH клиент** - [Putty](https://www.putty.org/)    

### Измените приглашение Bash в Linux:    
Чтобы изменить приглашение bash навсегда, мы можем отредактировать файл ~/.bashrc и изменить значения PS1. Для редактирования этого файла вы можете использовать любой редактор, но в этом руководстве мы используем nano editor, потому что он прост в использовании. Теперь, чтобы открыть файл ~/.bashrc, используйте следующую команду:
```yaml
nano ~/.bashrc
```

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

