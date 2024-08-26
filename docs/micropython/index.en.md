# MicroPython documentation

## Start micropython
1. Ensure your badge is upgraded to the latest version. [instructions](../reset)
1. After flashing has finished, press reset so that the main menu appears (with green buttons: Ota, Hello, Micropython, Retro-go)
1. Connect with [Fri3d ViperIDE](https://fri3dcamp.github.io/viper/)
   This will give a timeout error (because the micropython REPL does not answer, this is OK)
1. Now you can see on the bottom of the screen the serial logging of the badge
1. On the badge select micropython en press A
1. The badge reboots and you will see the serial output of the boot process. Do not interrupt this process!! Micropython is extracting the files to the fat partition.
1. After a while you will see a REPL promt `>>> `
1. You can now disconnect and reconnect the [Fri3d ViperIDE](https://fri3dcamp.github.io/viper/)

## improved `main.py`
By default, the badge will **not** reboot into MicroPython on reset.  
Should you want this, you need to confirm the switch to MicroPython was successful.  
You can do this like this:

```python
from fri3d import boot
boot.persist()
```
Note that now you no longer can get back to the main menu.  
To switch back you need to do this:  
```python
from fri3d import boot
boot.main_menu()
```

now let's put this into action in an improved version of `main.py`
```python
# Hello and welcome to the code of the Fri3d Badge!
# You have located the main entrypoint where the code of your badge is launched from.
# Feel free to modify this file or any of the files in the fri3d package.

# In case you mess up, just delete this file using the REPL, and it will be restored to the original state.
# Similarly, if you delete the fri3d or user package it will also get restored to its original state

import logging

from fri3d.badge.buttons import buttons
from fri3d import boot

# If you want you can increase the log output level here
logging.basicConfig(level=logging.INFO, force=True)

# create a logger for use in this file
logger = logging.Logger(__file__)

# create a callback function that is executed when the menu button is pressed, it needs to have 1 argument
def menu_button(_):
    logger.warning("MENU button pressed, rebooting to main menu")
    boot.main_menu()

# assign the callback function to the menu button
buttons.menu.cb = menu_button

logger.info("From now on you can press the MENU button to reboot to the main menu")

# stay in micropython, now that we have a button to go back to the main menu
boot.persist()
```

## Badge Examples
There are examples installed on the badge itself. [sources](https://github.com/Fri3dCamp/badge_2024_micropython/tree/develop/fri3d/fri3d_application/src/payload/examples)

You can explore these with [ViperIDE](https://fri3dcamp.github.io/viper/)

If some of the first 4 examples fail to run, this is likely because the first micropython boot was interrupted. The easiest way to fix this is to follow the steps above [Start micropython](#start-micropython).

## How to create and run a new file on your badge in Fri3d ViperIDE
Example to create a file `user/marco/first.py` on your badge and run it
1. Connect to your badge with [Fri3d ViperIDE](https://fri3dcamp.github.io/viper/)
1. on the left side in the files scroll down to the `user`folder
1. click on the `+`-sign next to the `user` folder
1. to create a folder end it with a `/`, so for our example fill in `marco/`
1. now click on the `+`-sign next to the `marco` folder
1. create a file `first.py`
1. in the file editor type
```python
print("Shout: Marco!")
print("...")
print("Answer: Polo!")
```
1. to run this example click on the blue play button (F5)
1. observe the output of this example on the bottom in the Terminal of ViperIDE
```
>>> 
Shout: Marco!
...
Answer: Polo!
>
>>> 
```

## How to reboot to the main menu when pressing the MENU button
run this script once in your active session and a press of the MENU button will bring you back to the main badge menu
```python
from fri3d.badge.buttons import buttons
from fri3d import boot

def menu_button(_):
    print("MENU button pressed")
    boot.main_menu()

buttons.menu.cb = menu_button
```

## How to run a local file
Install `mpremote` [howto](https://docs.micropython.org/en/latest/reference/mpremote.html)

TLDR; `pip install mpremote`

```sh
mpremote run local_test_file.py
```

[Thonny](https://thonny.org/) also works fine.

Unfortunately the cleanup of the Display module does not work entirely, so after this has been initialized and your next script tries to initialize it again, this will give errors.
You need to perform a hard reset (reset button on the badge)

## how to copy a file to the badge
```sh
mpremote resume fs cp local_path/file.jpg :file.jpg
```

## Blink the badge leds 10 times red
```python
import time
from fri3d.badge.leds import leds

for _ in range(10):
   leds.fill((255, 0, 0))
   leds.write()

   time.sleep(0.5)

   leds.fill((0, 0, 0))
   leds.write()

   time.sleep(0.5)
```

## Start the Fri3d application
```python
from fri3d.application import Application

app_main = Application()
app_main.run()
```

## Micropython libraries
Micropython [quick reference for the esp32](https://docs.micropython.org/en/v1.22.0/esp32/quickref.html)

Micropython standard libraries overview [doc](https://docs.micropython.org/en/v1.22.0/library/index.html)

The badge has [lvgl](lvgl) built-in.

Other interesting links
- https://github.com/peterhinch/micropython-samples
- https://github.com/mcauser/awesome-micropython

## micropython game ideas
- https://hackaday.com/2021/05/25/simple-micropython-game-is-a-30-minute-game-dev-course/
- pinball [link1](https://github.com/russhughes/s3lcd/blob/main/examples/pinball.py) or [link2](https://github.com/russhughes/st7789_mpy/blob/master/examples/pinball.py)
- [gameESP](https://github.com/cheungbx/gameESP-micropython)
- [snake](https://github.com/cheops/badge_2024_micropython/blob/s3lcd/fri3d/modules/demos/snake.py)
