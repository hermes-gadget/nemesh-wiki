---
title: About
description: Learn about mesh networking and the MeshCore ecosystem
---
# About Mesh Networking

Mesh networking is a decentralised communication technology where every device (node) connects directly to nearby nodes, forming a self-healing, resilient network. Unlike traditional client-server networks, mesh networks have no single point of failure — if one node goes offline, traffic automatically routes around it.

## What is MeshCore?

MeshCore is an open-source firmware that turns ESP32-based devices (like the Heltec T-Deck, T-Beam, and similar boards) into mesh network nodes. It operates in the unlicensed ISM bands (868/915 MHz) and provides:

- **Long-range communication** — kilometres between nodes with line of sight
- **Low power consumption** — battery-powered nodes can run for days
- **Decentralised routing** — no central server required
- **End-to-end encryption** — messages are secure by default
- **Open source** — the firmware is freely available and community-maintained

## How It Works

Each node in a MeshCore network periodically broadcasts a heartbeat to its neighbours. This builds a dynamic routing table that knows how to reach every other node in the mesh. When you send a message, it hops from node to node until it reaches its destination.

### Key Concepts

- **Node** — a single device running MeshCore firmware
- **Mesh** — the collection of all interconnected nodes
- **Hop** — a single relay of data between two nodes
- **Gateway** — a node that bridges the mesh to the internet
- **MQTT Gateway** — connects the mesh to an MQTT broker, enabling internet-based message routing

## Use Cases

- **Community networks** — stay connected during events or in areas with poor infrastructure
- **Emergency communication** — maintain contact when cellular networks are down
- **Outdoor activities** — hiking, camping, festivals where phone coverage is unreliable
- **IoT sensor networks** — collect data from distributed sensors
- **Rural connectivity** — bridge communication gaps in underserved areas

## Getting Involved

The MeshCore community is active and welcoming. Whether you're a developer, a hardware enthusiast, or just someone curious about mesh networking, there's a place for you.
