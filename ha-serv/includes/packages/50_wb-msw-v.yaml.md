```yaml
# Заводим многофункциональный датчик
# Тут мы получаем все данные с датчиков wirenboard wb-msw-v


# Детская 1  -11
# Детская 2  -12
# Гостевая   -13
# Спортзал   -14
# Стол SPA   -15
# Серверная  -16 коридор
# Кабинет    -17
# Столовая   -18
# Спальня    -19
# Входная группа -20
# Гараж      -21
# Спа коридор-22

wbmswv:
   
  mqtt:

#######################
##      SENSOR       ##
#######################
    sensor:
      
        # WB_11 # детская 1
       - name: "sensor_wb_11_temp"
         state_topic: "/devices/wb-msw-v3_11/controls/Temperature"
         unit_of_measurement: "°C"
         device_class: temperature
       - name: "sensor_wb_11_humidity"
         state_topic: "/devices/wb-msw-v3_11/controls/Humidity"
         value_template: "{{ value | round(0) }}"
         device_class: humidity
         unit_of_measurement: "%"
       - name: "sensor_wb_11_soundlevel"
         state_topic: "/devices/wb-msw-v3_11/controls/Sound Level"
         value_template: "{{ value | round(0) }}"
         device_class: sound_pressure
         unit_of_measurement: "dB"
       - name: "sensor_wb_11_illuminance"
         state_topic: "/devices/wb-msw-v3_11/controls/Illuminance"
         value_template: "{{ value | round(0) }}"
         device_class: illuminance
         unit_of_measurement: "lx"
       - name: "sensor_wb_11_motion_current"
         state_topic: "/devices/wb-msw-v3_11/controls/Current Motion"
         icon: mdi:motion-sensor
       - name: "sensor_wb_11_motion_max"
         state_topic: "/devices/wb-msw-v3_11/controls/Max Motion"
         icon: mdi:motion-sensor

        # WB_19 # мастерспальня co2
       - name: "sensor_wb_19_temp"
         state_topic: "/devices/wb-msw-v3_19/controls/Temperature"
         unit_of_measurement: "°C"
         device_class: temperature
       - name: "sensor_wb_19_humidity"
         state_topic: "/devices/wb-msw-v3_19/controls/Humidity"
         value_template: "{{ value | round(0) }}"
         device_class: humidity
         unit_of_measurement: "%"
       - name: "sensor_wb_19_soundlevel"
         state_topic: "/devices/wb-msw-v3_19/controls/Sound Level"
         value_template: "{{ value | round(0) }}"
         device_class: sound_pressure
         unit_of_measurement: "dB"
       - name: "sensor_wb_19_illuminance"
         state_topic: "/devices/wb-msw-v3_19/controls/Illuminance"
         value_template: "{{ value | round(0) }}"
         device_class: illuminance
         unit_of_measurement: "lx"
       - name: "sensor_wb_19_motion_current"
         state_topic: "/devices/wb-msw-v3_19/controls/Current Motion"
         icon: mdi:motion-sensor
       - name: "sensor_wb_19_motion_max"
         state_topic: "/devices/wb-msw-v3_19/controls/Max Motion"   
         icon: mdi:motion-sensor
       - name: "sensor_wb_19_co2"
         state_topic: "/devices/wb-msw-v3_19/controls/CO2" 
         device_class: carbon_dioxide
         unit_of_measurement: "ppm"
```
