# intelnuc

Beelink GK Mini часть 2 - Autoboot, Debian 11, Supervised Home Assistant
Subscribe

Beelink GK Mini на Celeron J4125 - обзор, легкая установка Home Assistant OS - пошаговая инструкция
Команды и ссылки из урока:
✅ Оригинальная инструкция - Community Home Assistant Forum

✅ Официальный репозиторий Debian 11 - Загрузка образа
✅ Неофициальный репозиторий Debian 11 non-free с драйверами - Загрузка образа

✅ Удобный SSH клиент - Putty

Home Assistant:
☑️ Переход в режим root

su
☑️ Редактирование источников

nano /etc/apt/sources.list
Комментируем строку  deb cdrom:[Debian GNU/Linux ....

Ctrl X - для выхода
Y для сохранения

☑️ Установка sudo

apt install sudo
☑️ Добавление пользователя в sudo

sudo usermod -aG sudo username
☑️ Выход из учетной записи root

exit
☑️ Выполнение команд с правами root

sudo -i
☑️ Обновление списка пакетов и установка обновлений

apt update && sudo apt upgrade -y && sudo apt autoremove -y
☑️ Исправление поврежденных пакетов

apt --fix-broken install
☑️ Установка зависимостей

apt-get install jq wget curl udisks2 libglib2.0-bin network-manager dbus -y
☑️ Установка Docker

curl -fsSL get.docker.com | sh
☑️ Установка OS-Agent
✅ Последний релиз
Загружаем - wget https://github.com/home-assistant/os-agent/releases/download/1.4.1/os-agent_1.4.1_linux_x86_64.deb (номер меняем на актуальный)
Установка - dpkg -i os-agent_1.4.1_linux_x86_64.deb

☑️ Установка Home Assisistant Supervised
Загружаем - wget https://github.com/home-assistant/supervised-installer/releases/latest/download/homeassistant-supervised.deb
Установка - dpkg -i homeassistant-supervised.deb

☑️ Перечень контейнеров docker ps --format "table {{.ID}}\t{{.Image}}\t{{.Status}}\t{{.Names}}"

☑️ Установка Bluetooth apt install bluez

☑️ Перечень Bluetooth адаптеров hciconfig
