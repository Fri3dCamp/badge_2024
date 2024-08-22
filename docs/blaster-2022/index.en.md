# Upgrade your Blaster-2022
You have a `blaster-2022` and you want to upgrade it to the latest software, so you can shoot together with the blasters from 2024? 

<img src="https://github.com/user-attachments/assets/ffb33687-16a3-4096-b759-7f38967c1e2d" width="400">

You can upgrade the firmware at the `badge flash station`. If you have an advanced version of the `blaster-2022` - with programmer - then you can also upgrade your firmware from your laptop with Embeetle IDE. On this page you'll find all the required steps.

&nbsp;<br>
# Embeetle IDE
Embeetle is an IDE of Belgian make. You can program the LANA module with it on the `blaster-2024` (flamingo), but you can also program the Atmel chip on the older `blaster-2022`.

&nbsp;<br>
## STEP 1: Download Embeetle IDE
First download Embeetle:
 - [https://embeetle.com/downloads](https://embeetle.com/#embeetle-ide/download)

You can download it for either **Windows** or **Linux**. We don't have MAC support yet.

<img src="https://github.com/user-attachments/assets/59498d20-e134-4101-98d4-90c1bf618ca1" width="400">

&nbsp;<br>
## STEP 2: Launch the `arduino-uno-blaster-2022` project
Launch Embeetle and click 'CREATE PROJECT'. Then select `Arduino` for the vendor and look for the project `arduino-uno-blaster-2022`:

<img src="https://github.com/user-attachments/assets/b7591d2e-6726-4ac6-aa90-f76f0e7ef021" width="600">

&nbsp;<br>
Now click `CREATE` at the bottom. Embeetle IDE will download the sample project and also all the required tools automatically. Then the project opens:

![image](https://github.com/user-attachments/assets/f7655b77-4fcc-4ea9-843f-ba8a7f89ddf7)

What you see in this screenshot is basically an Arduino UNO project that has been converted into a full-fledged makefile-based C/C++ project. Unlike Arduino, Embeetle IDE gives you access to all the driver files, linker scripts, assembly startup files and more! Nothing is hidden.

&nbsp;<br>
## STEP 3: Plug in the board
Important: your badge must be disconnected from the blaster (5V from the USB will distroy your 3,3V badge)  
Plug in your `blaster-2022` device.

&nbsp;<br>
## STEP 4: Flash the firmware
Now click the `flash` button at the top in Embeetle IDE. Embeetle flashes the firmware to the Atmel chip.

If the flash doesn't work, please check out the solutions on this page:

[Embeetle IDE Arduino UNO installation page](https://embeetle.com/#supported-hardware/arduino/probes/default)
