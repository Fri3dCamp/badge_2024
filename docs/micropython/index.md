# MicroPython documentation

## Flash the default fri3d micropython firmware
download firmware from
https://github.com/cheops/fri3d-ota/tree/main/ota/fri3d_badge_2024
select the version and then the *.zip file in that folder

flasher app 
https://fri3d-flasher.vercel.app/#/

You might need to put the badge in DOWNLOAD mode manually:
- PRESS + HOLD the START button
- PRESS the RESET button (while HOLDING the START button)
- the badge has now restarted in download mode

after the download you might need to reset the badge to boot normally (PRESS the RESET button)


## How to run a local file
Install `mpremote` [howto](https://docs.micropython.org/en/latest/reference/mpremote.html)

TLDR; `pip install mpremote`

```sh
mpremote resume run local_test_file.py
```
Unfortunately `Thonny` interrupts the startup of the badge when connecting, leaving some items (spi, display) in an undefined state.  
The same for `mpremote` if not supplied with the `resume` argument.

## how to copy a file to the badge
```sh
mpremote resume fs cp local_path/file.jpg :file.jpg
```

The badge has [lvgl](lvgl) built-in.