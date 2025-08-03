# ☑️ Quick-Ref: Networking & Crypto Terms

| Command / Term                           | What it is / Why you care                                     | Example invocation → trimmed output |
|------------------------------------------|---------------------------------------------------------------|-------------------------------------|
| **“Snake oil”**                          | Slang for bogus or un-vetted crypto schemes and products.     | N/A                                  |
| **ss**                                   | Modern socket-stats tool replacing `netstat`. Faster (Netlink).| `ss -tunap` → `ESTAB 0 0 192.0.2.5:22 198.51.100.10:54213 sshd` |
| **ip link show**                         | List NICs & state (iproute2).                                 | `2: eth0: <UP,LOWER_UP> mtu 1500 …` |
| **ip addr show**                         | Display all IPv4/6 addresses on all interfaces.               | `inet 192.0.2.10/24 brd 192.0.2.255 scope global eth0` |
| **ip -4 / -6 addr show**                 | Same as above, filtered to v4 or v6.                          | `inet6 2001:db8::1/64 scope global` |
| **ip route show**                        | Current routing table (replaces `route -n`).                  | `default via 192.0.2.1 dev eth0` |
| **ip route add default via <GW>**        | Set default gateway.                                          | (no stdout; `ip route show` confirms) |
| **ip link set eth0 up / down**           | Bring interface up or down (replaces `ifconfig eth0 up`).     | (no stdout; `ip link show eth0` confirms) |
| **ip addr add 192.0.2.20/24 dev eth0**   | Add a secondary IP to an interface.                           | (no stdout; shown by `ip addr show eth0`) |
| **ip neighbour show**                    | ARP/NDP table (replaces `arp -na`).                           | `192.0.2.1 dev eth0 lladdr 00:aa:… REACHABLE` |
| **tc qdisc show dev eth0**               | View QoS / traffic-control queue disciplines.                 | `qdisc fq_codel 0: root refcnt 2 limit 10240p …` |
| **bridge link show**                     | Inspect bridge devices/ports.                                 | `3: veth0 state UP … master br0` |

> **Why iproute2?**  
> - Consolidates `ifconfig`, `route`, `arp`, etc. into one syntax (`ip …`).  
> - Talks to kernel via Netlink → faster & script-friendly (`-json`, `-brief`).  
> - Continually maintained; supports VLANs, bonding, policy-based routing, etc.

**Mini-mnemonic:** *“ip all day, ss for sockets, tc for traffic, bridge for bridges.”*

Happy hacking! 🐱‍💻
