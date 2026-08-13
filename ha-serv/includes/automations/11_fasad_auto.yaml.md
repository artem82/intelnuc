
# АВТОМАТИЗАЦИИ 
# ВКЛЮЧЕНИЕ ФАСАДА
# https://apps.timwhitlock.info/emoji/tables/unicode

# ВКЛЮЧЕНИЕ по ЗАКАТУ (работает и летом, и зимой)
- alias: AUTO. Fasad ON
  id: AUTO. Fasad ON
  description: "Включение фасадной подсветки"
  mode: single
  trigger:
    - platform: sun
      event: sunset
      offset: "-00:10:00"
  condition: []
  action:
    - service: switch.turn_on
      target:
        entity_id: group.light_architect
    - service: tts.yandex_station_say
      entity_id: media_player.yandex_station_x11vhs700ctgck
      data:
        message: Включила архитектурную подсветку
        options:
          volume_level: 0.4
          

# ВЫКЛЮЧЕНИЕ в 1:00 НОЧИ (только зимой)
- alias: AUTO. Fasad OFF WIN 1am
  id: AUTO. Fasad OFF WIN 1am
  description: "Выключение фасадной подсветки в 1 утра зимой"
  mode: single
  triggers:
    - trigger: time_pattern
      hours: "1"
      minutes: "00"
  conditions:
    - condition: state
      entity_id: input_select.mode_year
      state: зима
  actions:
    - service: switch.turn_off
      target:
        entity_id: group.light_architect

# ВЫКЛЮЧЕНИЕ в 00:30 (только летом)
- alias: AUTO. Fasad OFF SUM 00_30am
  id: AUTO. Fasad OFF SUM 00_30am
  description: "Выключение фасадной подсветки в 00:30 летом"
  mode: single
  triggers:
    - trigger: time_pattern
      hours: "0"
      minutes: "30"
  conditions:
    - condition: state
      entity_id: input_select.mode_year
      state: лето
  actions:
    - service: switch.turn_off
      target:
        entity_id: group.light_architect
        
# ВКЛЮЧЕНИЕ в 6:00 УТРА (только зимой)
- alias: AUTO. Fasad ON WIN 6am
  id: AUTO. Fasad ON WIN 6am
  description: "Включение фасадной подсветки в 6 утра зимой"
  mode: single
  triggers:
    - trigger: time_pattern
      hours: "6"
      minutes: "00"
  conditions:
    - condition: state
      entity_id: input_select.mode_year
      state: зима
  actions:
    - service: switch.turn_on
      target:
        entity_id: group.light_architect

          
# ВЫКЛЮЧЕНИЕ на РАССВЕТЕ (только если горит, работает для всех сезонов)
- alias: AUTO. Fasad OFF
  id: AUTO. Fasad OFF
  description: "Выключение фасадной подсветки при рассвете"
  mode: single
  trigger:
    - platform: sun
      event: sunrise
  condition:
    - condition: state
      entity_id: group.light_architect
      state: "on"
  action:
    - service: switch.turn_off
      target:
        entity_id: group.light_architect
          
          
          
