---
title: "Xiaomi WSDCGQ11LM control via MQTT"
description: "Integrate your Xiaomi WSDCGQ11LM via Zigbee2mqtt with whatever smart home
 infrastructure you are using without the vendors bridge or gateway."
---

*To contribute to this page, edit the following
[file](https://github.com/Koenkk/zigbee2mqtt.io/blob/master/docs/devices/WSDCGQ11LM.md)*

# Xiaomi WSDCGQ11LM

| Model | WSDCGQ11LM  |
| Vendor  | Xiaomi  |
| Description | Aqara temperature, humidity and pressure sensor |
| Supports | temperature, humidity and pressure |
| Picture | ![Xiaomi WSDCGQ11LM](../images/devices/WSDCGQ11LM.jpg) |

## Notes


### Pairing
Press and hold reset button on the device for +- 5 seconds until the
blue light blinks three times, release the reset button (the blue light will blink once more) and wait.

*NOTE: When you fail to pair a device, try replacing the battery, this could solve the problem.*


### Device type specific configuration
*[How to use device type specific configuration](../configuration/device_specific_configuration.md)*


* `temperature_precision`: Controls the precision of `temperature` values,
e.g. `0`, `1` or `2`; default `2`.
* `temperature_calibration`: Allows to manually calibrate temperature values,
e.g. `1` would add 1 degree to the temperature reported by the device; default `0`.


* `humidity_precision`: Controls the precision of `humidity` values, e.g. `0`, `1` or `2`; default `2`.


* `pressure_precision`: Controls the precision of `pressure` values, e.g. `0` or `1`; default `1`.
* `pressure_calibration`: Allows to manually calibrate pressure values,
e.g. `1` would add 1 to the pressure reported by the device; default `0`.


## Manual Home Assistant configuration
Although Home Assistant integration through [MQTT discovery](../integration/home_assistant) is preferred,
manual integration is possbile with the following configuration:


{% raw %}
```yaml
sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "°C"
    device_class: "temperature"
    value_template: "{{ value_json.temperature }}"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "%"
    device_class: "humidity"
    value_template: "{{ value_json.humidity }}"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "hPa"
    device_class: "pressure"
    value_template: "{{ value_json.pressure }}"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "%"
    device_class: "battery"
    value_template: "{{ value_json.battery }}"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "-"
    value_template: "{{ value_json.linkquality }}"
```
{% endraw %}


