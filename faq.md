---
title: FAQ
description: Frequently asked questions about MeshCore
---
# Frequently Asked Questions

## General

### What is MeshCore?

MeshCore is an open-source (MIT) C++ library for multi-hop packet routing over LoRa radio. It provides secure, decentralised text messaging without the internet. Unlike flood-based mesh systems, it uses **path-based routing** for efficiency.

### What do I need to start?

- A supported LoRa device (see [Hardware](/hardware))
- A computer with Chrome/Edge to flash firmware via [meshcore.io/flasher](https://meshcore.io/flasher)
- A client app: [Android](https://play.google.com/store/apps/details?id=com.liamcottle.meshcore.android), [iOS](https://apps.apple.com/us/app/meshcore/id6742354151), or [web](https://app.meshcore.nz)

If you have a T-Deck with MeshCore Ultra firmware, it works standalone — no phone needed.

### Does MeshCore cost money?

All radio firmware is free and open source. The smartphone app uses a freemium model (some advanced features like remote server administration over RF have a wait timer that can be removed via in-app purchase). The T-Deck firmware is free; deeper map zoom and server administration features may require a paid unlock.

### What frequencies does MeshCore use?

UK/Europe use the 868 MHz band. USA, Canada, Australia, and New Zealand use the 915 MHz band. Many regions have moved to a "narrow" preset: **BW62.5, SF7-9, CR5**.

### What is an advert?

An advert (advertisement) is a periodic broadcast where a node announces its identity (public key, name, and optionally location) to nearby nodes. This is how nodes discover each other.

### Is there a hop limit?

Yes. Repeaters have a configurable maximum flood hop count (`set flood.max`). This prevents messages from propagating indefinitely.

## Firmware Types

### What firmware types are available?

- **Companion (BLE)** — connects to smartphone app over Bluetooth
- **Companion (USB)** — connects to web client or computer over USB Serial
- **Companion (Wi-Fi)** — connects over Wi-Fi (requires compiling with your SSID/password)
- **Repeater** — forwards packets to extend network range
- **Room Server** — a BBS-style server for message history
- **Sensor** — remote sensor node for telemetry

### Do MeshCore clients repeat?

**No.** Only repeaters and room servers (with repeat enabled) forward packets. Clients are endpoints only. This is central to MeshCore's messaging-first, low-airtime design.

## Hardware

### How many devices do I need?

One device with companion firmware + a smartphone is enough to start messaging. For extended range, add a second device as a repeater placed in a high location.

### Can I use a Raspberry Pi to flash a device?

Yes. Install esptool (ESP32) or adafruit-nrfutil (nRF52) and follow the instructions on [meshcore.io/flasher](https://meshcore.io/flasher).

## Routing

### How does MeshCore routing work?

The first message to a destination uses **flood routing** — all repeaters retransmit it. The destination replies with a **delivery report** listing the path the message took. Subsequent messages use that **direct path**, with only the repeaters on the path retransmitting.

### What happens if a path breaks?

The sender retries up to 3 times using the stored path, then falls back to flood routing on the last retry. If the destination is reachable via a different repeater, a new path is learned.

### Do public/private channels always flood?

Yes — group channels have no defined path, so they always flood. Repeaters can limit flood propagation with `set flood.max`.

## Troubleshooting

### My device doesn't see any other nodes

1. Check the frequency matches other nodes in your area
2. Check your antenna connection
3. Wait 2–5 minutes for adverts to propagate
4. Try a higher location
5. Verify other nodes are actually within range

### How do I connect via Bluetooth?

Flash **Companion (BLE)** firmware. The default pairing code is `123456`.

### My repeater's clock is wrong

Use the `time` command via USB serial console, or use remote administration over RF to set the correct Unix timestamp.

### How do I update firmware over the air?

- **nRF52 devices (RAK, T114, T1000-E):** Use the nRF DFU app. Put the device in OTA mode with `start ota`, then use the DFU app to upload the firmware ZIP.
- **ESP32 devices (Heltec V3, etc.):** Use `start ota` to start a Wi-Fi hotspot named `MeshCore OTA`. Connect to it and upload the firmware at `http://192.168.4.1/update`.

## Other

### Is MeshCore open source?

Most firmware is open source under the MIT license: [github.com/meshcore-dev/MeshCore](https://github.com/meshcore-dev/MeshCore). The T-Deck firmware and the native mobile apps are not open source.

### Are there other MeshCore-related projects?

Yes — there is a growing ecosystem of community projects. See [awesome-meshcore](https://github.com/samuk/awesome-meshcore) for a maintained list.

### Does MeshCore support ATAK?

ATAK is not currently on the roadmap. MeshCore's client-no-repeat design and dynamic routing make it less suited to the high-frequency position reporting that ATAK requires.
