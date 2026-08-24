# ATLAS-SRAD

ATLAS-SRAD contains the source code for Brad Morrows SRAD avionics system.

The repository contains four main systems:

* ATLAS V2 Onboard
  Firmware for the ATLAS V2 rocket flight computer.

* ATLAS V1 Ground Station
  Firmware for the STM32 based ground station that receives LoRa telemetry from ATLAS V2.

* Ground Station ESP32
  Firmware for the ESP32 used for the ground station web server, local networking, data handling, and communication with ATLAS V1.

* Ground Station UI
  HTML, CSS, and JavaScript for the ATLAS ground station telemetry interface.

## Repository Structure

atlas-srad/
├── atlas-v2-onboard/
├── atlas-v1-ground-station/
├── gs-esp32/
└── gs-ui/
