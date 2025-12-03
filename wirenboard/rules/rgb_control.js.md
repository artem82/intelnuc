
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
