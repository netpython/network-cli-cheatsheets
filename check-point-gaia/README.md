# Check Point Gaia / Quantum CLI Cheat Sheet

**55 commands** · Gaia R81.20 is the reference baseline. CLISH and EXPERT entries require different shells and privileges. ClusterXL and VSX commands require the corresponding feature and context.

[Command labels and usage notes](../README.md#command-labels) · [Check Point R81.20 CLI reference](https://sc1.checkpoint.com/documents/R81.20/WebAdminGuides/EN/CP_R81.20_CLI_ReferenceGuide/CP_R81.20_CLI_ReferenceGuide.pdf)

## Start with the symptom

Traffic blocked → identify the active ClusterXL member and VSX context first. Confirm the installed policy and route, then use a narrowly scoped capture only if you still need to locate the drop.

## Gaia Clish · system and connectivity

| Command | When to use it |
| --- | --- |
| `show version all` | Identify Gaia version, build and kernel. [CLISH] |
| `show hostname` | Read the configured system hostname. [CLISH] |
| `show uptime` | Check uptime since the last reboot. [CLISH] |
| `show asset all` | Review hardware asset identifiers. [CLISH] |
| `show interfaces all` | Inspect configured interfaces and state. [CLISH] |
| `show interface eth1` | Inspect a single Gaia interface. [CLISH] |
| `show route` | Inspect Gaia routing information. [CLISH] |
| `show arp dynamic all` | List dynamic IPv4 neighbor entries. [CLISH] |
| `show dns` | Check DNS configuration. [CLISH] |
| `show ntp active` | Check whether Gaia NTP is active. [CLISH] |
| `show ntp servers` | List configured NTP servers. [CLISH] |
| `show users` | List configured Gaia users. [CLISH] [SENSITIVE] |
| `show administrators` | List users with administrative access. [CLISH] [SENSITIVE] |
| `show configuration` | Review the Gaia configuration in Clish syntax. [CLISH] [SENSITIVE] |
| `show installer status` | Review CPUSE agent status. [CLISH] |
| `show installer packages installed` | List installed CPUSE packages. [CLISH] |
| `show bgp peers` | Inspect Gaia BGP peers when dynamic routing is configured. [CLISH] |
| `show ospf neighbors` | Inspect Gaia OSPF neighbors. [CLISH] |
| `show ospf interfaces` | Check Gaia OSPF-enabled interfaces. [CLISH] |
| `show ospf database` | Inspect the Gaia OSPF link-state database. [CLISH] |

## Expert shell · host and products

| Command | When to use it |
| --- | --- |
| `cpinfo -y all` | List installed Check Point products and hotfixes. [EXPERT] |
| `cpwd_admin list` | Check processes monitored by WatchDog. [EXPERT] |
| `cpstat os` | Inspect OS counters exposed through Check Point. [EXPERT] |
| `cpstat fw` | Review Firewall product statistics. [EXPERT] |
| `cpstat ha` | Review high-availability product statistics. [EXPERT] |
| `cpstat vpn` | Review VPN product statistics where available. [EXPERT] |
| `cpstat mg` | Review management product statistics on a management server. [EXPERT] |
| `cplic print` | Review installed licenses. [EXPERT] [SENSITIVE] |
| `df -h` | Review mounted filesystem capacity. [EXPERT] |
| `free -m` | Review host memory in MiB. [EXPERT] |
| `ip -s link show dev eth1` | Inspect kernel link counters for eth1. [EXPERT] |
| `ip route show` | Inspect the kernel routing table. [EXPERT] |
| `ip neigh show` | Inspect the kernel neighbor table. [EXPERT] |
| `ethtool eth1` | Inspect link negotiation on a supported interface. [EXPERT] |
| `ethtool -S eth1` | Inspect driver-level NIC counters. [EXPERT] |

## Firewall, acceleration and clustering

| Command | When to use it |
| --- | --- |
| `fw stat` | Check which policy is installed on the gateway. [EXPERT] |
| `fw ctl iflist` | Map firewall kernel interface indexes to interfaces. [EXPERT] |
| `fw ctl pstat` | Inspect firewall kernel memory and counters. [EXPERT] |
| `fw ctl multik stat` | Inspect CoreXL firewall instances. [EXPERT] |
| `fw ctl affinity -l -r` | Inspect firewall and interface CPU affinity. [EXPERT] |
| `fw tab -t connections -s` | Summarize the kernel connection table. [EXPERT] |
| `fwaccel stat` | Inspect SecureXL status and enabled acceleration features. [EXPERT] |
| `fwaccel stats -s` | Inspect summarized SecureXL counters. [EXPERT] |
| `fwaccel conns -s` | Inspect summarized accelerated connection counts. [EXPERT] |
| `cphaprob state` | Review ClusterXL member roles and state. [EXPERT] |
| `cphaprob -a if` | Review ClusterXL interface health and monitored links. [EXPERT] |
| `cphaprob list` | Inspect registered ClusterXL critical devices. [EXPERT] |
| `cphaprob syncstat` | Inspect ClusterXL synchronization statistics where supported. [EXPERT] |
| `vpn tu tlist` | List IPsec tunnels on releases supporting this subcommand. [EXPERT] [SENSITIVE] |
| `vsx stat -v` | List virtual systems and their state on a VSX gateway. [EXPERT] |
| `vsenv 2` | Switch the current Expert shell to Virtual System 2. [EXPERT] [CHANGE] |

## Expert packet troubleshooting

| Command | When to use it |
| --- | --- |
| `ping -c 5 192.0.2.10` | Send five reachability probes from the gateway shell. [EXPERT] [PROBE] |
| `tcpdump -ni eth1 -c 20 'host 192.0.2.10 and tcp port 443'` | Capture up to 20 matching packets on eth1. Stop manually if fewer arrive. [EXPERT] [DEBUG] [SENSITIVE] |
| `fw monitor -F '192.0.2.10,0,198.51.100.20,443,6'` | Capture the example TCP flow through firewall inspection points. End with Ctrl+C. [EXPERT] [DEBUG] [SENSITIVE] |
| `fw ctl zdebug + drop` | Watch firewall kernel drop debug on a lab gateway or during an approved incident window. End with Ctrl+C. [EXPERT] [DEBUG] [HEAVY] [SENSITIVE] |
