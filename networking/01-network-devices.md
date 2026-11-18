# Network Devices — Jeremy's IT Lab Day 1

**Date:** 2026-11-17 · **Source:** <https://www.youtube.com/watch?v=H8W9oMNSuwo&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=2>

## Key ideas
- A computer network is a digital telecommunications network that allows nodes to share resources.
- A client is a device that accesses a service made available by a server.
- A server is a device that provides functions or services for clients.
- Switches forward traffic within a LAN (Local Area Network).
- Routers provide connectivity between LANs.
- Firewalls monitor and control network traffic based on configured rules.

## New to me
- Honestly, I already knew a lot of the concepts in this first lesson, but I didn't know there are two types of firewalls:
  - **Network firewall:** a dedicated device that filters traffic between networks.
  - **Host-based firewall:** software that protects a single host (e.g. `ufw`, `nftables`).
- A network firewall can be placed inside or outside the network (before or after the router).
- Switches commonly have 24+ ports, while routers usually have fewer interfaces than switches. Something I had never thought about, but useful for identifying devices in a diagram.

## Lab
- First attempt: I didn't configure anything. I just recreated the diagram from the video to memorize the symbology of routers, switches, the internet, end hosts, etc.
- File: [`labs/day01-lab.pkt`](labs/day01-lab.pkt)

## Connect to security
- End hosts (endpoints) are usually the ones attacked, which is why firewalls are needed: they let you control the traffic on your network to protect your services and clients.
- Best practice is to use both types at the same time (*defense in depth*). For example, my home server needs its own host-based firewall even with the router in front of it.
