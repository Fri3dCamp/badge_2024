# De LANA Module Programmeren
Om de [LANA](https://phyx.be/LANA_TNY/) module op je `communicator` te programmeren, kun je zowel [Embeetle IDE](https://embeetle.com/) als [Mounriver Studio](http://www.mounriver.com/) gebruiken.

&nbsp;<br>
# Embeetle IDE
Embeetle is een IDE van Belgische makelij. De LANA kan worden geprogrammeerd via USB-C-aansluiting, maar ook met de [WCH-Link debugger](https://www.wch-ic.com/products/WCH-Link.html), wat extra debug-mogelijkheden biedt. <a href="https://embeetle.com/#supported-hardware/wch/boards/lana-tny-01">Klik hier</a> voor de volledige documentatie over hoe je de LANA module in Embeetle kunt programmeren. De onderstaande stappen zijn een quick start guide om je LANA module via de USB-C-poort te programmeren.

&nbsp;<br>
## STAP 1: Download Embeetle IDE
Download eerst Embeetle:
 - [https://embeetle.com/downloads](https://embeetle.com/#embeetle-ide/download)

Je kunt het downloaden voor zowel **Windows** als **Linux**. We hebben nog geen ondersteuning voor MAC.

<img src="https://github.com/user-attachments/assets/59498d20-e134-4101-98d4-90c1bf618ca1" width="400">

&nbsp;<br>
## STAP 2: Start het `lana-tny-01-communicator-2024` project
Start Embeetle en klik op 'CREATE PROJECT':

<img src="https://github.com/user-attachments/assets/8d881776-0d6e-4dac-a253-c3d7d610ed76" width="600">

&nbsp;<br>
Selecteer vervolgens `WCH` als chip fabrikant en zoek naar het project `lana-tny-01-communicator-2024`:

<img src="https://github.com/user-attachments/assets/9351d454-d978-404a-a586-55c1118d5d01" width="600">

&nbsp;<br>
Klik onderaan op `CREATE`. Embeetle IDE zal het project en ook alle benodigde tools automatisch downloaden. Dan opent het project:

![image](https://github.com/user-attachments/assets/caac076a-4451-4286-8899-637ecab647cd)

&nbsp;<br>
## STAP 3: Plug het bordje in
Belangrijk: je badge mag niet aangesloten zijn aan de communicator (5V van de USB maakt je 3,3V badge stuk)
DRUK EERST op de `BOOT`-knop en SLUIT DAN je bordje aan op de computer met een USB-C-kabel (terwijl je de `BOOT`-knop ingedrukt houdt):

<img src="https://github.com/user-attachments/assets/da84c6b6-a243-4aa3-ab76-96eced937d2a" width="200">

Wanneer het bordje is aangesloten, kun je de `BOOT`-knop loslaten. Deze procedure zorgt ervoor dat je bordje in "bootloader-modus" komt. Dit betekent dat de microcontroller klaar is om nieuwe firmware te ontvangen!

&nbsp;<br>
## STAP 4: Flash de firmware
Klik nu op de `flash`-knop bovenaan in Embeetle IDE. Embeetle zal proberen de firmware naar de LANA module te flashen. Echter, je kunt nu de volgende foutmelding krijgen:
```
Failed to open USB device: Bus 001 Device 008: ID 4348:55e0
Error: Failed to open USB device on Windows
```
Op Linux kun je een ander probleem tegenkomen:
```
Failed to open USB device: Bus 003 Device 010: ID 4348:55e0
Error: Failed to open USB device on Linux due to no enough permission
```
Hieronder is de oplossing.

&nbsp;<br>
## STAP 5a: Installeer Zadig (alleen Windows)
Je moet [Zadig](https://zadig.akeo.ie/) installeren en de driver voor het USB-apparaat vervangen door de WinUSB-driver. Download eerst [Zadig](https://zadig.akeo.ie/): 

<img src="https://github.com/user-attachments/assets/d537fe6a-de71-48dd-9269-857ddcadfe81" width="600">

&nbsp;<br>
Open vervolgens Zadig en selecteer **Options** -> **List All Devices**:

<img src="https://github.com/user-attachments/assets/7000ec9f-a97e-4c05-a57d-42b7e0265a69" width="600">

&nbsp;<br>
Selecteer **USB Module** uit de list of devices en kies **WinUSB** als driver. Klik vervolgens op **Replace Driver**:

<img src="https://github.com/user-attachments/assets/c5cb00ea-d307-4fd1-a668-03270ae98f34" width="600">

&nbsp;<br>
Wacht tot de driver-installatie is voltooid:

<img src="https://github.com/user-attachments/assets/b55a5996-c4af-4f2c-ac66-8b4f59a05aed" width="600">

&nbsp;<br>
Succes:

<img src="https://github.com/user-attachments/assets/4afdf22e-804a-4845-92a7-93bcdd6be906" width="600">

&nbsp;<br>
Probeer het opnieuw in Embeetle IDE. Het zou nu moeten werken:

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


Als het niet werkte, trek dan de LANA-module eruit en sluit hem opnieuw aan op je computer terwijl je de `BOOT`-knop ingedrukt houdt (laat de knop een paar seconden na het aansluiten op de computer los), om ervoor te zorgen dat het echt in "bootloader-modus" is. Als het nog steeds niet werkt, aarzel dan niet om contact met ons op te nemen:
 - E-mail: kristof@embeetle.com
 - Whatsapp: +32(0) 496 90 75 44
 - Discord: @kristof-at-embeetle

&nbsp;<br>
## STAP 5b: Voeg apparaat toe aan plugdev groep (alleen Linux)
Op Linux moet je het apparaat toevoegen aan de **plugdev** groep. Controleer eerst de groepen die gekoppeld zijn aan de huidige gebruiker:
```
$ groups whoami
kristof : kristof adm cdrom sudo dip plugdev lpadmin lxd sambashare
```
Als `plugdev` niet is vermeld, voeg dan de huidige gebruiker toe aan die groep: 
```
$ sudo useradd -G plugdev whoami
```
Bepaal de Vendor ID en Product ID van je apparaat met het `$ lsusb` commando: 
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
Zoek naar de lijn met `WinChipHead` (derde van onder). Zoals je kunt zien, bestaat de ID voor mijn apparaat uit twee 4-cijferige hex-getallen: `ID 4348:55e0`. De eerste is de Vendor ID, de tweede de Product ID. Verwissel ze niet!

Navigeer in de console naar `/etc/udev/rules.d` en lijst de inhoud van de directory:
```
$ cd /etc/udev/rules.d
$ ls
70-snap.core.rules
70-snap.firefox.rules
70-snap.snap-store.rules
```
Maak een nieuw bestand aan, bijvoorbeeld met de gedit-editor: 
```
$ sudo gedit 10-probe.rules
```
Je kunt dit bestand een willekeurige naam geven, zolang het maar eindigt op `.rules`. Rules files beginnen bij conventie met een nummer. Linux behandelt rules files in lexicale volgorde, en het nummer maakt het gemakkelijk te zien welke bestanden eerst worden gelezen. Het kiezen van een laag nummer (zoals 10, hierboven) betekent dat je bestand wordt gelezen vóór de system rules files.

Nu moet je een lijn aan het bestand toevoegen die je apparaat vertegenwoordigt. Als het bestand al bestond (van een eerder toegevoegd apparaat op deze manier), kun je alle inhoud laten zoals die is en gewoon een lijn onderaan toevoegen. De lijn die je moet toevoegen is:
```
ATTRS{idVendor}=="4348", ATTRS{idProduct}=="55e0", MODE="666", GROUP="plugdev"
```
<small>Opmerking: In oudere Ubuntu/Linux-installaties moet je 'ATTRS' mogelijk vervangen door 'SYSFS'.</small>

Vul natuurlijk je eigen Vendor ID en Product ID in! (hoewel de bovenstaande correct zouden moeten zijn voor het `LANA-TNY-01` bordje).
Sla het bestand op en sluit het. Nu moet je Linux opdracht geven om de udev-regels opnieuw te laden:
```
$ sudo udevadm trigger
```
Elk lid van de **plugdev** groep zou nu `wchisp` moeten kunnen uitvoeren zonder gebruik van `sudo`.

Probeer opnieuw te flashen in Embeetle IDE.
Als het niet werkt, trek dan de LANA-module eruit en sluit hem opnieuw aan op je computer terwijl je de `BOOT`-knop ingedrukt houdt (laat de knop een paar seconden na het aansluiten op de computer los), om ervoor te zorgen dat het echt in "bootloader-modus" is. Als het nog steeds niet werkt, aarzel dan niet om contact met ons op te nemen:
 - E-mail: kristof@embeetle.com
 - Whatsapp: +32(0) 496 90 75 44
 - Discord: @kristof-at-embeetle

&nbsp;<br>
# Mounriver Studio
[Mounriver](http://www.mounriver.com/) is een IDE gebaseerd op eclipse, uitgebracht door de chipmaker WCH. Dit werkt op Windows en er is een versie voor Linux en mogelijk ook voor Mac, maar de laatste twee lopen een beetje achter. [Mounriver](http://www.mounriver.com/) geeft ook vaak foutieve virusmeldingen op veel systemen en schendt de GPL-licentievoorwaarden van de GCC Compiler.

&nbsp;<br>
# Opmerkingen over de LANA-module
Als je zelf aan de slag gaat met de LANA TNY, moet je op één ding letten (ongeacht de IDE): LANA heeft geen externe klok en moet de interne klok (HSI) gebruiken, dit wordt ook vermeld in de standaard sketch van [Embeetle](https://embeetle.com/).
Als je per ongeluk je [LANA](https://phyx.be/LANA_TNY/) board "brickt", kun je deze meestal debricken via USB of door gebruik te maken van de power reset-functie van de [WCHISPTool](https://www.wch-ic.com/downloads/WCHISPTool_Setup_exe.html).
