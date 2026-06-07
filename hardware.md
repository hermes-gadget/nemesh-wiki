---
title: Hardware
description: Supported hardware for MeshCore mesh networking nodes
---
# Hardware

MeshCore runs on ESP32-based devices with LoRa radios. Here are the most common and recommended boards.

## Recommended Devices

### Heltec T-Deck

The T-Deck is a handheld device with a built-in keyboard and display, making it ideal as a portable mesh communicator.

- **MCU:** ESP32-S3
- **LoRa:** SX1262 (868/915 MHz)
- **Display:** 2.13-inch e-ink or 2.8-inch TFT
- **Input:** QWERTY keyboard, trackball
- **Battery:** Built-in 18650 support
- **Extras:** GPS, microSD slot, Wi-Fi/Bluetooth

### Heltec T-Beam

A popular GPS-enabled LoRa board, often used for tracking and stationary nodes.

- **MCU:** ESP32
- **LoRa:** SX1262 (868/915 MHz)
- **GPS:** NEO-6M / NEO-8M
- **Battery:** 18650 support
- **Extras:** Wi-Fi, Bluetooth

### Heltec LoRa 32 (V2/V3)

A compact development board, good for stationary nodes and IoT applications.

- **MCU:** ESP32 (V2) / ESP32-S3 (V3)
- **LoRa:** SX1276 (V2) / SX1262 (V3)
- **Display:** 0.96-inch OLED
- **Extras:** Wi-Fi, Bluetooth

### LilyGo T-ECHO

A compact handheld with LoRa and a small display.

- **MCU:** ESP32
- **LoRa:** SX1262
- **Display:** 1.54-inch e-ink
- **Battery:** Built-in 2000mAh
- **Extras:** Wi-Fi, Bluetooth

## Antennas

Antenna choice significantly affects range:

| Frequency | Recommended Antenna | Typical Range |
|-----------|-------------------|---------------|
| 868 MHz | Quarter-wave whip (17.3 cm) | 1-5 km (urban), 10-20 km (LOS) |
| 915 MHz | Quarter-wave whip (16.4 cm) | 1-5 km (urban), 10-20 km (LOS) |
| Dual-band | Half-wave dipole | 2-8 km (urban) |

Higher-gain antennas improve range but have a narrower radiation pattern. For mobile nodes, a quarter-wave whip is a good compromise.

## Power

- **USB power:** 5 V via USB-C or micro-USB
- **Battery:** Most boards support single-cell 18650 Li-Ion (3.7 V)
- **Power consumption:** ~80-120 mA idle, ~200-400 mA transmitting
- **Battery life:** 1-3 days typical with a 3000 mAh cell

## Enclosures

For outdoor or permanent installations, use a weatherproof enclosure rated at least IP65. The antenna should be mounted externally for best performance.
