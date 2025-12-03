
### // Так как зеркала имеют свою кнопку нужно держать их включенными
```javascript
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
```javascript
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
```javascript
### // нужен только импульс, поэтому выключатель возвращаем на место
defineRule({
  whenChanged: "wb-mr6c_129/K4",
  then: function (newValue, devName, cellName) {

    setTimeout(function () {
      dev["wb-mr6c_129/K4"] = false;  // ворота гаражные
    }, 900);
    
  }
});
```
