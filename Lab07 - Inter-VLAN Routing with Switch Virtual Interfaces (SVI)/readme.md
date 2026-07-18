


# Lab07 - Inter-VLAN Routing with Switch Virtual Interfaces (SVI)

## Objective 
The objective of this lab is to implement Inter-VLAN Routing using Switch Vitural Interfaces (SVI) on a multilayer switch. By replacing the Router-on-a-Stick architecture with Layer 3 switching, the network adopts a more scalable and enterprise-oriented desgin while maintaining logical segmentation between VLANs. Additionally, a dedicated Management VLAN is introduced to separate infrastructure management traffic from user tarffic, preparing the network for future security and management implementations.

## Topology
![Lab 07 Topology](Lab_07_Inter-VLAN_Routing_with_Switch_Virtual_Interfaces_(SVI).PNG)

## Technologies
- Cisco Devices
- Cisco IOS
- Switch Virtual Interface (SVI)
- Inter-VLAN Routing
## Verification
- show running-config
- show startup-config
- show interfaces status
- show interfaces trunk
- show vlan brief
- show ip interface brief
- show ip route 
- Verify end-to-end connectivity (ping)
- Path verification (traceroute) 
## Key Takeaways
This lab demonstrates how Router-on-a-Stick (ROAS) enables Inter-VLAN Routing by providing Layer 3 connectivity between previously isolated VLANs over a single IEEE 802.1Q trunk link.
It reinforces the relationship between VLANs, IP subnets, and default gateways, showing how proper Layer 3 routing allows communication while preserving Layer 2 segmentation.
