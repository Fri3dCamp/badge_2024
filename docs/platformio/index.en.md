# PlatformIO

## Visual Studio Code

You can download VS Code from <https://code.visualstudio.com/>.
Don't worry about what other extensions you need, you can easily install them whenever you need them.

## PlatformIO extension

1. Inside Visual Studio Code, go to the extensions tab. (CTRL+SHIFT+X)
2. In the search bar, type "platformio"
3. Install the one with the orange alien icon

  ![screenshot](platformio.png)

## Hello World

1. go to PlatformIO window (click on the alien face in the left column)
2. Choose "New Project"
      1. Alternatively, if you see the "PIO Home" window, you can click "+ new project" there.
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

<https://github.com/Fri3dCamp/badge_2024_arduino/tree/main/examples/platformio%20basic%20examples>

If you just want to try all examples:

1. In GitHub, goto <https://github.com/Fri3dCamp/badge_2024_arduino>
2. Click "Fork"
3. You now have the same repository, but in your own profile
4. Click the green button `<> Code`
5. copy the URL you see in the pop-up
6. Open the Git Bash CLI where you want to create the forked repository
7. Type `git clone ` and paste the URL from the Github repository

## Your own code on GitHub

1. Download GIT from <https://git-scm.com/downloads>
2. Create an account on <https://github.com>
3. At the top of the screen, click "+", click "New repository"
4. Follow the GitHub instructions to clone your repository to your local hard drive
5. Code away!
6. Open the Git Bash CLI in the root folder of your repository
7. `git add .`
8. `git commit -m "cool new program"`
9. `git push`
10. Check that your code has arrived on GitHub

## Your code in the Fri3d Camp repository

1. In GitHub, goto <https://github.com/Fri3dCamp/badge_2024_arduino>
2. Click "Fork"
3. You now have the same repository, but in your own profile
4. Click the green button `<> Code`
5. Copy the URL you see in the pop-up
6. Open the Git Bash CLI where you want to create the forked repository
7. Type `git clone ` and paste the URL from the Github repository

So far, the instructions are exactly the same as for downloading the examples

8. In github click on `main` to create a new branch
9. In the search bar, type a name of your choice, e.g. `newexample`
10. Click `create branch newexample` from main
11. Open the Git Bash CLI in the root folder of your repository
12. `git checkout -b newexample`
13. Add your example
14. `git add .`
15. `git commit -m "I created a new example"`
16. `git push`
17. in GitHub, click `compare and pull request`
18. Add a nice description,
19. Click `Create pull request`