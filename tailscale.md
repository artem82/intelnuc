# Установка Tailscale-клиента на Wiren Board через self-hosted Headscale

## Проблема

Прямое подключение к `tailscale.com` с Wiren Board не работает — провайдер режет TLS-соединение по SNI (DPI-блокировка). Решение: бинарник Tailscale лежит на собственном сервере (`files.artemvpn.ru`), скачивается на WB напрямую по своему домену, подключение идёт к собственному headscale-серверу.

**Требуется:**
- headscale-сервер: `hscale.artemvpn.ru`
- файл-хостинг: `files.artemvpn.ru` (уже настроен, файл `tailscale_arm64.tgz` загружен)

---

## 1. На Wiren Board — скачать бинарник со своего сервера

```bash
curl -fsSL https://files.artemvpn.ru/tailscale_arm64.tgz -o /root/tailscale_arm64.tgz
```

## 2. Распаковать архив

```bash
cd /root
tar xzf tailscale_arm64.tgz
cd tailscale_*_arm64
```

## 3. Установить бинарники

> **Важно:** systemd-юнит ищет исполняемые файлы в `/usr/sbin/`, а не `/usr/bin/`.

```bash
cp tailscale tailscaled /usr/sbin/
```

## 4. Установить и запустить systemd-сервис

```bash
cp systemd/tailscaled.service /etc/systemd/system/
cp systemd/tailscaled.defaults /etc/default/tailscaled
mkdir -p /var/lib/tailscale
systemctl daemon-reload
systemctl enable --now tailscaled
```

Проверка:

```bash
systemctl status tailscaled
```

Ожидаемый результат: `Active: active (running)`.

## 5. Подключить к своему headscale-серверу

```bash
tailscale up --login-server=https://hscale.artemvpn.ru
```

Команда выведет ключ авторизации вида:

```
hskey-authreq-XXXXXXXXXXXXXXXXXXXX
```

## 6. Зарегистрировать ноду на сервере headscale

Выполнить на сервере, где работает headscale (`msk-1-vm-o7su`):

```bash
headscale auth register --auth-id hskey-authreq-XXXXXXXXXXXXXXXXXXXX --user wirenboard
```

Если пользователь ещё не создан:

```bash
headscale users create wirenboard
```

Ожидаемый результат:

```
Node <hostname> registered
```

## 7. Проверка подключения на Wiren Board

```bash
tailscale status
tailscale ip -4
```

---

## Итог

Wiren Board подключён к приватной tailnet через self-hosted headscale, без зависимости от облака Tailscale и без блокировки DPI по SNI. Для установки на новых платах достаточно шагов 1-7 — бинарник уже лежит на `files.artemvpn.ru`, повторно скачивать и переносить его вручную через SFTP не нужно.

---

## Справочник команд Headscale

**Создание пользователя**
```bash
headscale users create <имя_пользователя>
```

**Список пользователей**
```bash
headscale users list
```

**Список устройств**
```bash
headscale nodes list
```

**Список маршрутов**
```bash
headscale nodes routes list
```

**Создание ключа предварительной авторизации**
```bash
headscale preauthkeys create --user <ID_пользователя>
```

**Переименование устройства**
```bash
headscale node rename -i <id_устройства> <новое_имя>
```

**Подтверждение Exit-Node**
```bash
headscale nodes approve-routes --identifier <id_устройства> --routes 0.0.0.0/0
```

**Подтверждение Network Routes**
```bash
headscale nodes approve-routes --identifier <id_устройства> --routes <ip_подсети>/24
```

**Подтверждение Exit-Node + Network Routes**
```bash
headscale nodes approve-routes --identifier <id_устройства> --routes 0.0.0.0/0,<ip_сети>/24
```

**Удаление устройства**
```bash
headscale nodes delete --identifier <id_устройства>
```

**Удаление пользователя**
```bash
headscale users destroy <имя_пользователя>
```

**Создание API-ключа**
```bash
headscale apikeys create --expiration 90d
```

**Список API-ключей**
```bash
headscale apikeys list
```

---

## Справочник команд Tailscale (клиент)

**Подключение к серверу**
```bash
tailscale up --login-server=https://hscale.artemvpn.ru
```

**Статус подключения**
```bash
tailscale status
```

**Свой IP в tailnet**
```bash
tailscale ip -4
```

**Отключиться от tailnet**
```bash
tailscale down
```

**Полностью выйти из аккаунта**
```bash
tailscale logout
```

**Стать exit-node**
```bash
tailscale up --login-server=https://hscale.artemvpn.ru --advertise-exit-node
```

**Раздать подсеть (subnet router)**
```bash
tailscale up --login-server=https://hscale.artemvpn.ru --advertise-routes=192.168.1.0/24
```

**Использовать чужой exit-node**
```bash
tailscale up --login-server=https://hscale.artemvpn.ru --exit-node=<ip_или_hostname>
```

**Включить SSH через tailscale**
```bash
tailscale up --login-server=https://hscale.artemvpn.ru --ssh
```

**Проверка доступности узла**
```bash
tailscale ping <hostname_или_ip>
```

**Обновить клиент**
```bash
tailscale update
```

**Перезапустить демон**
```bash
systemctl restart tailscaled
```
