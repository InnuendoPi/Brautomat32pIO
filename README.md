# Brautomat ESP32pIO

Brautomat32 platformIO Espressif Arduino Core 3.1 IDF v5.3 (pioarduino)

Der Brautomat ist eine Brausteuerung für die Induktionskochfelder GGM IDS1 und IDS2 mit einem ESP32 D1 mini. Der Brautomat bietet eine intuitiv einfach zu bedienende Steuerung.

_pIO Versionen sind nicht kompatibel mit Brautomat32. Vor der Installation die Konfiguration und die Maischepläne sichern!_

## Hauptfunktionen

* Steuerung der Induktionskochfelder GGM
  * GGM IDS1
  * GGM IDS2
* integrierter PID-Controller
* PID-AutoTune
* Temperatursensoren
  * Dallas DS18B20
  * PT100 und PT1000 (MAX31865)
* Maischeplan
  * Automatisches Anfahren und halten der Rasttemperaturen
  * Würzekochen
  * Alarmierung für Hopfengaben
  * Bis zu 20 Teilschritte
* Verwaltung von Maischeplänen
* Steuerung Induktionskochfeld als Maischepfanne
* Steuerung Induktionskochfeld als Sudpfanne (Würzepfanne)
* Steuerung Nachguss (HLT)
* Steuerung von Aktoren, wie bspw. Rührwerk, Pumpen, etc.
* PWM für Aktoren
* Audio Alarme
  * MP3 Alarme
  * Akkustische Signale (Piezo Buzzer)
* Toasts Nachrichten
* Temperaturverlauf im Maischeprozess als Grafik (line chart)
* Rezept Import
  * kleinen Brauhelfer2
  * Maische Malz und Mehr
  * BrewFather
* Rezept Export
* Unterstützung für 3,5" HMI Touchdisplay Nextion

## 📚 Changelog

Version 1.48.13

* Geändert:     WebIf Optimierung abgeschlossen
* Geändert:     Kessel Sud für die Verwendung von Webhooks erweitert
* Geändert:     einheitliche Optik für die Einstellungen Kessel Maische, Sud an Nachguss
* Gerändert:    Nachguss Tab Temperatursteuerung eingefügt
* Geändert:     Button Nachguss löschen entfernt. Funktion wird mit Auswahl deaktiviert ausgeführt
* Downgrade:    Arduino core 3.1.1 wegen Fehler in 53.03.12
* Geändert:     Nachguss für Verwendung mit IDS erweitert (wegen Downgrade noch nicht abgeschlossen)
* Geändert:     Verarbeitung der Kettle Parameter url, dutycycle und invert überarbeitet
* Update:       Arduino core 3.1.2
* Geändert:     träges WebIf Part 4: Ausblenden von Objekten überarbeitet
* Geändert:     träges WebIf Part 3: request Zeitkorrektur nach Stromlos/-Ausfall überarbeitet
* Geändert:     träges WebIf Part 2: request & response handling überarbeitet
* Fix:          träges WebIf Part 1: Server response mime Format für JSON korrigiert
* Geändert:     Abfrageintervall Sensoren von Minimum SampleTime MAISCHE, SUD und HLT auf festen Wert 2000ms gesetzt
* Geändert:     neuer Parameter DutyCycle im Relais Modus (1000ms bis 60000ms). Default 5000
* Geändert:     InnuAPID Bibliothek Übergabe KettleID für debug Ausgaben hinzugefügt (default 0)
* Geändert:     InnuAPID Bibliothek Berechnung der benötigten Leistung wenn lastTime null ist
* Fix:          Fehler in setProfil D Parameter behoben

## 📚 Dokumentation

Beschreibung & Anleitung: [https://innuendopi.gitbook.io/brautomat32/](https://innuendopi.gitbook.io/brautomat32/)\
Diskussion: [https://hobbybrauer.de/forum/viewtopic.php?p=486504#p486504](https://hobbybrauer.de/forum/viewtopic.php?p=486504#p486504)\

## 📘 Pinout ESP32 D1

Pinout based on ESP32 D1 Mini NodeMCU [AZ-Delivery](https://www.az-delivery.de/products/esp32-d1-mini)

| Name       | GPIO    | Input  | Output | Notes                                         |
| ---------- | ------- | ------ | ------ | --------------------------------------------- |
| D0         | GPIO026 | ok     | ok     |                                               |
| D1         | GPIO022 | ok     | ok     |                                               |
| D2         | GPIO021 | ok     | ok     |                                               |
| D3         | GPIO017 | ok     | ok     | DS18B20                                       |
| D4         | GPIO016 | ok     | ok     |                                               |
| D5         | GPIO018 | ok     | ok     | GGM IDS Interrupt blue/green                  |
| D6         | GPIO019 | ok     | ok     | GGM IDS Command yellow                        |
| D7         | GPIO023 | ok     | ok     | GGM IDS Relay white                           |
| D8         | GPIO005 | ok     | ok     | Buzzer, outputs PWM signal at boot            |
| D9         | GPIO027 | ok     | ok     | SCLK                                          |
| D10        | GPIO025 | ok     | ok     | MISO                                          |
| D11        | GPIO032 | ok     | ok     | MOSI                                          |
| D12        | GPIO012 | (ok)   | ok     | TDI, boot fails if pulled high                |
| D13        | GPIO004 | ok     | ok     | CS0                                           |
| D14        | GPIO000 | pullUp | (ok)   | must be low to enter flash mode               |
| D15        | GPIO002 | ok     | ok     | onboard LED, must be low to enter flash mode  |
| D16        | GPIO033 | ok     | ok     | CS1                                           |
| D17        | GPIO014 | ok     | ok     | CS2, outputs PWM signal at boot               |
| D18        | GPIO015 | ok     | ok     | outputs PWM signal at boot                    |
| D19        | GPIO013 | ok     | ok     |                                               |
| D20        | GPIO010 | (ok)   | (ok)   | SD3 SPI flash                                 |
||||||

Pins connected to the integrated SPI flash and not recommended for other use: CLK (IO6), SD0/SDD (IO7), SD1 (IO8), SD2 (IO9), SD3 (IO10), CMD (IO11)\
GPIOs 34 to 39 are input only pins.

## 🔉MP3 files

_Legal note: "Boxing Bell" (info), "Short School Bell" (error), "Ding sound effect" (warning) und "Success sound effect" (success) mp3 von Free Sounds Library_ [http://www.freesoundslibrary.com](http://www.freesoundslibrary.com) _Licence: Attribution 4.0 International (CC BY 4.0). You are allowed to use sound effects free of charge and royalty free in your multimedia projects for commercial or non-commercial purposes._
