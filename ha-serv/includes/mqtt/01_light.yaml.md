
```yaml
##############################
###          LIGHT         ###
##############################
light:

################ 70 ######################## гараж

# Гараж свет
  - name: "wb_mr_70_k1"
    unique_id: wb_mr_70_k1
    state_topic: "/devices/wb-mr6c_70/controls/K1"
    command_topic: "/devices/wb-mr6c_70/controls/K1/on"
    icon: mdi:lightbulb-outline
    payload_on: "1"
    payload_off: "0"
    retain: true   
    
# Котельная
  - name: "wb_mr_70_k2"
    unique_id: wb_mr_70_k2
    state_topic: "/devices/wb-mr6c_70/controls/K2"
    command_topic: "/devices/wb-mr6c_70/controls/K2/on"
    icon: mdi:lightbulb-outline
    payload_on: "1"
    payload_off: "0"
    retain: true
################ 106 ########################

# прачечная/посчтирочная
  - name: "wb_mr6cv3_106_k1"
    unique_id: wb_mr6cv3_106_k1
    state_topic: "/devices/wb-mr6cv3_106/controls/K1"
    command_topic: "/devices/wb-mr6cv3_106/controls/K1/on"
    icon: mdi:light-recessed
    payload_on: "1"
    payload_off: "0"
    retain: true

  - name: "wb_mr6c_111_k1"
    unique_id: wb_mr6c_111_k1
    state_topic: "/devices/wb-mr6c_111/controls/K1"
    command_topic: "/devices/wb-mr6c_111/controls/K1/on"
    icon: mdi:lightbulb-outline
    payload_on: "1"
    payload_off: "0"
    retain: true

########################################
###          LIGHT LED W4 DIM        ###
########################################


# гостиная
  - name: "wb_led_rgbw_125_ch1"
    unique_id: wb_led_rgbw_125_ch1
    state_topic: "/devices/wb-led_125/controls/Channel 1"
    command_topic: "/devices/wb-led_125/controls/Channel 1/on"
    brightness_state_topic: "/devices/wb-led_125/controls/Channel 1 Brightness"
    brightness_command_topic: "/devices/wb-led_125/controls/Channel 1 Brightness/on"
    icon: mdi:led-strip-variant
    payload_on: "1"
    payload_off: "0"
    brightness_scale: 100
    retain: true

```    
