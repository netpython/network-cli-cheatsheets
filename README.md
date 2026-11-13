# Network CLI Cheat Sheets

**A field reference for network engineers and NOC operators.**

`458 commands` · `8 platforms` · `Switching / Routing / Firewalls`

Each sheet starts with routine checks, then moves into platform-specific troubleshooting. Every command includes what to look for and any special handling.

## Choose your platform

| Platform | Commands |
| --- | ---: |
| [Cisco IOS](cisco-ios/README.md) | 61 |
| [Cisco IOS XE](cisco-ios-xe/README.md) | 61 |
| [Cisco NX-OS](cisco-nx-os/README.md) | 61 |
| [FortiGate / FortiOS](fortigate-fortios/README.md) | 54 |
| [Check Point Gaia / Quantum](check-point-gaia/README.md) | 55 |
| [Palo Alto PAN-OS](palo-alto-pan-os/README.md) | 55 |
| [Juniper Junos OS](juniper-junos/README.md) | 56 |
| [HPE Aruba Networking AOS-CX](aruba-aos-cx/README.md) | 55 |

## Command labels

| Label | Meaning |
| --- | --- |
| Unmarked | Query or display command. Access rights and platform support still apply. |
| **PROBE** | Generates network traffic. Use the intended source, VRF or routing instance. |
| **DEBUG** | Starts or changes live debugging or packet capture. Narrow the filter and plan how to stop it. |
| **CHANGE** | Changes operational context or diagnostic state. Coordinate with other operators. |
| **HEAVY** | Can generate extensive output or use noticeable device resources. |
| **SENSITIVE** | Output can include topology, identities, addresses, secrets or packet data. |
| **CLISH / EXPERT** | Check Point shell context. |

## Using these sheets

- Substitute your interface names, VRFs, addresses and other values. The addresses in examples are documentation addresses.
- Confirm syntax with CLI help and the linked vendor reference for your model and release. Commands in a sheet may come from different hardware families or require enabled features.
- Start with read-only checks. For debug and capture, scope the input, use a bounded run where possible, and stop the diagnostic explicitly.
- These are documentation-based references. Hardware and firmware coverage varies and the entries have not been exhaustively lab-tested.

## Git et contribution

Un guide de travail Git simple, incluant la protection des secrets et le retour arrière, est disponible dans [Git pour ingénieurs réseau](docs/git-for-network-engineers.md).
