
# СОЗДАЕМ РАДИАТОРЫ 


# Детская 1  -11
# Детская 2  -12
# Гостевая   -13
# Спортзал   -14
# Стол КО SPA   -15
# Серверная  -16 коридор
# Кабинет    -17
# Столовая   -18
# Спальня    -19
# Входная группа -20
# Гараж      -21
# Спа коридор-22

# насос 6 - 0.5А

# РАДИАТОРЫ 1-6, 7-13 - ТЕПЛЫЕ ПОЛЫ 
# насос 2 - 0.6А
# wb_radiator_183_k1  # Р+К СПОРТЗАЛ (конвекторы и батарея)
# wb_radiator_183_k2  # Р+К СПОРТЗАЛ (две дальние батареи)
# wb_radiator_183_k3  # Р+К КО SPA
# wb_radiator_183_k4  # Детская гостевая
# wb_radiator_183_k5  # Детская 2
# wb_radiator_183_k6  # Детская 1
# насос 4 вместе - 0.7А
# wb_radiator_183_k7 - ТП С/У Детская 1
# wb_radiator_183_k8 - ТП С/У Гостевой
# wb_radiator_183_k9 - ТП С/У SPA
# wb_radiator_183_k10 - ТП С/У Детская 2
# насос 3 - 0.19А
# wb_radiator_183_k11  #ТП Хамам+Душ
# wb_radiator_183_k12  #ТП Хамам сидушки
# wb_radiator_183_k13  #ТП Баня

#Радиаторы котел
# насос 5 - 0.45
# wb_radiator_68_k1 - #радиаторы при входе
# wb_radiator_68_k2 - #Столовая радиатор у кухни и конвектоор
# wb_radiator_68_k3 - #Столовая радиатор у кабинета
# wb_radiator_68_k4 - #Гостиная
# wb_radiator_68_k5 - #м спальня
# wb_radiator_68_k6 - #кабинет
# насос 1 - 0.5А
# wb_radiator_68_k7 -  #домик охраны
# wb_radiator_68_k8 -  #беседка тп
# wb_radiator_68_k9 -  #радиатор гаража
# wb_radiator_68_k10 - #радиатор гаража
# насос 4 вместе
# wb_radiator_68_k11  #ТП камин гостиная
# wb_radiator_68_k12  #ТП мастер спальня
# wb_radiator_68_k13  #ТП ВХОД гардеробом
# wb_radiator_68_k14  #ТП ВХОД С/У Прихожая
# wb_radiator_68_k15  #ТП столовая кухня
# wb_radiator_68_k16  #ТП столовая середина
# wb_radiator_60_k1   #ТП столовая кабинет

#################################
###          CLIMATE          ###
#################################




# generic_thermostat Детская 1
- platform: generic_thermostat 
  name: generic_radiator_11_det1
  unique_id: generic_radiator_11_det1
  heater: switch.wb_radiator_183_k6
  target_sensor: sensor.sensor_wb_11_temp  #Детская1
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.1
  hot_tolerance: 0.1
  target_temp: 25
  sleep_temp: 22
  comfort_temp: 23
  
# generic_thermostat Детская 2
- platform: generic_thermostat 
  name: generic_radiator_12_det2
  unique_id: generic_radiator_12_det1
  heater: switch.wb_radiator_183_k5
  target_sensor: sensor.sensor_wb_12_temp  #Детская2
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.1
  hot_tolerance: 0.1
  target_temp: 25
  sleep_temp: 22
  comfort_temp: 23

# generic_thermostat Детская гостевая
- platform: generic_thermostat 
  name: generic_radiator_13_gost
  unique_id: generic_radiator_13_gost
  heater: switch.wb_radiator_183_k4
  target_sensor: sensor.sensor_wb_13_temp  #Гостевая
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.1
  hot_tolerance: 0.1
  target_temp: 24
  sleep_temp: 22
  comfort_temp: 23

# generic_thermostat КО SPA
- platform: generic_thermostat 
  name: generic_radiator_15_kospa
  unique_id: generic_radiator_15_kospa
  heater: switch.wb_radiator_183_k3
  target_sensor: sensor.sensor_wb_15_temp  #Детская1
  target_temp_step: 1
  min_temp: 18
  cold_tolerance: 0.1
  hot_tolerance: 0.1
  target_temp: 24
  sleep_temp: 22
  comfort_temp: 23
  
# generic_thermostat СПОРТЗАЛ
- platform: generic_thermostat 
  name: generic_radiator_14_sportzal
  unique_id: generic_radiator_14_sportzal
  heater: switch.wb_radiator_183_k1
  target_sensor: sensor.sensor_wb_14_temp  #спортзал
  target_temp_step: 1
  min_temp: 18
  cold_tolerance: 0.1
  hot_tolerance: 0.1
  target_temp: 24
  sleep_temp: 22
  comfort_temp: 23

# generic_thermostat кабинет
- platform: generic_thermostat 
  name: generic_radiator_17_cabinet
  unique_id: generic_radiator_17_cabinet
  heater: switch.wb_radiator_68_k6
  target_sensor: sensor.sensor_wb_17_temp  #кабинет
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.1
  hot_tolerance: 0.1
  target_temp: 24
  sleep_temp: 22
  comfort_temp: 23

# generic_thermostat столовая
- platform: generic_thermostat 
  name: generic_radiator_18_diningroom
  unique_id: generic_radiator_18_diningroom
  heater: switch.wb_radiator_68_k3          #Столовая радиатор у кабинета
  target_sensor: sensor.sensor_wb_18_temp   #столовая
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.2
  hot_tolerance: 0.2
  target_temp: 24
  sleep_temp: 21
  comfort_temp: 23

# generic_thermostat гостиная
- platform: generic_thermostat 
  name: generic_radiator_18_gost
  unique_id: generic_radiator_18_gost
  heater: switch.wb_radiator_68_k4
  target_sensor: sensor.sensor_wb_18_temp  #столовая
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.2
  hot_tolerance: 0.2
  target_temp: 25
  sleep_temp: 22
  comfort_temp: 23
  
  
# generic_thermostat спальня
- platform: generic_thermostat 
  name: generic_radiator_19_bedroom
  unique_id: generic_radiator_19_bedroom
  heater: switch.wb_radiator_68_k5
  target_sensor: sensor.sensor_wb_19_temp  #спальня
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.2
  hot_tolerance: 0.2
  target_temp: 24
  sleep_temp: 22
  comfort_temp: 23

# generic_thermostat входная группа
- platform: generic_thermostat 
  name: generic_radiator_20_enter_zone
  unique_id: generic_radiator_20_enter_zone
  heater: switch.wb_radiator_68_k1
  target_sensor: sensor.sensor_wb_20_temp  #спальня
  target_temp_step: 1
  min_temp: 19
  cold_tolerance: 0.2
  hot_tolerance: 0.2
  target_temp: 24
  sleep_temp: 21
  comfort_temp: 23
  
# generic_thermostat гараж
- platform: generic_thermostat 
  name: generic_radiator_21_garag
  unique_id: generic_radiator_21_garag
  heater: switch.wb_radiator_68_k9
  target_sensor: sensor.sensor_wb_21_temp  #гараж
  target_temp_step: 1 
  min_temp: 18
  cold_tolerance: 0.2
  hot_tolerance: 0.2
  target_temp: 24
  sleep_temp: 21
  comfort_temp: 22
  
#  
# ТЕПЛЫЕ ПОЛЫ
#
# generic_thermostat ТП СУ Детская 1
#- platform: generic_thermostat 
#  name: generic_radiator_tp_11_det1
#  unique_id: generic_radiator_tp_11_det1
#  heater: switch.wb_radiator_183_k7
#  target_sensor: sensor.sensor_wb_11_temp  #Детская1
#  target_temp_step: 1 
#  min_temp: 19 
#  cold_tolerance: 0.2 
#  hot_tolerance: 0.3 
#  target_temp: 25 
#  sleep_temp: 22 
#  comfort_temp: 23  
  
# generic_thermostat ТП СУ Детская 2
#- platform: generic_thermostat 
#  name: generic_radiator_tp_12_det2
#  unique_id: generic_radiator_tp_12_det2
#  heater: switch.wb_radiator_183_k10
#  target_sensor: sensor.sensor_wb_12_temp  #Детская2
#  target_temp_step: 1 
#  min_temp: 19 
#  cold_tolerance: 0.2 
#  hot_tolerance: 0.3 
#  target_temp: 25 
#  sleep_temp: 22 
#  comfort_temp: 23 

## generic_thermostat ТП СУ Детская Гостевая
#- platform: generic_thermostat 
#  name: generic_radiator_tp_13_gost
#  unique_id: generic_radiator_tp_13_gost
#  heater: switch.wb_radiator_183_k8
#  target_sensor: sensor.sensor_wb_12_temp  #Гостевая
#  target_temp_step: 1 
#  min_temp: 19 
#  cold_tolerance: 0.2 
#  hot_tolerance: 0.3 
#  target_temp: 25 
#  sleep_temp: 22 
#  comfort_temp: 23   
  
  
  
  
  
  
  
  
  
  
  
  
