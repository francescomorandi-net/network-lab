
# Lab08 - Rapid PVST+ Best Practices

## Objective 
Implement a production-oriented Rapid PVST+ configuration by selecting an appropriate Root Bridge, optimizing Layer 2 forwarding paths, and securing edge ports using PortFast and BPDU Guard, the most relevant STP features supported by Cisco Packet Tracer.
#### Design Note
By default, Rapid PVST+ elected an acce switch as the Root Bridge based on the Lowest Bridge ID. 
In this lab, the Distribution Switch is intentionally configured as the Root Bridge to create deterministic Layer 2 forwarding paths that better reflect an enterprise network design and simplify future troubleshooting.
PortFast and BPDU Guard are also configured on all access interfaces to provide faster edge-port convergence and protect against accidental switch connections. Although Cisco IOsS commonly enables these features trought global configuration, Cisco Packet Tracer dos not concistency reproduce this behavior. For this reason, they are configured individually on each access interface troughout this lab. 
Root Guard and Loop Guard are intentionally omitted, as their behavior to the limitations of the Cisco Packet Trace environment

#### Prerequisites 
Lab

## Topology
![Lab 08 Topology](Lab_08_Rapid_PVST+_Best_Practices.PNG)

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
This lab demonstrates how Switch Virtual Interface (SVI) enables Inter-VLAN Routing eliminating the need for an external router.
It reinforces the concepts of Layer 3 switching, default gateways, and logical network segmentation, while introducing a dedicated Management VLAN to separate infrastructure management traffic from user traffic within a more scalable enterprise-oriented network design.
