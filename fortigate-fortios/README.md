# FortiGate / FortiOS CLI Cheat Sheet

**54 commands** · FortiGate CLI. Check the current VDOM, HA member and FortiOS version. SD-WAN and VPN syntax varies across releases and models.

[Command labels and usage notes](../README.md#command-labels) · [FortiOS CLI reference](https://docs.fortinet.com/document/fortigate/latest/cli-reference/159376337/diagnose-debug)

## Start with the symptom

Flow blocked → check the route and policy routes, then inspect a narrowly filtered session. If needed, use a scoped flow trace and stop it explicitly. Coordinate debug filters with other operators. Existing hardware-offloaded sessions may not appear in a CPU-based flow trace.

## System, HA and VDOMs

| Command | When to use it |
| --- | --- |
| `get system status` | Identify FortiOS build, hardware and VDOM mode. |
| `get system performance status` | Check CPU, memory, sessions and throughput. |
| `get system ha status` | Inspect cluster roles, peers and synchronization state. |
| `diagnose sys ha checksum cluster` | Compare configuration checksums across HA members. |
| `diagnose sys ha status` | Inspect HA runtime details. |
| `diagnose sys top 1 10 3` | Sample the ten busiest processes three times. |
| `diagnose sys session stat` | Review session-table occupancy and counters. |
| `diagnose hardware sysinfo memory` | Inspect detailed memory statistics. |
| `diagnose hardware sysinfo conserve` | Check conserve-mode state and thresholds. |
| `diagnose sys vd list` | List VDOM identifiers and runtime state. |
| `show system interface` | Review configured interfaces and addresses. [SENSITIVE] |
| `show system zone` | Inspect zone membership. |
| `get system arp` | Inspect resolved IPv4 neighbors. |
| `get system interface physical` | Inspect physical interface status. |
| `diagnose hardware deviceinfo nic port1` | Inspect driver counters on a supported NIC. |
| `diagnose netlink interface list port1` | Inspect interface flags, MTU and kernel counters. |
| `diagnose ip address list` | List IP addresses known to the kernel. |

## Routing and SD-WAN

| Command | When to use it |
| --- | --- |
| `get router info routing-table all` | Read the current IPv4 routing table. |
| `get router info routing-table details 192.0.2.10` | Inspect the route for a destination. |
| `get router info routing-table database` | Review routing candidates and installation status. |
| `get router info bgp summary` | Inspect BGP peers and prefix counts. |
| `get router info bgp neighbors 192.0.2.1` | Review one BGP peer and negotiated capabilities. |
| `get router info bgp network` | Inspect BGP routes. |
| `get router info ospf neighbor` | Inspect OSPF neighbors. |
| `get router info ospf interface` | Check OSPF interfaces and timers. |
| `diagnose firewall proute list` | List installed policy routes. |
| `diagnose sys sdwan health-check` | Inspect SD-WAN SLA probe results on modern FortiOS. |
| `diagnose sys sdwan service` | Inspect SD-WAN rule selection on releases exposing this subcommand. |
| `diagnose sys sdwan member` | Inspect SD-WAN member details. |
| `execute ping 192.0.2.10` | Send reachability probes from the FortiGate. [PROBE] |
| `execute traceroute 198.51.100.20` | Probe the path from the FortiGate. [PROBE] |

## Policy, sessions and VPN

| Command | When to use it |
| --- | --- |
| `show firewall policy` | Inspect IPv4 firewall policies. [SENSITIVE] |
| `show firewall vip` | Inspect VIP definitions for destination NAT. [SENSITIVE] |
| `show firewall ippool` | Inspect configured source NAT pools. [SENSITIVE] |
| `show firewall central-snat-map` | Inspect central SNAT rules where enabled. [SENSITIVE] |
| `diagnose sys session filter clear` | Reset the session display filter. [CHANGE] |
| `diagnose sys session filter src 192.0.2.10` | Limit subsequent session display to a source. [CHANGE] |
| `diagnose sys session filter dst 198.51.100.20` | Limit subsequent session display to a destination. [CHANGE] |
| `diagnose sys session list` | Inspect sessions, policy ID, NAT and offload status. Apply a narrow filter first. [SENSITIVE] [HEAVY] |
| `get vpn ipsec tunnel summary` | Check IPsec tunnel and selector status. |
| `diagnose vpn ike gateway list` | Inspect IKE gateway and SA state. [SENSITIVE] |
| `diagnose vpn tunnel list` | Inspect IPsec tunnel, selectors and counters. Output can expose key material. [SENSITIVE] |
| `diagnose vpn ssl list` | Inspect SSL VPN sessions where the feature is available. [SENSITIVE] |
| `get vpn ssl monitor` | Review active SSL VPN sessions where supported. [SENSITIVE] |

## Expert diagnostics

| Command | When to use it |
| --- | --- |
| `diagnose sniffer packet any 'host 192.0.2.10 and tcp port 443' 4 20 a` | Capture up to 20 packets matching a narrow filter. Stop manually if fewer arrive. [DEBUG] [SENSITIVE] |
| `diagnose debug flow filter clear` | Reset flow debug filters. [CHANGE] |
| `diagnose debug flow filter addr 192.0.2.10` | Scope flow debug to the example address. [CHANGE] |
| `diagnose debug flow filter proto 6` | Scope flow debug to TCP. [CHANGE] |
| `diagnose debug flow show function-name enable` | Include function names in flow debug output. [DEBUG] |
| `diagnose debug flow trace start 20` | Arm a flow trace for up to 20 packets. [DEBUG] [SENSITIVE] |
| `diagnose debug enable` | Enable live debug output. Coordinate with other operators. [DEBUG] |
| `diagnose debug flow trace stop` | Stop flow tracing. [CHANGE] |
| `diagnose debug disable` | Disable live debug output. [CHANGE] |
| `diagnose debug reset` | Reset debug settings. Coordinate with other operators. [CHANGE] |
