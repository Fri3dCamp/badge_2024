# ESPHome documentation

This page contains reference code for each badge component. It currently assumes you have [esphome](https://esphome.io/guides/getting_started_command_line) installed and are familiar adding a device.

## Common code
```
substitutions:
  esphome_name: fri3d2024

esphome:
  name: ${esphome_name}

esp32:
  board: esp32-s3-devkitc-1
  framework:
    type: arduino
```

## Display
```
spi:
  clk_pin: GPIO7
  mosi_pin: GPIO6

display:
  - platform: ili9xxx
    model: ST7789V
    dimensions:
      height: 240
      width: 296
    transform:
      swap_xy: true
      mirror_x: false
    data_rate: 80MHz
    dc_pin: GPIO4
    cs_pin: GPIO5
    reset_pin: GPIO48
    auto_clear_enabled: false
    lambda: |-
      it.image(0, 0, id(my_image));
#      it.print(0, 0, id(my_font), "Hello World!");
#      it.printf(0, 15, id(my_font), TextAlign::BASELINE_LEFT, "%.1f graden", id(temperature).state);
# sensor.living_room_temperature
#      it.line(0, 0, 50, 50);

font:
  - file: "opensans.ttf"
    id: my_font
    size: 20

image:
  - file: "fri3d.png"
    id: my_image
    type: RGB24
```
*TODO*
- refresh log error

## Status light
```
light:
  - platform: status_led
    name: "State"
    id: "state"
    pin: GPIO21
```

## RGB leds
```
light:
  - platform: neopixelbus
    type: GRB
    variant: WS2812
    pin: GPIO12
    num_leds: 5
    name: "NeoPixel Light"
```

## Buttons
```
binary_sensor:
  - platform: gpio
    pin:
      number: GPIO39
      mode:
        input: true
        pullup: true
      inverted: true
    name: "A"
  - platform: gpio
    pin:
      number: GPIO40
      mode:
        input: true
        pullup: true
      inverted: true
    name: "B"
  - platform: gpio
    pin:
      number: GPIO38
      mode:
        input: true
        pullup: true
      inverted: true
    name: "X"
  - platform: gpio
    pin:
      number: GPIO41
      mode:
        input: true
        pullup: true
      inverted: true
    name: "Y"
  - platform: gpio
    pin:
      number: GPIO45
      mode:
        input: true
        pullup: true
      inverted: true
    name: "menu"
  - platform: gpio
    pin:
      number: GPIO0
      mode:
        input: true
        #pullup: true
      inverted: true
    name: "start"
```

## Joystick
```
sensor:
  - platform: adc
    id: joystick_x  
    name: "Joystick X axis"  
    pin: GPIO01
    internal: True
    attenuation: auto
    update_interval: 500ms

  - platform: adc
    id: joystick_y  
    name: "Joystick Y axis"  
    pin: GPIO03
    internal: True
    attenuation: 11db
    update_interval: 500ms
```
*TODO*
- disable logging
- on_xxx: left/right & up/down

## Buzzer
```
```
*TODO*
- test

## Accelerometer
```
i2c:
  sda: GPIO9
  scl: GPIO18
  scan: true
  id: bus_i2c
```
*TODO*
- contribute code & test

## IR Receiver
```
remote_receiver:
  pin:
    number: GPIO11
    inverted: true
    mode:
      input: true
      pullup: true
  dump: all
```
*TODO*
- test

## Battery monitor
```
```
*TODO*
- test

## AUX power
```
```
*TODO*
- test

## SD Card
```
```
*TODO*
- define use case

