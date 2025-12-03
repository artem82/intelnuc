пример 1
```javascript

defineRule( "light_change_rgbw_w", {
  whenChanged: "wb-gpio/EXT2_IN5",
  then: function (newValue, devName, cellName){

    if ( newValue == 1) { //если кнопка нажата
    dev["wb-led_231/RGB Strip"] = false; 
    dev["wb-led_231/Channel 4"] = !dev["wb-led_231/Channel 4"]; 
    } 
         // dev["wb-led_103/Channel 4"] = false   
  }
});

defineRule( "light_change_rgbw_rgb", {
  whenChanged: "wb-gpio/EXT2_IN4",
  then: function (newValue, devName, cellName){

    if ( newValue == 1) { //если кнопка нажата
    dev["wb-led_231/Channel 4"] = false; 
    dev["wb-led_231/RGB Strip"] = true;    

      
    } 
  
  }
});
```
пример 2
```javascript
var dimmNumber = "93" //name VIRTUAL device (this) #ChangeMe!#
var devDimmer = "wb-mrgbw-d-fw3_93" // For name REAL MRGBW-D device #ChangeMe!#

defineVirtualDevice("virtual_mrgbw-d_" + dimmNumber, {
  title: "virtual_mrgbw-d_" + dimmNumber, //
  cells: {
    RGBPalette : {
        type : "text",
        readonly: false,
        value : "0,0,0",
    }
  }
});

defineRule( "RGB_change", {
  whenChanged: "virtual_mrgbw-d_" + dimmNumber + "/RGBPalette",
  then: function (newValue, devName, cellName){
    log.info(typeof newValue);
    var cmd = newValue.replace(/,/g,';');
	log.info(typeof newValue);
    log.info("RGB changed. old: ", newValue, ", new: ", cmd);
    log.info("Путь:", "/devices/"+ devDimmer +"/controls/RGB Palette/on");
    dev[devDimmer +"/RGB Palette"] = cmd;
  }
});
```
```javascript
trackMqtt("/devices/daikin-lon_5/controls/1_ON_OFF_VIRTUAL", function(message){
  log.info("name 1: {}, value: {}".format(message.topic, message.value))

  if(message.value === "0"){
    publish("/devices/daikin-lon_5/controls/1_ON_OFF_WRITE/on", "0"); 
  }
  else if(message.value === "100"){
  	publish("/devices/daikin-lon_5/controls/1_ON_OFF_WRITE/on", "100"); 
  }

});
```
