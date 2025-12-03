
```javascript
 function makeMotionDetector(name, timeout_s, detector_control, name_mqtt) {
  var motion_timer_id = null;
  var timeout_ms = timeout_s * 1000;
  defineRule(name, {
      whenChanged: detector_control + "/Max Motion",
      then: function(newValue, devName, cellName) {
          if (newValue>100) {
              log(newValue);
              publish("/devices/" + detector_control + "/controls/" + name_mqtt, 1, 0, true);
              if (motion_timer_id) {
                  clearTimeout(motion_timer_id);
              }

              motion_timer_id = setTimeout(function() {
                  publish("/devices/" + detector_control + "/controls/" + name_mqtt, 0, 0, true);
                  motion_timer_id = null;
              }, timeout_ms);
          }
      }
  });
 }

 function makeMotionDetectorBin(name, timeout_s, detector_control, name_mqtt) {
  var motion_timer_id = null;
  var timeout_ms = timeout_s * 1000;
  defineRule(name, {
      whenChanged: "wb-gpio/" + detector_control,
      then: function(newValue, devName, cellName) {
          if (newValue>0) {
              log(newValue);
              publish("/devices/wb-gpio/controls/" + detector_control + "_" + name_mqtt, 1, 0, true);
              if (motion_timer_id) {
                  clearTimeout(motion_timer_id);
              }

              motion_timer_id = setTimeout(function() {
                  publish("/devices/wb-gpio/controls/" + detector_control + "_" + name_mqtt, 0, 0, true);
                  motion_timer_id = null;
              }, timeout_ms);
          }
      }
  });
 } 
makeMotionDetector("motion_detector_11", 300, "wb-msw-v3_11", "Max Motion Time");
makeMotionDetector("motion_detector_12", 300, "wb-msw-v3_12", "Max Motion Time");
makeMotionDetector("motion_detector_13", 300, "wb-msw-v3_13", "Max Motion Time");
makeMotionDetector("motion_detector_14", 300, "wb-msw-v3_14", "Max Motion Time");
makeMotionDetector("motion_detector_15", 300, "wb-msw-v3_15", "Max Motion Time");
makeMotionDetector("motion_detector_16", 300, "wb-msw-v3_16", "Max Motion Time");
makeMotionDetector("motion_detector_17", 300, "wb-msw-v3_17", "Max Motion Time");
makeMotionDetector("motion_detector_18", 300, "wb-msw-v3_18", "Max Motion Time");
makeMotionDetector("motion_detector_19", 300, "wb-msw-v3_19", "Max Motion Time");
makeMotionDetector("motion_detector_20", 300, "wb-msw-v3_20", "Max Motion Time");
makeMotionDetector("motion_detector_21", 300, "wb-msw-v3_21", "Max Motion Time");
makeMotionDetector("motion_detector_22", 300, "wb-msw-v3_22", "Max Motion Time");

makeMotionDetector("motion_detector_30s_11", 30, "wb-msw-v3_11", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_12", 30, "wb-msw-v3_12", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_13", 30, "wb-msw-v3_13", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_14", 30, "wb-msw-v3_14", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_15", 30, "wb-msw-v3_15", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_16", 30, "wb-msw-v3_16", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_17", 30, "wb-msw-v3_17", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_18", 30, "wb-msw-v3_18", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_19", 30, "wb-msw-v3_19", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_20", 30, "wb-msw-v3_20", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_21", 30, "wb-msw-v3_21", "Max Motion Time 30s");
makeMotionDetector("motion_detector_30s_22", 30, "wb-msw-v3_22", "Max Motion Time 30s");

makeMotionDetectorBin("motion_detector_30s_2021", 60, "EXT1_IN1", "Max Motion Time 30s");

```
