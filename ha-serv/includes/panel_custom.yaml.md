```yaml
#                         _  
#  _ __   __ _ _ __   ___| | 
# | '_ \ / _` | '_ \ / _ \ | 
# | |_) | (_| | | | |  __/ | 
# | .__/ \__,_|_| |_|\___|_| 
# |_|                    
#
#####################################
#####          PANEL           ######
#####################################
# V1.1

# ЛОГИ
  - name: ha_logs
    # url_path needs to be unique for each panel_custom config
    url_path: config/logs
    sidebar_title: HA Logs
    sidebar_icon: mdi:math-log
    module_url: /local/panel-redirect.js
    config:
      target: /config/logs
# СЕРВЕР
  - name: ha_server
    sidebar_title: Server Control
    sidebar_icon: mdi:server
    module_url: /local/panel-redirect.js
    #js_url: /api/hassio/app/entrypoint.js
    url_path: "developer-tools/yaml"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator
# АВТОМАТИЗАЦИИ      
  - name: ha_automation
    sidebar_title: Automation
    sidebar_icon: mdi:home-automation
    module_url: /local/panel-redirect.js
    url_path: "config/automation/dashboard"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator
# ИНТЕГРАЦИИ      
  - name: ha_integration
    sidebar_title: Integration
    sidebar_icon: mdi:monitor
    module_url: /local/panel-redirect.js
    url_path: "config/integrations"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator

# HASC SHOP
  - name: hassioshop
    sidebar_title: HASSIO
    sidebar_icon: mdi:download-circle-outline
    module_url: /local/panel-redirect.js
    url_path: "hassio/dashboard"
#    url_path: "hassio/store"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator
# HASC сервер
  - name: server_state
    sidebar_title: "Система"
    sidebar_icon: mdi:database-outline
    js_url: /api/hassio/app/entrypoint.js
    url_path: "hassio/system"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator
# Мобильное приложение
  - name: ha_mobile
    sidebar_title: "Телефоны"
    sidebar_icon: mdi:cellphone
    js_url: /api/hassio/app/entrypoint.js
    url_path: "config/integrations/integration/mobile_app"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator
# Backup
  - name: ha_mobile
    sidebar_title: "Backup"
    sidebar_icon: mdi:cloud-upload
    js_url: /api/hassio/app/entrypoint.js
    url_path: "config/backup/overview"
    embed_iframe: true
    require_admin: true
    config:
      ingress: core_configurator
```
