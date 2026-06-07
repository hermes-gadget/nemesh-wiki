---
title: Hardware
description: Supported hardware for running MeshCore
---
# Hardware

MeshCore runs on a variety of LoRa-equipped devices. For the most up-to-date list, visit the [MeshCore Flasher](https://meshcore.io/flasher) which lists all supported boards with ready-to-flash firmware.

## Popular Devices

### LilyGo T-Deck / T-Deck Plus

A handheld device with keyboard and display — a complete off-grid communicator out of the box.

- **MCU:** ESP32-S3
- **LoRa:** SX1262 (868/915 MHz)
- **Display:** 2.13-inch e-ink (T-Deck) or 2.8-inch TFT (T-Deck Plus)
- **Input:** QWERTY keyboard
- **Extras:** GPS, microSD slot, speaker, Wi-Fi/Bluetooth

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

### Heltec T114

A compact nRF52 device with LoRa and optional GPS.

- **MCU:** nRF52840
- **LoRa:** SX1262
- **Extras:** Bluetooth, optional GPS

### Seeed Studio T1000-E

A tiny, battery-powered LoRa tracker.

- **MCU:** nRF52840
- **LoRa:** SX1262
- **Battery:** Built-in rechargeable
- **Extras:** Bluetooth

### LilyGo T-Pager

A LoRa pager-style device with a small display.

- **MCU:** ESP32-S3
- **LoRa:** SX1262
- **Display:** Round LCD
- **Extras:** Wi-Fi/Bluetooth, vibration motor

## Antennas

Antenna choice significantly affects range:

- **Quarter-wave whip** (≈17 cm for 868 MHz, ≈16 cm for 915 MHz) — good all-rounder
- **Half-wave dipole** — better gain, narrower pattern
- **High-gain directional** — for fixed point-to-point links

A poorly matched or low-quality antenna will severely limit performance. Use an antenna designed for your operating frequency.

## Power

- Most ESP32 boards are powered via USB (5 V)
- Many boards support a single-cell 18650 Li-Ion battery (3.7 V)
- nRF52-based devices (RAK, T114, T1000-E) are very power-efficient and can run for extended periods on battery
- Actual battery life varies greatly with transmit frequency, power level, and device type
