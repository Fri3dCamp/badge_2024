# Flashing

![Rest to Firmware Neuralizer](neuralizer.jpg)

After your adventures in programming yielded unexpected results, you might want to go back to the default firmware.

## Fri3d Camp Reset Booth

During the Fri3d Camp, at the "Badge EHBO", we can help you!
Look around for a "badge reset firmware" booth on the Fri3d camp. We sort of anticipated this ... :-)

## Web interface

The online flasher app works with chrome based browsers (Chrome, Edge) (not Firefox, Safari).

1. download latest zip file from <https://github.com/tomvanbraeckel/retro-go-fri3d/releases>
2. go to <https://fri3d-flasher.vercel.app/>
3. click on icon to upload the zip file you downloaded earlier
4. click "begin te flashen" button

If the flashing fails because your badge keeps resetting, you can force every ESP32-based board as follows:
    11. press and hold "start" button (this is the "boot" button of the microcontroller)
    12. press and release "reset" button
    13. your badge will now be ready to be flashed with a new program
    
Now the device should boot into the Fri3d App.

## ESP-IDF

This is the complicated version. Only worth it if the web flasher failed.

1. if your badge seems to reset every few seconds, You can force every ESP32-based board as follows:
    11. press and hold "start" button (this is the "boot" button of the microcontroller)
    12. press and release "reset" button
    13. your badge will now be ready to be flashed with a new program
2. install ESP-IDF <https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/index.html#installation>
3. download the latest firmware from <https://github.com/Fri3dCamp/badge_2024_micropython>
4. on your command line interface type:

        python -m esptool -p (PORT) -b 460800 --before default_reset --after no_reset --chip esp32s3 write_flash --flash_mode dio --flash_size 16MB --flash_freq 80m 0x0 bootloader.bin 0x8000 partition-table.bin 0x1d000 ota_data_initial.bin 0x30000 micropython.bin

