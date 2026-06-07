---
title: Coverage
description: How MeshCore network coverage works in the North East UK
---
# Coverage

MeshCore coverage depends on the placement of nodes and repeaters. Unlike a cellular network with tall towers, a mesh network's reach grows with every additional repeater.

## How It Works

Each device has a radio range — typically a few hundred metres to several kilometres depending on terrain, antenna, and power. **Clients do not repeat.** Only repeaters (and room servers with repeat enabled) forward traffic.

This means coverage is determined by the **reach and placement of repeaters**, not the number of clients.

## Radio Settings & Range

The North East network uses **869.618 MHz** with the **narrow preset** (BW62.5, SF8, CR5). This configuration:

- **Fits between ISM band interference** — the narrow bandwidth avoids noisy parts of the 868 MHz band
- **Provides better SNR** — lower noise floor improves signal-to-noise ratio
- **Gives good range** — SF8 balances distance and airtime. Higher SF (e.g. SF11) goes further but uses more airtime; lower SF (SF7) is faster but shorter range
- **Standard coding rate (CR5)** — reliable forward error correction

All nodes in the North East mesh should use the same radio settings to communicate.

## Factors Affecting Range

| Factor | Impact |
|--------|--------|
| **Line of sight** | Best case — maximum range |
| **Urban environment** | Buildings and obstacles reduce range significantly |
| **Antenna quality** | A good antenna tuned for 868 MHz is the most effective upgrade |
| **Antenna height** | Higher placement = better range. Roof height is ideal |
| **Spreading Factor** | Higher SF = longer range, slower data, more airtime |
| **Bandwidth** | Narrower BW fits between interference but reduces data rate |

## Improving Coverage

- **Add repeaters** — each repeater extends the mesh and provides alternative routing paths
- **Elevate antennas** — place repeaters as high as practical (roof height or higher)
- **Use line of sight** — position repeaters with clear paths to neighbouring nodes
- **Use the right antenna** — a good antenna tuned for 868/869 MHz is the most effective upgrade. A quarter-wave whip is only ≈ 8.2 cm at 868 MHz, so check any whip is cut for this band

## Path-Based Routing vs Flood

MeshCore uses **hybrid path-based routing** — it floods only briefly to discover a destination, then messages follow a specific learned sequence of repeaters. This means:

- Coverage is not simply "all nodes within range of any node" — routes must exist through repeaters
- A client within radio range of a repeater has coverage to any destination that repeater can reach
- Without a repeater nearby, a client can only communicate with other clients within direct radio range

## Hop Limit

Repeaters have a configurable maximum hop count (`set flood.max`). This prevents messages from propagating indefinitely and lets repeater administrators control their network. The internal firmware maximum is 64 hops.
