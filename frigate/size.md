# Frigate

:ballot_box_with_check:  Посмотреть, сколько места занимают записи по дням
### Размер записей по датам
```yaml
du -sh /media/frigate/recordings/* | sort -hr | head -20
```
### Или посмотреть общий размер
```yaml
du -sh /media/frigate/recordings/

```
### Быстрая очистка одной командой
:ballot_box_with_check: Быстрая очистка одной командой
```yaml
rm -rf /media/frigate/recordings/2026-03-31 /media/frigate/recordings/2026-04-01
```
