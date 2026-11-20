# Interfaces and Cables — Jeremy's IT Lab Day 2

**Date:** 2026-11-19 · **Source:** <https://www.youtube.com/watch?v=ieTH5lVhNaY&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=4>

## Key ideas
- Network devices usually have **RJ-45** ports (Registered Jack 45), used with copper cables.
- **Ethernet** is a collection of network protocols and standards.
- Connections between devices operate at a set speed, measured in **bits per second** (bps).
- A **bit** is a value of 0 or 1. A **byte** is 8 bits.
- **Bits vs bytes:** network speeds use bits (Mbps, lowercase b). File sizes use bytes (MB, uppercase B). Divide by 8 to convert: a 100 Mbps link downloads ~12.5 MB/s at most.
- The copper cables used in Ethernet standards are **UTP** (Unshielded Twisted Pair). There is no metal shield; twisting the pairs reduces **EMI** (electromagnetic interference).
- Informal names like `100BASE-T`: the number is the speed in Mbps, **BASE** = baseband signaling, **T** = twisted pair.

## Conversions
- 1 kilobit (kb) = 1,000 bits
- 1 megabit (Mb) = 1,000,000 bits
- 1 gigabit (Gb) = 1,000,000,000 bits
- 1 terabit (Tb) = 1,000,000,000,000 bits

## Ethernet standards (copper)

| Speed | Common name | IEEE standard | Informal name | Max length | Pairs used |
|---|---|---|---|---|---|
| 10 Mbps | Ethernet | 802.3i | 10BASE-T | 100 m | 2 pairs (4 wires) |
| 100 Mbps | Fast Ethernet | 802.3u | 100BASE-T | 100 m | 2 pairs (4 wires) |
| 1 Gbps | Gigabit Ethernet | 802.3ab | 1000BASE-T | 100 m | 4 pairs (8 wires) |
| 10 Gbps | 10 Gig Ethernet | 802.3an | 10GBASE-T | 100 m | 4 pairs (8 wires) |

All copper (UTP) standards have a maximum length of **100 m**.

## UTP pinout (10BASE-T, 100BASE-T)

| Device type | Transmit (Tx) pins | Receive (Rx) pins |
|---|---|---|
| Router | 1 and 2 | 3 and 6 |
| Firewall | 1 and 2 | 3 and 6 |
| PC | 1 and 2 | 3 and 6 |
| **Switch** | **3 and 6** | **1 and 2** |

Switches are the exception: they transmit on the pins where the other devices receive.

## Straight-through vs crossover cables
- **Straight-through:** pin 1 connects to pin 1, pin 2 to pin 2, etc. Used between **different** types of devices (PC ↔ switch, router ↔ switch), because one transmits on 1/2 and the other receives on 1/2.
- **Crossover:** pins 1/2 on one end connect to pins 3/6 on the other end. Used between **the same** type of device (router ↔ router, switch ↔ switch, PC ↔ PC). With a straight-through cable, both devices would transmit on the same pins and they couldn't communicate.

| Connection | Cable |
|---|---|
| Router ↔ Switch | Straight-through |
| Firewall ↔ Switch | Straight-through |
| PC ↔ Switch | Straight-through |
| Router ↔ Router | Crossover |
| Router ↔ Firewall | Crossover |
| Router ↔ PC | Crossover |
| Switch ↔ Switch | Crossover |

- **Auto MDI-X:** newer devices automatically detect which pins their neighbor transmits on and adjust their own Tx/Rx pins. So in practice the "wrong" cable usually still works.
- **1000BASE-T and 10GBASE-T** use all 4 pairs (8 wires), and each pair is **bidirectional** (it can transmit and receive). This is part of the reason they're much faster.

## Fiber-optic
- Fiber cables send **light** over glass fibers instead of electrical signals over copper.
- They connect to an **SFP transceiver** (Small Form-Factor Pluggable), which plugs into an SFP port on the device.
- Each end has **two connectors**: one to transmit and one to receive.
- Cable layers (inside → outside): (1) fiberglass core, (2) cladding that reflects light, (3) protective buffer, (4) outer jacket.

### Multimode vs single-mode
- **Multimode:** wider core. Light enters through multiple paths ("modes") and bounces around, so the signal spreads out with distance. **Shorter max length** (hundreds of meters). Cheaper transceivers.
- **Single-mode:** very narrow core. Light travels in a single path, so the signal stays clean over long distances. **Longer max length** (kilometers). More expensive transceivers (lasers).

### Fiber-optic standards

| Informal name | IEEE standard | Speed | Cable type | Max length |
|---|---|---|---|---|
| 1000BASE-LX | 802.3z | 1 Gbps | Multimode or single-mode | 550 m (MM) / 5 km (SM) |
| 10GBASE-SR | 802.3ae | 10 Gbps | Multimode | 400 m |
| 10GBASE-LR | 802.3ae | 10 Gbps | Single-mode | 10 km |
| 10GBASE-ER | 802.3ae | 10 Gbps | Single-mode | 30 km |

Memory trick: **S**R = **S**hort range, **L**R = **L**ong range, **E**R = **E**xtended range.

## UTP vs fiber-optic

| | UTP | Fiber-optic |
|---|---|---|
| Cost | Lower | Higher |
| Max distance | ~100 m | Much longer (up to km) |
| EMI | Can be affected | Not affected |
| Ports | RJ-45 (cheaper) | SFP (more expensive; single-mode > multimode) |
| Signal leakage | Emits a faint signal that can be copied (security risk) | Doesn't emit signal outside the cable |

## Lab
- Connected network devices in Packet Tracer using straight-through and crossover cables depending on the device types. For longer distances I chose fiber-optic cables (single-mode or multimode).

## Connect to security
- UTP cables leak a faint signal outside the cable that can be captured. This is a security risk to consider in sensitive scenarios.
- Fiber doesn't leak signal, which makes eavesdropping much harder (it would require physically tapping the cable).
- Physical security matters too: whoever can reach the cables or network ports can plug in or listen. That's why network closets and unused ports get locked down.
