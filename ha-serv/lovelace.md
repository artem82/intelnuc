### Нажатый MCM8
```yaml
type: grid
cards:
  - type: heading
    heading: Нажатый MCM8
    heading_style: title
  - type: custom:auto-entities
    card:
      type: entities
    filter:
      include:
        - options: {}
          entity_id: binary_sensor.wb_mcm8*
          state: "on"
      exclude: []
```
### MCM8
```yaml
type: grid
cards:
  - type: heading
    heading: MCM8
    heading_style: title
  - type: custom:auto-entities
    card:
      type: entities
    filter:
      include:
        - options: {}
          entity_id: binary_sensor.wb_mcm8_51*
      exclude: []
  - type: custom:auto-entities
    card:
      type: entities
    filter:
      include:
        - options: {}
          entity_id: binary_sensor.wb_mcm8_6*
      exclude: []
```
### 50_mcm8.yaml
```yaml
mcm8:
   
  mqtt:

##############################
##      BINARY SENSOR       ##
##############################
    binary_sensor:
        # WB_MCM8_51 #
       - name: "wb_mcm8_51_IN01"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 1"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN02"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 2"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN03"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 3"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN04"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 4"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN05"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 5"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN06"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 6"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN07"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 7"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_51_IN08"
         state_topic: "WB8IP22/devices/wb-mcm8_51/controls/Input 8"
         payload_on: "1"
         payload_off: "0"

        # WB_MCM8_61 #
       - name: "wb_mcm8_61_IN01"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 1"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN02"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 2"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN03"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 3"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN04"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 4"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN05"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 5"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN06"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 6"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN07"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 7"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_61_IN08"
         state_topic: "WB8IP21/devices/wb-mcm8_61/controls/Input 8"
         payload_on: "1"
         payload_off: "0"
         
        # WB_MCM8_62 #
       - name: "wb_mcm8_62_IN01"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 1"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN02"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 2"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN03"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 3"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN04"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 4"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN05"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 5"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN06"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 6"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN07"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 7"
         payload_on: "1"
         payload_off: "0"
       - name: "wb_mcm8_62_IN08"
         state_topic: "WB8IP21/devices/wb-mcm8_62/controls/Input 8"
         payload_on: "1"
         payload_off: "0"
```    
