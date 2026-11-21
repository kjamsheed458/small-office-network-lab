# Small Office Network Lab

A Cisco Packet Tracer lab simulating a small office network with
segmented VLANs, DHCP, access control, and internet access via NAT.

## Topology
![Network Topology](screenshort/Network%20Topology.png)

## Features
- 3 VLANs (Staff, Guest, IT) with inter-VLAN routing (router-on-a-stick)
- DHCP server on R1 for all VLANs
- Extended ACL isolating the Guest VLAN from Staff and IT
- NAT overload (PAT) for internet access
- Default route to the ISP router

## IP Addressing
| VLAN | Name | Network | Gateway |
|---|---|---|---|
| 10 | STAFF | 192.168.10.0/24 | 192.168.10.1 |
| 20 | GUEST | 192.168.20.0/24 | 192.168.20.1 |
| 30 | IT | 192.168.30.0/24 | 192.168.30.1 |

WAN link: R1 (203.0.113.1/30) to ISP (203.0.113.2/30)

## Verification

**Sub-interfaces are up**
![Sub-interfaces](screenshort/sub-interfaces%20are%20up.png)

**Inter-VLAN routing works: Staff can ping IT**
![Staff to IT](screenshort/Staff%20pc%20pinging%20IT%20pc%20means%20inter-vlan-routing%20work.png)

**ACL works: Guest cannot ping Staff**
![Guest blocked](screenshort/Guest%20pc%20can%27t%20ping%20Staff%20pc%20mean%20ACL%20work.png)

**ACL counters show blocked traffic**
![ACL counters](screenshort/ACL%20counter%20show%20block%20traffic.png)

**NAT and routing work: Guest can ping 8.8.8.8**
![Guest to internet](screenshort/Guest%20can%20ping%208.8.8.8%20mean%20NAT%20and%20routing%20work.png)

**NAT is translating addresses**
![NAT translations](screenshort/NAT%20is%20translating%20addresses.png)

## Files
- [Packet Tracer file](small-office-network.pkt)
- [R1 config](Configs/R1.txt)
- [SW1 config](Configs/SW1.txt)
- [ISP config](Configs/ISP.txt)

## Tools
Cisco Packet Tracer, Cisco IOS CLI

## What I learned
[Write 2-3 real sentences about a problem you hit and how you fixed it.]

## Next steps
- Add OSPF with a branch router
- Site-to-site VPN
- Network monitoring with Zabbix or LibreNMS
