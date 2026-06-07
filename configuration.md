---
title: Configuration
description: Detailed configuration guide for MeshCore nodes
---
# Configuration

This guide covers the detailed configuration options available on a MeshCore node. For basic setup, see the [Join](/join) guide.

## Accessing the Config Panel

1. Power on your node
2. Connect to the `MeshCore-XXXX` Wi-Fi access point
3. Open `http://192.168.4.1` in a browser
4. The configuration panel opens automatically

## Network Settings

### Node Name

A human-readable identifier that appears to other mesh nodes. Choose something unique but recognisable, like your callsign or location.

### Mesh Channel

Nodes must be on the same channel to communicate. Channels correspond to specific LoRa frequencies within your region's ISM band.

- **Default:** Channel 0 (usually 868.1 MHz in EU, 915.0 MHz in US)
- **Changing channels** requires all nodes in your mesh to use the same channel
- **Bandwidth:** Standard channels use 125 kHz; some regions support 250 kHz for higher data rates

### Region Setting

Sets the regulatory domain for frequency and power limits:

| Region | Frequency | Max Power |
|--------|-----------|-----------|
| EU868 | 863-870 MHz | 14 dBm (25 mW) |
| US915 | 902-928 MHz | 22 dBm (158 mW) |
| AU915 | 915-928 MHz | 22 dBm (158 mW) |
| CN470 | 470-510 MHz | 13 dBm (20 mW) |

### Encryption Key

An optional pre-shared key that encrypts all mesh traffic. If your network uses encryption, all nodes must share the same key.

- **Min length:** 8 characters
- **Recommended:** 16+ characters
- **Leave blank** for an open (unencrypted) mesh

## Radio Settings

### Transmit Power

Higher power increases range but drains the battery faster. Start with the regional default and adjust based on your needs.

- **Typical range:** 2-22 dBm
- **Battery-saving:** 10-14 dBm for short-range urban meshes
- **Maximum range:** 20-22 dBm for long-distance links

### Spreading Factor

Controls the trade-off between range and data rate:

| SF | Range | Data Rate | Air Time |
|----|-------|-----------|----------|
| SF7 | Short | Highest | Fastest |
| SF9 | Medium | Medium | Medium |
| SF12 | Longest | Lowest | Slowest |

Higher spreading factors (SF11-12) can extend range by 2-3× but dramatically increase airtime and power consumption.

## GPS and Location

- **GPS enabled** — uses the onboard GPS module for automatic positioning
- **Fixed location** — manually enter lat/lon if GPS is unavailable or for stationary nodes
- **Update interval:** How often the node broadcasts its position (default: 300 seconds)

## MQTT Gateway

MQTT configuration requires:

1. **Server address** — hostname or IP of the MQTT broker
2. **Port** — typically 1883 (unencrypted) or 8883 (TLS)
3. **Username/password** — if authentication is required
4. **Topic prefix** — base topic for mesh messages (e.g. `meshcore/network_name`)

## Firmware Updates

MeshCore supports over-the-air (OTA) updates. Check the admin panel for available updates, or flash via USB using the web flasher for major version upgrades.

> ⚠️ Always back up your configuration before performing a firmware update.
