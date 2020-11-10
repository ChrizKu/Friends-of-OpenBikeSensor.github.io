---
layout: default
title: Upgrade von 0.2 nach 0.3+ü
has_children: true
parent: Software
nav_order: 1
---

# Firmware Upgrade von <0.3 auf 0.3+

Da sich das interne Partitionsschema des OpenBikeSensors geändert hat, ist es für eine Version kleiner 0.3 notwendig, das Upgrade über den USB-Port durchzuführen.

Dazu muss man das Gerät aufschrauben und den internen USB-Port mit dem PC per Kabel verbinden.

## Vorbereitungen
Über die Weboberfläche sollte man die Konfiguration des OpenBikeSensors herunterladen, da diese beim Upgrade zurückgesetzt wird. Das Zurücksetzen passiert nur bei einem Upgrade von <0.3 auf 0.3, bei anderen Upgrades bleibt die Konfiguration erhalten.

Nach dem Upgrade startet man den OpenBikeSensor entweder ohne angeschlossenes Display oder hält den Bestätigungsknopf beim Einschalten fest, sodass das Gerät einen WLAN-Hotspot startet. Darüber lässt sich dann das Backup der Konfiguration wieder auf das Gerät hochladen.

## Upgrade
### Linux
**/dev/ttyUSB0** muss für den Benutzer beschreibbar sein.

#### Variante 1: Download und Esptool
Die aktuelle Firmware kann man [hier herunterladen](https://github.com/Friends-of-OpenBikeSensor/OpenBikeSensorFirmware/releases).

Dann führt man aus:

````esptool.py --port /dev/ttyUSB0 write_flash FIXME(Adresse) pfad/zur/firmware.bin````

Fertig.

#### Variante 2: Git und PlatformIO
Git und PlatformIO müssen installiert sein.

Zuerst klont man das Repo mit der Firmware.

````git clone https://github.com/Friends-of-OpenBikeSensor/OpenBikeSensorFirmware.git````

Dann wechselt man in das Verzeichnis
````cd OpenBikeSensorFirmware````

und führt das folgende Kommando aus:

````platformio run --target upload -e esp32dev````

Die Ausgabe sollte so aussehen:

````
Processing esp32dev (platform: espressif32; board: esp32dev; framework: arduino)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Tool Manager: Installing platformio/tool-mkspiffs @ ~2.230.0
Tool Manager: tool-mkspiffs @ 2.230.0 has been installed!
Verbose mode can be enabled via `-v, --verbose` option
CONFIGURATION: https://docs.platformio.org/page/boards/espressif32/esp32dev.html
PLATFORM: Espressif 32 (2.0.0) > Espressif ESP32 Dev Module
HARDWARE: ESP32 240MHz, 320KB RAM, 4MB Flash
DEBUG: Current (esp-prog) External (esp-prog, iot-bus-jtag, jlink, minimodule, olimex-arm-usb-ocd, olimex-arm-usb-ocd-h, olimex-arm-usb-tiny-h, olimex-jtag-tiny, tumpa)
[...]
````

### Windows
FIXME
