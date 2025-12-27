```yaml
##################################
####    YANDEX SMART HOME     ####
##################################

################
##   ФИЛЬТР   ##
################
  filter:
    #exclude_domains:
    #  - sensor
    #  - binary_sensor
    include_domains:   #ВКЛЮЧЕНО
      - light
      - switch
    include_entity_globs:   #ВКЛЮЧЕНО
      - binary_sensor.contact_*
      - sensor.temp_hum_*_temperature
      - sensor.temp_hum_*_humidity
      - script.apple_tv_open_*
    include_entities:
      - media_player.oled_tv_s9
      - light.wledlamp
      - media_player.denon_avr_x2800h
      - sensor.temp_hum_balcony_humidity
      - sensor.temp_hum_bathroom_humidity
      - sensor.temp_hum_bedroom_lcd_humidity
    exclude_entities:
      - switch.fingerbot_reverse
    exclude_entity_globs:    #ВЫКЛЮЧЕНО
      - binary_sensor.temp_hum*humidity
      - binary_sensor.iphone*
      - switch.cell_3c_38d7_headerdetect
      - switch.cell*
      - switch.espresense*
      - sensor.weather_*
      - switch.wled*
      - switch*sync*
      - switch.*reverse*
      - switch.r4s_gate*
      - switch.switch
      - switch.nuc*
      - switch.p1s*
      - switch.zigbee2mqtt*
      - media_player.yandex*
      - nspanel*
      - switch.dahuacam*
      - light.dahuacam*
      - light.p1s*
      - switch.fingerbot_*
##################
##  УСТРОЙСТВА  ##
##################

  entity_config:
    light.wled_soundreactive:
      name: Елка
      room: Спальня    
    media_player.oled_tv_s9:
      name: Телевизор
      room: Спальня
      type: devices.types.media_device.tv
    switch.sw_bedroom_left:
      name: Подсветка спальни
      room: Спальня
      type: devices.types.light
#      type: devices.types.switch
    switch.sw_bedroom_right:
      name: Люстра
      room: Спальня
      type: devices.types.light
#
    switch.sw_corridor_left:
      name: Зеркало
      room: Коридор 
      type: devices.types.light
    switch.sw_corridor_right:
      name: Основной свет
      room: Коридор
      type: devices.types.light
#      
    switch.sw_kitchen:
      name: Основной свет
      room: Кухня
      type: devices.types.light
      
    light.tv65light:
      name: Подсветка телевизора
      room: Спальня
      type: devices.types.switch
#    light.wled_table:
#      name: Подсветка тумбочки
#      room: Спальня
#      type: devices.types.switch
# Датчики      
    binary_sensor.contact_door_contact:
      name: Дверь входная
      room: Коридор
      type: devices.types.openable
    binary_sensor.contact_fridge_contact:
      name: Холодильник
      room: Коридор
      type: devices.types.openable
    binary_sensor.contact_child_contact:
      name: Дверь детская
      room: Детская
      type: devices.types.openable
      
    light.rabbit_hue:
      name: Заяц
      room: Спальня
      type: devices.types.switch
      
    sensor.temp_hum_balcony_temperature:
      name: Температура
      room: Балкон
      type: devices.types.sensor
    sensor.temp_hum_balcony_humidity:
      name: Влажность
      room: Балкон
      type: devices.types.sensor    
    sensor.temp_hum_bathroom_temperature: 
      name: Температура
      room: Ванная
      type: devices.types.sensor
    sensor.temp_hum_bathroom_humidity:
      name: Влажность
      room: Ванная
      type: devices.types.sensor     
    sensor.temp_hum_bedroom_lcd_temperature:
      name: Температура
      room: Спальня
      type: devices.types.sensor
    sensor.temp_hum_bedroom_lcd_humidity:
      name: Влажность
      room: Спальня
      type: devices.types.sensor

```  
      
      
      
      
      
      
      
      
      
      
      
      
