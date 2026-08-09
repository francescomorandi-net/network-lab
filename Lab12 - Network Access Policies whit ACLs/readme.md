
# Lab12 - Network Access Policies whit ACLs

## Objective 
Design and implement Multi-Area OSPF network to demonstrate route advertisement, path selection, and key OSPF routing behaviours

### Design Note
Since this lab includes several advanced OSPF features working together, this Design Note highlights the main behaviors to observe while testing the topology.

The topology was designed for demonstration purposes only, in order to show specific OSPF behaviors that would be difficult to observe in a small and simple network.

In particular, this lab demonstrates the following features:
- **Intra-area route preference over inter-area routes**. To reach the 10.0.0.4 network, the OSPF costs were intentionally changed so that the path through R3 (Area1) has a lower metric than the path completely inside the Backbone Area. Even so, OSPF still prefers the intra-area path through R1 (10.0.0.2) or R2 (10.0.0.18), showing that the route type has higher priority than the metric alone.
- **Equal-cost Multi-Path (ECMP)**. The paths through R1 and R2 were configured with the same total cost to reach the 10.0.0.4 network. As a result, the Layer 3 switch SWDIST installs both routes in the routing table and performs load balancing. This behavior can be observed with "*show ip route*" and can also be verified with "*traceroute*", which may display different paths depending on the route selected by OSPF.
- **Default route advertisement**. The edge router R2 advertises a default route in the OSPF domain using "*default-information originate*", simulating access to an external network (WEB/Internet). NAT was intentionally not configured because it is not the goal of this lab and will be covered in a dedicated lab.
- **Passive Interface**. The interfaces connected to LANs, where no other OSPF routers are present, were configured as passive. This allows the networks to be advertised without sending unnecessary hello packets. This behaviour can be verified with "*show ip ospf interface*".
  
#### Prerequisites 
Lab08 - Rapid PVST+ Best Practices

## Topology
### Overall Topology
![Lab 12 Overall Topology](Lab_12_Network_Access_Policies_whit_ACLs.PNG)

### Details Policies
![Lab 12 Details Policies](Lab_12_Network_Access_Policies_whit_ACLs_details_policies.PNG)

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

