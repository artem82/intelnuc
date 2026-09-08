# Установка Tailscale-клиента на Wiren Board через self-hosted Headscale

## Проблема

Прямое подключение к `tailscale.com` с Wiren Board не работает — провайдер режет TLS-соединение по SNI (DPI-блокировка). Решение: скачать бинарники на другом сервере с открытым интернетом, перенести на WB вручную, подключить к собственному headscale-серверу.

**Требуется:**
- Работающий headscale-сервер (в примере — `hscale.artemvpn.ru`)
- Любой Linux-сервер с открытым интернетом для скачивания бинарников
- SFTP/SCP доступ для переноса файла на WB

---

## 1. Скачать бинарник на сервере с рабочим интернетом

Проверить актуальную версию и архитектуру на https://pkgs.tailscale.com/stable/#static (для Wiren Board — `arm64`).

```bash
curl -fsSL https://pkgs.tailscale.com/stable/tailscale_1.102.3_arm64.tgz -o /root/tailscale_arm64.tgz
```

## 2. Перенести файл на Wiren Board

Через SFTP/SCP скопировать `tailscale_arm64.tgz` в `/root/` на WB.

Вариант через `scp` напрямую (если есть доступ между серверами):

```bash
scp root@<сервер-с-файлом>:/root/tailscale_arm64.tgz /root/
```

## 3. На Wiren Board — распаковать архив

```bash
cd /root
tar xzf tailscale_arm64.tgz
cd tailscale_*_arm64
```

## 4. Установить бинарники

> **Важно:** systemd-юнит ищет исполняемые файлы в `/usr/sbin/`, а не `/usr/bin/`.

```bash
cp tailscale tailscaled /usr/sbin/
```

## 5. Установить и запустить systemd-сервис

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

## 6. Подключить к своему headscale-серверу

```bash
tailscale up --login-server=https://hscale.artemvpn.ru
```

Команда выведет ключ авторизации вида:

```
hskey-authreq-XXXXXXXXXXXXXXXXXXXX
```

## 7. Зарегистрировать ноду на сервере headscale

Выполнить на сервере, где работает headscale:

```bash
# создать пользователя (если ещё не создан)
headscale users create wirenboard

# зарегистрировать ноду, подставив свой auth-id
headscale auth register --auth-id hskey-authreq-XXXXXXXXXXXXXXXXXXXX --user wirenboard
```

Ожидаемый результат:

```
Node <hostname> registered
```

## 8. Проверка подключения на Wiren Board

```bash
tailscale status
tailscale ip -4
```

---

## Итог

Wiren Board подключён к приватной tailnet через self-hosted headscale — без зависимости от облака Tailscale и без блокировки DPI по SNI.
