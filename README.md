# ATLAS-SRAD

ATLAS is a student-developed avionics and telemetry system.

This repository contains the firmware and software used across the onboard flight computer and ground station. If you are new to the avionics team, start here to understand how the main parts of ATLAS work together.

## System Overview

ATLAS is split into four main projects:

### ATLAS V2, Onboard Flight Computer

ATLAS V2 flies inside the rocket.

It handles:

* Flight sensors
* GPS
* LoRa telemetry
* Flight event detection
* microSD flight logging
* Flash black-box logging
* Battery monitoring
* Deployment system monitoring and control

ATLAS V2 uses an STM32 microcontroller as the main processor.

### ATLAS V1, Ground Station

ATLAS V1 is the STM32-based ground station controller.

It handles:

* Receiving LoRa telemetry from ATLAS V2
* Processing received packets
* Ground station GPS
* Communication with the ESP32

### Ground Station ESP32

The ESP32 connects the ground station hardware to the user interface.

It handles:

* Receiving data from ATLAS V1
* Hosting the local Ground Station UI
* Ground station data logging
* Offline operation in the field
* Communication with phones, tablets, or other devices

### Ground Station UI

The Ground Station UI displays live flight information.

This includes:

* Altitude
* GPS position
* Vertical speed
* Distance and bearing
* LoRa signal strength
* GPS status
* Battery voltage
* Flight state
* Last received packet
* Offline maps

## How Everything Connects

Rocket:

ATLAS V2
↓
915 MHz LoRa
↓
ATLAS V1 Ground Station
↓
UART
↓
ESP32
↓
Ground Station UI

ATLAS V2 also records flight data locally so telemetry loss does not mean flight data loss.

## Repository Structure

`ATLAS-SRAD/`

`ATLAS-V2/`
Onboard STM32 flight computer firmware.

`ATLAS-V1/`
Ground station STM32 firmware.

`GS-ESP32/`
ESP32 firmware for networking, logging, and UI hosting.

`GS-UI/`
Ground station web interface.

Each project should be treated as its own system while keeping the telemetry protocol between devices compatible.

## Main Technologies

* STM32
* ESP32
* C / C++
* STM32CubeIDE
* LoRa 915 MHz
* GPS
* SPI
* UART
* I2C
* microSD
* NOR Flash
* HTML / CSS / JavaScript

## Flight Data

ATLAS V2 uses two main logging systems.

microSD stores detailed flight data for post-flight analysis.

Onboard flash stores essential telemetry, system states, and major flight events as a black-box backup.

The ground station also records received telemetry.

## Before Changing Code

Understand which device you are working on before making changes.

Changes to packet formats, telemetry fields, UART communication, or LoRa settings often require matching changes on multiple devices.

Avoid changing flight detection, deployment logic, GPIO assignments, or hardware configuration without checking the electrical design and current flight logic first.

Use Git commits regularly so known working versions stay easy to restore.

## Getting Started

If you are joining the avionics team:

1. Clone the repository.
2. Read this README.
3. Identify which ATLAS project you are working on.
4. Open STM32 projects in STM32CubeIDE.
5. Review the project-specific source files before changing anything.
6. Build the existing code before making changes.
7. Test changes on hardware before merging them into the main branch.

The goal of this repository is to keep the full ATLAS system organized, documented, and recoverable as the avionics system continues to develop.
