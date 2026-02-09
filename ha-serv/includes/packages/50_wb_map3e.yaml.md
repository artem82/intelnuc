# Cбор данных с контроллера посредством wb-map3e

wb_map3e:
######################## MQTT #############################################################
    mqtt: 
      sensor:
#######################
##  ЕЛЕКТРИЧЕСТВО    ##
#######################


# Фаза 1
      - name: "electro_volt_l1"
        unique_id: electro_volt_l1
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Urms L1"
        device_class: voltage
        unit_of_measurement: 'V'
        value_template: "{{ value|round(0) }}"
# Фаза 2    
      - name: "electro_volt_l2"
        unique_id: electro_volt_l2
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Urms L2"
        value_template: "{{ value|round(0) }}"
        device_class: voltage
        unit_of_measurement: 'V'    
# Фаза 3    
      - name: "electro_volt_l3"
        unique_id: electro_volt_l3
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Urms L3"
        device_class: voltage
        unit_of_measurement: 'V'    
        value_template: "{{ value|round(0) }}"

# ТОК входной
      - name: "electro_curent_l1"
        unique_id: electro_curent_l1
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Irms L1"
        device_class: current
        unit_of_measurement: 'A'
        value_template: "{{ value|round(1) }}"
    
      - name: "electro_curent_l2"
        unique_id: electro_curent_l2
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Irms L2"
        device_class: current
        unit_of_measurement: 'A'
        value_template: "{{ value|round(1) }}"

      - name: "electro_curent_l3"
        unique_id: electro_curent_l3
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Irms L3"
        device_class: current
        unit_of_measurement: 'A'
        value_template: "{{ value|round(1) }}"

# МОЩНОСТЬ входная
      - name: "electro_power_l1"
        unique_id: electro_power_l1
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/P L1"
        device_class: power
        unit_of_measurement: 'W'
        value_template: "{{ value|round(0) }}"
    
      - name: "electro_power_l2"
        unique_id: electro_power_l2
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/P L2"
        device_class: power
        unit_of_measurement: 'W'
        value_template: "{{ value|round(0) }}" 


      - name: "electro_power_l3"
        unique_id: electro_power_l3
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/P L3"
        device_class: power
        unit_of_measurement: 'W'
        value_template: "{{ value|round(0) }}"
        
# общая мощность по трем фазам
      - name: "electro_power_total"
        unique_id: electro_power_total
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Total P"
        device_class: power
        unit_of_measurement: 'W'
        value_template: "{{ value|round(0) }}"   

#"Энергия AP по трем фазам"
      - name: "electro_energy_total" 
        unique_id: electro_energy_total
        device_class: energy
        state_class: total
        state_topic: "WB8IP21/devices/wb-map3e_21/controls/Total AP energy"
        unit_of_measurement: 'kWh' 
