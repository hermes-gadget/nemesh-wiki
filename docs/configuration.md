---
title: Configuration
description: Configuring MeshCore repeaters and room servers — UK radio settings
---
# Configuration

Configuration methods differ by firmware type.

## Radio Settings (North East UK)

The North East England MeshCore network uses the **narrow preset** within the 868 MHz band:

| Parameter | Value | Notes |
|-----------|-------|-------|
| **Frequency** | **869.618 MHz** | Within the UK 869.4–869.65 MHz sub-band (up to 500 mW ERP at ≤10% duty cycle) |
| **Bandwidth** | **62.5 kHz** | Narrow preset — fits between ISM band interference |
| **Spreading Factor** | **SF8** | Good balance of range and data rate |
| **Coding Rate** | **5** | Standard forward error correction |

Set these via serial CLI (repeater/room server) or the smartphone app (companion):

```
set freq 869.618
set radio 869.618,62.5,8,5
```

After changing radio params, **reboot** for them to take effect.

> **Why these settings?** Since October 2025, many MeshCore regions have moved to the narrow preset (BW62.5, SF7–9). This gives a lower noise floor, better SNR, and faster transmissions by fitting between interference in the ISM band. SF8 was chosen for the North East as the best balance — longer range than SF7, faster airtime than SF9.

### Transmit Power

The appropriate transmit power depends on your device. As a guideline:

- **Most ESP32 boards (Heltec V3, T-Deck):** start at 10–14 dBm
- **High-power modules (Station G2, E22-900M30S):** consult manufacturer specs — wrong settings can damage hardware

Set with: `set tx <dBm>`. The firmware accepts values from **1 to 22 dBm**; any further gain must come from the antenna while staying within the legal ERP limit for the band.

## Companion Firmware

Companion (BLE/USB) devices have minimal configurable settings — most configuration is done through the connected client app (smartphone or web).

The main setting to check is the **frequency**, which must match your region and the rest of your mesh. Set it via the flasher Console or the smartphone app.

## Repeater and Room Server Configuration

Repeaters and room servers use a **CLI over USB serial** or **remote administration over RF**. There is no web-based admin panel on the device itself.

### Accessing the CLI

- **USB serial** — connect the device to a computer and use the Console at [flasher.meshcore.io](https://flasher.meshcore.io), or a terminal app (picocom, screen, PuTTY)
- **Web config tool** at [config.meshcore.io](https://config.meshcore.io)
- **Remote RF** — use the smartphone app's remote management feature, or a T-Deck with remote administration unlocked

### Essential Commands

| Command | Description |
|---------|-------------|
| `set freq <MHz>` | Set operating frequency (e.g. `set freq 869.618`) |
| `set radio <freq>,<bw>,<sf>,<cr>` | Set all radio params at once (reboot afterwards) |
| `get freq` | Show current frequency |
| `get radio` | Show current radio parameters (freq/BW/SF/CR) |
| `set tx <dBm>` | Set transmit power (1–22 dBm) |
| `get tx` | Show current transmit power |
| `set repeat <on/off>` | Enable or disable packet repeating |
| `set flood.max <n>` | Set maximum flood hop count |
| `set name <name>` | Set node name |
| `set lat <degrees>` | Set node latitude |
| `set lon <degrees>` | Set node longitude |
| `password <new-password>` | Change admin password |
| `clock` | Show the node's clock (UTC) |
| `time <epoch_seconds>` | Set the clock to a Unix timestamp |
| `advert` | Send a flood advert |
| `start ota` | Enter OTA update mode |
| `stats-core` | Show system stats (battery, uptime, queue) |
| `stats-radio` | Show radio stats (noise floor, RSSI/SNR, airtime) |
| `stats-packets` | Show packet counters (sent/received) |
| `neighbors` | Show known neighbouring nodes (repeater only) |

Full reference: [docs.meshcore.io/cli_commands](https://docs.meshcore.io/cli_commands)

### Remote Administration

To administer a repeater or room server over RF:

1. Authenticate with the device's **admin password** (default: `password`)
2. Send CLI commands as direct messages
3. The device processes them and responds over the air

Change the default password with: `password <new-password>`

> **Change the defaults.** Repeaters and room servers ship with the admin password `password`, and room servers also have a guest (read-only) password defaulting to `hello`. Set your own before deploying a node so others can't reconfigure it.
