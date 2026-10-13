# Home Network Lab

A physical Cisco home lab I built while studying for the CCNA (200-301). The goal is to practice real switching, routing, and security work on actual hardware, not just in a simulator.

> Addresses, credentials, device configs, and management details are intentionally left out of this repo.

## Hardware

| Role | Device |
|---|---|
| Router | Cisco 1921/K9 |
| Switch | Cisco Catalyst WS-C2960-24TT-L |
| Wi-Fi | Two TP-Link Omada access points (one wired, one meshed) |
| Practice gear | Spare Cisco routers and switches for CCNA topologies |

## What is built

- **Segmentation:** five VLAN subnets, including family Wi-Fi, guest, and IoT.
- **Routing:** the switch trunks the VLANs to the router, which handles inter-VLAN routing (router-on-a-stick) and DHCP.
- **Access control:** ACLs on the router keep the guest and IoT subnets away from trusted VLANs.
- **Layer 2 hardening:** port security and DHCP snooping on the switch.
- **Wireless:** access points covering multiple floors.

## Lessons learned

- Dynamic ARP Inspection is not supported on the Catalyst 2960 platform, so DAI has to be done on a different switch.

## Troubleshooting write-up

- [Microphone echo in a live-event audio chain](troubleshooting/propresenter-echo.md)
