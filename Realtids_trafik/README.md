**Realtids Trafik**

This sensors show realtime traffic information for Aarhus Kommune.

**Screenshot(s):**

![Screenshot 2](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Realtids_trafik/screenshot_1.jpg)

![Screenshot 1](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Realtids_trafik/screenshot)

**Config:**

Is coming here....

**Template Sensors:**

This will generate template sensors for all attributes.

```
sensor:
  ---
  platform: template
  sensors:
    live_traffic_randersvej_ikea_id:
      friendly_name: "[Live Traffic] Randersvej, Ikea (_id)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes._id }}"
    live_traffic_randersvej_ikea_report_id:
      friendly_name: "[Live Traffic] Randersvej, Ikea (report_id)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes.REPORT_ID }}"
    live_traffic_randersvej_ikea_timestamp:
      friendly_name: "[Live Traffic] Randersvej, Ikea (timestamp)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes.TIMESTAMP }}"
    live_traffic_randersvej_ikea_status:
      friendly_name: "[Live Traffic] Randersvej, Ikea (status)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes.status }}"
    live_traffic_randersvej_ikea_avgmeasuredtime:
      friendly_name: "[Live Traffic] Randersvej, Ikea (avgmeasuredtime)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes.avgMeasuredTime }}"
    live_traffic_randersvej_ikea_medianmeasuredtime:
      friendly_name: "[Live Traffic] Randersvej, Ikea (medianmeasuredtime)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes.medianMeasuredTime }}"
    live_traffic_randersvej_ikea_avgspeed:
      friendly_name: "[Live Traffic] Randersvej, Ikea (avgspeed)"
      entity_id:
        - sensor.live_traffic_randersvej_ikea_vehiclecount
      value_template: "{{ states.sensor.live_traffic_randersvej_ikea_vehiclecount.attributes.avgSpeed }}"
```

**Data:**

The following data points are available:
```
_id
REPORT_ID
TIMESTAMP
status
avgMeasuredTime
medianMeasuredTime
vehicleCount
avgSpeed
```
