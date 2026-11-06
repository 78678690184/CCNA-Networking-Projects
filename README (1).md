# Project 05 – VLAN Configuration

## Overview
This Packet Tracer project demonstrates how to create VLANs on a Cisco Layer 2 switch and assign access ports to them.

**Scenario:** A university department has three groups connected to one switch:
- VLAN 10 – A (192.168.1.0/24)
- VLAN 20 – B (192.168.2.0/24)
- VLAN 30 – C (192.168.3.0/24)

Each group has two PCs connected to the same switch.

## Topology and Port Assignment

| Switch Port | Connected PC | VLAN | Network |
|---|---|---:|---|
| Fa0/1 | PC (top-left) | 10 | 192.168.1.0/24 |
| Fa0/2 | PC (middle-left) | 20 | 192.168.2.0/24 |
| Fa0/3 | PC (bottom-left) | 30 | 192.168.3.0/24 |
| Fa0/4 | PC (top-right) | 10 | 192.168.1.0/24 |
| Fa0/5 | PC (middle-right) | 20 | 192.168.2.0/24 |
| Fa0/6 | PC (bottom-right) | 30 | 192.168.3.0/24 |

## VLAN Configuration

The switch has these VLANs:
- VLAN 10: A
- VLAN 20: B
- VLAN 30: 30

Access ports are assigned as follows:
- Fa0/1 and Fa0/4 → VLAN 10
- Fa0/2 and Fa0/5 → VLAN 20
- Fa0/3 and Fa0/6 → VLAN 30

## Important Communication Rule

> **PCs in the same VLAN can communicate with each other (provided their IP addressing is correct). PCs in different VLANs cannot communicate in this Layer 2-only lab.**

For example:
- VLAN 10 PC ↔ VLAN 10 PC: Ping should work.
- VLAN 20 PC ↔ VLAN 20 PC: Ping should work.
- VLAN 30 PC ↔ VLAN 30 PC: Ping should work.
- VLAN 10 ↔ VLAN 20 or VLAN 30: Ping will fail in this lab.

**Reason:** Different VLANs are separate Layer 2 broadcast domains and are normally assigned different IP subnets. Communication between them requires **Inter-VLAN Routing**, provided by a router (for example, Router-on-a-Stick) or a Layer 3 switch with routing configured. No router or Layer 3 switch is configured in this project.

## Verification

Run these commands on the switch:

```cisco
show vlan brief
show interfaces fa0/1 switchport
show running-config
```

`show vlan brief` should show:
- VLAN 10: Fa0/1, Fa0/4
- VLAN 20: Fa0/2, Fa0/5
- VLAN 30: Fa0/3, Fa0/6

## Learning Outcomes
- Create VLANs.
- Name VLANs.
- Configure switch ports as access ports.
- Assign access ports to VLANs.
- Verify VLAN membership.
- Understand why Inter-VLAN Routing is required for communication between different VLANs.

## Files
- `VLAN-Configuration.pkt` – Packet Tracer topology and configuration.
- `VLAN-Commands.txt` – CLI commands used in this lab.
- `README.md` – Project overview, topology, VLAN mapping, and ping behavior.
