# Juniper Junos OS CLI Cheat Sheet

**56 commands** · Junos operational mode. Switching examples target EX/QFX. MPLS, EVPN and chassis commands depend on hardware and features.

[Command labels and usage notes](../README.md#command-labels) · [Junos OS CLI reference](https://www.juniper.net/documentation/us/en/software/junos/cli-reference/)

## Start with the symptom

BGP route missing → check peer state, compare routes received and advertised, inspect hidden routes and confirm the selected forwarding entry.

## Chassis, operations and system

| Command | When to use it |
| --- | --- |
| `show version` | Identify Junos version and hardware model. |
| `show chassis hardware detail` | Inspect chassis, FPC, PIC and transceiver inventory. |
| `show chassis alarms` | Inspect active chassis alarms. |
| `show system alarms` | Inspect active system alarms. |
| `show chassis environment` | Inspect fan, power and temperature state. |
| `show chassis routing-engine` | Inspect Routing Engine CPU, memory and redundancy. |
| `show chassis fpc` | Inspect FPC state and resource usage. |
| `show chassis fpc pic-status` | Inspect PIC status by slot. |
| `show system uptime` | Inspect boot time, uptime and last configuration change. |
| `show system processes extensive` | Inspect active processes and resource usage. |
| `show system storage` | Check filesystem capacity. |
| `show system core-dumps` | List saved process core dumps. |
| `show system commit` | Inspect commit history and user attribution. |
| `show log messages \| last 50` | Read the last 50 system log lines. [SENSITIVE] |
| `show ntp associations` | Inspect NTP peer status. |
| `show virtual-chassis status` | Inspect Virtual Chassis members and roles where configured. |

## Interfaces and switching

| Command | When to use it |
| --- | --- |
| `show interfaces terse` | Summarize interface administration, link state and addressing. |
| `show interfaces ge-0/0/1 extensive` | Inspect errors, queue drops and link transitions. |
| `show interfaces diagnostics optics ge-0/0/1` | Inspect supported optical transceiver telemetry. |
| `show interfaces queue ge-0/0/1` | Inspect egress queues and drop counters. |
| `show interfaces descriptions` | List descriptions and link state. |
| `show lldp neighbors detail` | Inspect LLDP remote port and system data. |
| `show ethernet-switching table` | Inspect learned MAC addresses on a switch. |
| `show ethernet-switching interfaces` | Inspect Ethernet switching interface state. |
| `show vlans extensive` | Review VLAN membership and forwarding context. |
| `show spanning-tree bridge` | Inspect STP bridge and root selection. |
| `show spanning-tree interface` | Inspect STP state and port role. |
| `show lacp interfaces` | Inspect aggregated Ethernet member state. |
| `show lacp statistics interfaces ae0` | Inspect LACP protocol counters for ae0. |

## Routing, forwarding and filtering

| Command | When to use it |
| --- | --- |
| `show route summary` | Review route counts by table and protocol. |
| `show route 192.0.2.0/24 exact` | Inspect one exact route prefix. |
| `show route table BLUE.inet.0` | Inspect the IPv4 RIB of routing instance BLUE. |
| `show route hidden extensive` | Inspect unusable routes and hidden-route reasons. |
| `show route forwarding-table destination 192.0.2.10` | Inspect the installed forwarding decision. |
| `show route instance` | Inspect routing instances. |
| `show arp no-resolve` | Inspect IPv4 neighbors without reverse DNS lookup. |
| `show ipv6 neighbors` | Inspect IPv6 neighbor entries. |
| `show bgp summary` | Inspect BGP peer state and prefix counts. |
| `show bgp neighbor 192.0.2.1` | Inspect BGP session and capability details. |
| `show route receive-protocol bgp 192.0.2.1` | Inspect visible routes received from a peer. |
| `show route advertising-protocol bgp 192.0.2.1` | Inspect routes selected for advertisement to a peer. |
| `show ospf neighbor detail` | Inspect adjacency state and timers. |
| `show ospf database` | Inspect the OSPF link-state database. |
| `show ospf interface detail` | Inspect OSPF area, interface and network settings. |
| `show isis adjacency detail` | Inspect IS-IS neighbors and adjacency details where enabled. |
| `show isis database detail` | Inspect the IS-IS link-state database. |
| `show bfd session extensive` | Inspect BFD state, timers and diagnostics. |
| `show mpls lsp extensive` | Inspect signaled MPLS LSPs where configured. |
| `show evpn database extensive` | Inspect EVPN MAC and IP learning where configured. |
| `show firewall` | Inspect firewall filter counters that have been configured. |

## Expert troubleshooting and change review

| Command | When to use it |
| --- | --- |
| `show configuration \| compare rollback 1` | Compare the active configuration with its predecessor. [SENSITIVE] |
| `show configuration interfaces ge-0/0/1 \| display set` | Read the committed interface configuration in set format. [SENSITIVE] |
| `ping 192.0.2.10 count 5 routing-instance BLUE` | Send five probes through routing instance BLUE. [PROBE] |
| `traceroute 198.51.100.20 no-resolve` | Trace a path without reverse DNS lookups. [PROBE] |
| `monitor traffic interface ge-0/0/1 no-resolve matching "host 192.0.2.10 and tcp port 443" count 20` | Capture matching Routing Engine-visible traffic. End manually if fewer packets arrive. [DEBUG] [SENSITIVE] |
| `request support information` | Collect broad platform diagnostics on supported hardware. [HEAVY] [SENSITIVE] |
