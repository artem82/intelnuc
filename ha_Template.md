
---

### Jinja / Template примеры команд

`Список включенных светов в комнате` (по area)
```yaml
{{ states.light
   | selectattr('entity_id', 'in', area_entities('spalnia_master'))
   | selectattr('state', 'eq', 'on')
   | map(attribute='entity_id')
   | list
}}
```

`Поиск светов по entity_id` (regex search)
```yaml
{{ states.light
   | selectattr('entity_id', 'search', '(wb_mr6c_2|wb_mr6c_1)')
   | map(attribute='entity_id')
   | list
}}
```

`Список всех light entities с именами`
```yaml
{% for light in states.light %}
  - {{ light.entity_id }}: {{ light.name }}
{% endfor %}
```

`Список всех switch entities с именами`
```yaml
{% for switch in states.switch %}
  - {{ switch.entity_id }}: {{ switch.name }}
{% endfor %}
```

`Список всех areas в HA`
```yaml
{{ areas() }}
```
