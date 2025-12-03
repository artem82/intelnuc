
### // Так как зеркала имеют свою кнопку нужно держать их включенными
```yaml
defineRule({
  whenChanged: "wb-mr6c_132/K4",
  then: function (newValue, devName, cellName) {
   
   if (newValue) {
    log(newValue);
   }
    else {
//    dev["wb-mr6c_132/K4"] = true;  // второй контур отопления 
      setTimeout(function () {
        dev["wb-mr6c_132/K4"] = true;  // су зеркало
      }, 1000);
    }    
    
  }
});
```
```yaml
defineRule({
  whenChanged: "wb-mr6c_132/K6",
  then: function (newValue, devName, cellName) {
   
   if (newValue) {
    log(newValue);
   }
    else {

      setTimeout(function () {
        dev["wb-mr6c_132/K6"] = true;  // су зеркало
      }, 1000);
    }    
    
  }
});
```
