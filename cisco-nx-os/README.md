# Cisco NX-OS CLI Cheat Sheet

**61 commands** · Nexus 9000 with separate vPC, VXLAN and EVPN sections where those features are configured. Some hardware diagnostics are platform-specific.

[Command labels and usage notes](../README.md#command-labels) · [Nexus 9000 NX-OS command references](https://www.cisco.com/c/en/us/support/switches/nexus-9000-series-switches/products-command-reference-list.html)

## Start with the symptom

vPC down → check peer adjacency, peer keepalive and consistency. VXLAN endpoint missing → check the VNI and NVE peer, then compare the EVPN route with the local forwarding information.

## System and access

| Command | When to use it |
| --- | --- |
| `show version` | Identify NX-OS release, image and uptime. |
| `show inventory` | List chassis and component identifiers. |
| `show module` | Inspect module and supervisor states. |
| `show feature` | Review available features and enablement. |
| `show system resources` | Inspect CPU, memory and process counts. |
| `show processes cpu sort` | Find high CPU processes. |
| `show environment` | Inspect thermal, fan and power state. |
| `show logging logfile` | Review persistent event logs. |
| `show logging last 50` | Read recent log entries. |
| `show users` | List current CLI sessions. |
| `show clock` | Inspect device time. |
| `show ntp peers` | Review NTP peers and status. |
| `show cores` | List saved process core files. |
| `show boot` | Inspect boot variables. |
| `dir bootflash:` | List image and diagnostic files. |

## Switching and vPC

| Command | When to use it |
| --- | --- |
| `show interface brief` | Summarize physical and logical interfaces. |
| `show interface ethernet 1/1` | Inspect counters and operational state for a port. |
| `show interface status` | List port status, speed and VLAN mode. |
| `show interface counters errors` | Find port-level physical errors. |
| `show interface transceiver details` | Inspect optical power and thresholds. |
| `show interface ethernet 1/1 switchport` | Inspect access and trunk properties. |
| `show interface trunk` | Check operational trunks and VLAN lists. |
| `show vlan brief` | List VLANs and access membership. |
| `show mac address-table dynamic` | Inspect learned MAC addresses. |
| `show mac address-table address aaaa.bbbb.cccc` | Locate a specific MAC. |
| `show port-channel summary` | Inspect bundle and member state. |
| `show lacp neighbor` | Review remote LACP partners. |
| `show spanning-tree summary` | Review STP mode and root summary. |
| `show spanning-tree vlan 20 detail` | Trace STP changes for VLAN 20. |
| `show spanning-tree inconsistentports` | Identify ports blocked by consistency checks. |
| `show lldp neighbors detail` | Inspect neighbor identity and links. |
| `show cdp neighbors detail` | Inspect Cisco discovery information. |
| `show vpc brief` | Inspect peer adjacency, peer-link and vPC state. |
| `show vpc role` | Check operational vPC role and election priority. |
| `show vpc peer-keepalive` | Inspect peer keepalive state. |
| `show vpc consistency-parameters global` | Inspect global parameter consistency. |
| `show vpc consistency-parameters vpc 10` | Inspect consistency for vPC 10. |

## Layer 3 and fabric

| Command | When to use it |
| --- | --- |
| `show vrf` | List routing instances. |
| `show ip interface brief vrf all` | Summarize IPv4 interfaces across VRFs. |
| `show ip arp vrf all` | Inspect IPv4 neighbor entries across VRFs. |
| `show ip route vrf all` | Inspect the IPv4 RIB across VRFs. |
| `show ip route 192.0.2.0/24 vrf BLUE` | Inspect a prefix in a tenant routing table. |
| `show ip ospf neighbors` | Inspect OSPF adjacency state. |
| `show bgp ipv4 unicast summary` | Check IPv4 BGP peers and prefix counts. |
| `show bgp l2vpn evpn summary` | Check BGP EVPN peers. |
| `show bgp l2vpn evpn route-type 2` | Review MAC and IP advertisement routes. |
| `show bgp l2vpn evpn route-type 5` | Review IP prefix routes where supported. |
| `show nve interface nve1 detail` | Inspect NVE interface and source state. |
| `show nve peers` | Review learned VXLAN peers. |
| `show nve vni` | Map VNIs to VLANs or VRFs and inspect state. |
| `show l2route evpn mac all` | Inspect EVPN MAC routing records. |
| `show l2route evpn mac-ip all` | Inspect EVPN MAC/IP records. |
| `show hsrp brief` | Inspect HSRP group roles and state. |
| `show bfd neighbors` | Inspect BFD session state. |

## Expert diagnostics

| Command | When to use it |
| --- | --- |
| `show policy-map interface ethernet 1/1` | Inspect attached QoS and interface policy counters. |
| `show queuing interface ethernet 1/1` | Inspect hardware queue statistics. |
| `show interface ethernet 1/1 priority-flow-control` | Inspect PFC state and counters where supported. |
| `show hardware internal errors` | Inspect internal hardware errors where the command is exposed. |
| `ping 192.0.2.10 vrf BLUE count 5` | Send a bounded reachability probe in a VRF. [PROBE] |
| `ethanalyzer local interface inband limit-captured-frames 20` | Sample control-plane inband traffic. [DEBUG] [SENSITIVE] |
| `show tech-support` | Collect broad platform diagnostics. [HEAVY] [SENSITIVE] |
