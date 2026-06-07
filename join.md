---
title: Join
description: How to get started with MeshCore
---
# Join

Here's how to join a MeshCore mesh network.

## 1. Get a Device

You need a supported LoRa device. Good options for beginners:

- **LilyGo T-Deck** — all-in-one handheld with keyboard and screen
- **Heltec V3** — compact development board
- **RAK4631** — modular WisBlock (nRF52)

See the [Hardware](/hardware) page for more options. Visit the [MeshCore Flasher](https://meshcore.io/flasher) for the full list of supported boards.

## 2. Flash the Firmware

Go to [meshcore.io/flasher](https://meshcore.io/flasher) in a browser (Chrome or Edge recommended for Web Serial support).

1. Connect your device via USB
2. Select your device model
3. Choose a firmware type:
   - **Companion (BLE)** — for use with the smartphone app over Bluetooth
   - **Companion (USB)** — for use with the web client or a computer
   - **Repeater** — to extend network range (always-on)
   - **Room Server** — for message storage and retrieval
4. Click **Flash**

For first-time setup, a Companion (BLE) firmware is the easiest starting point.

## 3. Connect a Client

### Smartphone App

Download the MeshCore app:

- **Android:** [Google Play](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android)
- **iOS:** [App Store](https://apps.apple.com/us/app/meshcore/id6742354151)

Pair with your companion device over Bluetooth (pairing code: `123456`).

### Web Client

Open [app.meshcore.nz](https://app.meshcore.nz) and connect via USB Serial.

### T-Deck

If you have a T-Deck with MeshCore Ultra firmware, it works as a standalone communicator — no phone needed.

## 4. Configure Your Region

After flashing, use the **Console** on the flasher website or the smartphone app to set your region's frequency:

```
set freq 868.0
```

Or use [config.meshcore.io](https://config.meshcore.io) for repeaters and room servers connected via USB.

## 5. Start Messaging

Once configured, your device will start sending **adverts** — periodic announcements that tell nearby nodes you exist. You should start seeing other nodes appear within range.

### For Repeaters and Room Servers

These are managed via:
- **USB serial console** — use the [flasher Console](https://meshcore.io/flasher) or a terminal app (picocom, PuTTY)
- **Remote administration over RF** — using the smartphone app or a T-Deck (some features may require an unlock code)
- **Web config tool** at [config.meshcore.io](https://config.meshcore.io)
