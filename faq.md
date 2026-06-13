---
title: FAQ
description: Frequently asked questions about MeshCore
---
# Frequently Asked Questions

## General

### What is MeshCore?

MeshCore is an open-source (MIT) C++ library for multi-hop packet routing over LoRa radio. It provides secure, decentralised text messaging without the internet. Unlike pure flood-based mesh systems, it uses **hybrid path-based routing** for efficiency.

### What do I need to start?

- A supported LoRa device (see [Hardware](/hardware))
- A computer with Chrome/Edge to flash firmware via [flasher.meshcore.io](https://flasher.meshcore.io)
- A client app: [Android](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android), [iOS](https://apps.apple.com/us/app/meshcore/id6742354151), or [web app](https://app.meshcore.nz)

If you have a T-Deck running Ripple's standalone **T-Deck "Ultra"** firmware, it works standalone — no phone needed.

### Does MeshCore cost money?

All radio firmware is free and open source (MIT). The smartphone app uses a freemium model (some advanced features like remote server administration over RF have a wait timer that can be removed via in-app purchase). T-Deck firmware is free; deeper map zoom and server administration features may require a paid unlock.

## Radio & Region

### What frequencies does MeshCore use?

UK/Europe use the **868 MHz band**. USA, Canada, Australia, and New Zealand use the **915 MHz band**.

### What radio settings should I use in the North East UK?

The North East MeshCore network uses:

| Setting | Value |
|---------|-------|
| Frequency | **869.618 MHz** |
| Bandwidth | **62.5 kHz** (narrow) |
| Spreading Factor | **8** |
| Coding Rate | **5** |

Set via serial CLI: `set freq 869.618` then `set radio 869.618,62.5,8,5` then reboot.

> Many regions have moved to the **narrow preset** since October 2025 (BW62.5, SF7–9). Narrow bandwidth lets MeshCore signals fit between ISM band interference, giving a lower noise floor, better SNR, and faster transmissions.

### What if I want to use a different frequency?

The appropriate frequency depends on your local MeshCore community. If the consensus in your area changes, post an update request on the [#meshcore-app channel](https://discord.com/channels/1343693475589263471/1391681655911088241) on the [MeshCore Discord](https://discord.gg/GyWBxsytQg) so the app presets can be updated.

### What is the default MeshCore frequency?

MeshCore's original EU/UK default was **869.525 MHz** with BW250, SF11, CR5 — the "wide" preset. The narrow preset (BW62.5, lower SF) is now recommended for most regions due to better interference resilience.

### What is an advert?

An advert (advertisement) is a periodic broadcast where a node announces its identity (public key, name, and optionally location) to nearby nodes. This is how nodes discover each other. Repeaters send a flood advert every 12 hours by default (`set flood.advert.interval`). Clients advertise only when the user initiates it.

### Is there a hop limit?

Yes. Internally the firmware has a maximum of 64 hops, though real-world conditions usually limit this well before the cap. Repeaters can also limit flood propagation with `set flood.max`.

## Firmware Types

### What firmware types are available?

- **Companion (BLE)** — connects to smartphone app over Bluetooth
- **Companion (USB)** — connects to web client or computer over USB
- **Companion (Wi-Fi)** — connects over Wi-Fi (requires compiling with your SSID/password)
- **Repeater** — forwards packets to extend network range
- **Room Server** — a BBS-style server for message history
- **Sensor** — remote sensor node for telemetry

### Do MeshCore clients repeat?

**No.** Only repeaters and room servers (with `set repeat on`) forward packets. Clients are endpoints only — this is core to MeshCore's messaging-first, low-airtime design.

## Hardware

### How many devices do I need?

One device with companion firmware + a smartphone is enough to start messaging. For extended range, add a second device as a repeater placed in a high location.

### Can I use a Raspberry Pi to flash a device?

Yes. Install esptool (ESP32) or adafruit-nrfutil (nRF52) and use [flasher.meshcore.io](https://flasher.meshcore.io).

## Routing

### How does MeshCore routing work?

Your first message to a destination uses **flood routing** — all repeaters retransmit it. The destination replies with a **delivery report** listing the path (the sequence of repeaters). Subsequent messages use that **direct path**, with only those repeaters retransmitting.

### What happens if a path breaks?

The sender retries up to **3 times** using the stored path, then falls back to flood routing on the last retry. If the destination is reachable through a different repeater, a new path is learned.

### Do public/private channels always flood?

Yes — group channels have no defined destination path, so they always flood. Repeaters can limit flood propagation with `set flood.max`.

## Troubleshooting

### My device doesn't see any other nodes

1. Check the **frequency matches** other nodes in the area (869.618 MHz in NE UK)
2. Check your antenna connection
3. Wait 2–5 minutes for adverts to propagate
4. Try a higher location
5. Verify other nodes are actually within range

### How do I connect via Bluetooth?

Flash **Companion (BLE)** firmware. The default BLE pairing code is `123456`.

### My repeater's clock is wrong

Check it with `clock` (shown in UTC). Set it with `time <epoch_seconds>` over the USB serial console, or use remote administration over RF to send the correct Unix timestamp. GPS-equipped nodes can also use `gps sync`.

### How do I update firmware over the air?

- **nRF52 devices (RAK, T114, T1000-E):** Use the nRF DFU app. Put the device in OTA mode with `start ota`, then use the DFU app to upload the firmware ZIP.
- **ESP32 devices (Heltec V3, etc.):** Use `start ota` to start a Wi-Fi hotspot named `MeshCore OTA`. Connect to it and upload the firmware at `http://192.168.4.1/update`.

### How do I reset AGC deafness on my repeater?

If the repeater stops hearing in-range nodes due to AGC issues, use: `set agc.reset.interval 4` (auto-resets AGC every ~4 seconds).

## Other

### Is MeshCore open source?

Most firmware is open source under the MIT license: [github.com/meshcore-dev/MeshCore](https://github.com/meshcore-dev/MeshCore). The T-Deck Ultra firmware and the native mobile apps are not open source.

### Are there community projects?

Yes — see [awesome-meshcore](https://github.com/samuk/awesome-meshcore) for a maintained list.

### Does MeshCore support ATAK?

ATAK is not currently on the roadmap. MeshCore's client-no-repeat design and dynamic path-based routing make it less suited to the high-frequency position reporting that ATAK requires.
