---
title: Join
description: How to get started with MeshCore in the North East UK
---
# Join

Here's how to join the **North East MeshCore Network**.

## 1. Get a Device

You need a supported LoRa device. Good options for beginners:

- **LilyGo T-Deck** — all-in-one handheld with keyboard and screen (standalone, no phone needed)
- **Heltec V3** — compact development board (use with smartphone app)
- **RAK4631** — modular WisBlock, very power-efficient (nRF52)

See the [Hardware](/hardware) page for more options. Visit [flasher.meshcore.io](https://flasher.meshcore.io) for the full list of supported boards.

## 2. Flash the Firmware

Go to [flasher.meshcore.io](https://flasher.meshcore.io) in Chrome or Edge (required for Web Serial support).

1. Connect your device via USB
2. Select your device model
3. Choose a firmware type:
   - **Companion (BLE)** — for use with the smartphone app over Bluetooth
   - **Companion (USB)** — for use with the web client or a computer
   - **Repeater** — to extend network range (always-on)
   - **Room Server** — for message storage and retrieval
4. Click **Flash**

For first-time setup, **Companion (BLE)** is the easiest starting point.

## 3. Set Your Radio Frequency

After flashing, you **must** set the frequency to match the North East network. Do this through the **Console** on the flasher website, the smartphone app, or [config.meshcore.io](https://config.meshcore.io):

```
set freq 869.618
set radio 869.618,62.5,8,5
```

Then **reboot** the device for the new settings to take effect.

The North East network uses the **narrow preset** (BW62.5, SF8, CR5) at **869.618 MHz**. Make sure your frequency matches other nodes in your area.

## 4. Connect a Client

### Smartphone App

Download the MeshCore app:

- **Android:** [Google Play](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android)
- **iOS:** [App Store](https://apps.apple.com/us/app/meshcore/id6742354151)

Pair with your companion device over Bluetooth (pairing code: `123456`).

### Web Client

Open [app.meshcore.nz](https://app.meshcore.nz) and connect via USB Serial.

### T-Deck

If you have a T-Deck running Ripple's standalone **T-Deck "Ultra"** firmware, it works as a standalone communicator — no phone needed.

## 5. Start Messaging

Once configured, trigger an **advert** from your app to announce yourself on the network. You should start seeing other nodes within range.

### For Repeaters and Room Servers

These are managed via:

- **USB serial console** — use the [flasher Console](https://flasher.meshcore.io) or a terminal app (picocom, screen)
- **Web config tool** at [config.meshcore.io](https://config.meshcore.io)
- **Remote administration over RF** — using the smartphone app or a T-Deck
