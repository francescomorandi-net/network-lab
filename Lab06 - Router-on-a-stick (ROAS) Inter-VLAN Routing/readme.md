

# Lab06 - Router-on-a-Stick (ROAS) Inter-VLAN Routing

## Objective 
The objective of this lab is to implement Inter-VLAN Routing using the Router-on-a-Stick (ROAS) architecture. By configuring IEEE 802.1Q subinterfaces, the router provides Layer 3 connectivity between previosly isolated VLANs while preserving Layer 2 segmentation.

### Design Note & Prerequisites
Lab05 - VLANs and IEEE 802.1Q Trunking

This topology has been intentionally preserved from the previous lab to clearly demonstrate the implementation of Router-on-a-Stick (ROAS).
Althoug this asymmetrical design is not representative of a production environment, it effectively highlites the solution to the communication limitations introduced in the previous lab.


## Topology
![Lab 06 Topology](Lab06_Router-on-a-stick_(ROAS)_Inter-VLAN_Routing.PNG)

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
- Verify end-to-end connectivity (ping):
    - Between hosts in the same VLAN
    - To the intentionally misconfigured host to verify VLAN isolation
## Key Takeaways
This lab demonstrates how VLANs logically segment Layer 2 networks and how IEEE 802.1Q trunking carries multiple VLANs across interconnected switches. It also reinforces Layer 2 security best practices and shows how an incorrect VLAN assignment prevents communication, even between hosts in the same IP subnet.
