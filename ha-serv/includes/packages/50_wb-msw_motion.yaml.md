```yaml
# Заводим многофункциональный датчик
# Тут мы обрабатываем данные и делаем бинарные сенсоры с числовых датчиков wb-msw
# Делаем сенсоры движения
# Два сенсора от 50/100 и от 300 чувствительности движение
# Иногда нужно делать 100, так как на датчик попадает солнце
msw:
  template:
    binary_sensor:
  
# group
      - name: "wb_motion_all_devices_norm"
        unique_id: wb_motion_all_devices_norm
        state: "{{is_state('group.wb_motion_all_devices_norm', 'on')}}"
        device_class: motion
        icon: mdi:motion-sensor
      
# ****************************************************************     

    
# ****************************************************************    
  # Детская 1  -11
      - name: "wb_motion_11_norm"
        unique_id: wb_motion_11_norm
        state: "{{states('sensor.sensor_wb_11_motion_max')|int > 100}}"
        device_class: motion
        icon: mdi:motion-sensor
        availability: "{{ states('sensor.sensor_wb_11_motion_max') }}"
        
      - name: "wb_motion_11_high"
        unique_id: wb_motion_11_high
        state: "{{states('sensor.sensor_wb_11_motion_max')|int > 300}}"
        device_class: motion
        availability: "{{ states('sensor.sensor_wb_11_motion_max') }}"
        
  # Детская 2  -12
      - name: "wb_motion_12_norm"
        unique_id: wb_motion_12_norm
        state: "{{states('sensor.sensor_wb_12_motion_max')|int > 100}}"
        device_class: motion
        icon: mdi:motion-sensor
        availability: "{{ states('sensor.sensor_wb_12_motion_max') }}"
        
      - name: "wb_motion_12_high"
        unique_id: wb_motion_12_high
        state: "{{states('sensor.sensor_wb_12_motion_max')|int > 300}}"
        device_class: motion
        availability: "{{ states('sensor.sensor_wb_12_motion_max') }}"

```
        state: "{{states('sensor.sensor_wb_12_motion_max')|int > 300}}"
        device_class: motion
        availability: "{{ states('sensor.sensor_wb_12_motion_max') }}"
