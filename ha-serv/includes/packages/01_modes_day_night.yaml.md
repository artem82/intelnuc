```yaml
# День/ночь (ночной режим)

daymode:   # название пакаджа ДЕНЬ/НОЧЬ (ночной режим)


###############################
# сам режим
  input_select:
    
    mode_daynight:
      options:
        - день
        - вечер
        - ночь
      initial: день

####################################################
# скрипты на переключение режима ДЕНЬ/НОЧЬ/ВЕЧЕР 
  script:

    mode_daynight_day:
      alias: mode_daynight_day
      sequence:
        - service: input_select.select_option
          data:
            option: 'день'
          target:
            entity_id: input_select.mode_daynight
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modeday
            payload: день
            
  
    mode_daynight_night:
      alias: mode_daynight_night
      sequence:
        - service: input_select.select_option
          data:
            option: 'ночь'
          target:
            entity_id: input_select.mode_daynight
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modeday
            payload: night
            
            
    mode_daynight_sunset:
      alias: mode_daynight_sunset
      sequence:
        - service: input_select.select_option
          data:
            option: 'вечер'
          target:
            entity_id: input_select.mode_daynight
        - service: mqtt.publish
          data:
            qos: 0
            retain: true
            topic: /homeassistant/modeday
            payload: sunset
            
###############################################################


###############################################################
# кнопка ручного включения режима ДЕНЬ/НОЧЬ/ВЕЧЕР
  switch:
    platform: template
    switches:
        mode_daynight:
          unique_id: mode_daynight
          value_template: "{{ is_state('input_select.mode_daynight', 'ночь') }}"
          turn_on:
            service: script.mode_daynight_night
          turn_off:
            service: script.mode_daynight_day
            
        mode_daysunset:
          unique_id: mode_daysunset
          value_template: "{{ is_state('input_select.mode_daynight', 'вечер') }}"
          turn_on:
            service: script.mode_daynight_sunset
          turn_off:
            service: script.mode_daynight_day

#################################################################

################################################
# автоматизации

  automation:


# ДЕНЬ
  - alias: mode_daynight_auto_night_to_day
    id: mode_daynight_auto_night_to_day
    mode: single
    trigger:
      - platform: time
        at: "06:00:00"
    action:
      - service: script.mode_daynight_day

# НОЧЬ
  - alias: mode_daynight_auto_day_to_night
    id: mode_daynight_auto_day_to_night
    mode: single
    trigger:
      - platform: time
        at: "23:30:00"
    action:
      - service: script.mode_daynight_night
      
# ЗАКАТ      
      
  - alias: mode_daynight_auto_day_to_sunset
    id: mode_daynight_auto_day_to_sunset
    mode: single
    trigger:   # ранбше заката на 30 минут
      - platform: sun
        event: sunset
        offset: "-00:30:00"
    action:
      - service: script.mode_daynight_sunset

# старт системы        
  - alias: mode_daynight_auto_hastart
    id: mode_daynight_auto_hastart
    mode: single
    trigger:
      - platform: homeassistant
        event: start
    action:
      - if:
          - condition: time
            after: "23:30:00"
        then:
          - service: script.mode_daynight_night
            data: {}
        else:
          - service: script.mode_daynight_day
            data: {}


```





