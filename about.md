---
title: About
description: What MeshCore is and how mesh networking works
---
# About

## What is MeshCore?

MeshCore is a lightweight, portable C++ library for multi-hop packet routing over LoRa radio. It enables secure, text-based communication without the internet or any central infrastructure.

Unlike pure flood-based mesh systems, MeshCore uses **hybrid path-based routing** — after an initial flood to discover a destination, nodes learn the most efficient route and use it for subsequent messages, minimising airtime and collisions.

## Firmware Types

MeshCore provides several firmware types for different roles:

| Firmware | Role |
|----------|------|
| **Companion (BLE)** | Connects to a smartphone app over Bluetooth |
| **Companion (USB Serial)** | Connects to a computer or the web client over USB |
| **Companion (Wi-Fi)** | Connects over Wi‑Fi (requires compiling with your SSID) |
| **Repeater** | Extends network range by forwarding packets to their destination |
| **Room Server** | A BBS-style server that stores messages for later retrieval |
| **Sensor** | A remote sensor node for telemetry and alerting |

**Clients do not repeat.** Only repeaters and room servers (with repeat enabled) forward packets. This is central to MeshCore's messaging-first design — it avoids the flooding and collisions that plague other LoRa mesh systems.

## How Routing Works

1. You send a message to a destination. The first message uses **flood routing** — every repeater that hears it retransmits until the destination is reached.
2. The destination sends back a **delivery report** listing the path the message took (the sequence of repeaters).
3. Future messages use that **direct path** — only the repeaters on the path retransmit, keeping airtime low.

If a path breaks, the client retries and falls back to flood automatically.

## Key Properties

- **Decentralised** — no servers, no internet, no single point of failure
- **Hybrid path-based routing** — efficient, low-airtime multi-hop
- **Public-key cryptography** — Ed25519 node identities; messages are AES-encrypted using per-contact keys derived via X25519 (ECDH)
- **Open source** — MIT license
- **Multi-platform** — runs on ESP32, nRF52, and other MCUs

## Use Cases

- Off-grid messaging
- Emergency and disaster response
- Outdoor activities (hiking, camping, events)
- Community mesh networks
- IoT and sensor telemetry
