# Cisco IOS CLI Cheat Sheet

**61 commands** · Classic IOS, with Catalyst switching and IOS router commands. Use privileged EXEC where required.

[Command labels and usage notes](../README.md#command-labels) · [Catalyst 2960 IOS command references](https://www.cisco.com/c/en/us/support/switches/catalyst-2960-series-switches/products-command-reference-list.html)

## Start with the symptom

Port flaps → inspect interface errors, then check optics or cabling and correlate timestamps in the system log. For a host you cannot locate, resolve its IP in ARP and trace its MAC through the switching table.

## System and access

| Command | When to use it |
| --- | --- |
| `show version` | Identify release, uptime and image. |
| `show inventory` | List hardware PIDs and serial numbers. |
| `show clock detail` | Check time, timezone and clock source. |
| `show logging` | Review buffered events and severity settings. |
| `show users` | See active terminal sessions. |
| `show privilege` | Check the current EXEC privilege level. |
| `show processes cpu sorted` | Identify processes with high CPU utilization. |
| `show processes memory sorted` | Identify processes using the most memory. |
| `show file systems` | Discover available filesystems and prefixes. |
| `dir flash:` | List images and files on platforms with flash:. |
| `show environment all` | Inspect power, fan and temperature status where supported. |
| `show redundancy` | Inspect supervisor or route-processor redundancy. |

## Interfaces and campus switching

| Command | When to use it |
| --- | --- |
| `show interfaces` | Inspect link state, traffic rates and error counters. |
| `show interfaces GigabitEthernet0/1` | Inspect one interface in detail. |
| `show ip interface brief` | Summarize IPv4 interfaces and line protocol. |
| `show ipv6 interface brief` | Summarize IPv6 interface state and addresses. |
| `show interfaces status` | List Catalyst switchport states and VLANs. |
| `show interfaces counters errors` | Compare port error counters across a Catalyst switch. |
| `show interfaces GigabitEthernet0/1 switchport` | Check access VLAN, trunk mode and negotiation. |
| `show interfaces trunk` | Check operational trunks and allowed, active and forwarding VLANs. |
| `show vlan brief` | List VLANs and associated access ports. |
| `show mac address-table dynamic` | Find dynamically learned MAC addresses. |
| `show mac address-table address aaaa.bbbb.cccc` | Trace a specific MAC to a local port. |
| `show etherchannel summary` | Check bundled links and suspended members. |
| `show lacp neighbor` | Inspect the remote LACP system and member ports. |
| `show spanning-tree summary` | Identify STP mode and topology summary. |
| `show spanning-tree vlan 20 detail` | Inspect root selection and topology changes for VLAN 20. |
| `show spanning-tree inconsistentports` | Identify ports blocked by STP consistency checks. |
| `show cdp neighbors detail` | Discover Cisco neighbors and management addresses. |
| `show lldp neighbors detail` | Discover vendor-neutral neighbor and port details. |
| `show power inline` | Review PoE allocation on compatible switches. |

## Routing and edge services

| Command | When to use it |
| --- | --- |
| `show ip arp` | Inspect the IPv4 neighbor cache. |
| `show ipv6 neighbors` | Inspect IPv6 neighbor discovery entries. |
| `show ip route` | Read the IPv4 routing table. |
| `show ip route 192.0.2.0` | Inspect the matching route and next hop. |
| `show ipv6 route` | Read the IPv6 routing table. |
| `show ip protocols` | Review active IPv4 routing protocols and settings. |
| `show ip ospf neighbor` | Inspect OSPF adjacency state. |
| `show ip ospf interface brief` | Check OSPF interface areas and roles. |
| `show ip ospf database` | Inspect OSPF link-state database. |
| `show ip bgp summary` | Check IPv4 unicast BGP sessions and prefix counts. |
| `show ip bgp 192.0.2.0/24` | Inspect BGP paths and best-path selection. |
| `show ip eigrp neighbors` | Inspect EIGRP neighbors and queue counters. |
| `show ip eigrp topology` | Review EIGRP successors and feasibility. |
| `show standby brief` | Check HSRP active and standby roles. |
| `show ip dhcp binding` | Inspect leases on an IOS DHCP server. |
| `show ip nat translations` | Inspect NAT translations on a configured router. |
| `show ip nat statistics` | Review NAT pools, hits and misses. |
| `show access-lists` | Review ACL entries and available hit counters. |
| `show policy-map interface` | Inspect attached QoS policies and drop counters. |
| `show ntp associations` | Check time peers, reachability and selection. |

## Expert troubleshooting

| Command | When to use it |
| --- | --- |
| `show ip cef exact-route 192.0.2.10 198.51.100.20` | Inspect CEF forwarding for a source and destination. |
| `show adjacency detail` | Inspect CEF adjacency and rewrite state. |
| `show ip sla statistics` | Check configured IP SLA probe results. |
| `show ip traffic` | Inspect IP protocol and error counters. |
| `show running-config interface GigabitEthernet0/1` | Inspect active configuration for an interface. |
| `show archive` | Inspect configured archive state and known backups. |
| `ping 192.0.2.10 repeat 5` | Send five reachability probes. [PROBE] |
| `traceroute 198.51.100.20` | Probe the path toward a destination. [PROBE] |
| `debug ip ospf adj` | Trace OSPF adjacency events during a bounded troubleshooting window. [DEBUG] |
| `undebug all` | Stop all active IOS debugs. [CHANGE] |
