https://www.mostlychris.com/installing-frigate-nvr-on-proxmox-in-an-lxc-container/

### Настройка в докере Frigate

:ballot_box_with_check: Создаем пустые файлы docker-compose.yml
```yaml
mkdir storage config && touch docker-compose.yml
```

:ballot_box_with_check: Запустить docker-compose.yml
```yaml
docker compose up -d
```

:ballot_box_with_check: Файлы настройки docker-compose.yml пример 
```yaml
version: "3.9"
services:
  frigate:
    container_name: frigate
    restart: unless-stopped
    network_mode: host
    stop_grace_period: 30s
    image: ghcr.io/blakeblackshear/frigate:stable
    volumes:
      - ./config:/config
      - ./storage:/media/frigate
      - type: tmpfs # Optional: 1GB of memory, reduces SSD/SD Card wear
        target: /tmp/cache
        tmpfs:
          size: 1000000000
    ports:
      - "8971:8971"
      - "8554:8554" # RTSP feeds

```
