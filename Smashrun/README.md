**Smashrun**

This sensors show running data from Smashrun. Smashrun have autosync from many other sites including Garmin Connect.

**Screenshot(s):**

![Screenshot 3](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Smashrun/screenshot_2.jpg)

![Screenshot 2](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Smashrun/screenshot_1.jpg)

![Screenshot 1](https://github.com/Danish-Home-Assistant-Community/projects_and_ideas/blob/master/Smashrun/screenshot.jpg)

**Configuration:**

1: If you not already have a Smashrun account visit https://smashrun.com/allan.persson/invite and make your account, and setup auto sync to the fitness trackers you want to sync with.

2: Go to https://api.smashrun.com/v1/explorer and write *client* in top left corner and press Smashrun Link and authorize.

2a: Full api documentation can be found here: https://api.smashrun.com/documentation

3: When authorized (in top left corner you will now see a token) go to the api you want to use and click execute, the one used for last run distance is *Get all activities in summary format (ordered by StartDate)*

The full url including token is copied to the clipboard and you can now insert it in ressources in the sensor, if not copied go back to **3:** and repeat the steps.

**Visualization:**

Mini Media Graph lovelace code (below) from screenshot example based on year sensors.

```
color_thresholds:
  - color: '#33cc33'
    value: '2000.00'
  - color: '#FFFF00'
    value: '1000.00'
  - color: '#ff0000'
    value: '0.00'
entities:
  - sensor.2020_year_total_distance_smashrun
  - sensor.2019_year_total_distance_smashrun
  - sensor.2018_year_total_distance_smashrun
  - sensor.2017_year_total_distance_smashrun
  - sensor.2016_year_total_distance_smashrun
  - sensor.2015_year_total_distance_smashrun
font_size: 75
hours_to_show: 196
line_color: black
line_width: 2
name: Year on Year @ Smashrun
points_per_hour: 0.1
show:
  extrema: true
  fill: fade
  labels: true
  legends: true
type: 'custom:mini-graph-card'
```


Bar Card lovelace code (below) from screenshot example based on year sensors.

```
type: 'custom:bar-card'
entities:
  - entity: sensor.2020_year_total_distance_smashrun
  - entity: sensor.2019_year_total_distance_smashrun
  - entity: sensor.2018_year_total_distance_smashrun
  - entity: sensor.2017_year_total_distance_smashrun
  - entity: sensor.2016_year_total_distance_smashrun
  - entity: sensor.2015_year_total_distance_smashrun
direction: right
positions:
  minmax: 'off'
  value: inside
  indicator: inside
  name: outside
  icon: 'off'
severity:
  - from: '0'
    to: '500'
    color: red
  - from: '500'
    to: '1000'
    color: orange
  - from: '1000'
    to: '1500'
    color: yellow
  - from: '1500'
    to: '2000'
    color: lightgreen
  - from: '2000'
    to: '1000000'
    color: green
animation:
  state: 'on'
height: 60px
entity_row: true
decimal: '0'
min: '0'
max: '3402'
columns: '1'
width: 330px

```
