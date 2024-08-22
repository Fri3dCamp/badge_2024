# Upgrade je Blaster-2022
Je hebt een `blaster-2022` en je wil die upgraden zodat deze samenwerkt met de blasters van 2024?

<img src="https://github.com/user-attachments/assets/ffb33687-16a3-4096-b759-7f38967c1e2d" width="400">

Je kan de firmware upgraden aan de `badge flash station`. Als je een geavanceerde versie van de `blaster-2022` hebt - met programmer - dan kan je de upgrade van de firmware ook met je laptop doen, via Embeetle IDE. Op deze pagina vind je alle stappen.

&nbsp;<br>
# Embeetle IDE
Embeetle is een IDE van Belgische makelij. Je kan de LANA module ermee programmeren op de `blaster-2024` (flamingo), maar je kan er ook de Atmel chip mee programmeren op de oudere `blaster-2022`.

&nbsp;<br>
## STEP 1: Download Embeetle IDE
Download eerst Embeetle IDE:
 - [https://embeetle.com/downloads](https://embeetle.com/#embeetle-ide/download)

Je kan Embeetle downloaden voor **Windows** of **Linux**. We hebben nog geen MAC support.

<img src="https://github.com/user-attachments/assets/59498d20-e134-4101-98d4-90c1bf618ca1" width="400">

&nbsp;<br>
## STEP 2: Lanceer het `arduino-uno-blaster-2022` project
Start Embeetle en klik `CREATE PROJECT`. Selecteer dan `Arduino` voor de vendor en zoek het project `arduino-uno-blaster-2022`:

<img src="https://github.com/user-attachments/assets/b7591d2e-6726-4ac6-aa90-f76f0e7ef021" width="600">

&nbsp;<br>
Klik `CREATE` onderaan. Embeetle IDE zal het blaster project downloaden, alsook alle nodige tools. Dan opent het project:

![image](https://github.com/user-attachments/assets/f7655b77-4fcc-4ea9-843f-ba8a7f89ddf7)

Wat je in deze screenshot ziet is feitelijk een Arduino UNO project dat geconverteerd is naar een full-fledged makefile-gebaseerd C/C++ project. In tegenstelling tot Arduino, geeft Embeetle je toegang tot alle driver files, linker script en assembly startup files, en meer! Niks is nog verborgen.

&nbsp;<br>
## STEP 3: Plug in je bordje
Belangrijk: je badge mag niet aangesloten zijn aan de blaster (5V van de USB maakt je 3,3V badge stuk)  
Plug je `blaster-2022` bordje in.

&nbsp;<br>
## STEP 4: Flash de firmware
Klik de `flash` knop bovenaan in Embeetle IDE. Embeetle flasht nu de firmware op de Atmel chip.

Als het flashen niet werkt, moet je op deze link klikken voor de oplossing:

[Embeetle IDE Arduino UNO installation page](https://embeetle.com/#supported-hardware/arduino/probes/default)
