---
title: Coverage
description: Understanding mesh network coverage and how to improve it
---
# Coverage

Mesh network coverage depends on the density and placement of nodes. Unlike a cellular network with tall towers, a mesh network's reach grows with every additional node.

## How Coverage Works

Each node in the mesh has a radio range of roughly 1-5 km in urban environments and 10-20 km with clear line of sight. When nodes overlap, they form a connected mesh. Messages hop through intermediate nodes to reach their destination, so coverage is the union of all individual node ranges.

```
    [Node A] --- 3 km --- [Node B] --- 2 km --- [Node C]
        |                     |
     4 km                 5 km
        |                     |
    [Node D]             [Node E]
```

In this example, Node C can reach Node B (2 km), and Node B can reach Node A (3 km). Node C can talk to Node A even though they're 5 km apart, because Node B relays the message.

## Factors Affecting Range

| Factor | Impact |
|--------|--------|
| **Line of sight** | Best — range up to 20 km |
| **Urban environment** | Buildings reduce range to 1-3 km |
| **Indoor placement** | Walls and structures reduce range significantly |
| **Antenna quality** | A good antenna can double effective range |
| **Antenna height** | Higher placement = better range |
| **Weather** | Heavy rain can attenuate signals by 10-20% |
| **Radio interference** | Other devices on the same frequency band |

## Improving Coverage

The single best way to improve mesh coverage is to add more nodes. Each new node extends the mesh and creates alternative routing paths.

### Tips

- **Elevate antennas** — place them as high as practical, ideally at roof height or higher
- **Use line of sight** — position nodes to have a clear path to nearby nodes
- **Dense areas** — in urban areas, place nodes in upper-floor windows for best results
- **Gateways** — a node with internet backhaul extends the mesh globally via MQTT
- **Directional antennas** — for point-to-point links between fixed locations

## Checking Coverage

Use the MeshCore mobile app or web dashboard to see live node positions and signal strengths. Nodes that haven't been heard from in a while appear as offline.

### Key Metrics

- **SNR (Signal-to-Noise Ratio)** — higher is better; above 0 dB is usable, above 10 dB is excellent
- **RSSI (Received Signal Strength Indicator)** — closer to 0 is stronger; -80 dBm is good, -120 dBm is marginal
- **Hop count** — the number of relays your message travelled through; lower is faster and more reliable
