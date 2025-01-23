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

Version 1.48.4

* Geändert:     Der Sonderbefehl IDSPROFIL prüft vor dem Profilwechsel den Gerätetyp
* Fix:          SensorID wurde im Sonderbefehl IDSPROFIL nicht korrekt übertragen
* Update:       Dallas Temperature Bibliothek 4.0.3
* Fix:          Bei Profilwechsel und Sonderbefehl IDSPROFIL wurde der Status GPIO invertieren im Relais Modus nicht korrekt übernommen
* Geändert:     default Status GPIO invertieren in der Kessel Konfiguration auf false gesetzt
* Neu:          Im Relais Modus kann der GPIO nun invertiert werden
* Fix:          Freigabe GPIOs bei Wechsel Kesseltyp (off, IDS, Relais) korrigiert
* Fix:          Fehler in der Profilverwaltung behoben
* Update:       Dallas Temperature Bibliothek 4.0.1 (fix err handling, fix device search)
* Update:       Arduino core 3.1.1 based on IDF 5.3.2.250106
* Neu:          Link nach gitbook für Parameter Voreinstellungen Import eingefügt
* Geändert:     bei Klick auf Prev oder Next wird der Status Button Play zurückgesetzt (ein dekativiertes autonext wird aufgehoben)
* Fix:          Auswertung Sonderbefehle bei Klick auf den Button Play korrigiert
* Fix:          der PID Controller wurde mit dem Sonderbefehl IDS nicht korrekt gestartet, wenn die IDS ausgeschaltet war
* Fix:          Verzögerung Ablauf Maischeplan behoben, wenn die Rastdauer mit 0s eingetragen war
* Geändert:     Parameter Temperatur Kochen wurde in die Einstellungen Maischeplan verschoben
* Fix:          InnuAPID PID Controller debug Ausgaben aktuelle Leistung typo
* Fix:          Korrekturen html und CSS
* Fix:          Korrektur Links nach gitbook
* Geändert:     Sensor Informationen als Tab eingefügt
* Fix:          Korrektur Links nach gitbook
* Geändert:     Sensor Informationen als Tab eingefügt
* Fix:          es ist nun möglich, alle PID Parameter für Maische, Sud und HLT bei aktivem PID Controller (beim Brauen) anzupassen
* Fix:          wenn SoftSerial keinen oder einen fehlerhaften Wert für den PowerButton von Display im manuellen Modus liefert
* Geändert:     Modul checkIDSState Kessel Sud
* Neu:          Auswahl Gerätetyp GGM oder Relais für Maische und Sud
* Fix:          Korrektur Sprachdateien für das Objekt SUD
* Fix:          Korrektur Pin Interrupt handling zweite GGM IDS
* Fix:          Korrektur task watchdog timer ESP32 IDF5.x (platformIO)
* Update:       Erläuterungen Steuerbefehle in der Anleitung erweitert
* Fix:          Debug Ausgaben Braustatus Flash (read/write/erase)
* Geändert:     deprecated lib EEPROM durch Preferences für ESP32 ersetzt (save states in flash)
* Fix:          Casting private ArduinoJSON objects (Update 7.3)
* Update:       ArduinoJSON 7.3
* Update:       VSCode 1.96
* Fix:          die Berechnung der erforderlichen Leistung IDS (PID Controller) bei einem Sensorfehler (-127 Grad) nicht mehr ausgeführt
* Fix:          Einlesen Maischeplan nach Stromunterbrechung: Zuweisung Maische, Sud, HLT, Steuerbefehl oder Aktor korrigiert
* Fix:          Fehler Hinzufügen/Entfernen von Maischeschritte behoben, wenn der Brauprozess gestartet ist
* Update:       Nextion Display Dateien aktualisiert
* Fix:          Brautomat Status nach Stromunterbrechung (verschiedene Zustände korrigiert)
* Fix:          typedef time_t
* Fix:          Das Logging für den Maischeprozess war zu Debugzwecken fest auf VERBOSE eingestellt
* Neu:          Toast Message, wenn der Rast Timer nach einer Unterbrechung angeapsst wurde
* Fix:          Webhook Nachguss wurde nicht korrekt verarbeitet
* Fix:          TickerMash Status war nach Reset/Stromunterbrechung bei deaktiviertem autonext nicht korrekt
* Geändert:     die Dauer einer Stromunterbrechung während einer aktiven Rast (Timer läuft), wird nach dem Neustart von der Rastzeit automatisch abgezogen
* Neu:          es wird ein Zeitstempel mitgespeichert, um die Dauer einer Unterbrechung bemessen zu können
* Geändert:     die aktuelle Rastzeit wird nun im 10s Takt in Sekunden statt Restminuten alle 60s gespeichert
* Fix:          Autorestart Maischestep nach Reset oder Ausschalten, wenn Timer noch nicht gestartet war
* Fix:          Anzeige Restzeit Maischestep nach Reset oder Ausschalten nicht korrekt
* Fix:          Nachguss/Sud ein oder ausschalten ohne Braustart hat fehlerhaft den Brauprozess gestartet.
* Neu:          Webhook für Nachguss
* Neu:          Webhook für Aktoren
* Geändert:     im WebIf Aktoren werden PWM und invertieren passend zur Auswahl GPIO/Webhook ein- bzw. ausgeblendet
* Fix:          default Kesselname gesetzt
* Neu:          Eigenschaft Name hinzugefügt
* Neu:          zweites Induktionskochfeld "SUD" kann mit dem Brautomat gesteuert werden
* Neu:          neuer Sonderbefehl SUD für die zweite GGM IDS
* Neu:          Display Firmware Anzeige Kesselübersicht um zweites Induktionskochfeld erweitert
* Geändert:     Sonderbefehle können auch Dauer und Temperatur verarbeiten
* Geändert:     im Display wird auf der Seite Kesselübersicht der Name angezeigt
* Fix:          Suche nach DS18B20 Adressen korrigiert
* Update:       VSCode 1.95
* Update:       ESP32 Arduino 3.0.7 ESP-IDF v5.1.4

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
