

```javascript
defineRule({  
  whenChanged: "wb-mr3_127/K1",
  then: function (newValue, devName, cellName) {
 
    if (newValue === true) {
        dev["wb-mr3_127/K2"] = true;  // вкл второй подсветки
    }//end if
    if (newValue === false) {
        dev["wb-mr3_127/K2"] = false;  // вкл второй подсветки
    }//end if
    
  }
    
});
```
```javascript
defineRule({
  whenChanged: "wb-mcm8_51/Input 4 Single Press Counter",
  then: function (newValue, devName, cellName) {
    dev["wb-mr6c_184/K1"] = false;
    dev["wb-mr6c_184/K2"] = false; 
    dev["wb-mr6c_184/K3"] = false; 
    dev["wb-mr6c_184/K4"] = false; 
    dev["wb-mr6c_184/K5"] = false; 
    dev["wb-mr6c_184/K6"] = false; 
    
    dev["wb-led_125/Channel 3"] = false;  // 24 вольт Шторы
    
    dev["wb-mr6c_126/K5"] = false;  // гардероб
    
    dev["wb-mr6c_132/K3"] = false;  // су
    dev["wb-mr6c_132/K4"] = false;  // су зеркало
    dev["wb-mr6c_77/K2"] = false;   // су 24 вольт Подсветка
```

    setTimeout(function () {
      dev["wb-mr6c_132/K4"] = true;  // су зеркало
    }, 500);
    
  }
});
