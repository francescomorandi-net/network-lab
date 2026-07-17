

# Lab06 - Router-on-a-stick (ROAS) Inter-VLAN Routing

## Objective 
The objective of this lab is to implement Inter-VLAN Routing using the Router-on-a-stick (ROAS) architecture. By configuring IEEE 802.1Q subinterfaces, the router provides Layer 3 connectivity between previosly isolated VLANs while preserving Layer 2 segmentation.

###Design note & Prerequisites


## Topology
![Lab 06 Topology](Lab06_Router-on-a-stick_(ROAS)_Inter-VLAN_Routing.PNG)

## Technologies
- Cisco Devices
- Cisco IOS
- VLANs
- IEEE 802.1Q Trunking
    #### Configuration Highlights
- Dedicated unused native VLAN
- Restricted allowed VLAN list on the trunk
- Intentional VLAN misconfiguration for connectivity testing
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
