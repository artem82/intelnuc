```yaml
climate:
  - name: airac_mqtt_onokom_91
    unique_id: airac_mqtt_onokom_91
    icon: mdi:air-conditioner
    modes:
      - "off"
      - "cool"
      - "fan_only"
      - "auto"
      - "heat"
    current_temperature_topic: "/devices/wb-msw-v4_53/controls/Temperature"
    temperature_command_topic: "/devices/ONOKOM-AIR-HR-1-MB-B_91/controls/Target temperature/on"
    mode_state_topic: "/devices/ONOKOM-AIR-HR-1-MB-B_91/controls/Active mode"
    mode_state_template: >-
      {% set values = { '0':'off', '1':'heat', '2':'cool', '3':'auto', '5':'fan_only'} %}
      {{ values[value] }}
    mode_command_topic: "/devices/ONOKOM-AIR-HR-1-MB-B_91/controls/Active mode/on"
    mode_command_template: >- 
      {% set values = { 'off':'0', 'heat':'1', 'cool':'2', 'auto':'3', 'fan_only':'5'} %}
      {{ values[value] }}
    initial: 23
    min_temp: 16
    max_temp: 32
    temp_step: 1.0
    fan_modes:
      - "auto"
      - "low"
      - "medium"    
      - "high" 
    fan_mode_state_topic: "/devices/ONOKOM-AIR-HR-1-MB-B_91/controls/Fan speed"
    fan_mode_state_template: >- 
      {% set values = { '0':'auto', '1':'low', '2':'medium', '3':'high'} %}
      {{ values[value] }}
    fan_mode_command_topic: "/devices/ONOKOM-AIR-HR-1-MB-B_91/controls/Fan speed/on"
    fan_mode_command_template: >- 
      {% set values = { 'auto':'0', 'low':'1', 'medium':'2', 'high':'3'} %}
      {{ values[value]}}
    retain: true
```
