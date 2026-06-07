---
title: Configuration
description: Configuring MeshCore repeaters and room servers
---
# Configuration

Configuration methods differ by firmware type.

## Companion Firmware

Companion (BLE/USB) devices have minimal configurable settings — most configuration is done through the connected client app (smartphone or web).

The main setting to check is the **frequency**, which must match your region and the rest of your mesh. Set it via the flasher Console or the smartphone app.

## Repeater and Room Server Configuration

Repeaters and room servers use a **CLI over USB serial** or **remote administration over RF**. There is no web-based admin panel on the device itself.

### Accessing the CLI

- **USB serial** — connect the device to a computer and use the Console at [meshcore.io/flasher](https://meshcore.io/flasher), or a terminal app (picocom, PuTTY, screen)
- **Remote RF** — use the smartphone app's remote management feature, or a T-Deck with remote administration unlocked

### Essential Commands

| Command | Description |
|---------|-------------|
| `set freq <MHz>` | Set operating frequency (e.g. `set freq 868.0`) |
| `get freq` | Show current frequency |
| `set tx <dBm>` | Set transmit power |
| `get tx` | Show current transmit power |
| `set repeat on/off` | Enable or disable packet repeating |
| `set flood.max <n>` | Set maximum flood hop count |
| `set name <name>` | Set node name |
| `set location <lat> <lon>` | Set fixed location |
| `get location` | Show current location |
| `time` | Show or set the node's clock |
| `start ota` | Enter OTA update mode |
| `get stats` | Show node statistics |
| `get neighbors` | Show known neighbouring nodes |
| `get config` | Show all configuration values |

A full reference is available at [docs.meshcore.io/cli_commands](https://docs.meshcore.io/cli_commands).

### Frequency and Region

MeshCore uses ISM bands:

| Region | Frequency |
|--------|-----------|
| UK / Europe | 868 MHz band (e.g. 868.0 MHz) |
| USA / Canada | 915 MHz band (e.g. 910.525 MHz) |
| Australia / NZ | 915 MHz band |

Many regions now use the "narrow" preset: **BW62.5, SF7-9, CR5**. Check with your local MeshCore community for the recommended settings.

### Transmit Power

The appropriate transmit power depends on your device's hardware. Refer to the hardware documentation for safe limits. As a general guideline:

- Most ESP32 boards: start at 10–14 dBm and increase as needed
- High-power modules (Station G2, E22-900M30S): consult the manufacturer's specifications — incorrect settings can damage the hardware

### Remote Administration

To administer a repeater or room server over RF:

1. Authenticate with the device's **admin password**
2. Send CLI commands as direct messages
3. The device processes them and responds over the air

The default admin password is set during first-time setup. Change it using:
```
set password <new-password>
```
