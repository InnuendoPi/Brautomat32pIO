# Brautomat ESP32 platformIO build

Brautomat32 V 1.47.5 platformIO espressif Arduino Core 3.0.7 IDF v5.1.4+ (pioarduino)

Brautomat 1.47+ expands the range of functions with a second induction hob GGM IDS. If you want you can use up to three kettles:

- brew kettle, first induction hob GGM IDS
- mash tun, the new second induction hob GGM IDS
- hot liquid tank (sparge water)

1th note: contrary to the manual below special funktions do not need to have a temperature and a time set to zero anymore. Now you can use special functions to start your hlt with a setpoint or a mash rests on your second induction hob.

2nd note: Brautomat32 1.47 platformIO is an early alpha test.

3rd note: have fun and send feedback

_pIO versions are not compatible with Brautomat32: you can not upgrade from brautomat32 to brautomat32 pIO due to different partition layout. Use backup & restore for your configuration!_

## 📚 Documentation

Docs (german language): [https://innuendopi.gitbook.io/brautomat32/](https://innuendopi.gitbook.io/brautomat32/)\
Discussion (german forum): [https://hobbybrauer.de/forum/viewtopic.php?p=486504#p486504](https://hobbybrauer.de/forum/viewtopic.php?p=486504#p486504)

## 📘 Pinout ESP32 D1

Pinout below based on ESP32 D1 Mini NodeMCU [AZ-Delivery](https://www.az-delivery.de/products/esp32-d1-mini)

| Bezeichner | GPIO    | Input  | Output | Beschreibung                                  |
| ---------- | ------- | ------ | ------ | --------------------------------------------- |
| D0         | GPIO026 | ok     | ok     |                                               |
| D1         | GPIO022 | ok     | ok     |                                               |
| D2         | GPIO021 | ok     | ok     |                                               |
| D3         | GPIO017 | ok     | ok     | DS18B20                                       |
| D4         | GPIO016 | ok     | ok     |                                               |
| D5         | GPIO018 | ok     | ok     | GGM IDS Interrupt blue/green                  |
| D6         | GPIO019 | ok     | ok     | GGM IDS Command yellow                        |
| D7         | GPIO023 | ok     | ok     | GGM IDS Relay white                           |
| D8         | GPIO005 | ok     | ok     | Buzzer                                        |
| D9         | GPIO027 | ok     | ok     | SCLK                                          |
| D10        | GPIO025 | ok     | ok     | MISO                                          |
| D11        | GPIO032 | ok     | ok     | MOSI                                          |
| D12        | GPIO012 | (ok)   | ok     | TDI, boot fails if pulled high, strapping pin |
| D13        | GPIO004 | ok     | ok     | CS0                                           |
| D14        | GPIO000 | pullUp | (ok)   | must be low to enter flash mode               |
| D15        | GPIO002 | ok     | ok     | onboard LED, must be low to enter flash mode  |
| D16        | GPIO033 | ok     | ok     | CS1                                           |
| D17        | GPIO014 | ok     | ok     | CS2                                           |
| D18        | GPIO015 | ok     | ok     |                                               |
| D19        | GPIO013 | ok     | ok     |                                               |
||||||

Pins connected to onboard flash and not recommended for GPIO use: CMD (IO11), CLK (IO6), SD0/SDD (IO7), SD1 (IO8), SD2 (IO9) and SD3 (IO10)

## 🔉MP3 files

_Legal note: "Boxing Bell" (info), "Short School Bell" (error), "Ding sound effect" (warning) und "Success sound effect" (success) mp3 von Free Sounds Library_ [http://www.freesoundslibrary.com](http://www.freesoundslibrary.com) _Licence: Attribution 4.0 International (CC BY 4.0). You are allowed to use sound effects free of charge and royalty free in your multimedia projects for commercial or non-commercial purposes._
