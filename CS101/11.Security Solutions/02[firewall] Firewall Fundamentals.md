# 37. SAL1 — Security Solutions: Firewall Fundamentals (Cheat Sheet)
tags: [firewall, stateless, stateful, proxy, ngfw, rules, windows-defender, ufw, linux, netfilter]

> Use in authorized lab/enterprise environments only.

---

## TL;DR
- A **firewall** inspects **incoming/outgoing** traffic and allows/denies it based on **rules** (source, destination, protocol, port, action, direction). :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}  
- Types: **Stateless (L3/4)**, **Stateful (L3/4, keeps connection state)**, **Proxy/App-layer (L7)**, **NGFW (L3–L7, DPI/IPS/heuristics/SSL inspection)**. :contentReference[oaicite:2]{index=2}  
- Windows: **Windows Defender Firewall** with profiles, GUI rules, inbound/outbound control. Linux: **Netfilter** stack with **ufw** as a friendly front-end. :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

---

## Core Concepts (Why Firewalls)
- Act as a **gatekeeper** between device/network and the Internet, enforcing policy via rules. :contentReference[oaicite:5]{index=5}  
- Modern firewalls add features beyond basic filtering (e.g., IPS, TLS decryption). :contentReference[oaicite:6]{index=6}

---

## Types of Firewalls (at a glance)
| Type | OSI Layer(s) | Strengths | Limits |
|---|---|---|---|
| Stateless | L3–L4 | Fast, simple per-packet rules | No connection context | :contentReference[oaicite:7]{index=7} |
| Stateful | L3–L4 | Tracks connection **state** in a **state table** | More overhead than stateless | :contentReference[oaicite:8]{index=8} |
| Proxy / App | L7 | Inspects **content**, application control | Added latency; per-app tuning | :contentReference[oaicite:9]{index=9} |
| NGFW | L3–L7 | DPI, **IPS**, heuristics, **SSL/TLS** decrypt | Cost/complexity | :contentReference[oaicite:10]{index=10} |

---

## Rules & Components
- **Fields:** Source IP, Destination IP, Protocol, Port, **Action** (Allow/Deny/Forward), **Direction** (Inbound/Outbound/Forward). :contentReference[oaicite:11]{index=11}  
- **Actions:**  
  - **Allow** (permit defined traffic) :contentReference[oaicite:12]{index=12}  
  - **Deny** (block defined traffic) :contentReference[oaicite:13]{index=13}  
  - **Forward** (redirect to different network segment) :contentReference[oaicite:14]{index=14}  
- **Directionality:** Inbound, Outbound, Forward rules. :contentReference[oaicite:15]{index=15}

---

## Windows Defender Firewall (GUI quick path)
1) Open **Windows Defender Firewall** → review **Private/Public** profiles. :contentReference[oaicite:16]{index=16}  
2) **Allow an app** through firewall (per profile), or **Turn Windows Defender Firewall on/off** (not recommended to fully disable). :contentReference[oaicite:17]{index=17}  
3) **Advanced settings** → create rules:  
   - Example (block outbound **HTTP/HTTPS**): **Outbound Rules → New Rule → Custom → All programs → TCP → Remote ports `80,443` → Action: Block → Profile: All → Name → Finish.** :contentReference[oaicite:18]{index=18}  
4) Test by browsing a site; expect blocked access if rule is active. :contentReference[oaicite:19]{index=19}

> Practice scenario in the room asks you to read created rules (e.g., **Core Op** blocks inbound SSH; **Infra team** allows SSH from **192.168.13.7**). :contentReference[oaicite:20]{index=20}

---

## Linux Firewall (Netfilter family) — `ufw` quick cmds
`ufw` is a friendly front-end to **Netfilter** (`iptables`/`nftables`/`firewalld`). :contentReference[oaicite:21]{index=21}

```bash
# Check status
sudo ufw status
# Enable / Disable
sudo ufw enable
sudo ufw disable
````



```bash
# Set default policies
sudo ufw default allow outgoing     # allow all egress by default
sudo ufw default deny outgoing      # (exercise answer variant)
```



```bash
# Block inbound SSH (TCP/22)
sudo ufw deny 22/tcp
# List numbered rules
sudo ufw status numbered
# Delete rule by number (example: 2)
sudo ufw delete 2
```



> **Successor to `iptables`**: **`nftables`** (modern Netfilter utility). 

---

## Mini Playbook Snippets

* **Permit web from any to web-server via forward (concept):** Action **Forward**, Dst `192.168.1.8`, TCP **80**, **Inbound**. 
* **Block all outbound web** (Windows GUI): Outbound **Block** rule for **TCP 80,443**. 
* **Default deny egress** (Linux): `ufw default deny outgoing`. 

---

## Gotchas (and Fast Fixes)

| Pitfall                                             | Why it hurts                      | Fast Fix                                                       |
| --------------------------------------------------- | --------------------------------- | -------------------------------------------------------------- |
| Relying on stateless filtering for complex policies | No session context → gaps         | Use **stateful** or **NGFW** for connection-aware rules.       |
| Forgetting direction                                | Rule never matches                | Verify **Inbound/Outbound/Forward** is correct.                |
| Over-permissive defaults                            | Unexpected exposure               | Set sane defaults (e.g., **deny inbound**, review outbound).   |
| Blocking yourself from management                   | Loss of access                    | Add **allowlist** for admin IPs before enabling strict rules.  |
| TLS inspection without planning                     | Breaks apps, privacy/legal issues | Deploy NGFW **SSL/TLS** decryption with scope & consent.       |

---

## Reference

* 37.SAL1 Note_ Security Solutions - Firewall Fundamentals.pdf
* 37.SAL1 Note  Security Solutions - Firewall Fundamentals.gdoc
* https://docs.google.com/document/d/1oFH009g-XzdGxwCDXotwPd2ZAxUWHRyZ2SmnLhYe1sY/edit?tab=t.0


