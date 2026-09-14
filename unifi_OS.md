# 🛰️ UniFi OS Server в LXC на Proxmox (обход геоблокировки RU)

> Пошаговая инструкция по установке **UniFi OS Server** в privileged LXC-контейнере на Proxmox VE, включая обход геоблокировки серверов Ubiquiti для IP из России.

---

## 📋 Что понадобится

| Требование | Значение |
|---|---|
| 🖥️ Хост | Proxmox VE 9.x |
| 📦 Шаблон контейнера | Debian 12/13 |
| 🔐 Тип контейнера | **Privileged** (обязательно!) |
| 💾 Диск | 20+ ГБ |
| 🧠 RAM | 2+ ГБ (рекомендуется 4 ГБ) |
| 🌍 VPN | Обязателен — сервера `fw-update.ui.com` блокируют RU-IP (451/403) |

> ⚠️ **Важно:** UniFi OS Server официально не поддерживает **unprivileged** контейнеры — без этого Podman внутри LXC не заработает.

---

## 🧭 Почему именно OS Server, а не классический UniFi Network Application

Мы сначала пробовали классику (`.deb`-пакет) — она легче (~150 МБ) и проще, но начиная с версии **10.x** UniFi Network Application требует локальный сервис **`unifi-core`** (порт `11081`), который **не публикуется отдельным пакетом** для голого Linux — только внутри UniFi OS Server.

Официальная позиция Ubiquiti:

> *"Going forward, we recommend users upgrade to UniFi OS Server for all self-hosted deployments."*

Поэтому если ставите версию свежее — сразу берите **UniFi OS Server**, не тратьте время на классику.

---

## 🚫 Шаг 0. Обход геоблокировки

Все домены `ui.com`, `dl.ui.com`, `fw-update.ui.com`, `fw-download.ubnt.com` **блокируют IP из России** (`403`/`451`). Без VPN на **самом хосте Proxmox** ничего скачать не получится.

Варианты:
- 🔌 Поднять WireGuard/VLESS-клиент прямо на хосте Proxmox с выходом через Европу
- 🌐 Скачать файл на компьютере через VPN и залить на Proxmox вручную (см. ниже)

Проверка, что VPN реально работает на хосте:

```bash
curl -s ipinfo.io
```

Ожидаем страну **не RU** в ответе (у нас было `FI` — Финляндия, Хельсинки).

---

## 1️⃣ Скачиваем установщик UniFi OS Server

### Вариант А — напрямую на хосте Proxmox (если VPN настроен на хосте)

```bash
curl -fsSL "https://fw-update.ui.com/api/firmware-latest" -o /tmp/uos.json
apt install -y jq   # если jq ещё не стоит

UOS_URL=$(jq -r '._embedded.firmware
  | map(select(.product=="unifi-os-server"))
  | map(select(.platform=="linux-x64"))
  | sort_by(.version_major,.version_minor,.version_patch)
  | last
  | ._links.data.href' /tmp/uos.json)

echo "$UOS_URL"
curl -fsSL "$UOS_URL" -o /var/lib/vz/template/iso/unifi-os-server.iso
```

📦 Итоговый файл — **~850-900 МБ**.

### Вариант Б — скачать в браузере (через VPN) и залить вручную

1. Открой [ui.com/download](https://www.ui.com/download) через VPN → **UniFi OS Server → Linux**
2. Скачай файл на компьютер
3. В Proxmox: **Datacenter → нужный узел → local (storage) → ISO Images → Upload**
4. Загрузи скачанный файл (Proxmox сам переименует расширение в `.iso` — это нормально, содержимое не меняется)

---

## 2️⃣ Создаём privileged LXC-контейнер

В веб-интерфейсе Proxmox: **Create CT**

- Шаблон: **Debian 12/13**
- ❗ На вкладке *General* **сними галочку "Unprivileged container"**
- Диск: 20+ ГБ
- RAM: 4096 МБ (рекомендуется)
- CPU: 2-4 ядра

Либо через community-scripts (быстрее): [ProxmoxVE Debian LXC script](https://community-scripts.github.io/ProxmoxVE/scripts) → выбери **Debian**, версия **12** или **13**.

---

## 3️⃣ Пробрасываем `/dev/net/tun` и включаем nesting

Podman внутри LXC требует доступ к `/dev/net/tun` (для сетевого стека контейнеров) и включённые фичи `nesting`/`keyctl`.

На **хосте** Proxmox (замени `102` на свой CTID):

```bash
pct set 102 --features nesting=1,keyctl=1

cat >> /etc/pve/lxc/102.conf << 'EOF'
lxc.cgroup2.devices.allow: c 10:200 rwm
lxc.mount.entry: /dev/net/tun dev/net/tun none bind,create=file
EOF

pct reboot 102
```

> 💡 Пробрасывать `/dev/net/tun` через `--mp0` (mountpoint) **нельзя** — это char-device, а не блочное устройство. Именно поэтому используется `lxc.mount.entry` напрямую в конфиге.

Проверка после ребута:

```bash
pct enter 102
ls -la /dev/net/tun
```

Ожидаем: `crw-rw-rw- 1 root root 10, 200 ... /dev/net/tun`

---

## 4️⃣ Устанавливаем Podman внутри контейнера

```bash
apt update
apt install -y podman uidmap slirp4netns
```

---

## 5️⃣ Переносим установщик в контейнер и запускаем

На **хосте** Proxmox:

```bash
pct push 102 /var/lib/vz/template/iso/unifi-os-server.iso /usr/local/sbin/unifi-os-server.bin
```

Внутри **контейнера**:

```bash
pct enter 102
chmod +x /usr/local/sbin/unifi-os-server.bin
/usr/local/sbin/unifi-os-server.bin
```

Установщик сам:
- ✅ Создаст `/var/lib/uosserver/server.conf`
- ✅ Настроит systemd-сервисы
- ✅ Скачает и запустит Podman-образ `uosserver`
- ✅ Пробросит все нужные порты (9543, 8443, 8080, 8880, 8881, 8882, 3478/udp, 6789, 11084/mongo и др.)

Процесс занимает 2-5 минут. В конце появится:

```
!!! INSTALLATION COMPLETE !!!
UniFi OS Server is running at: https://<IP-контейнера>:11443/
```

---

## 🎉 Готово!

Узнать IP контейнера:

```bash
ip -4 addr show eth0 | grep inet
```

Открой в браузере:

```
https://<IP-контейнера>:11443/
```

> ⚠️ Сертификат самоподписанный — браузер предупредит, жми **"Дополнительно" → "Перейти на сайт"**.

Дальше — мастер первоначальной настройки UniFi OS: создание учётной записи, инициализация Network Application.

---

## 🩹 Возможные проблемы

<details>
<summary>❌ <code>curl: (22) The requested URL returned error: 451/403</code></summary>

Геоблокировка. VPN не активен на том узле, откуда идёт запрос (хост или контейнер). Проверь `curl -s ipinfo.io` — страна должна быть не RU.
</details>

<details>
<summary>❌ <code>mount: /dev/net/tun: Can't lookup blockdev</code></summary>

Пытаешься пробросить `/dev/net/tun` через `--mp0` — так нельзя, это char-device. Используй `lxc.mount.entry` в конфиге контейнера (см. Шаг 3).
</details>

<details>
<summary>❌ <code>Job for unifi.service failed</code> / краш-луп у классического UniFi Network</summary>

Скорее всего у вас версия 10.x классического пакета, которой нужен `unifi-core` (порт 11081) — а он не ставится отдельно на голый Linux. Решение — переходить на **UniFi OS Server** (эта инструкция).
</details>

<details>
<summary>❌ <code>bash: unifi-os-server.bin: Permission denied</code></summary>

Забыли/не сработал `chmod +x`. Повторите:
```bash
chmod +x /usr/local/sbin/unifi-os-server.bin
ls -la /usr/local/sbin/unifi-os-server.bin
```
Убедитесь, что в правах есть `x`.
</details>

---

## 📚 Источники

- [Официальная страница загрузок UniFi](https://www.ui.com/download)
- [community-scripts ProxmoxVE](https://community-scripts.github.io/ProxmoxVE/scripts)
- [Firmware API Ubiquiti](https://fw-update.ui.com/api/firmware-latest)

---

<p align="center">
  Собрано методом проб, ошибок и одного упорного вечера с VPN 🇫🇮
</p>
