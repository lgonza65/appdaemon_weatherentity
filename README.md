# Description
Base weather widget for appdaemon homeassistant dashboards.

Based on the [appdaemon weather official widget](https://github.com/AppDaemon/appdaemon/blob/dev/appdaemon/widgets/baseweather/baseweather.js), this extends it by allowing to get weather from a weather entity in addition to sensors.
This avoids having to declare sensors, often specifics to each provider, and use directly the homeassistant weather entity. This makes the feature more generic (currently tested with openweathermap).

In addition, this version also adds the feature to display up to 4 days/hours of forecast.
This is fully compliant with the official base widget, so any working configuration will also work with this widget.

**Note: For 2x2 widget, only 1 forecast should be used with a 120x120 widget. Up to for can be used in 3x2.**

#### 3x2 widget with 4 forecasts
<img src="https://github.com/vche/appdaemon_weatherentity/blob/master/etc/3x2.png" width="360">

#### 2x2 widget with 1 forecasts
<img src="https://github.com/vche/appdaemon_weatherentity/blob/master/etc/2x2.png" width="240">

## Configuration

The configuration is almost identical to the official daemon, with the following differences:
- ```entity```: Can be specified in place of ```entities``` to use a weather entities instead of a sensor list
- ```show_forecast``` can be set to the number of forecasts to displqy (up to 4, 0 = no forecast)

## Example configuration

```yaml
openweathermap:
  title: Now
  widget_type: weatherentity
  entity: weather.openweathermap
  show_forecast: 4
  prefer_icons: 1
  # Units as configured in homeassistant
  units: "&deg;C"
  wind_unit: "km/h"
  pressure_unit: "hPa"
  rain_unit: "%"

layout:
    - label(2x2),openweathermap(3x2)
```
