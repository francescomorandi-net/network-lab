
# Lab09 - OSPF Multi-Area and Path Selection

## Objective 
Design and impement Multi-Area OSPF network to demonstrate route advertisment, path selection, and key OSPF routing behaviours

### Design Note
Since this lab includes several advanced OSPF feautures working together, this Design Note highlights the main behaviors to observe while testing the topology.

The topology was designed for demostration purposes only, in order to show specific OSPF behaviors that would be difficult to observe in a small and simple network.

In particular, this lab demostrates the following features:
- **Intra-area route preference over inter-area routes**. To reach the 10.0.0.4 network, the OSPF costs were intentionally changed so that the path trough R3 (Area1) has a lower metric than the path completely inside the Backcone Area. Even so, OSPF still prefers the intra-area path trough R1(10.0.0.2) or R2 (10.0.0.18), showing that the route type has higher priority than the matric alone.
- **Equal-cost Multi-Patch (ECMP)**. The paths trough R1 and R2 were configured with the same total cost to reach the 10.0.0.4 network. As a result, the Layer 3 switch SWDIST installs both routes in the routing table and performs load balancing. This behavior can be observed whit "*show ip route*" and can also be verified with "*traceroute*", which may display different paths depending on the route selected by OSPF.
- **Default route advertisment**. The edge router R2 advertises a default route in the OSPF domain using "*default-information originate*", simulating access to an external network (WEB/Internet). NAT was intentionally not configured because it is not the goal of this lab and will be covered in a dedicated lab.
- **Passive Interface**. The interfaces connected to LANs, where no other OSPF routers are present, were configured as passive. This allows the networks to be advertised without sending unnecessary hello packets. This behaviour can be verified with "*show ip ospf interface*".
  
#### Prerequisites 
Lab08 - Lab0 8 Rapid PVST+ Best Practices

## Topology
![Lab 08 Topology](Lab_08_Rapid_PVST+_Best_Practices.PNG)

## Technologies
- Cisco Devices
- Cisco IOS
- Rapid PVST+
- PortFast
- BPDU Guard
  
## Verification
- show running-config
- show startup-config
- show spanning-tree
- show spanning-tree interfaces <interface> details
- show MAC address-table (confirm MAC learning and forwarding along the active Rapid PVST+ spanning tree)
- Verify end-to-end connectivity (ping)
## Key Takeaways
