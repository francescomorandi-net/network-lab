
# Lab12 - Network Access Policies whit ACLs

## Objective 
Implement and verify network access policies using Standard and Extended ACLs within an existing OSPF multi-area topology, controlling communication between internal networks, access to specific services, and traffic to and from the Internet.

### Design Note

  
#### Prerequisites 
Lab08 - Rapid PVST+ Best Practices

## Topology
### Overall Topology
![Lab 12 Overall Topology](Lab12_Network_Access_Policies_whit_ACLs.PNG)

### Details Policies
![Lab 12 Details Policies](Lab12_Network_Access_Policies_whit_ACLs_details_policies.PNG)

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

