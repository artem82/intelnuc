```yaml
##############################################
###      При старте HA Делаем Группы
#############################################

# ВЕНТИЛЯТОРЫ
- alias: "Create Group FAN"
  trigger:
    - platform: homeassistant
      event: start
  action:
    - service: group.set
      data:
        object_id: fan_wb_fan_devices
        entities: > 
           {{states.fan
              | selectattr('entity_id', 'search', 'fan.wb_fan') 
              | map(attribute='entity_id') 
              | list}}

# 1 Этаж
# ОСВЕЩЕНИЕ РЕЛЕ
- alias: "Create Group Lights WB_MR"
  trigger:
    - platform: homeassistant
      event: start
  action:
    - service: group.set
      data:
        object_id: light_wb_mr_devices
        entities: > 
           {{states.light
              | selectattr('entity_id', 'search', 'light.wb_mr') 
              | map(attribute='entity_id') 
              | list}}
              
- alias: "Create Group Lights WB_LED"
  trigger:
    - platform: homeassistant
      event: start
  action:
    - service: group.set
      data:
        object_id: light_wb_led_devices
        entities: > 
           {{states.light
              | selectattr('entity_id', 'search', 'light.wb_led') 
              | map(attribute='entity_id') 
              | list}}
              
- alias: "Create Group Lights WB_MIRROR"
  trigger:
    - platform: homeassistant
      event: start
  action:
    - service: group.set
      data:
        object_id: light_wb_mirror_devices
        entities: > 
           {{states.light
              | selectattr('entity_id', 'search', 'light.wb_mirror') 
              | map(attribute='entity_id') 
              | list}}
              
# ручные допы              
- alias: "Create Group Lights ALL"
  trigger:
    - platform: homeassistant
      event: start
  action:
    - service: group.set
      data:
        object_id: light_all_devices
        add_entities:
          - group.light_wb_led_devices
          - group.light_wb_mr_devices
          
          
# Все датчики движения
- alias: "Create Group MOTION High"
  trigger:
    - platform: homeassistant
      event: start
  action:
    - service: group.set
      data:
        object_id: motion_all_devices_high
        entities: > 
           {{states.binary_sensor
              | selectattr('entity_id', 'search', 'high') 
              | map(attribute='entity_id') 
              | list}}

```
```yaml
- alias: "Create MQTT Topic"
  trigger:
    - platform: homeassistant
      event: start
  action:
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_11/controls/Max Motion Time
      payload: 0
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_12/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_13/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_14/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_15/controls/Max Motion Time
      payload: 0
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_16/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_17/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_18/controls/Max Motion Time
      payload: 0    
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_19/controls/Max Motion Time
      payload: 0
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_20/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_21/controls/Max Motion Time
      payload: 0  
  - service: mqtt.publish
    data:
      qos: 0
      retain: false
      topic: /devices/wb-msw-v3_22/controls/Max Motion Time
      payload: 0    
  
```  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
