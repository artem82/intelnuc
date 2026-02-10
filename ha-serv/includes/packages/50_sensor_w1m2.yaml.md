```yaml

w1m2:
   
  mqtt:

##############################
##       SENSOR             ##
##############################
    sensor:
    
        # WB_10 # 
       - name: "sensor_wb_10_temp1"
         unique_id: sensor_wb_10_temp1
         state_topic: "/devices/wb-m1w2_10/controls/External Sensor 1"
         unit_of_measurement: "°C"
         device_class: temperature
         value_template: "{{ value | round(1) }}"

       - name: "sensor_wb_10_temp2"
         unique_id: sensor_wb_10_temp2
         state_topic: "/devices/wb-m1w2_10/controls/External Sensor 2"
         unit_of_measurement: "°C"
         device_class: temperature
         value_template: "{{ value | round(1) }}"


```
