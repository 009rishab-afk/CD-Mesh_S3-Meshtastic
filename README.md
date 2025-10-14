
# Custom ESP32-S3 Meshtastic Node

<div align="left">

![Project Status](https://img.shields.io/badge/Status-Active-success)
![Platform](https://img.shields.io/badge/Platform-ESP32--S3-orange)
![Meshtastic](https://img.shields.io/badge/Meshtastic-Compatible-green)

*A compact, professional-grade Meshtastic node with integrated power management and long-range LoRa communication*

</div>

---

## 📋 Overview

This project is a fully custom PCB design for a **Meshtastic mesh networking node** powered by the ESP32-S3 microcontroller and SX1262 LoRa transceiver. Unlike projects that rely on stacking development boards or breadboard prototypes, this design integrates all essential components into a single, professional PCB with complete power management, USB-C connectivity, and field-ready durability.

**Meshtastic** is an open-source, off-grid communication platform that uses LoRa radios to create decentralized mesh networks. These networks can carry text messages, GPS coordinates, and sensor data over several kilometers without relying on cellular towers, Wi-Fi infrastructure, or satellites.

### What Makes This Different?

- 🎯 **All-in-One Design**: No jumper wires, no stacked modules, just a single professional PCB
- 🔋 **Complete Power Management**: USB-C charging, battery operation, and seamless power switching
- 📡 **Long-Range Communication**: SX1262 LoRa transceiver with excellent range (several km line-of-sight)
- 🔧 **Expandable Platform**: GPIO headers, OLED support, and sensor connections
- 💪 **Field-Ready**: Compact form factor with optional 3D-printed enclosure
- 📱 **Easy Configuration**: Setup via Bluetooth app or web interface

---

## 🎯 Features

### Hardware Features
- **ESP32-S3-WROOM-1** microcontroller (dual-core, Wi-Fi, Bluetooth)
- **Wio SX1262 LoRa Module** for long-range communication
- **USB-C connector** for power delivery and programming
- **LTC4054 Li-Ion charger** with status indication
- **ADP124 3.3V LDO regulator** for clean, stable power
- **Battery voltage monitoring** via voltage divider and ADC
- **Status LEDs** (power and charging indicators)
- **GPIO expansion headers** for sensors and peripherals
- **OLED display header** (I²C) for status display
- **Compact 2-layer PCB** design (~60x80mm)
- **ESD protection** on USB data and power lines

### Software Features
- **Meshtastic firmware** pre-configured for this hardware
- **Text messaging** over LoRa mesh network
- **Position sharing** (GPS via phone or external module)
- **Channel encryption** for private communication
- **Mesh routing** with automatic message forwarding
- **Battery monitoring** and reporting
- **Bluetooth configuration** via mobile app
- **Web-based configuration** via USB
- **Multiple region support** (US, EU, Asia, etc.)
- **Custom channel keys** for private groups

---

## 🛠️ Hardware

### Bill of Materials (BOM)

| Component | Part Number | Quantity | Notes |
|-----------|------------|----------|-------|
| **Core Components** |
| ESP32-S3-WROOM-1 | ESP32-S3-WROOM-1 | 1 | Main processor |
| LoRa Module | Wio SX1262 (Seeed Studio) | 1 | Long-range transceiver |
| **Power Management** |
| Battery Charger | LTC4054ES5-4.2 | 1 | 500mA Li-Ion charger |
| LDO Regulator | ADP124AUJZ-3.3-R7 | 1 | 3.3V output |
| **Connectors** |
| USB-C Connector | USB4105-GF-A | 1 | Power & programming |
| Battery Connector | JST XH-2 | 1 | 2-pin, 2.5mm pitch |
| **Passive Components** |
| Capacitors | 10µF (0805) | 6 | Bulk decoupling |
| Capacitors | 0.1µF (0603) | 8 | High-frequency decoupling |
| Resistors | 390kΩ (0603) | 1 | Voltage divider (high) |
| Resistors | 100kΩ (0603) | 1 | Voltage divider (low) |
| Resistors | 10kΩ (0603) | 4 | Pull-ups |
| Resistors | 5.1kΩ (0603) | 2 | USB-C CC resistors |
| Resistors | 2kΩ (0603) | 1 | Charge current setting |
| Resistors | 330Ω (0603) | 2 | LED current limiting |
| **Protection & Indicators** |
| TVS Diode | USBLC6-2SC6 | 1 | USB ESD protection |
| LED | Green (0603) | 1 | Power indicator |
| LED | Blue (0603) | 1 | Charging indicator |
| Tactile Switch | 6x6mm SPST | 2 | Reset & Boot |
| **Optional** |
| OLED Display | 128x64 I²C | 1 | Status display |
| Antenna | 868/915MHz LoRa | 1 | U.FL or SMA connector |

**📥 Complete BOM with part numbers**: [Download BOM.csv](Hardware/BOM.csv)

### PCB Specifications

- **Dimensions**: Approximately 35mm x 45mm
- **Layers**: 2-layer FR4
- **Thickness**: 1.6mm standard
- **Copper**: 1oz (35µm)
- **Surface Finish**: HASL or ENIG recommended
- **Minimum Track/Space**: 6/6 mil
- **Mounting Holes**: 4x M3 holes for enclosure mounting

### Schematic Highlights

**Key Design Decisions**:
- 5.1kΩ resistors on USB-C CC pins for proper power negotiation
- TVS diodes for ESD protection on USB lines
- Hardware debouncing on tactile switches (10kΩ pull-up + 0.1µF cap)
- Voltage divider (390kΩ/100kΩ) for battery monitoring
- Comprehensive decoupling (0.1µF + 10µF) on all ICs
- GPIO breakout for future expansion

**📐 Design Files**:
- `Hardware/PCB/Schematics/` - Altium Designer schematic files
- `Hardware/PCB/` - PCB layout files
- `Hardware/Gerbers/` - Gerber files ready for fabrication


---

## 📡 LoRa Performance

### Expected Range
- **Line of Sight**: 5-10 km (depending on antenna and terrain)
- **Urban Environment**: 1-3 km
- **Indoor to Outdoor**: 500m - 1km
- **Forest/Hilly Terrain**: 2-5 km

### Frequency Bands
Configure your region in the Meshtastic app:
- **US**: 902-928 MHz (US915)
- **Europe**: 868 MHz (EU868)
- **Asia**: 923 MHz (AS923)
- **Australia**: 915 MHz (AU915)

### LoRa Settings
Default configuration (can be customized):
- **Bandwidth**: 125 kHz
- **Spreading Factor**: SF11 (long range) or SF7 (fast)
- **Coding Rate**: 4/5
- **TX Power**: 22 dBm (configurable)

---

## 🚀 Getting Started

### Prerequisites

**Hardware Tools**:
- Soldering iron and solder
- Hot air station (optional, for SMD components)
- Multimeter for testing
- USB-C cable (data capable)
- Li-Ion or LiPo battery (3.7V, 1000-3000mAh recommended)
- LoRa antenna (868/915 MHz)

**Software Requirements**:
- [Visual Studio Code](https://code.visualstudio.com/)
- [PlatformIO Extension](https://platformio.org/install/ide?install=vscode)
- [Meshtastic Mobile App](https://meshtastic.org/downloads) (Android/iOS)
- USB drivers for ESP32-S3

### PCB Fabrication

1. **Download Gerber files**: Get them from `hardware/gerbers/`
2. **Choose a fab house**: Upload to JLCPCB, PCBWay, or ALLPCB
3. **Configure options**:
   - PCB Thickness: 1.6mm
   - Surface Finish: HASL or ENIG
   - Solder Mask: Any color (green/black recommended)
   - Silkscreen: White
4. **Order**: Minimum order is typically 5 PCBs
5. **Wait**: Typical turnaround is 5-10 days

**Cost**: ~$5-15 for 5 boards including shipping

### Source Components

**Critical Components**:
- ESP32-S3-WROOM-1 (must match exact part number)
- Wio SX1262 module from Seeed Studio
- LTC4054ES5-4.2 in SOT-23-5 package
- ADP124AUJZ-3.3-R7 in SOT-23-5 package


### Firmware Installation

#### Build from Source (PlatformIO)

```bash
# Clone the custom firmware repository
git clone https://github.com/DhamuVkl/CD-Mesh_S3-Meshtastic.git
cd CD-Mesh_S3-Meshtastic

# Open in VS Code
code .

# In PlatformIO:
# 1. Select environment: CD-Mesh_S3
# 2. Click "Build" (checkmark icon)
# 3. Click "Upload" (arrow icon)
```

The firmware is pre-configured for this hardware with correct pin mappings.

### Initial Configuration

#### Via Mobile App (Bluetooth)

1. Install **Meshtastic** app from Play Store or App Store
2. Open app and tap "+" to add device
3. Select your node from Bluetooth device list
4. Enter pairing PIN: `123456`
5. Configure basic settings:
   - Region (US915, EU868, etc.)
   - Node name
   - Channel settings

#### Via Web Interface (USB)

1. Connect node to PC via USB-C
2. Navigate to [client.meshtastic.org](https://client.meshtastic.org/)
3. Click "Connect" and select COM port
4. Configure settings:
   - **Radio Config** → Select your region
   - **Channels** → Set channel name and key
   - **Device** → Set node name and role
   - **Power** → Verify battery monitoring is working

**Important Settings**:
- **Region**: Must match your location for legal operation
- **Channel Key**: Use same key for all nodes you want to communicate with
- **Role**: Set to "Client" for normal use, "Router" for fixed installations

---

## 📱 Using Your Meshtastic Node

### Basic Operations

**Sending Messages**:
1. Open Meshtastic app
2. Select "Messages" tab
3. Type message and send
4. Message routes through mesh to all nodes on same channel

**Position Sharing**:
1. Enable location in phone settings
2. In app: Settings → Position → Enable
3. Your location broadcasts periodically
4. View other nodes' locations on map

**Battery Monitoring**:
- Check battery voltage in app under "Device Metrics"
- Node reports battery percentage
- Low battery warning when <20%

### Advanced Features

**Channel Encryption**:
```
Settings → Channels → Primary → Encryption
- Use default key for public network
- Set custom key for private group
- Share key securely with group members
```

**Mesh Routing**:
- Messages automatically hop through intermediate nodes
- Maximum 3 hops by default
- Configure in Settings → LoRa → Hop Limit

**Multiple Channels**:
- Create up to 8 channels
- Different channels for different groups
- Channel 0 is always primary/LongFast

---

## 🔧 Configuration Examples

### Long Range Setup (Maximum Distance)
```
Modem Preset: Long Fast
Region: Your region
Hop Limit: 3
TX Power: 22 dBm
```

### High Speed Setup (Short Range, Fast Messages)
```
Modem Preset: Short Fast
Region: Your region
Hop Limit: 3
TX Power: 17 dBm
```

### Battery Saver Setup (Portable Use)
```
Modem Preset: Long Slow
TX Power: 17 dBm
Screen Timeout: 60 seconds
Wait Bluetooth: 60 seconds
```

---




## 🔬 Applications

### Outdoor Adventures
- **Hiking Groups**: Stay connected beyond cell coverage
- **Mountain Biking**: Real-time location sharing
- **Kayaking/Sailing**: Off-shore communication
- **Camping**: Coordinate between campsites

### Emergency Preparedness
- **Disaster Response**: Communication when infrastructure fails
- **Search and Rescue**: Coordinate teams in remote areas
- **Emergency Kits**: Reliable off-grid communication
- **Community Networks**: Neighborhood emergency mesh

### IoT and Monitoring
- **Environmental Sensors**: Temperature, humidity, air quality
- **Agricultural Monitoring**: Soil moisture, weather stations
- **Remote Asset Tracking**: Location monitoring
- **Wildlife Research**: Animal tracking and data collection

### Events and Festivals
- **Music Festivals**: Coordinate with friends without cell service
- **Outdoor Events**: Staff communication
- **Races/Competitions**: Timing and coordination
- **Ham Radio**: Digital mode experimentation



## 🔗 Related Projects

- [Official Meshtastic Firmware](https://github.com/meshtastic/firmware)
- [Meshtastic Android App](https://github.com/meshtastic/Meshtastic-Android)
- [Meshtastic Python CLI](https://github.com/meshtastic/Meshtastic-python)
- [RAK WisBlock Meshtastic](https://github.com/RAKWireless/WisBlock)
- [LilyGO T-Beam](https://github.com/Xinyuan-LilyGO/LilyGo-LoRa-Series)

---

## 📄 License

This project is licensed under the **MIT License** - see [LICENSE](LICENSE) for details.

### Component Licenses
- Meshtastic Firmware: GPL v3
- ESP-IDF: Apache 2.0
- PCB Design Files: MIT (this repository)
- 3D Models: CC BY-SA 4.0

---

## 🙏 Acknowledgments

- **Meshtastic Community** for developing and maintaining the firmware
- **Espressif** for the powerful ESP32-S3 platform
- **Semtech** for LoRa technology
- **Seeed Studio** for the Wio SX1262 module
- **Open-source community** for tools, libraries, and inspiration
- **Beta testers** who helped refine this design

---


**Meshtastic Community**:
- Discord: [Join Meshtastic Discord](https://discord.gg/meshtastic)
- Reddit: [r/meshtastic](https://reddit.com/r/meshtastic)

---



<div align="center">

**Built for the off-grid community, by the off-grid community**

[Hardware](hardware/) • [Firmware](firmware/) • [Enclosure](enclosure/) • [Docs](docs/)

*Stay connected, stay independent* 📡

</div>
