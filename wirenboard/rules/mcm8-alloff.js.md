```javascript
// wb-mcm8_51/Input 6

/* ---------------------------- */
/* 1. Single Press Counter: On action*/
/* ---------------------------- */

defineRule({
  whenChanged: "wb-mcm8_51/Input 6 Single Press Counter",
  then: function (newValue, devName, cellName) {
    dev["wb-mr6c_70/K1"] = false;
    dev["wb-mr6c_70/K2"] = false; 
    
    dev["wb-mr6c_36/K1"] = false;
    dev["wb-mr6c_36/K2"] = false; 
    dev["wb-mr6c_36/K3"] = false; 
    dev["wb-mr6c_36/K4"] = false; 
    dev["wb-mr6c_36/K5"] = false; 
    dev["wb-mr6c_36/K6"] = false; 
    
    dev["wb-mr6c_72/K1"] = false;
    dev["wb-mr6c_72/K2"] = false; 
    dev["wb-mr6c_72/K3"] = false; 
    dev["wb-mr6c_72/K4"] = false; 
    dev["wb-mr6c_72/K5"] = false; 
    dev["wb-mr6c_72/K6"] = false; 
    
    dev["wb-mr6c_76/K1"] = false;
    dev["wb-mr6c_76/K2"] = false; 
    dev["wb-mr6c_76/K3"] = false; 
    dev["wb-mr6c_76/K4"] = false; 
    dev["wb-mr6c_76/K5"] = false; 
    dev["wb-mr6c_76/K6"] = false; 

    dev["wb-mr6c_126/K1"] = false;
    dev["wb-mr6c_126/K2"] = false; 
    dev["wb-mr6c_126/K3"] = false; 
    dev["wb-mr6c_126/K4"] = false; 
    dev["wb-mr6c_126/K5"] = false; 
    dev["wb-mr6c_126/K6"] = false; 

    dev["wb-mr6c_132/K1"] = false;
    dev["wb-mr6c_132/K2"] = false; 
    dev["wb-mr6c_132/K3"] = false; 
    dev["wb-mr6c_132/K4"] = false; 
    dev["wb-mr6c_132/K5"] = false; 
    dev["wb-mr6c_132/K6"] = false; 

    dev["wb-mr6c_173/K1"] = false;
    dev["wb-mr6c_173/K2"] = false; 
    dev["wb-mr6c_173/K3"] = false; 
    dev["wb-mr6c_173/K4"] = false; 
    dev["wb-mr6c_173/K5"] = false; 
    dev["wb-mr6c_173/K6"] = false; 

    dev["wb-mr6c_175/K1"] = false;
    dev["wb-mr6c_175/K2"] = false; 
    dev["wb-mr6c_175/K3"] = false; 
    dev["wb-mr6c_175/K4"] = false; 
    dev["wb-mr6c_175/K5"] = false; 
    dev["wb-mr6c_175/K6"] = false; 
    
    dev["wb-mr6c_180/K1"] = false;
    dev["wb-mr6c_180/K2"] = false; 
    dev["wb-mr6c_180/K3"] = false; 
    dev["wb-mr6c_180/K4"] = false; 
    dev["wb-mr6c_180/K5"] = false; 
    dev["wb-mr6c_180/K6"] = false; 
    
    dev["wb-mr6c_184/K1"] = false;
    dev["wb-mr6c_184/K2"] = false; 
    dev["wb-mr6c_184/K3"] = false; 
    dev["wb-mr6c_184/K4"] = false; 
    dev["wb-mr6c_184/K5"] = false; 
    dev["wb-mr6c_184/K6"] = false; 
    
    dev["wb-mr6c_185/K1"] = false;
    dev["wb-mr6c_185/K2"] = false; 
    dev["wb-mr6c_185/K3"] = false; 
    dev["wb-mr6c_185/K4"] = false; 
    dev["wb-mr6c_185/K5"] = false; 
    dev["wb-mr6c_185/K6"] = false; 
    
    dev["wb-mr6c_186/K1"] = false;
    dev["wb-mr6c_186/K2"] = false; 
    dev["wb-mr6c_186/K3"] = false; 
    dev["wb-mr6c_186/K4"] = false; 
    dev["wb-mr6c_186/K5"] = false; 
    dev["wb-mr6c_186/K6"] = false; 

    dev["wb-mr6c_187/K1"] = false;
    dev["wb-mr6c_187/K2"] = false; 
    dev["wb-mr6c_187/K3"] = false; 
    dev["wb-mr6c_187/K4"] = false; 
    dev["wb-mr6c_187/K5"] = false; 
    dev["wb-mr6c_187/K6"] = false; 
    
    dev["wb-led_125/Channel 1"] = false;
    dev["wb-led_125/Channel 2"] = false;
    dev["wb-led_125/Channel 3"] = false;  // 24 вольт Шторы
    dev["wb-led_125/Channel 4"] = false;  // 24 вольт Шторы
    
    dev["wb-mr6c_132/K3"] = false;  // су
    dev["wb-mr6c_132/K4"] = false;  // су зеркало
    dev["wb-mr6c_77/K2"] = false;   // су 24 вольт Подсветка

    // вентиляторы
    
    dev["wb-mr6c_99/K1"] = false;
    dev["wb-mr6c_99/K2"] = false; 
    dev["wb-mr6c_99/K3"] = false; 
    dev["wb-mr6c_99/K4"] = false; 
    dev["wb-mr6c_99/K5"] = false; 
    dev["wb-mr6c_99/K6"] = false; 
    dev["wb-mr6c_119/K1"] = false;
    dev["wb-mr6c_119/K2"] = false; 
    dev["wb-mr6c_119/K3"] = false;
    
    setTimeout(function () {
      dev["wb-mr6c_132/K4"] = true;  // су зеркало
    }, 500);
    
  }
});

```
