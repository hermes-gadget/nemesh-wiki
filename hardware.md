---
title: Hardware
description: Supported hardware for running MeshCore
---
# Hardware

MeshCore runs on a variety of LoRa-equipped devices. For the most up-to-date list, visit the [MeshCore Flasher](https://flasher.meshcore.io) which lists all supported boards with ready-to-flash firmware.

## Popular Devices

### LilyGo T-Deck / T-Deck Plus

A handheld device with keyboard and display — a complete off-grid communicator out of the box.

- **MCU:** ESP32-S3
- **LoRa:** SX1262 (433/868/915 MHz)
- **Display:** 2.8-inch IPS LCD (320×240), capacitive touch — same on both T-Deck and T-Deck Plus
- **Input:** QWERTY keyboard + trackball
- **Extras:** microSD slot, microphone, speaker, Wi-Fi/Bluetooth. The **T-Deck Plus** adds a built-in GPS module and a larger 2000 mAh battery (the original T-Deck has a GPS socket but no module fitted)

### Heltec V3

A compact LoRa development board, usable as a companion or repeater.

- **MCU:** ESP32-S3
- **LoRa:** SX1262
- **Display:** 0.96-inch OLED
- **Extras:** Wi-Fi/Bluetooth

### RAK4631 (WisBlock)

An nRF52-based LoRA board in modular form factor. Commonly used as a companion or repeater.

- **MCU:** nRF52840
- **LoRa:** SX1262
- **Extras:** Bluetooth only (no Wi-Fi)

### Heltec Mesh Node T114

A compact nRF52 device with LoRa and an optional GPS module.

- **MCU:** nRF52840
- **LoRa:** SX1262
- **Display:** 1.14-inch TFT colour display
- **Extras:** Bluetooth, optional GPS, 18650 battery holder

### Seeed Studio SenseCAP T1000-E

A tiny, credit-card-sized battery-powered LoRa tracker.

- **MCU:** nRF52840
- **LoRa:** Semtech **LR1110** (combined LoRa transceiver, GNSS scanner and Wi-Fi scanner) — *not* an SX1262
- **Battery:** Built-in 700 mAh rechargeable
- **Extras:** Bluetooth, built-in GPS, IP65-rated enclosure

### LilyGo T-LoRa Pager

A pager-style handheld communicator.

- **MCU:** ESP32-S3
- **LoRa:** SX1262
- **Display:** 2.33-inch IPS strip display (480×222)
- **Input:** QWERTY keyboard + rotary encoder
- **Extras:** Wi-Fi/Bluetooth, GNSS, NFC/RFID, 6-axis IMU, microSD

## Antennas

Antenna choice significantly affects range:

- **Quarter-wave whip** (≈8.2 cm for 868 MHz, ≈7.8 cm for 915 MHz) — good all-rounder
- **Half-wave dipole** (≈16–17 cm element for 868 MHz) — better gain, narrower pattern
- **High-gain directional** — for fixed point-to-point links

A poorly matched or low-quality antenna will severely limit performance. Use an antenna designed for your operating frequency.

## Power

- Most ESP32 boards are powered via USB (5 V)
- Many boards support a single-cell 18650 Li-Ion battery (3.7 V)
- nRF52-based devices (RAK, T114, T1000-E) are very power-efficient and can run for extended periods on battery
- Actual battery life varies greatly with transmit frequency, power level, and device type
