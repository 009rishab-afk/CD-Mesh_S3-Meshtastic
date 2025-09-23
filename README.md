<div align="center" markdown="1">

<img src=".github/meshtastic_logo.png" alt="Meshtastic Logo" width="80"/>
<h1>Meshtastic Firmware</h1>

![GitHub release downloads](https://img.shields.io/github/downloads/meshtastic/firmware/total)
[![CI](https://img.shields.io/github/actions/workflow/status/meshtastic/firmware/main_matrix.yml?branch=master&label=actions&logo=github&color=yellow)](https://github.com/meshtastic/firmware/actions/workflows/ci.yml)
[![CLA assistant](https://cla-assistant.io/readme/badge/meshtastic/firmware)](https://cla-assistant.io/meshtastic/firmware)
[![Fiscal Contributors](https://opencollective.com/meshtastic/tiers/badge.svg?label=Fiscal%20Contributors&color=deeppink)](https://opencollective.com/meshtastic/)
[![Vercel](https://img.shields.io/static/v1?label=Powered%20by&message=Vercel&style=flat&logo=vercel&color=000000)](https://vercel.com?utm_source=meshtastic&utm_campaign=oss)

<a href="https://trendshift.io/repositories/5524" target="_blank"><img src="https://trendshift.io/api/badge/repositories/5524" alt="meshtastic%2Ffirmware | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>

</div>

</div>

<div align="center">
	<a href="https://meshtastic.org">Website</a>
	-
	<a href="https://meshtastic.org/docs/">Documentation</a>
</div>

## Overview

This repository contains the official device firmware for Meshtastic, an open-source LoRa mesh networking project designed for long-range, low-power communication without relying on internet or cellular infrastructure. The firmware supports various hardware platforms, including ESP32, nRF52, RP2040/RP2350, and Linux-based devices.

Meshtastic enables text messaging, location sharing, and telemetry over a decentralized mesh network, making it ideal for outdoor adventures, emergency preparedness, and remote operations.

### Get Started

- 🔧 **[Building Instructions](https://meshtastic.org/docs/development/firmware/build)** – Learn how to compile the firmware from source.
- ⚡ **[Flashing Instructions](https://meshtastic.org/docs/getting-started/flashing-firmware/)** – Install or update the firmware on your device.

Join our community and help improve Meshtastic! 🚀

## Stats

![Alt](https://repobeats.axiom.co/api/embed/8025e56c482ec63541593cc5bd322c19d5c0bdcf.svg "Repobeats analytics image")


# Custom Meshtastic Node PCB (ESP32-S3 + SX1262)

A compact, all-in-one **Meshtastic node** designed around the **ESP32-S3-WROOM-1** and **Wio SX1262 LoRa module**.  
This project integrates USB-C charging, power management, LoRa communication, and user interface options into a single PCB, making it a reliable platform for off-grid mesh networking.


---

## ✨ Features

- **ESP32-S3-WROOM-1** – Dual-core microcontroller with Wi-Fi + Bluetooth
- **Wio SX1262 LoRa Module** – Long-range wireless communication
- **USB Type-C** – Charging + programming
- **LTC4054 Li-Ion charger IC** – Battery charging with blue LED indicator
- **ADP124 LDO regulator** – Stable 3.3V supply
- **User buttons** – Boot and Reset with debouncing
- **Green status LED** – Connected to GPIO48
- **User interface ports** – GPIO headers, battery connector, OLED header
- **Optional PI antenna filter network** – For future RF tuning
- Designed in **Altium Designer** (also reproducible in KiCad)

---

## 📦 Bill of Materials (BOM)

| Component | Value / Part | Qty | Notes |
|-----------|--------------|-----|-------|
| MCU | ESP32-S3-WROOM-1 | 1 | Main processor |
| LoRa Module | Wio SX1262 | 1 | Long-range RF |
| Charger IC | LTC4054ES5 | 1 | Li-Ion charging |
| LDO Regulator | ADP124-3.3 | 1 | Stable 3.3V output |
| Capacitors | 10µF, 0.1µF | multiple | Decoupling |
| LEDs | Green (GPIO48), Blue (charging) | 2 | Status |
| Resistors | 390K, 100K, 10K, 5.1K, 2K, 330R | assorted | Pull-ups, dividers |
| USB-C Connector | USB4105 | 1 | Power/programming |
| JST Connector | 2-pin XH | 1 | Battery input |
| Tactile Switches | SPST | 2 | Boot + Reset |

Full BOM with part numbers: [BOM.txt](BOM.txt)

---

## 🖥️ Schematic Breakdown

The schematic is segmented into six groups:

1. **USB Type-C Port**  
   - 5.1k resistors on CC1/CC2  
   - TVS diodes on data + power lines  
   - 10µF bulk capacitor for stability  

2. **ESP32-S3-WROOM-1**  
   - Decoupling (0.1µF + 10µF)  
   - Green LED on IO48 for status  
   - All other pins netlabeled  

3. **User Buttons**  
   - Boot + Reset tactile switches  
   - 10k pull-ups and 0.1µF debounce caps  
   - 390k/100k voltage divider for battery ADC  

4. **User Interface Ports**  
   - Extra GPIO headers  
   - JST battery connector  
   - OLED display header  

5. **LoRa SX1262**  
   - Wio SX1262 module with decoupling caps  
   - Reset pulled up with 10k resistor  
   - Optional PI antenna filter network (not populated)  

6. **Power Supply**  
   - LTC4054 Li-Ion charger with blue LED  
   - 2k resistor sets charging current  
   - ADP124-3.3 LDO regulator for clean 3.3V  
   - 10µF caps on input/output of both ICs  

---


