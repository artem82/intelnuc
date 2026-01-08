## PROXMOX
:ballot_box_with_check:  Proxmox WEB
```yaml
https://192.168.1.222:8006/
```

Логин пароль - `ubnt/ubnt ....`    
### Proxmox VE Helper-Scripts
:white_check_mark: **github** - [Ссылка](https://github.com/community-scripts/ProxmoxVE)    
:white_check_mark: **сайт** - [Ссылка](https://community-scripts.github.io/ProxmoxVE/)    
:ballot_box_with_check: Ссылка 1
```yaml
https://github.com/community-scripts/ProxmoxVE
```
### Ссылки на скрипты
:ballot_box_with_check:  [Proxmox VE Home Assistant OS VM скрипт](https://community-scripts.github.io/ProxmoxVE/scripts?id=haos-vm)
```yaml
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/vm/haos-vm.sh)"
```
:ballot_box_with_check:  [Proxmox UniFi Network Server](https://community-scripts.github.io/ProxmoxVE/scripts?id=unifi) 
```yaml
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/unifi.sh)"
```
### Типичная структура Proxmox:
```yaml
/var/lib/vz/              # Основная директория для хранения VM/CT
├── dump/                 # Дампы памяти
├── images/               # Диски виртуальных машин
│   ├── <VMID>/          # По VM ID
│   └── <CTID>/          # По CT ID
├── template/             # Шаблоны
└── snippets/             # Фрагменты cloud-init
```


### Распределение по умолчанию:
```yaml
root раздел - система Proxmox (обычно 20-30GB)

LVM-Thin или ZFS - основное хранилище для виртуальных машин

Дисковые образы хранятся в:

Локальное хранилище: /var/lib/vz/images/

Хранилища NFS/iSCSI/etc: в соответствующих точках монтирования
```
### Просмотр дискового пространства:
:ballot_box_with_check:   Основные команды для просмотра дискового пространства # с информацией о файловых системах
```yaml
lsblk -f
```
```yaml
lsblk -o NAME,SIZE,TYPE,MOUNTPOINT,FSTYPE
```
