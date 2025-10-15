# ESP32 Firmware Flash Map

Use the following binary files and flash addresses when programming the ESP32 (via `esptool.py` or [esptool-js](https://espressif.github.io/esptool-js/)).

## Flash Address Table

| Address  | File Name         | Description             |
|-----------|------------------|--------------------------|
| 0x0000    | bootloader.bin   | Bootloader               |
| 0x8000    | partitions.bin   | Partition Table          |
| 0x10000   | firmware.bin     | Main Application Binary  |

## Example Command (Python esptool)

```bash
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z \
  0x0000 bootloader.bin \
  0x8000 partitions.bin \
  0x10000 firmware.bin
