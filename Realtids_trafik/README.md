**Realtids Trafik**

This sensors show realtime traffic information for Aarhus Kommune.

**Screenshot(s):**

![Screenshot 2](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Realtids_trafik/screenshot_1.jpg)

![Screenshot 1](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Realtids_trafik/screenshot)

**Configuration:**

1: Go to this url https://www.opendata.dk/city-of-aarhus/realtids-trafikdata#resource-realtids_trafikdata_datadictionary and find the place you want to track, and copy the "REPORT_ID".

2: Now replace REPORT_ID in this url https://admin.opendata.dk/api/3/action/datastore_search?q=REPORT_ID&resource_id=b3eeb0ff-c8a8-4824-99d6-e0a3747c8b0d

this could look like this https://admin.opendata.dk/api/3/action/datastore_search?q=158776&resource_id=b3eeb0ff-c8a8-4824-99d6-e0a3747c8b0d

3: Visit the url in your browser and make sure under records only 1 entry is listed.

4: Now use the rest sensor with your url under resource.

**Main sensor:**

This will generate the main sensor (Required to use template sensors!).

```
---
# https://www.opendata.dk/city-of-aarhus/realtids-trafikdata
# https://www.openstreetmap.org/#map=19/56.21831/10.16672
sensor:
  platform: rest
  name: "[Live Traffic] Randersvej, Ikea (vehicleCount)"
  resource: https://admin.opendata.dk/api/3/action/datastore_search?q=158776&resource_id=b3eeb0ff-c8a8-4824-99d6-e0a3747c8b0d
  method: GET
  json_attributes_path: "result.records[0]"
  json_attributes:
    - _id
    - REPORT_ID
    - TIMESTAMP
    - status
    - avgMeasuredTime
    - medianMeasuredTime
    - vehicleCount
    - avgSpeed
  value_template: '{{ value_json.result.records[0].vehicleCount }}'
  scan_interval: 60
  force_update: false
  ```

**Template Sensors:**

This will generate template sensors for all attributes.

```
sensor:
  ---
  # https://www.opendata.dk/city-of-aarhus/realtids-trafikdata
  # Pkt 1 https://www.openstreetmap.org/#map=19/56.21831017223658/10.167189431877205
  # Pkt 2 https://www.openstreetmap.org/#map=19/56.21071820426365/10.173023480985648
  # Distance 920 meters
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

Origin data source: https://www.opendata.dk/city-of-aarhus/realtids-trafikdata

For data sources from other kommuner visit https://www.opendata.dk and search for available datasets for your kommune.

*Note: This is my first try with use of rest api, so this sensors can be make more smooth and with better quality!*
