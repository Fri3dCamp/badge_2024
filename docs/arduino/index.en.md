
download the Arduino IDE from <https://www.arduino.cc/en/software>

# Arduino IDE setup steps
For the Fri3d badge to be usable in the Arduino IDE, you need to install version 2.0.17 of the esp32 board package. Below are the steps:

## General Arduino IDE Setup
- From the Tools Menu, select Boards -> Boards Manager in the Arduino IDE, then install **version 2.0.17** of the esp32 package.
  - Reason for version 2.0.17 is that I tried version 3.0.2 and **version 3.0.2 causes compilation errors** for the ESP32S3 board.
- From the Tools Menu, select Board -> esp32 -> ESP32S3 Dev Module

## How to Upload in Arduino IDE
- Turn on your badge
- connect your badge via usb to your computer
- From the Tools Menu, select Port and select the entry that looks like it might be your badge.
- Click the Upload Button (right pointing arrow button in green)