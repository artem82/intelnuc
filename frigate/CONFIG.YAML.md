:ballot_box_with_check: Файлы настройки CONFIG.YAML пример Кирилла работает отлично
```yaml
mqtt:
  topic_prefix: frigate
  host: 192.168.1.10
  user: artem
  password: artem

cameras:
  dahua:                     # <------ Name the camera
    enabled: true
    ffmpeg:
      inputs:
        - path: 
            rtsp://admin:candel82@192.168.1.50:554/ISAPI/Streaming/channels/101     # <----- The stream you want to use for detection
          roles:
            - detect        # Роль: детектирование объектов
            - record
            - audio
    detect:                 # Настройки обнаружения объектов
      enabled: true         # Включение функции обнаружения объектов
      width: 1280           # Ширина видео для анализа. Чем выше разрешение, тем больше нагрузка на процессор.
      height: 720           # высота
      fps: 5                # Частота кадров для анализа. Увеличение FPS значительно повышает нагрузку на процессор.
    objects:
      track:  # Список объектов, которые будут отслеживаться
        - person     # Отслеживание людей
        - cell phone
        - bottle
        - cat        # Отслеживание кошек
        - dog        # Отслеживание собак
        - backpack   # Отслеживание рюкзаков
        - umbrella   # Отслеживание зонтов

##### Конфигурация записи, сколько хранить
    motion:
      threshold: 25
      contour_area: 10
      improve_contrast: true
record:                                    ## Основной блок настроек записи видео
  enabled: true                            # Включает запись видео (если false – записи не будут вестись)
  detections:                              # Настройки для записей, связанных с детекцией объектов или событий
    retain:
      days: 3
      mode: motion
  alerts:                                  ## Настройки для тревожных событий (например, при срабатывании датчиков движения)
    pre_capture: 1
    retain:                                # Параметры хранения тревожных клипов
      days: 3                              # Хранить тревожные записи 30 дней
      mode: motion                         # Записывать только события, где обнаружено движение (обычно актуально для оповещений)
detect:
  enabled: true
version: 0.17-0
```
