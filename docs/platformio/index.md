# PlatformIO

## Installation

### Visual Studio Code

### PlatformIO extension

## Hello World

1. go to PlatformIO window
2. Choose "New Project"
3. For board, choose "esp32-s3-devkitc-1". PlatformIO will start downloading necessary libraries
4. Open platformio.ini - you should see the following:
```
[env:esp32-s3-devkitc-1]
platform = espressif32
board = esp32-s3-devkitc-1
framework = arduino
```
5. add the following lines at the bottom:
```
board_build.arduino.memory_type = qio_opi 
board_build.partitions = default_16MB.csv
board_upload.flash_size = 16MB
monitor_speed = 115200
lib_deps = bodmer/TFT_eSPI@^2.5.33
build_flags = 
    -DBOARD_HAS_PSRAM # N16R8V has PSRAM
    -DARDUINO_USB_MODE=1 # necessary for serial port
    -DARDUINO_USB_CDC_ON_BOOT=1 # necessary for serial port
```


## Examples in GitHub

## Your own code on GitHub

## Your code in the Fri3d Camp repository