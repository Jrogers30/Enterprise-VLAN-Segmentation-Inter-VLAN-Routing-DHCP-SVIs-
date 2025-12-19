Enterprise VLAN Segmentation and Inter-VLAN Routing
Project Overview

This project demonstrates the design and implementation of a small enterprise LAN using VLAN segmentation and inter-VLAN routing on a multilayer switch. The network separates departments into individual broadcast domains while allowing controlled communication through Layer 3 routing.

The goal of this project is to show practical understanding of basic enterprise network design, not just configuration commands.

Network Purpose

The network represents a small office environment where different departments must be logically separated for stability and security, but still need to communicate through a central routing device.

Topology

The network uses a simple two-tier design:

End devices connect to an access switch

The access switch connects to a multilayer switch using an 802.1Q trunk

All routing and DHCP services are handled by the multilayer switch

This design keeps Layer 2 traffic local and centralizes routing.

VLAN and IP Design
VLAN	Purpose	Subnet	Gateway
10	IT	10.10.10.0/24	10.10.10.1
20	Users	10.10.20.0/24	10.10.20.1
30	Servers	10.10.30.0/24	10.10.30.1

Each VLAN is a separate broadcast domain, with routing provided by SVIs on the multilayer switch.

Configuration Summary

VLANs created on both switches

Access ports assigned to the correct VLANs

Trunk configured between switches with required VLANs only

SVIs created on the multilayer switch

IP routing enabled on the multilayer switch

DHCP pools configured for each VLAN

Verification

The following checks were used to confirm correct operation:

VLAN membership and trunk status

SVI interface status

Routing table entries

DHCP address assignment

Inter-VLAN connectivity using ping

Example commands:

show vlan brief
show interfaces trunk
show ip interface brief
show ip route

Design Decisions

Routing is centralized on the multilayer switch to avoid router-on-a-stick bottlenecks

VLANs are used to limit broadcast traffic and separate departments

Trunk VLANs are explicitly defined to avoid unnecessary traffic
