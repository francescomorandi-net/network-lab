


# Lab06 - Router-on-a-Stick (ROAS) Inter-VLAN Routing

## Objective 
The objective of this lab is to implement Inter-VLAN Routing using the Router-on-a-Stick (ROAS) architecture. By configuring IEEE 802.1Q subinterfaces, the router provides Layer 3 connectivity between previosly isolated VLANs while preserving Layer 2 segmentation.

### Design Note & Prerequisites
Lab05 - VLANs and IEEE 802.1Q Trunking

This topology has been intentionally preserved from the previous lab to clearly demonstrate the implementation of Router-on-a-Stick (ROAS).
Althoug this asymmetrical design is not representative of a production environment, it effectively highlites the solution to the communication limitations introduced in the previous lab.


## Topology
![Lab 07 Topology](Lab06_Router-on-a-stick_(ROAS)_Inter-VLAN_Routing.PNG)

## Technologies
- Cisco Devices
- Cisco IOS
- Router-on-a-Stick (ROAS)
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
