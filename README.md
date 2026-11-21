# Small Office Network Lab

A Cisco Packet Tracer lab simulating a small office network with
segmented VLANs, DHCP, access control, and internet access via NAT.

## Topology
![Topology](screenshots/topology.png)

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

**Interfaces up with correct IPs**
![Interfaces](screenshots/show-ip-interface-brief.png)

**DHCP working on a PC**
![DHCP](screenshots/dhcp-ipconfig.png)

**Inter-VLAN routing: Staff can reach IT**
![Staff to IT](screenshots/staff-to-it-ping.png)

**ACL working: Guest is blocked from Staff**
![ACL](screenshots/guest-blocked-acl.png)

**NAT working: Guest can reach the internet**
![Internet](screenshots/guest-to-internet-nat.png)

**NAT translations table**
![NAT](screenshots/nat-translations.png)

## Configs
- [R1](configs/R1.txt)
- [SW1](configs/SW1.txt)
- [ISP](configs/ISP.txt)

## Tools
Cisco Packet Tracer, Cisco IOS CLI

## What I learned
[Write 2-3 real sentences here. Example: "My trunk between R1 and SW1
was down at first because I forgot `no shutdown` on the physical
interface. I also learned that an ACL applied in the wrong direction
blocks the wrong traffic, so I applied it inbound on the Guest
subinterface."]

## Next steps
- Add OSPF with a branch router
- Site-to-site VPN
- Network monitoring with Zabbix or LibreNMS
