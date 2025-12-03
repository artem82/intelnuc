zigbee2mqtt

```javascript
defineRule( "cover_child_open", {
  whenChanged: "wb-gpio/EXT2_IN10",
  then: function (newValue, devName, cellName){

    if ( newValue == 1) { //если кнопка нажата
    runShellCommand("mosquitto_pub -t 'zigbee2mqtt/cover_child_l/set' -m 'OPEN'"); //
    runShellCommand("mosquitto_pub -t 'zigbee2mqtt/cover_child_r/set' -m 'OPEN'"); // 
    } 
    
  }
});

defineRule( "cover_child_close", {
  whenChanged: "wb-gpio/EXT2_IN11",
  then: function (newValue, devName, cellName){

    if ( newValue == 1) { //если кнопка нажата
    runShellCommand("mosquitto_pub -t 'zigbee2mqtt/cover_child_l/set' -m 'CLOSE'"); //
    runShellCommand("mosquitto_pub -t 'zigbee2mqtt/cover_child_r/set' -m 'CLOSE'"); // 
    } 
    
    // mosquitto_pub -h 192.168.1.10 -t 'zigbee2mqtt/cover_dinning_l/set' -m 'CLOSE'
  }
});
```
