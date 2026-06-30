:ballot_box_with_check: Файлы настройки Advanced Camera Card
```yaml
type: custom:advanced-camera-card        # тип карточки — указываем кастомную карту Advanced Camera Card
cameras:                                 # начало списка камер в карточке (можно несколько)
  - id: hik_i11                          # произвольный ID камеры внутри карточки, просто метка для внутренних ссылок
    title: Камера 101 (Hikvision)        # заголовок, показывается в меню/шапке карточки
    live_provider: go2rtc                # откуда брать живое видео — через go2rtc (а не через HA-сущность напрямую)
    go2rtc:                              # настройки для go2rtc-провайдера
      stream: hik_i11_main               # имя потока из go2rtc.streams в frigate.yml — реальный источник видео
    frigate:                             # привязка камеры к Frigate (обязательно для events/engine!)
      camera_name: hik_i11_frigate       # имя камеры как в frigate.yml -> cameras: (НЕ entity_id и НЕ id выше)
live:                                    # глобальные настройки живого вида (общие для всех камер карточки)
  preload: true                          # грузить поток заранее, до того как карточка попадёт в зону видимости
  zoomable: false                        # запрещает зум/пан жестами на видео
```
:ballot_box_with_check: Файлы настройки Advanced Camera Card
```yaml
type: custom:advanced-camera-card
cameras:
  - id: hik_i11
    title: Камера 101 (Hikvision)
    live_provider: go2rtc
    go2rtc:
      stream: hik_i11_main
    frigate:
      camera_name: hik_i11_frigate
view:
  default: live
  triggers:
    actions:
      interaction_mode: all
menu:
  buttons:
    snapshots:
      enabled: false
    timeline:
      enabled: false
live:
  controls:
    thumbnails:
      mode: below
      size: 100
      media_type: events
      events_media_type: clips
      show_details: true
      show_favorite_control: true
      show_download_control: true
      show_timeline_control: false
media_viewer:
  controls:
    thumbnails:
      mode: below
      size: 100
      show_details: true
      show_timeline_control: false

```
