# HPE Aruba Networking AOS-CX CLI Cheat Sheet

**55 commands** · AOS-CX 10.13 is the reference baseline. VSX, EVPN, and PoE commands depend on the switch series and enabled features.

[Command labels and usage notes](../README.md#command-labels) · [AOS-CX 10.13 CLI guide](https://arubanetworking.hpe.com/techdocs/AOS-CX/10.13/PDF/cli_6300-6400.pdf)

## Start with the symptom

Client cannot connect → check link and PoE, then inspect LLDP, VLAN membership and MAC learning. For an authenticated port, inspect the port-access session.

## System and hardware

| Command | When to use it |
| --- | --- |
| `show version` | Identify the AOS-CX software release and active image. |
| `show system` | Inspect hardware identification and system status. |
| `show inventory` | List chassis and hardware component identifiers. |
| `show images` | Review software versions in the image banks. |
| `show boot-history` | Inspect reboot history and reasons. |
| `show clock` | Check system time. |
| `show ntp status` | Inspect NTP synchronization status. |
| `show ntp associations` | Inspect NTP peer reachability and selection. |
| `show events` | Review recent system events. [SENSITIVE] |
| `show environment fan` | Inspect fan status. |
| `show environment power-supply` | Inspect power supply health. |
| `show environment temperature` | Inspect sensor and temperature status. |
| `show capacities` | Inspect limits exposed by the platform. |
| `show capacities-status` | Compare current resource use with platform limits. |
| `show running-config` | Review the active configuration. [SENSITIVE] |

## Interfaces and campus switching

| Command | When to use it |
| --- | --- |
| `show interface brief` | Summarize physical and logical interface state. |
| `show interface 1/1/1` | Inspect a single physical interface. |
| `show interface 1/1/1 statistics` | Inspect traffic and error counters for the interface. |
| `show interface transceiver` | Summarize installed optics and transceivers. |
| `show interface transceiver detail` | Inspect optical diagnostics where the transceiver supports them. |
| `show ip interface brief` | Summarize IPv4 interface state and addresses. |
| `show ipv6 interface brief` | Summarize IPv6 interface state and addresses. |
| `show vlan` | List VLANs and associated ports. |
| `show vlan 20` | Inspect membership and state for VLAN 20. |
| `show mac-address-table` | Inspect the learned forwarding table. |
| `show mac-address-table vlan 20` | Scope MAC learning to VLAN 20. |
| `show lldp neighbor-info` | Inspect remote system and port information. |
| `show lldp local-device` | Check the switch identity and capabilities advertised through LLDP. |
| `show lacp interfaces` | Inspect LACP actor, partner and member states. |
| `show lacp aggregates` | Inspect aggregated links and member selection. |
| `show spanning-tree` | Review spanning-tree role and state. |
| `show spanning-tree detail` | Inspect detailed topology and port information. |
| `show spanning-tree inconsistent-ports` | Inspect interfaces in spanning-tree inconsistent states where supported. |
| `show power-over-ethernet brief` | Summarize PoE allocation on supported switches. |
| `show port-access clients` | Inspect authenticated access sessions on supported switches. [SENSITIVE] |

## Routing, overlay and high availability

| Command | When to use it |
| --- | --- |
| `show vrf` | List configured VRFs. |
| `show ip route` | Inspect the default IPv4 routing table. |
| `show ip route vrf BLUE` | Inspect the IPv4 routing table for VRF BLUE. |
| `show ipv6 route` | Inspect the IPv6 routing table. |
| `show arp` | Inspect IPv4 neighbors. |
| `show ipv6 neighbors` | Inspect IPv6 neighbors. |
| `show ip ospf neighbors` | Inspect OSPF adjacency state. |
| `show ip ospf interface` | Inspect OSPF-enabled interfaces and parameters. |
| `show ip ospf database` | Inspect the OSPF link-state database. |
| `show bgp ipv4 unicast summary` | Inspect IPv4 BGP session state and prefix counts. |
| `show bgp l2vpn evpn summary` | Inspect BGP EVPN sessions on supported releases. |
| `show vsx status` | Inspect VSX roles, inter-switch link and keepalive state on a VSX pair. |
| `show vsx configuration inter-switch-link` | Inspect VSX inter-switch link configuration where supported. |
| `show vsx configuration keepalive` | Inspect VSX keepalive configuration where supported. |
| `show vrrp` | Inspect VRRP groups and local state. |

## Expert troubleshooting

| Command | When to use it |
| --- | --- |
| `show interface vxlan 1` | Inspect the VXLAN interface and related information where configured. |
| `show access-list` | Inspect configured ACL definitions. [SENSITIVE] |
| `show tech` | Collect broad diagnostic output. [HEAVY] [SENSITIVE] |
| `ping 192.0.2.10` | Send reachability probes from the switch. [PROBE] |
| `traceroute 198.51.100.20` | Probe the path from the switch. [PROBE] |
