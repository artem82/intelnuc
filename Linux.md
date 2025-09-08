
## LINUX подготовка и красота

:white_check_mark: **Удобный SSH клиент** - [Putty](https://www.putty.org/)    

### Измените приглашение Bash в Linux:    
Чтобы изменить приглашение bash навсегда, мы можем отредактировать файл ~/.bashrc и изменить значения PS1. Для редактирования этого файла вы можете использовать любой редактор, но в этом руководстве мы используем nano editor, потому что он прост в использовании. Теперь, чтобы открыть файл ~/.bashrc, используйте следующую команду:
```yaml
nano ~/.bashrc
```

:ballot_box_with_check: Строка для зеленого цвета    
```yaml
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
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

### Поиск и удаление ненужных файлов в Linux / MacOS
:ballot_box_with_check: Установка
```yaml
sudo apt install ncdu
```
Сканировать корневой каталог (всю систему):
```yaml
sudo ncdu /
```
### Внешний диск в Linux / MacOS
```yaml
sudo fdisk -l
```
```yaml
sudo mkdir /mnt/ssd
```
```yaml
sudo mount /dev/sdb1 /mnt/ssd

```
:ballot_box_with_check: форматирование раздела /dev/sdb1 в файловую систему ext4: 
```yaml
sudo mkfs.ext4 /dev/sdb1
```
