
# Lab09 - OSPF Multi-Area and Path Selection

## Objective 
Design and implement Multi-Area OSPF network to demonstrate route advertisement, path selection, and key OSPF routing behaviours

### Design Note
The original infrastructure was based on routers interconnected through point-to-point links and the OSPF routing protocol, which provided alternative paths within the network. However, the Layer 3 switch SW-DIST, responsible for inter-VLAN routing, and the R2 Edge router, responsible for external connectivity and NAT functions, represented two single points of failure (SPOFs).

To introduce redundancy at both levels while preserving the existing architecture as much as possible, a backup router configured in Router-on-a-Stick mode was added. Through an additional Layer 2 switch and an IEEE 802.1Q trunk link, the backup router participates in the HSRP groups for VLANs 10 and 20, assuming the Active role and taking over forwarding through the respective virtual gateways if SW-DIST becomes unavailable.

On the WAN side, the original architecture included a point-to-point link between the WEB router and the Edge router. To implement HSRP redundancy at this level as well, the link was replaced with a multiaccess network using a Layer 2 switch, creating a shared broadcast domain between WEB, Edge, and the backup router.

However, introducing a single switch would have created a new single point of failure on the WAN side. To eliminate this dependency, a second independent multiaccess network was implemented using an additional Layer 2 switch, providing an alternative WAN path in case the first segment becomes unavailable.

The solution uses a total of six HSRP groups: two dedicated to the virtual gateways of VLANs 10 and 20, and four distributed across the two WAN segments. Each WAN broadcast domain contains two HSRP groups with distinct virtual IP addresses, independently used by the WEB router as next hops to reach the public IP addresses associated with static NAT and dynamic NAT/PAT, respectively.

This separation allows different priorities and interface tracking mechanisms to be configured, enabling independent selection of the HSRP Active router for the two traffic categories. For example, if SW-DIST fails, the backup router assumes the Active role for the groups dedicated to dynamic NAT/PAT, while R2 Edge remains Active for the groups associated with the server's static NAT, as long as it remains operational.

The coordination of HSRP, OSPF, and static routing manages path selection. On the WEB router, primary and floating static routes were configured with next hops corresponding to the HSRP virtual IP addresses of the respective WAN segments, allowing failover to the alternative WAN link. Within the internal network, since both Edge and the backup router can advertise a default route through OSPF, static routes with an administrative distance of 105 were configured on selected devices to prefer the path through Edge over OSPF routes with an administrative distance of 110.

The public IP addresses used for NAT translations are kept independent of the WAN transit subnets, allowing them to remain reachable through either WAN segment without changing the translated addresses during failover.

The solution still has some limitations. Dynamic NAT sessions are not synchronized between Edge and the backup router and may therefore be interrupted during failover, requiring new connections to be established. Additionally, failure detection based on interface status and route availability does not guarantee coverage of every possible partial connectivity failure, especially when interfaces remain operational.
  
#### Prerequisites 
Lab08 - Rapid PVST+ Best Practices

## Topology
### Overall Topology
![Lab 09 Overall Topology](Lab09_OSPF_Multi-Area_Routing_and_Path_Selection.PNG)

### Routing Topology (Detailed View)
![Lab 09 Routing Topology](Lab09_OSPF_Multi-Area_Routing_and_Path_Selection_Routing_View.PNG)

## Technologies
- Cisco Devices
- Cisco IOS
- IPv4
- OSPFv2
  
## Verification
- show running-config
- show startup-config
- show ip protocols
- show ip ospf database
- show ip ospf neighbor
- show ip ospf interface brief
- show ip ospf interface
- show ip route
- Verify end-to-end connectivity (ping)
- Path verification (traceroute)
  
## Key Takeaways
This lab was designed to demonstrate OSPF's decision-making process and help understand how the protocol works. It also shows how proper network design allows the administrator to influence OSPF's behaviour, making routing decisions predictable and controlled.
