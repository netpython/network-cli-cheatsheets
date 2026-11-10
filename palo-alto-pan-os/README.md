# Palo Alto PAN-OS CLI Cheat Sheet

**55 commands** · PAN-OS firewall operational mode. Classic virtual-router commands differ from Advanced Routing Engine commands. Verify the applicable hierarchy on the target device.

[Command labels and usage notes](../README.md#command-labels) · [PAN-OS CLI command discovery and hierarchy](https://docs.paloaltonetworks.com/ngfw/pan-os-cli-quick-start/get-started-with-the-cli/find-a-command)

## Start with the symptom

Policy mismatch → check the route or FIB lookup, run a hypothetical security and NAT policy match, then confirm the outcome in the live session if one exists.

## System, HA and management

| Command | When to use it |
| --- | --- |
| `show system info` | Identify model, serial number and PAN-OS version. |
| `show system resources` | Inspect management-plane CPU and memory usage. |
| `show system disk-space` | Check management-plane filesystem capacity. |
| `show system software status` | Inspect management software process state. |
| `show system environmentals` | Inspect sensor status on supported hardware. |
| `show jobs all` | List commit, install and other asynchronous jobs. |
| `show jobs id 123` | Inspect a particular job and its result. |
| `show admins` | List active administrator sessions. [SENSITIVE] |
| `show ntp` | Inspect configured NTP synchronization state. |
| `show panorama-status` | Check connectivity and state for Panorama. |
| `show high-availability state` | Inspect the local and peer HA roles. |
| `show high-availability all` | Review HA links, state and configuration. |
| `show high-availability state-synchronization` | Inspect HA runtime synchronization. |
| `show high-availability link-monitoring` | Review HA link monitoring. |
| `show high-availability path-monitoring` | Review HA path monitoring. |

## Interfaces, routing and neighbors

| Command | When to use it |
| --- | --- |
| `show interface all` | Summarize interface inventory and operational state. |
| `show interface ethernet1/1` | Inspect the specified interface. |
| `show counter interface all` | Inspect interface packet and error counters. |
| `show arp all` | Inspect IPv4 neighbors and interface associations. |
| `show neighbor all` | Inspect IPv6 neighbor entries where supported. |
| `show lldp neighbors all` | Inspect LLDP neighbors when LLDP is enabled. |
| `show routing route` | Inspect the classic routing engine RIB. |
| `show routing fib` | Inspect the classic routing engine FIB. |
| `test routing fib-lookup virtual-router default ip 192.0.2.10` | Test a forwarding lookup on the classic routing engine. |
| `show routing protocol bgp summary` | Review BGP state on the classic routing engine. |
| `show routing protocol bgp peer` | Inspect configured BGP peers on the classic routing engine. |
| `show routing protocol ospf neighbor` | Inspect classic routing engine OSPF adjacencies. |
| `show routing protocol ospf interface` | Inspect classic routing engine OSPF interfaces. |
| `show routing protocol bfd summary` | Inspect BFD state where the classic routing engine exposes it. |
| `ping source 192.0.2.1 host 198.51.100.20` | Test reachability from an assigned source. End with Ctrl+C if needed. [PROBE] |
| `traceroute host 198.51.100.20` | Send path probes to a destination. [PROBE] |

## Policy, sessions and VPN

| Command | When to use it |
| --- | --- |
| `show running security-policy` | Inspect the effective security policy. [SENSITIVE] |
| `show running nat-policy` | Inspect the effective NAT policy. [SENSITIVE] |
| `test security-policy-match from trust to untrust source 192.0.2.10 destination 198.51.100.20 protocol 6 destination-port 443` | Find the policy match for a hypothetical TCP flow. [SENSITIVE] |
| `test nat-policy-match from trust to untrust source 192.0.2.10 destination 198.51.100.20 protocol 6 destination-port 443` | Find the NAT policy match for a hypothetical TCP flow. [SENSITIVE] |
| `show session info` | Inspect session counts, limits and packet rates. |
| `show session all filter source 192.0.2.10 destination 198.51.100.20 destination-port 443` | Find sessions for a narrowly scoped TCP or UDP flow. [SENSITIVE] |
| `show session id 12345` | Inspect one session, including NAT, policy and byte counters. [SENSITIVE] |
| `show vpn ike-sa` | Inspect IKE SAs and peers. [SENSITIVE] |
| `show vpn ipsec-sa` | Inspect IPsec SAs and tunnel state. [SENSITIVE] |
| `show vpn flow` | Inspect dataplane VPN tunnel flow counters. |
| `show vpn gateway` | Inspect configured IKE gateways. [SENSITIVE] |
| `show vpn tunnel` | Inspect configured IPsec tunnels. [SENSITIVE] |
| `show global-protect-gateway current-user` | Inspect connected GlobalProtect gateway users. [SENSITIVE] |
| `show user ip-user-mapping ip 192.0.2.10` | Check the User-ID mapping for an IP. [SENSITIVE] |

## Expert dataplane diagnostics

| Command | When to use it |
| --- | --- |
| `show running resource-monitor` | Inspect dataplane utilization and packet buffers. |
| `show running resource-monitor minute last 5` | Inspect recent dataplane load samples. |
| `show counter global filter severity drop` | Inspect dataplane drop counters. |
| `show counter global filter severity drop delta yes` | Inspect drop counter deltas between observations. |
| `show counter global filter packet-filter yes delta yes` | Inspect counters scoped to an existing packet filter. Coordinate filter ownership. |
| `debug dataplane packet-diag show setting` | Inspect active dataplane packet diagnostic settings. |
| `debug dataplane packet-diag set capture off` | Stop an existing packet capture. Coordinate with the capture owner. [CHANGE] |
| `less mp-log ms.log` | Read management-server logs. Quit with q. [SENSITIVE] |
| `less mp-log ikemgr.log` | Read IKE manager logs. Quit with q. [SENSITIVE] |
| `find command keyword packet-diag` | Discover available packet diagnostic syntax on the running release. |
