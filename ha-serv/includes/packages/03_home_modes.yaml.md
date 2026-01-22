

homemode:   # название пакаджа ДОМА/НЕ ДОМА/ОХРАНА (ночной режим)

###############################
# сам режим
  input_select:
    
    mode_homeaway_eng:
      options:
        - home
        - away
        - guard
      initial: away
    mode_homeaway:
      options:
        - дома
        - не дома
        - охрана
        - отпуск


##################################
##         автоматизации
###################################
  automation:
  
  
# утром до движения система будет считать вас не дома ! если только телефон не подключен к wifi
  - alias: mode_homeaway_auto_home_to_away
    id: mode_homeaway_auto_home_to_away
    mode: single
    trigger:
      - platform: time
        at: "08:00:00"
    condition:
      - condition: state
        entity_id: device_tracker.iphoneanton
        state: not_home
    action:
      - service: input_select.select_option
        data:
          option: не дома      
        target:
          entity_id: input_select.mode_homeaway 
          

# ВКЛ РЕЖИМ ДОМА
  - alias: mode_homeaway_auto_away_to_home
    id: mode_homeaway_auto_away_to_home
    mode: single
    trigger:
      - platform: state
        entity_id:
          - binary_sensor.wb_motion_all_devices_norm
        to: "on"
    action:
      - service: input_select.select_option
        data:
          option: дома      
        target:
          entity_id: input_select.mode_homeaway 

# по телефону
# # ВКЛ РЕЖИМ ДОМА по телефону когда Антон возвращается          
  - alias: mode_homeaway_iphone_away_to_home
    id: mode_homeaway_iphone_away_to_home
    mode: single
    trigger:
      - platform: state
        entity_id:
          - device_tracker.iphoneanton
        to: "home"
    action:
      - service: input_select.select_option
        data:
          option: дома
        target:
          entity_id: input_select.mode_homeaway 
          
# по телефону не дома         
  - alias: mode_homeaway_iphone_away_to_not_home
    id: mode_homeaway_iphone_away_to_not_home
    mode: single
    trigger:
      - platform: state
        entity_id:
          - device_tracker.iphoneanton
        to: "not_home"
    action:
      - service: input_select.select_option
        data:
          option: не дома
        target:
          entity_id: input_select.mode_homeaway           

#############################################################            
###        включаем режим НЕ ДОМА                         ###
#############################################################

# в режиме НЕ ДОМА отключаем некоторые автоматизации
  - alias: mode_homeaway_auto_off
    id: mode_homeaway_auto_off
    mode: single
    trigger:
      - platform: state
        entity_id:
          - input_select.mode_homeaway
        to: не дома
    condition: []
    action:
      - service: automation.turn_off
        data:
          stop_actions: true
        target:
          entity_id: 
            - automation.auto_nightlight_onoff
            - automation.auto_fasad_on
            
            
            
            
            
###############################################################            
# в режиме ДОМА включаем некоторые автоматизации
  - alias: mode_homeaway_auto_on
    id: mode_homeaway_auto_on
    mode: single
    trigger:
      - platform: state
        entity_id:
          - input_select.mode_homeaway
        to: дома
    condition: []
    action:
      - service: automation.turn_on
        data: {}
        target:
          entity_id:
            - automation.auto_nightlight_onoff
            - automation.auto_fasad_on
#      - service: climate.set_temperature
#        data:
#          temperature: "{{states('input_number.all_set_temperature_radiator')}}"
#          temperature: "23"
#        target:
#          entity_id:
#            - group.climate_radiator

#############################################################            
###        включаем режим отпуск                          ###
#############################################################
  - alias: mode_homeaway_otpusk_on
    id: mode_homeaway_otpusk_on
    mode: single
    trigger:
      - platform: state
        entity_id:
          - input_select.mode_homeaway
        to: отпуск
    condition: []
    action:
      - service: automation.turn_off
        data: {}
        target:
          entity_id:
            - automation.auto_nightlight_onoff
            - automation.auto_fasad_on
      - service: climate.set_temperature
        data:
#          temperature: "{{states('input_number.all_set_temperature_radiator')}}"
          temperature: "18"
        target:
          entity_id:
            - group.climate_radiator  
            
            
            
##################################
# скрипты на переключение
  script:

    mode_homeaway_home:
      alias: mode_homeaway_home
      sequence:
        - service: input_select.select_option
          data:
            option: 'дома'
          target:
            entity_id: input_select.mode_homeaway
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modehome
            payload: дома
            
  
    mode_homeaway_nothome:
      alias: mode_homeaway_nothome
      sequence:
        - service: input_select.select_option
          data:
            option: 'не дома'
          target:
            entity_id: input_select.mode_homeaway
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modehome
            payload: не дома
            
            
    mode_homeaway_otpusk:
      alias: mode_homeaway_otpusk
      sequence:
        - service: input_select.select_option
          data:
            option: 'отпуск'
          target:
            entity_id: input_select.mode_homeaway
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modehome
            payload: отпуск


    mode_homeaway_guard:
      alias: mode_homeaway_guard
      sequence:
        - service: input_select.select_option
          data:
            option: 'охрана'
          target:
            entity_id: input_select.mode_homeaway
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modehome
            payload: охрана     
##################################





