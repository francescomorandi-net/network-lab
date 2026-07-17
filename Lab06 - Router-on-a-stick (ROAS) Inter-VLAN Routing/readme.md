

# Lab06 - Router-on-a-stick (ROAS) Inter-VLAN Routing

## Objective 
Configure VLANs and IEEE 802.1Q trunking to extend Layer 2 connectivity across multiple switches, implement Layer 2 security best practices, and verify VLAN-based network segmentation.

## Topology
![Lab 06 Topology](Lab_05_VLANs_and_IEEE_802.1Q_Trunking.PNG)

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
