
# Lab12 - Network Access Policies whit ACLs

## Objective 
Implement and verify network access policies using Standard and Extended ACLs within an existing OSPF multi-area topology, controlling communication between internal networks, access to specific services, and traffic to and from the Internet.

### Design Note
- Policy 1 – Internet Anti-Spoofing
A Standard ACL was applied inbound on the Internet-facing interface to block traffic with source addresses belonging to the RFC1918 private address ranges. This provides basic anti-spoofing protection against packets entering the network with private source addresses that should not originate from the Internet.

2. Policy 2 – Restricted Network Internet Access
Internet access from the Restricted Network (192.168.40.0/24) was denied through a Standard ACL applied outbound on the Internet-facing interface. This placement ensures that only Restricted Network traffic actually leaving the infrastructure is blocked, without having to explicitly exclude the multiple internal networks that must remain reachable.

3. Policy 3 – Network Isolation
Communication between the Users network (192.168.10.0/24) and the Restricted Network (192.168.40.0/24) was denied in both directions. The policy was distributed across the gateways of both networks, filtering unauthorized traffic close to each source. This prevents packets that will ultimately be dropped from unnecessarily traversing the shared routed infrastructure. This approach also reduces dependency on a single filtering point: if one of the two ACLs were removed, the other would still prevent bidirectional communication from being successfully completed between the two networks. However, this does not provide complete redundancy, since unidirectional traffic could still reach the opposite network.

4. Policy 4 – Service Access Control
Access from the Users network (192.168.10.0/24) to the remote server was restricted to HTTP, HTTPS, DNS, and ICMP. All other traffic from the Users network toward the server is denied, while traffic not affected by this policy remains permitted.

5. Stateful Firewall Consideration
No mirrored policy was implemented to specifically block connections initiated from the Internet toward the Restricted Network. In a typical enterprise architecture, this function would normally be handled by a stateful firewall at the network perimeter. A firewall is not implemented in this lab, as the focus is specifically on ACL-based policy enforcement.

6. Stateless ACLs and Server Return Traffic
No mirrored ACL was implemented on the server side to filter return traffic toward the Users network. Traditional ACLs are stateless and do not maintain information about established sessions. Client-initiated connections normally use ephemeral source ports, which become destination ports in the server's return traffic. Therefore, a simple mirrored policy based on service ports cannot automatically identify legitimate return traffic. A stateful firewall, instead, maintains session state and can dynamically distinguish legitimate return traffic from newly initiated connections.

7. ACL Testing and OSPF ECMP
To test Policy 1 – Internet Anti-Spoofing without adding additional external networks to the topology, loopback interfaces using RFC1918 private address ranges were configured on the router simulating the Internet. During tracert testing, non-intuitive hop sequences were observed due to OSPF ECMP paths with equal cost but different hop counts, which can cause successive probes to follow different paths. Despite this behavior, the test produced the expected result, confirming that the anti-spoofing policy was operating correctly.
  
#### Prerequisites 
Lab08 - Rapid PVST+ Best Practices

## Topology
### Overall Topology
![Lab 12 Overall Topology](Lab12_Network_Access_Policies_whit_ACLs.png)

### Details Policies
![Lab 12 Details Policies](Lab12_Network_Access_Policies_whit_ACLs_details_policies.png)

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

