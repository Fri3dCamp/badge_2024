# MicroPython documentation

## Flash the default fri3d micropython firmware
download firmware from
https://github.com/cheops/fri3d-ota/blob/main/ota/fri3d_badge_2024/0.0.2/fri3d_badge_2024-0.0.2.zip

flasher app 
https://fri3d-flasher.vercel.app/#/


## How to run a local file
Install `mpremote` [howto](https://docs.micropython.org/en/latest/reference/mpremote.html)

`pip install mpremote`

```
mpremote resume run local_test_file.py
```
Unfortunately `Thonny` interrupts the startup of the badge when connecting, leaving some items (spi, display) in an undefined state.  
The same for `mpremote` if not supplied with the `resume` argument.

## how to copy a file to the badge
```
mpremote resume fs cp local_path/file.jpg :file.jpg
```