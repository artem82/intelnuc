## Frigate

:ballot_box_with_check: Файлы ЗАПИСИ на диске
```yaml
/usr/share/hassio/media
```
:ballot_box_with_check: Файлы настройки CONFIG.YAML
```yaml
/usr/share/hassio/addon_configs/*frigate-fa/
```

:ballot_box_with_check: Файлы настройки CONFIG.YAML пример 
```yaml
mqtt:
  topic_prefix: frigate
  host: 192.168.100.11
  user: artem
  password: artem

  
detectors:
  coral:
    type: edgetpu
    device: usb

snapshots:
  enabled: True
  retain:
    default: 10

record:
  enabled: true
  retain:
    days: 5
    mode: all
  detections:
    retain:
      days: 5
  alerts:
    pre_capture: 1
    retain:
      days: 5
      mode: motion
objects:
  # Optional: list of objects to track from labelmap.txt (default: shown below)
  track:
    - person
    - cell phone
    - dog
    - cup
    - laptop
    - shoe
    - backpack
    - handbag
    - suitcase
    - knife
    - eye glasses
    - bottle
    - door
    - book
    - apple
detect:
  width: 1280
  height: 720
  fps: 9
  enabled: true
go2rtc:
  streams:
    dahua13door_go2rtc:
      - rtsp://admin:candel82@192.168.100.52/cam/realmonitor?channel=1&subtype=0
    dahua14door_go2rtc:
      - rtsp://admin:candel82@192.168.100.51/cam/realmonitor?channel=1&subtype=0
    hikholl_go2rtc:
      - rtsp://admin:candel82@192.168.100.110:554/ISAPI/Streaming/Channels/101
    hikholl2fl_go2rtc:
      - rtsp://admin:candel82@192.168.100.114:554/ISAPI/Streaming/Channels/101

cameras:
  dahua13door_go2rtc: # <------ Name the camera
    ffmpeg:
      inputs:
        - path: rtsp://192.168.100.11:8554/dahua13door_go2rtc
          input_args: preset-rtsp-restream
          roles:
            - detect
            - record
    detect:
      enabled: true # 
      width: 1280
      height: 720
      fps: 7
    objects:
      track:
        - person
        - cell phone
        - bottle
        - dog
        - knife
        - backpack
        - handbag
  dahua14door_go2rtc: # <------ Name the camera
    ffmpeg:
      inputs:
        - path: rtsp://192.168.100.11:8554/dahua14door_go2rtc
          input_args: preset-rtsp-restream
          roles:
            - detect
            - record
    detect:
      enabled: true # 
      width: 720
      height: 576
      fps: 6
    objects:
      track:
        - person
        - cell phone
        - backpack
        - handbag
version: 0.16-0
```
:ballot_box_with_check: Файлы настройки CONFIG.YAML пример 
```yaml
mqtt:
  topic_prefix: frigate
  enabled: true
  host: 192.168.1.10
  user: artem
  password: artem

face_recognition:
  enabled: true
lpr:
  enabled: True
  
detect:
  enabled: true
  width: 1280
  height: 720
  fps: 5

record:
  enabled: True
  retain:
    days: 3
    mode: all
  alerts:
    retain:
      days: 3
      mode: motion
  detections:
    retain:
      days: 3
      mode: motion



cameras:
  hik_c02_frigate:
    type: "lpr" # required to use dedicated LPR camera mode
    lpr:
      enabled: True
    detect:
      enabled: false
    objects:
      track: []
    ffmpeg:
      inputs:
        - path: rtsp://admin:candel82@192.168.10.52:554/Streaming/Channels/101 # <--- the name here must match the name of the camera in restream
          roles:
            - record
        - path: rtsp://admin:candel82@192.168.10.52:554/Streaming/Channels/102 # <--- the name here must match the name of the camera_sub in restream
          roles:
            - audio # <- only necessary if audio detection is enabled
            - detect
  
  kalitka: # <------ Name the camera
    enabled: true
    type: "lpr" # required to use dedicated LPR camera mode
    lpr:
      enabled: True
    record:
      enabled: false
    objects:
      track: []
    ffmpeg:
      inputs:
        - path: rtsp://192.168.1.10:8554/acuvox_s539_kalitka # <----- The stream you want to use for detection
          roles:
            - detect

  hik_in01_frigate:
    lpr:
      enabled: false
    ffmpeg:
      inputs:
        - path: rtsp://admin:candel82@192.168.10.71:554/Streaming/Channels/101 # <--- the name here must match the name of the camera in restream
          roles:
            - record
        - path: rtsp://admin:candel82@192.168.10.71:554/Streaming/Channels/102 # <--- the name here must match the name of the camera_sub in restream
          roles:
            - audio # <- only necessary if audio detection is enabled
            - detect
version: 0.16-0
```
