---
title: Join
description: How to join a MeshCore mesh network
---
# Join the Mesh

Joining a MeshCore network is straightforward. You need a compatible device, the MeshCore firmware installed, and a basic configuration.

## Step 1: Get Hardware

Choose a compatible ESP32 LoRa board. The easiest starting point is a **Heltec T-Deck** or **T-Beam**, which come with the radio, antenna, and battery support built in. See the [Hardware](/hardware) page for recommendations.

## Step 2: Flash the Firmware

MeshCore firmware can be installed via:

### Web Flasher (Easiest)

1. Connect your device to your computer via USB
2. Open the MeshCore web flasher at [meshcore.flasher](https://meshcore.github.io/flasher)
3. Select your device model
4. Click **Flash** and wait for the process to complete
5. Disconnect and reconnect the device

### PlatformIO (Advanced)

For developers or those who want the latest nightly builds:

```bash
git clone https://github.com/OpenMeshCore/MeshCore.git
cd MeshCore
pio run -e your_board -t upload
```

## Step 3: Configure Your Node

After flashing, the device creates a Wi-Fi access point called `MeshCore-XXXX`. Connect to it and open `http://192.168.4.1` in your browser.

### Basic Settings

| Setting | Description |
|---------|-------------|
| **Node Name** | A human-readable name for your node |
| **Location** | Enable GPS or manually set your approximate coordinates |
| **Region** | Set your regulatory region for the correct frequency |
| **Channel** | Leave as default unless instructed otherwise |
| **Encryption Key** | Set a mesh-wide encryption key if the network uses one |

### MQTT Gateway (Optional)

If your node has Wi-Fi, you can configure it as an MQTT gateway to bridge the mesh to the internet:

1. Connect your node to your home Wi-Fi
2. Set the MQTT server address (provided by your network operator)
3. Messages from the mesh will now be available via MQTT

## Step 4: Connect and Test

Once configured, your node will start broadcasting its presence. Within a few minutes, you should see other nodes appear if you're in range.

### What to Check

- LED blinking pattern indicates mesh activity
- The display (if your device has one) shows nearby nodes
- Try sending a message to a known node or a broadcast to the mesh
- Check signal strength indicators (RSSI/SNR) for link quality

## Step 5: Extend the Network

The most valuable thing you can do is simply keep your node powered on. Every active node strengthens the mesh and extends coverage for everyone.

Consider becoming a gateway operator if you have a reliable internet connection — this bridges the local mesh with the wider world.
