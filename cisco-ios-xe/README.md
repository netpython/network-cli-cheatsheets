# Cisco IOS XE CLI Cheat Sheet

**61 commands** · Catalyst 9000 and IOS XE routers. FED examples target supported Catalyst models. QFP examples require a QFP-based router. StackWise commands require compatible switches.

[Command labels and usage notes](../README.md#command-labels) · [Catalyst 9300 IOS XE command reference](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/17-18/command_reference/b_1718_9300_cr.pdf)

## Start with the symptom

High CPU → compare IOSd and platform process views, then inspect punt causes on Catalyst 9000. For a suspected forwarding drop on a QFP router, compare QFP drop counters across two observations.

## System and software lifecycle

| Command | When to use it |
| --- | --- |
| `show version` | Identify IOS XE release, boot image and uptime. |
| `show inventory` | List chassis, modules and transceiver inventory where available. |
| `show platform` | Inspect hardware slots and states. |
| `show platform software status control-processor brief` | Review control-plane CPU, memory and status. |
| `show platform resources` | Inspect platform resource utilization on supported families. |
| `show processes cpu sorted` | Find high CPU processes in IOSd. |
| `show processes cpu platform sorted` | Find high CPU processes across the IOS XE platform. |
| `show processes memory sorted` | Inspect IOSd memory by process. |
| `show processes memory platform sorted` | Inspect IOS XE platform memory by process. |
| `show logging` | Review system and subsystem events. |
| `show redundancy states` | Inspect route processor or supervisor redundancy. |
| `show boot` | Inspect boot variables on supported Catalyst switches. |
| `show install summary` | Review active and committed package state in install mode. |
| `show install log` | Inspect software install history and errors. |
| `dir bootflash:` | List packages and crash files on platforms with bootflash:. |
| `show license summary` | Review detected licenses and usage. |
| `show license status` | Inspect licensing and reporting state. |
| `show environment all` | Inspect thermal, power and fan status on supported hardware. |

## Catalyst campus operations

| Command | When to use it |
| --- | --- |
| `show switch` | Inspect StackWise members, roles and versions. |
| `show switch stack-ports summary` | Inspect StackWise stack port state. |
| `show interfaces status` | Summarize Catalyst switchports. |
| `show interfaces counters errors` | Compare interface error counters. |
| `show interfaces transceiver detail` | Inspect transceiver telemetry where DOM is supported. |
| `show interfaces trunk` | Review allowed, active and forwarding VLANs. |
| `show interfaces GigabitEthernet1/0/1 switchport` | Inspect switchport mode and VLAN settings. |
| `show etherchannel summary` | Identify bundled, individual and suspended members. |
| `show lacp neighbor` | Inspect remote LACP partners. |
| `show spanning-tree vlan 20 detail` | Trace topology changes and root selection. |
| `show spanning-tree inconsistentports` | Locate ports blocked by STP consistency checks. |
| `show mac address-table address aaaa.bbbb.cccc` | Trace a MAC through the local switch. |
| `show lldp neighbors detail` | Inspect remote identity and port descriptions. |
| `show power inline` | Review PoE consumption and allocation. |
| `show access-session interface GigabitEthernet1/0/1 details` | Inspect access authentication, authorization and policy. |
| `show authentication sessions` | List access sessions on platforms exposing the legacy view. |
| `show device-tracking database` | Inspect learned IP-to-port and MAC bindings. |
| `show ip dhcp snooping binding` | Inspect dynamic DHCP snooping bindings. |
| `show ip arp inspection statistics` | Inspect DAI counters and drops. |

## Routing and service assurance

| Command | When to use it |
| --- | --- |
| `show vrf` | List VRFs and address-family membership. |
| `show ip route vrf BLUE` | Inspect the IPv4 RIB in VRF BLUE. |
| `show ip cef vrf BLUE 192.0.2.10 detail` | Inspect the forwarding entry in VRF BLUE. |
| `show ip ospf neighbor` | Inspect OSPF adjacency state. |
| `show bgp ipv4 unicast summary` | Inspect IPv4 BGP peer state and prefix counts. |
| `show bgp l2vpn evpn summary` | Inspect EVPN peer state where the feature is configured. |
| `show bfd neighbors details` | Inspect BFD sessions, timers and diagnostics. |
| `show policy-map interface` | Inspect QoS class counters and drops. |
| `show ip nat translations verbose` | Inspect NAT translation details on supported routers. |
| `show crypto ikev2 sa` | Inspect IKEv2 negotiation and peer state. |
| `show crypto ipsec sa` | Compare encryption and decryption counters for tunnels. |
| `show ip sla statistics` | Inspect configured synthetic probe results. |
| `show ntp status` | Check synchronization and stratum. |
| `ping vrf BLUE 192.0.2.10 repeat 5` | Send reachability probes within a VRF. [PROBE] |

## Expert forwarding and capture

| Command | When to use it |
| --- | --- |
| `show platform hardware qfp active datapath utilization` | Inspect QFP utilization on QFP-based routers. |
| `show platform hardware qfp active statistics drop` | Inspect QFP drop reasons on QFP-based routers. |
| `show platform hardware qfp active feature nat datapath statistics` | Inspect NAT datapath counters where supported by the QFP platform and release. |
| `show platform software fed switch active ifm mappings` | Map interfaces to forwarding-engine identifiers on supported Catalyst 9000 switches. |
| `show platform software fed switch active punt cause summary` | Inspect control-plane punt causes on supported Catalyst 9000 switches. |
| `show platform hardware fed switch active qos queue stats interface GigabitEthernet1/0/1` | Inspect hardware queue counters on supported Catalyst 9000 switches. |
| `show monitor capture` | Inspect configured Embedded Packet Capture sessions. |
| `show monitor capture LAB buffer brief` | Summarize packets already captured in LAB. [SENSITIVE] |
| `monitor capture LAB stop` | Stop an existing Embedded Packet Capture session. [CHANGE] |
| `show tech-support` | Collect broad diagnostic output. Redirect only to an approved location. [SENSITIVE] [HEAVY] |
