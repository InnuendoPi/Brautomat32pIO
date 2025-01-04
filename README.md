# Brautomat ESP32 platformIO build

Brautomat32 V 1.47 platformIO espressif Arduino Core 3.1.0 IDF v5.3 (pioarduino)

Brautomat 1.47+ expands the range of functions with a second induction hob GGM IDS. If you want you can use up to three kettles:

- brew kettle, first induction hob GGM IDS
- mash tun, the new second induction hob GGM IDS
- hot liquid tank (sparge water)

1th note: contrary to the manual below special funktions do not need to have a temperature and a time set to zero anymore. Now you can use special functions to start your hlt with a setpoint or a mash rests on your second induction hob.

2nd note: Brautomat32 1.47 platformIO is an early beta.

3rd note: have fun and send feedback

_pIO versions are not compatible with Brautomat32: you can not upgrade from brautomat32 to brautomat32 pIO due to different partition layout. Use backup & restore for your configuration!_

## 📚 Changelog

Version 1.47.6

- Fix:          fixed wrong setpoint for kettle maische, when changing PID parameters while brewing
- Fix:          fixed read wrong value for object powerButton from display in manual mode
- changed:      modul checkIDSState changed handling kettle Sud
- Neu:          device type relay added to kttle Maische and Sud
- Fix:          some corrections in language files for object Sud
- Fix:          fixed handling pin Interrupt kettle Sud
- Fix:          reworked task watchdog timer ESP32 IDF5.x (platformIO)
- changed:      [switched to pioarduino stable branch](https://github.com/pioarduino/platform-espressif32/releases/download/stable/platform-espressif32.zip)
- Fix:          typo debug output flash (read/write/erase)
- Update:       Arduino core 3.1.0 based on IDF 5.3.2.241210
- Replaced:     Replaced deprecated lib EEPROM with Preferences for ESP32 IDF5 (save states in flash)
- Error:        lib EEPROM not working in IDF 5 environments
- Fix:          Casting private ArduinoJSON objects (Update 7.3)
- Update:       ArduinoJSON 7.3
- Update:       VSCode 1.96
- Fix:          PID Controller compute will be ignored in sensor error events (PID input -127 degrees)
- Fix:          read mashplan after power disconnect: fixed error addressing correct kettle MAISCHE, SUD or HLT
- Fix:          error fixed when adding or removing mash steps while mashplan is runing
- Update:       Nextion Display files TFT
- Fix:          Brautomat states after power disconnect
- changed:      switched to pioarduino IDE 1.0.4
- changed:      [switched to pioarduino develop platform](https://github.com/pioarduino/platform-espressif32.git#develop)
- fix:          typedef time_t
- fix:          predefined logging for debug removed
- new:          Toast message, when rest time was automatically adjusted after restart
- fix:          fixed handling webhook hlt
- fix:          TickerMash state incorrect after restart, when autonext disabled
- changed:      duration of a power interruption during an active rest (active timer) is automatically adjusted from the rest time after the restart
- new:          time stamp added to brewing state
- changed:      interval for saving brewing state reduced to every 10 seconds
- fix:          display rest time after reset or power interruption inccorect
- fix:          stop auto start  mash plan when switching hlt or mlt on/off
- new:          hlt webhook
- new:          enabled webhooks on actors w/o GPIO. Example Shelly 1PM: <http://192.168.x.x/relay/0?turn=> without trailing on off
- changed:      web interface actors visability
- fix:          default kettle name
- new:          second induction hob "SUD"
- new:          new method SUD for mash plan include temperature and timer
- changed:      firmware nextion display kettle page
- Fix:          sensor search DS18B20 addresses
- Update:       VSCode 1.95
- Update:       ESP32 Arduino 3.0.7 ESP-IDF v5.1.4

## 📚 Documentation

Docs (german language): [https://innuendopi.gitbook.io/brautomat32/](https://innuendopi.gitbook.io/brautomat32/)\
Discussion (german forum): [https://hobbybrauer.de/forum/viewtopic.php?p=486504#p486504](https://hobbybrauer.de/forum/viewtopic.php?p=486504#p486504)

## 📘 Pinout ESP32 D1

Pinout below based on ESP32 D1 Mini NodeMCU [AZ-Delivery](https://www.az-delivery.de/products/esp32-d1-mini)

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
