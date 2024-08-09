# Big Flamingo Gun 9000

## Kenmerken
De flamingo blaster is opgebouwd rond volgende basiscomponenten:

- een IR LED
- 2 IR-ontvangers
- 4 WS2812 LED's
- RISC-V-gebaseerd microcontrollerbord [LANA TNY](https://phyx.be/LANA_TNY/)

**Sluit de USB-kabel niet aan wanneer deze is aangesloten op de badge**!

![blockdiagram](blockdiagram.png)

## Stapsgewijze montagehandleiding

![pakketinhoud](overview.jpg)

### Alle componenten netjes verpakt
Het pakket dat u hebt ontvangen, bevat alles wat u nodig hebt om uw eigen flamingo blaster te bouwen.

- 1 IR LED
- 1 team selector switch
- 1 grote blauwe condensator
- 1 buzzer
- 1 trigger pushbutton
- 1 lange strip pin headers (in tweeën te splitsen)
- 1 enkele pin header
- 1 MOSFET
- 1 [LANA TNY](https://phyx.be/LANA_TNY/)
- 1 roze PCB
- 1 badge link kabel
- 2 IR ontvangers
- 2 weerstanden
- 2 badge link connectoren
- 3 gele condensatoren (100nF)
- 4 WS2812 LED's

![parts spread out](parts.jpg)

### Begin met solderen
Er is geen verkeerde volgorde om de onderdelen te solderen, maar we raden aan om eerst met de laagste componenten te beginnen.

### Weerstanden
Het pakket bevat een grotere 33R weerstand en een kleinere 1k weerstand.

![weerstanden gemonteerd](resistors.jpg)

### Teamschakelaar en luidspreker
De volgende componenten met een laag profiel zijn de zoemer en de teamschakelaar. Monteer de schakelaar met de actuator weg van de PCB gericht.

![teamschakelaar en zoemer gemonteerd](switch_speaker.jpg)

### IR-LED
De infrarood-LED heeft wel een polariteit. Als u hem verkeerd om monteert, werkt de blaster niet. De lange pin van de LED moet in het vierkante gat met het `+`-symbool ernaast. Zorg ervoor dat u wat ruimte overlaat om de LED naar voren te buigen (of nog beter, buig hem voordat u hem soldeert!)

![IR-LED voor het solderen](IR_LED.jpg)

![IR-LED gesoldeerd](IR_LED2.jpg)

### IR-ontvangers
De montagerichtingen van de 2 IR-ontvangers worden aangegeven door een pijl. Deze pijl wijst in de richting waarin de pinnen moeten gaan.

![IR-ontvanger aan de componentzijde](IR_rx.jpg)

![IR-ontvanger aan de achterkant](IR_rx2.jpg)

### RGB-LED's
De RGB-LED's hebben 4 aansluitingen, de langste aansluiting moet in het gat met de letter `c`. Buig de LED na het plaatsen maar voor u gaat solderen. Zo kunt u de uitlijning enigszins aanpassen voordat u ze op hun plaats bevestigt.

![RGB-LED-oriëntatie](RGB_LED.jpg)

![RGB-LED's gesoldeerd](RGB_LED2.jpg)

### Triggerknop
Als u rechtshandig bent, soldeert u de drukknop aan de zijkant met alle andere componenten.

![Triggerschakelaar gemonteerd](switch.jpg)

### LANA TNY-module
Gebruik de grote en de losse enkele pinheader om de [LANA TNY](https://phyx.be/LANA_TNY/)-module te solderen. Breek de lange pinheader in 2 voor de zijkanten. Plaats de pinnen in de flamingo en lijn de LANA-module er bovenop uit. Soldeer de pinnen afwisselend om te voorkomen dat de pinheader smelt.

![LANA-module](LANA.jpg)

![LANA-pinnen](LANA_pins.jpg)

### Condensatoren
De grote blauwe condensator, net als de IR-LED, heeft een lange pin die de anode van dit onderdeel aangeeft. Deze langere pin moet in het gat met het `+`-symbool worden geplaatst.

De kleinere gele condensatoren hebben geen polriteit en kunnen op beide manieren worden gemonteerd.

![Grote condensator gemonteerd](capacitor.jpg)

![100nF condensatoren gemonteerd](100n.jpg)

### Badge-linkconnector
Het laatste onderdeel is de badge-linkconnector. Deze 3,5 mm audio-aansluiting is aan dezelfde kant gesoldeerd als alle andere componenten

![badge-linkconnector op de flamingo](badge_link.jpg)

### Afgewerkte blaster
Als alles volgens plan verloopt, zou u nu een functionele blaster moeten hebben.

![volledig gemonteerde flamingo](done.jpg)

### Monteer de connector op uw badge
Nu hoeft u alleen nog maar de badge-linkconnector aan uw badge toe te voegen. Monteer deze connector aan de achterkant van de badge (dezelfde kant als de draadloze module en de batterij).

![badge link connector naast de badge](badge_link2.jpg)

![badge link connector gesoldeerd](badge_link3.jpg)

Let op dat er geen kortsluiting is tussen de voorste pin en de decoratie van de badge!

![badge link connector nakijken](badge_link4.jpg)

## Opmerkingen

Firmware-updates kunnen worden geflasht via het badge-flashstation in het soldeergebied.

Hardware-ontwerpbestanden en firmware zijn te vinden in [de GitHub-repository.](https://github.com/Fri3dCamp/blaster_2024)