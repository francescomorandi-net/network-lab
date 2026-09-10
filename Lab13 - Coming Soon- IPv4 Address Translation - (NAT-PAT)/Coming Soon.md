
# Lab13 - IPv4 Address Translation - (NAT/PAT)

## Objective 
Implement and verify different IPv4 address translation mechanisms on the network edge, integrating Static NAT, Dynamic NAT, and NAT OVERLOAD/PAT into the existing network access policies.
The lab demonstrates how different internal networks can use different translation methods while maintaining clear and non-overlapping NAT classifications.

### Design Note
The topology builds upon Lab 12 – Network Access Policies with ACLs, preserving the previously implemented traffic policies while introducing IPv4 address translation on the Edge router.

Three different translation mechanisms were implemented:

- Static NAT maps Server0 (192.168.30.2) to a dedicated public address, providing a permanent one-to-one translation and allowing the server to be addressed from the outside through its Inside Global address.

- Dynamic NAT translates hosts belonging to the 192.168.20.0/24 Servers network using addresses dynamically allocated from a configured public address pool.

- PAT (NAT Overload) provides Internet translation for the 192.168.10.0/24 Users network, allowing multiple internal hosts to share the Edge router public address.

The 192.168.40.0/24 Restricted network is deliberately excluded from NAT classification, consistently with the Internet access restriction already implemented in Lab 12.

NAT classification was intentionally designed to avoid unnecessary overlapping matches. Networks associated with Static NAT, Dynamic NAT, or restricted access are explicitly excluded from the PAT classification. This makes the intended translation behavior immediately identifiable and improves configuration readability, troubleshooting, and future maintenance.

Descriptive ACL and NAT pool names are also used to make the relationship between traffic classification and translation policy easier to identify.

#### Prerequisites 
Lab12 - Network Access Policies with ACLs
## Topology
### Overall Topology
![Lab 12 Overall Topology](Lab12_Network_Access_Policies_with_ACLs.png)

### Details Policies
![Lab 12 Details Policies](Lab12_Network_Access_Policies_with_ACLs_details_policies.png)

## Technologies
- Cisco Devices
- Cisco IOS
- IPv4
- OSPFv2
- Named Standard/Extended ACLs
  
## Verification
- show running-config
- show startup-config
- show ip access-list
- show ip interface
- show ip route
- Verify end-to-end connectivity (ping)
- Path verification (traceroute)
  
## Key Takeaways
ACL placement and direction are as important as ACL configuration, as they determine where traffic is filtered and how efficiently security policies are enforced. Standard and Extended ACLs provide different levels of control: Standard ACLs filter traffic based on source addresses, while Extended ACLs allow more granular filtering based on source, destination, protocol, and service. Traditional ACLs are stateless and have limitations when applying mirrored controls to client-server traffic. In this lab, no ACL was implemented on the server side toward VLAN 10 because responses to client-initiated connections are directed to ephemeral ports that cannot be known in advance. A stateful control, as provided by a firewall, would instead dynamically allow traffic belonging to previously established sessions. When multiple security policies must be enforced on the same interface and in the same direction, their rules must be combined into a single ACL.

N.B. – Multipath Routing: In multipath environments, traceroute results require careful interpretation, as successive probes may follow different paths and produce non-intuitive hop sequences. Such behavior does not necessarily indicate a routing or connectivity issue; in this lab, despite the unusual traceroute output, traffic behavior and policy enforcement operated as expected.

