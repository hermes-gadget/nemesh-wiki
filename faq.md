---
title: FAQ
description: Frequently asked questions about mesh networking and MeshCore
---
# Frequently Asked Questions

## General

### What is the range of a mesh node?

Typical range is 1-5 km in urban environments and 10-20 km with clear line of sight. Range depends on antenna, power, and environmental factors. See the [Coverage](/coverage) page for more details.

### Do I need internet access to use the mesh?

No! The mesh network operates independently of the internet. Nodes communicate directly over LoRa radio. Internet is only needed if you want to bridge the mesh to other networks via an MQTT gateway.

### Can I send messages to someone on the other side of the world?

If both meshes have MQTT gateways connected to the same broker, yes. Messages flow mesh → MQTT → internet → MQTT → mesh. Without gateways, the mesh is limited to radio range (multi-hop).

## Hardware

### What's the cheapest way to get started?

A Heltec LoRa 32 V3 board costs around £20-25. It has a small OLED display and built-in LoRa radio. You'll also need a USB cable and a 868/915 MHz antenna.

### Can I build my own node?

Yes. Any ESP32 board with an SX1262 or SX1276 LoRa module can run MeshCore. The [Hardware](/hardware) page lists compatible options.

### How long does the battery last?

With a 3000 mAh 18650 cell, expect 1-3 days depending on transmit frequency. Reducing transmit power and increasing the position update interval can extend battery life significantly.

## Network

### How many nodes can the mesh support?

MeshCore networks can scale to hundreds of nodes. The practical limit depends on channel congestion — more nodes mean more routing traffic. Gateways and careful channel planning help with scaling.

### What happens if a node goes offline?

The mesh automatically re-routes around it. Messages intended for nodes reachable only through the offline node will queue until an alternative path appears.

### Is the mesh encrypted?

Optionally. You can set a pre-shared encryption key that all nodes in your mesh must use. Without encryption, messages are sent in plain text (though still over the air using LoRa modulation).

## Troubleshooting

### My node doesn't see any other nodes

1. Check that your node is on the correct channel and region
2. Verify there are other nodes within range
3. Check your antenna connection
4. Ensure your node has been running long enough to send heartbeats (2-5 minutes)
5. Try moving to a higher location

### Messages are getting through but very slowly

- Lower the spreading factor (SF7-9 instead of SF11-12)
- Reduce the number of repeaters if too many are covering the same area
- Check for channel congestion — too many nodes transmitting simultaneously

### Poor signal quality (low RSSI/SNR)

- Check antenna connection and quality
- Try a different antenna with better gain
- Elevate the node
- Remove obstacles between nodes
- Increase transmit power (within regulatory limits)
