```yaml
type: grid
cards:
  - type: heading
    heading: Нажатый MCM8
    heading_style: title
  - type: custom:auto-entities
    card:
      type: entities
    filter:
      include:
        - options: {}
          entity_id: binary_sensor.wb_mcm8*
          state: "on"
      exclude: []
```
