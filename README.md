**Zenith: Stratospheric Balloon Communication Systems**

A project for apex.hackclub.com by Aileen Rivera with help from Benjamin Faershtein

**Abstract**
This research investigates the feasibility of deploying decentralized LoRa mesh networks at stratospheric altitudes to extend emergency communication capabilities beyong traditional terrestrial limitations. Through rigorous analysis of RF propagation characteristics, network topology optimization, and environmental factor correlations, this project aims to validate theoretical models for near-space mesh networking while establishing practical frameworks for rapid-deployment emergency communication systems.

**Research Motivation & Problem Statement**
Critical infrastructure failures during natural disasters consistently demonstrate the vulnerability of centralized communication networks. The 2011 Tōhoku earthquake, Hurricane Maria's impact on Puerto Rico, and recent wildfire communications blackouts highlight a persistent challenge: when commerical networks fail, communities become isolated precisely when coordination is most critical.

Traditional amateur radio emergency networks, while resilient are constrained by line-of-sight limitations and terrain obstacles. Satellite communication systems, though effective, require substantial infrastructure investments and often suffer from capacity limitations during widespread emergencies.

Research Question: Can stratospheric LoRa mesh networks provide a cost-effective, rapidly-deployable solution for emergency communications that bridges the gap between terrestrial amateur radio and satellite systems?

**Theoretical Framework & Hypotheses**
**Primary Hypothesis**
Deploying LoRa mesh nodes at stratospheric altitudes (60,000-100,000 feet) will demonstrate exponential improvements in communication range compared to ground-level deployments, enabling practical emergency communication coverage over 400+ mile radius areas through mesh topology redundancy.

**Secondary Hypotheses**
1. **Propagation Enhancement:** Reduced atmospheric density and unobstructed line-of-sight at stratospheric altitudes will enable LoRa communication ranges exceeding 100 kilometers between nodes
2. **Network Resilience:** Mesh topology will maintain connectivity even with 40-60% node failure rates through dynamic routing optimization
3. **Environmental Correlation:** Atmospheric conditions, electromagnetic interference, and altitude-dependent factors will exhibit measurable correlations with network performance metrics

**Technical Architecture & Innovation**
Hardware Platform Selection
After extensive comparative analysis of available platforms, I selected the RAK Wireless ecosystem for its optimal balance of power efficiency, environmental resilience, and modular expandability:

Primary MCU: nRF52840 (ARM Cortex-M4, 1MB Flash, 256KB RAM)
LoRa Transceiver: Semtech SX1262 (configurable spreading factors SF7-SF12)
GNSS Module: u-blox ZOE-M8Q with high-altitude flight mode capability
Environmental Sensing: Integrated temperature, pressure, humidity, and air quality monitoring

**Power Managmenet Optimization**
Power is always the limiting factor in balloon payloads:

LoRa radio: ~20 mA during transmission (13 dBm output), 0.2 µA standby
GPS module: 25 mA during acquisition, 20 mA tracking (34s cold start, 1s hot start)
Environmental sensor: Few mA when active
nRF52: Leveraging power-saving modes and configurable sleep cycles

The Energizer Ultimate Lithium batteries are key here - they maintain performance in extreme cold and have excellent energy density.

**Data Collection Plan**
Performance Data
- Communication range between balloon and ground stations
- Message success rates and retry statistics
- Network topology changes as balloons move
- Signal strength (RSSI) variations with distance/altitude

**Environmental Context**
GPS telemetry (position, altitude, speed)
Temperature, pressure, humidity from environmental sensors
Battery voltage and power consumption over time

**Network Analysis**
- Mesh routing efficiency - how messages find their way through the network
- Node discovery - how quickly balloons find each other
- Range limits - where does connectivity finally break down?

**Technical Challenges I'm Solving**
Weight Optimization
Target weight: ~125g total. Every component choice matters when you're trying to reach maximum altitude.

Cold Weather Operation
The stratosphere is brutal (-40°F+). I'm using components rated for extended temperature ranges and adding thermal insulation where needed.

Integration Flexibility
The RAK WisBlock system gives me I2C, SPI, and GPIO connectivity. The GPS connects via UART, environmental sensors use the modular ecosystem, and Bluetooth enables pre-launch configuration.

Hybrid Communications
The beauty of this setup is creating a hybrid air-to-ground system. Ground-based Meshtastic nodes integrate seamlessly, and with MQTT bridging, telemetry could potentially reach internet-connected nodes for global dissemination.

Why This Matters
When disasters strike and cell towers fail, we need communication systems that work independently. A stratospheric LoRa mesh could:

- Provide emergency coverage over 400+ mile radius areas
- Create redundant networks by launching multiple balloons
- Enable delay-tolerant messaging for disaster coordination
- Work with existing Meshtastic infrastructure on the ground

Expected Results
I'm hoping to demonstrate:

- Extreme range performance - potentially 100+ km between nodes
- Reliable mesh routing even as balloons drift and move
- Practical emergency applications with real-world range data
- Integration capabilities between aerial and ground-based nodes

Follow along for launch updates and data analysis. Let's see just how far we can push LoRa mesh networking! :)
