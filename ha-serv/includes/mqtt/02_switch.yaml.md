```yaml

switch:
################ 102 ######################## 

# теплый пол
  - name: "wb-mrwm2_102_k1"
    unique_id: wb-mrwm2_102_k1
    state_topic: "/devices/wb-mrwm2_102/controls/K1"
    command_topic: "/devices/wb-mrwm2_102/controls/K1/on"
    icon: mdi:heat-wave
    payload_on: "1"
    payload_off: "0"
    retain: true 

  - name: "wb-mrwm2_102_k2"
    unique_id: wb-mrwm2_102_k2
    state_topic: "/devices/wb-mrwm2_102/controls/K2"
    command_topic: "/devices/wb-mrwm2_102/controls/K2/on"
    icon: mdi:heat-wave
    payload_on: "1"
    payload_off: "0"
    retain: true

################  103  #####################################  
# розетки 
  - name: "wb-mrwm2_103_k1"
    unique_id: wb-mrwm2_103_k1
    state_topic: "/devices/wb-mrwm2_103/controls/K1"
    command_topic: "/devices/wb-mrwm2_103/controls/K1/on"
    icon: mdi:power-socket-eu
    payload_on: "1"
    payload_off: "0"
    retain: true 

  - name: "wb-mrwm2_103_k2"
    unique_id: wb-mrwm2_103_k2
    state_topic: "/devices/wb-mrwm2_103/controls/K2"
    command_topic: "/devices/wb-mrwm2_103/controls/K2/on"
    icon: mdi:power-socket-eu
    payload_on: "1"
    payload_off: "0"
    retain: true 

################  104  #####################################  
# полотенцесушитель
  - name: "wb-mr6cv3_104_k6"
    unique_id: wb-mr6cv3_104_k6
    state_topic: "/devices/wb-mr6cv3_104/controls/K6"
    command_topic: "/devices/wb-mr6cv3_104/controls/K6/on"
    icon: mdi:heating-coi
    payload_on: "1"
    payload_off: "0"
    retain: true 



######################################
###          SWITCH RADIATOR       ###
######################################

# РАДИАТОРЫ 1-6, 7-13 - ТЕПЛЫЕ ПОЛЫ 

  - name: "wb_radiator_183_k1"
    unique_id: wb_radiator_183_k1
    state_topic: "/devices/wb-mio-gpio_183:1/controls/K1"
    command_topic: "/devices/wb-mio-gpio_183:1/controls/K1/on"
    icon: mdi:radiator
    payload_on: "0"
    payload_off: "1"
    retain: true

  - name: "wb_radiator_183_k2"
    unique_id: wb_radiator_183_k2
    state_topic: "/devices/wb-mio-gpio_183:1/controls/K2"
    command_topic: "/devices/wb-mio-gpio_183:1/controls/K2/on"
    icon: mdi:radiator
    payload_on: "0"
    payload_off: "1"
    retain: true

  - name: "wb_radiator_183_k3"
    unique_id: wb_radiator_183_k3
    state_topic: "/devices/wb-mio-gpio_183:1/controls/K3"
    command_topic: "/devices/wb-mio-gpio_183:1/controls/K3/on"
    icon: mdi:radiator
    payload_on: "0"
    payload_off: "1"
    retain: true
    
# wb_radiator_183_k4 - Детская гостевая    
  - name: "wb_radiator_183_k4"
    unique_id: wb_radiator_183_k4
    state_topic: "/devices/wb-mio-gpio_183:1/controls/K4"
    command_topic: "/devices/wb-mio-gpio_183:1/controls/K4/on"
    icon: mdi:radiator
    payload_on: "0"
    payload_off: "1"
    retain: true

```
    
    
    
