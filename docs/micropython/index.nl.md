# MicroPython documentatie

## Start micropython
1. Update je badge naar de laatste versie. [instructies](../reset)
1. Als het flashen klaar is, druk dan RESET zodat het hoofd menu verschijnt (met de groene knoppen: Ota, Hello, Micropython, Retro-go)
1. Maak een verbinding met [Fri3d ViperIDE](https://fri3dcamp.github.io/viper/)  
   Dit zal een Timeout Error geven (omdat de Micropython REPL nog niet actief is, dit is OK)
1. Nu kan je vanonder op het scherm (in Fri3d Viper IDE) de seriele logging van de badge zien
1. Selecteer nu op de badge Micropython en druk op A
1. De badge start nu opnieuw op en je kan de seriele logging van het boot process volgen. Onderbreek dit process niet!! Micropython is files aan het extracten op de fat partitie.
1. Na een poos zie je de REPL promt verschijnen `>>> `
1. Je kan nu in de Fri3d Viper IDE de verbinding verbreken en opnieuw connecteren [Fri3d ViperIDE](https://fri3dcamp.github.io/viper/)


Standaard gaat de badge niet opnieuw Micropython opstarten na een reset.
Als je dit toch wil, moet je het booten in Micropython nog bevestigen.
Je kan dit doen als volgt:

```python
from fri3d import boot
boot.persist()
```
Nu geraak je niet langer meer in het main menu.
Om hierin terug te kunnen booten moet je dit doen:
```python
from fri3d import boot
boot.main_menu()
```

## Badge Examples
Er is voorbeeld code geinstalleerd op de badge zelf. [sources](https://github.com/Fri3dCamp/badge_2024_micropython/tree/develop/fri3d/fri3d_application/src/payload/examples)

Je kan deze bekijken en runnen met [Fri3d ViperIDE](https://fri3dcamp.github.io/viper/)

Als je error krijgt van onbestaande modules bij de eerste 4 voorbeelden, dan is waarschijnlijk het extractie process bij de eerste opstart van Micropython onderbroken.
De eenvoudigste manier om dit op te lossen is om de stappen hierboven te volgen.

## Een lokale file uitvoeren
Installeer `mpremote` [howto](https://docs.micropython.org/en/latest/reference/mpremote.html)

TLDR; `pip install mpremote`

```sh
mpremote run local_test_file.py
```

[Thonny](https://thonny.org/) werkt ook prima.

Helaas werkt de cleanup van de Display module niet helemaal correct, nadat die geinitialiseerd is, en je volgende script probeert dit opnieuw, zal dit fouten geven.
Je moet een reset uitvoeren (RESET button op de badge)

## Een file kopieren naar de badge
```sh
mpremote resume fs cp local_path/file.jpg :file.jpg
```

## De Fri3d applicatie starten
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
