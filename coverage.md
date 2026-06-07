---
title: Coverage
description: How MeshCore network coverage works
---
# Coverage

MeshCore coverage depends on the placement of nodes and repeaters. Unlike a cellular network with tall towers, a mesh network's reach grows with every additional repeater.

## How It Works

Each device has a radio range — typically a few hundred metres to several kilometres depending on terrain, antenna, and power. **Clients do not repeat.** Only repeaters (and room servers with repeat enabled) forward traffic.

This means coverage is determined by the reach and placement of repeaters, not the number of clients.

## Factors Affecting Range

| Factor | Impact |
|--------|--------|
| **Line of sight** | Best case — maximum range |
| **Urban environment** | Buildings and obstacles reduce range significantly |
| **Antenna** | Quality, tuning, and height matter more than power |
| **Antenna height** | Higher placement = better range |
| **Spreading Factor** | Higher SF = longer range, slower data, more airtime |
| **Bandwidth** | Narrower BW fits between interference but reduces data rate |

## Improving Coverage

- **Add repeaters** — each repeater extends the mesh and provides alternative routing paths
- **Elevate antennas** — place repeaters as high as practical (roof height or higher)
- **Use line of sight** — position repeaters with clear paths to neighbouring nodes
- **Use the right antenna** — a good antenna tuned for your frequency is the most effective upgrade

## Coverage vs MeshTopology

MeshCore is not a flood-based system. It uses path-based routing: messages follow a specific sequence of repeaters to their destination. This means:

- Coverage is not simply "all nodes within range of any node" — routes must exist through repeaters
- A client within radio range of a repeater has coverage to any destination that repeater can reach
- Without a repeater nearby, a client can only communicate with other clients within direct radio range

## Hop Limit

Repeaters have a configurable maximum hop count (`set flood.max`). This prevents messages from propagating indefinitely and lets repeater administrators control their network.
