# Enterprise VLAN Segmentation and Inter-VLAN Routing

## Overview
This project demonstrates a small enterprise LAN design using VLAN segmentation and inter-VLAN routing on a multilayer switch. Departments are separated into individual broadcast domains while still allowing controlled communication through Layer 3 routing.

The focus of this project is practical enterprise networking fundamentals rather than complex or oversized designs.

---

## Network Purpose
The network represents a small office environment where different departments require logical separation for stability and security while maintaining routed connectivity.

---

## Topology Design
The network uses a simple two-tier layout:

- End devices connect to an access switch
- The access switch connects to a multilayer switch using an 802.1Q trunk
- All routing and DHCP services are handled by the multilayer switch

This approach keeps Layer 2 traffic local and centralizes routing.

---

## VLAN and IP Addressing

| VLAN | Department | Subnet | Default Gateway |
|-----|-----------|--------|----------------|
| 10 | IT | 10.10.10.0/24 | 10.10.10.1 |
| 20 | Users | 10.10.20.0/24 | 10.10.20.1 |
| 30 | Servers | 10.10.30.0/24 | 10.10.30.1 |

Each VLAN is a separate broadcast domain, with routing provided by SVIs on the multilayer switch.

---

## Configuration Summary
- VLANs created on both switches
- Access ports assigned to the appropriate VLANs
- Trunk configured between switches with only required VLANs allowed
- SVIs created for each VLAN on the multilayer switch
- IP routing enabled on the multilayer switch
- DHCP pools configured for each VLAN

---

## Verification and Testing
The following checks were used to confirm correct operation:

- VLAN membership and trunk status
- SVI interface status (up/up)
- Routing table entries
- DHCP address assignment
- Inter-VLAN connectivity using ping

Example verification commands:
show vlan brief
show interfaces trunk
show ip interface brief
show ip route

yaml
Copy code

---

## Design Decisions
- Routing is centralized on the multilayer switch to avoid router-on-a-stick bottlenecks
- VLAN segmentation is used to reduce broadcast traffic and separate departments
- Trunk VLANs are explicitly defined to prevent unnecessary traffic
