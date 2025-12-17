```yaml

'switch_turnoffall':
  alias: Выключить ВЫКЛЮЧАТЕЛИ во всей квартире
  sequence:
  - service: switch.turn_off
    data: {}
    target:
      entity_id: all
  mode: single
  icon: mdi:lightbulb-group-off-outline
  

'light_turnoffall':
  alias: Выключить СВЕТ во всей квартире
  sequence:
  - service: light.turn_off
    data: {}
    target:
      entity_id: all
  mode: single
  icon: mdi:lightbulb-group-off-outline

```
