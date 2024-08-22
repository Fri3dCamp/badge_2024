# Programming the LANA Module
To program the small [LANA](https://phyx.be/LANA_TNY/) module on your `blaster` (flamingo), you can use either [Embeetle IDE](https://embeetle.com/) or [Mounriver Studio](http://www.mounriver.com/). 

&nbsp;<br>
# Embeetle IDE
Embeetle is an IDE of Belgian make. The LANA can be programmed directly via the USB-C connector but also with the [WCH-Link debugger](https://www.wch-ic.com/products/WCH-Link.html), which gives extra debugging options. <a href="https://embeetle.com/#supported-hardware/wch/boards/lana-tny-01">Click here</a> For the complete documentation on how to program the LANA module in Embeetle. The steps below show how to get started quickly to program your LANA module via its USB-C port.

&nbsp;<br>
## STEP 1: Download Embeetle IDE
First download Embeetle:
 - [https://embeetle.com/downloads](https://embeetle.com/#embeetle-ide/download)

You can download it for either **Windows** or **Linux**. We don't have MAC support yet.

<img src="https://github.com/user-attachments/assets/59498d20-e134-4101-98d4-90c1bf618ca1" width="400">

&nbsp;<br>
## STEP 2: Launch the `lana-tny-01-blaster-2024` project
Launch Embeetle and click 'CREATE PROJECT':

<img src="https://github.com/user-attachments/assets/8d881776-0d6e-4dac-a253-c3d7d610ed76" width="600">

&nbsp;<br>
Then select `WCH` for the vendor (that's the vendor of the microcontroller) and look for the project `lana-tny-01-blaster-2024`:

<img src="https://github.com/user-attachments/assets/a00f00fb-5c35-4ee6-9703-bc0f17b03a32" width="600">

&nbsp;<br>
Now click `CREATE` at the bottom. Embeetle IDE will download the sample project and also all the required tools automatically. Then the project opens:

![image](https://github.com/user-attachments/assets/caac076a-4451-4286-8899-637ecab647cd)

&nbsp;<br>
## STEP 3: Plug in the board
Important: your badge must be disconnected from the `blaster` (flamingo) (5V from the USB will distroy your 3,3V badge)  
FIRST press the `BOOT` switch, THEN plug your board into the computer with a USB-C cable (while keeping the `BOOT` switch pressed):

<img src="https://github.com/user-attachments/assets/da84c6b6-a243-4aa3-ab76-96eced937d2a" width="200">

When the board is plugged in, you can release the `BOOT` switch. This procedure ensures that your board is now in "bootloader mode". That means the microcontroller is ready to receive a new firmware!

&nbsp;<br>
## STEP 4: Flash the firmware
Now click the `flash` button at the top in Embeetle IDE. Embeetle will try to flash the firmware to the LANA module. However, you might experience the following error now:
```
Failed to open USB device: Bus 001 Device 008: ID 4348:55e0
Error: Failed to open USB device on Windows
```
On Linux you might experience another issue:
```
Failed to open USB device: Bus 003 Device 010: ID 4348:55e0
Error: Failed to open USB device on Linux due to no enough permission
```
Let's fix this.

&nbsp;<br>
## STEP 5a: Install Zadig (Windows only)
You must install [Zadig](https://zadig.akeo.ie/) and replace the driver for the USB device with the WinUSB driver. First, [download Zadig](https://zadig.akeo.ie/): 

<img src="https://github.com/user-attachments/assets/d537fe6a-de71-48dd-9269-857ddcadfe81" width="600">

&nbsp;<br>
Then, open Zadig and select **Options** -> **List All Devices**:

<img src="https://github.com/user-attachments/assets/7000ec9f-a97e-4c05-a57d-42b7e0265a69" width="600">

&nbsp;<br>
Select **USB Module** from the list of devices and choose **WinUSB** as the driver. Then click **Replace Driver**:

<img src="https://github.com/user-attachments/assets/c5cb00ea-d307-4fd1-a668-03270ae98f34" width="600">

&nbsp;<br>
Maybe you didn't find **USB Module** in the list of devices? In that case, you might find **Unknown Device #1** instead. Take that one and choose **WinUSB** as the driver. Then click **Replace Driver**:

<img src="https://github.com/user-attachments/assets/aef2f087-8a58-48e2-8b7c-f9f30b3cbd15" width="600">

&nbsp;<br>
Wait for the driver installation to complete:

<img src="https://github.com/user-attachments/assets/b55a5996-c4af-4f2c-ac66-8b4f59a05aed" width="600">

&nbsp;<br>
Success:

<img src="https://github.com/user-attachments/assets/4afdf22e-804a-4845-92a7-93bcdd6be906" width="600">

&nbsp;<br>
Try again in Embeetle IDE. It should work now:

```
"C:/Users/krist/EMBEETLE IDE/embeetle/beetle_tools/windows/wchisp_0.2.2_64b/wchisp.exe" flash application.elf
14:57:06 [INFO] Chip: CH32V203G6U6[0x3619] (Code Flash: 32KiB)
14:57:06 [INFO] Chip UID: CD-AB-19-97-D0-BC-B6-FF
14:57:06 [INFO] BTVER(bootloader ver): 02.70
14:57:06 [INFO] Code Flash protected: false
14:57:06 [INFO] Current config registers: a55aff0000ff00ffffffffff00020700cdab1997d0bcb6ff
RDPR_USER: 0x00FF5AA5
  [7:0]   RDPR 0xA5 (0b10100101)
    `- Unprotected
  [16:16] IWDG_SW 0x1 (0b1)
    `- IWDG enabled by the software, and disabled by hardware
  [17:17] STOP_RST 0x1 (0b1)
    `- Disable
  [18:18] STANDBY_RST 0x1 (0b1)
    `- Disable, entering standby-mode without RST
  [23:22] SRAM_CODE_MODE 0x3 (0b11)
    `- CODE-228KB + RAM-32KB / CODE-160KB + RAM-32KB depending on the chip
DATA: 0xFF00FF00
  [7:0]   DATA0 0x0 (0b0)
  [23:16] DATA1 0x0 (0b0)
WRP: 0xFFFFFFFF
  `- Unprotected
14:57:06 [INFO] Read application.elf as ELF format
14:57:06 [INFO] Found loadable segment, physical address: 0x00000000, virtual address: 0x00000000, flags: 0x5
14:57:06 [INFO] Section names: [".init", ".vector", ".text"]
14:57:06 [INFO] Found loadable segment, physical address: 0x00000dbc, virtual address: 0x20000000, flags: 0x6
14:57:06 [INFO] Section names: [".data"]
14:57:06 [INFO] Firmware size: 4096
14:57:06 [INFO] Erasing...
14:57:06 [WARN] erase_code: set min number of erased sectors to 8
14:57:06 [INFO] Erased 8 code flash sectors
14:57:07 [INFO] Erase done
14:57:07 [INFO] Writing to code flash...
██████████████████████████████████████ 4096/409614:57:07 [INFO] Code flash 4096 bytes written
14:57:08 [INFO] Verifying...
██████████████████████████████████████ 4096/409614:57:08 [INFO] Verify OK
14:57:08 [INFO] Now reset device and skip any communication errors
14:57:08 [INFO] Device reset
```

If it didn't work, pull out the LANA module and plug it back into your computer while pressing the `BOOT` switch (release the button a few seconds after you plugged it into the computer), to ensure it really is in "bootloader mode". If it still doesn't work, don't hesitate to contact us:
 - Email: kristof@embeetle.com
 - Whatsapp: +32(0) 496 90 75 44
 - Discord: @kristof-at-embeetle

&nbsp;<br>
## STEP 5b: Add device to plugdev group (Linux only)
On Linux you'll have to add the device to the **plugdev** group. First check groups related to the current user:
```
$ groups `whoami`
kristof : kristof adm cdrom sudo dip plugdev lpadmin lxd sambashare
```
If `plugdev` would not be listed, add the current user to that group: 
```
$ sudo useradd -G plugdev `whoami`
```
Figure out your device's Vendor ID and Product ID through the `$ lsusb` command: 
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c548 Logitech, Inc. Logi Bolt Receiver
Bus 003 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 004: ID 04f2:b75c Chicony Electronics Co., Ltd FHD Webcam
Bus 003 Device 005: ID 1a2c:4324 China Resource Semico Co., Ltd USB Keyboard
Bus 003 Device 006: ID 048d:6005 Integrated Technology Express, Inc. ITE Device(8291)
Bus 003 Device 007: ID 1bcf:2701 Sunplus Innovation Technology Inc. HD 720P webcam
Bus 003 Device 008: ID 048d:ce00 Integrated Technology Express, Inc. ITE Device(8291)
Bus 003 Device 009: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 011: ID 4348:55e0 WinChipHead
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 0bda:0316 Realtek Semiconductor Corp. Card Reader
```
Look for the line with `WinChipHead` (third to last). As you can see, the ID for my device consists of two 4-digit hex numbers: `ID 4348:55e0`. The first one is the Vendor ID, the second one the Product ID. Do not confuse them! 

In the console, navigate to `/etc/udev/rules.d` and list the contents of the directory:
```
$ cd /etc/udev/rules.d
$ ls
70-snap.core.rules
70-snap.firefox.rules
70-snap.snap-store.rules
```
Now create a new file, for example with the gedit editor: 
```
$ sudo gedit 10-probe.rules
```
You can name this file whatever you want, so long as it ends in `.rules`. Rules files by convention begin with a number. Linux parses rules files in lexical order, and the number makes it easy to see which files will be parsed first. Choosing a low number (like 10, as above) means that your file will be parsed before system rules files.

Now you need to add a line in the file that represents your device. If the file already existed (from a previous device you added this way), you can leave all the content as-is and just add a line at the bottom. The line you need to add is:
```
ATTRS{idVendor}=="4348", ATTRS{idProduct}=="55e0", MODE="666", GROUP="plugdev"
```
<small>Note: In older Ubuntu/Linux installations, you might need to replace 'ATTRS' with 'SYSFS' in the line below.</small>

Of course, fill in your own Vendor ID and Product ID! (although the ones above should be correct for the `LANA-TNY-01` board).
Save the file and close it. Now you need to tell Linux to reload the udev rules:
```
$ sudo udevadm trigger
```
Any member of the **plugdev** group should now be able to run `wchisp` without using sudo. 

Try again to flash in Embeetle IDE.
If it doesn't work, pull out the LANA module and plug it back into your computer while pressing the `BOOT` switch (release the button a few seconds after you plugged it into the computer), to ensure it really is in "bootloader mode". If it still doesn't work, don't hesitate to contact us:
 - Email: kristof@embeetle.com
 - Whatsapp: +32(0) 496 90 75 44
 - Discord: @kristof-at-embeetle

&nbsp;<br>
# Mounriver Studio
[Mounriver](http://www.mounriver.com/) is an ide based on eclipse released by the chipmaker WCH. This works on Windows and there is a version for linux and possibly also for Mac, but the last 2 are a bit behind. [Mounriver](http://www.mounriver.com/) also gives false reports of viruses on many systems and violates the GPL license conditions of the GCC Compiler.

&nbsp;<br>
# Notes on LANA module
If you are going to work with the blaster/LANA TNY yourself, you have to pay attention to 1 thing (regardless of the IDE) that is that LANA does not have an external clock and must use the internal clock (HSI), this is also stated in the default sketch of [Embeetle](https://embeetle.com/).
If you accidentally "brick" your [LANA](https://phyx.be/LANA_TNY/) board, you can usually unbrick it via USB or by using the power reset feature of the [WCHISPTool](https://www.wch-ic.com/downloads/WCHISPTool_Setup_exe.html).
