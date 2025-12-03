

##############################
###          FAN           ###
##############################
fan:

############################ 108 ВЕНТИЛЯТОРЫ ##################  

# 61

  - name: "wb_mdm3_61_k1"
    unique_id: wb_mdm3_61_k1
    state_topic: "/devices/wb-mdm3_61/controls/K1"
    command_topic: "/devices/wb-mdm3_61/controls/K1/on"
    percentage_state_topic: "/devices/wb-mdm3_61/controls/Channel 1"
    percentage_command_topic: "/devices/wb-mdm3_61/controls/Channel 1/on"
    icon: mdi:fan
    payload_on: "1"
    payload_off: "0"
    retain: true

  - name: "wb_mdm3_61_k2"
    unique_id: wb_mdm3_61_k2
    state_topic: "/devices/wb-mdm3_61/controls/K2"
    command_topic: "/devices/wb-mdm3_61/controls/K2/on"
    percentage_state_topic: "/devices/wb-mdm3_61/controls/Channel 2"
    percentage_command_topic: "/devices/wb-mdm3_61/controls/Channel 2/on"
    icon: mdi:fan
    payload_on: "1"
    payload_off: "0"
    retain: true
