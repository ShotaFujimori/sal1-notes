# SAL1/Start\_Your\_Cyber\_Security\_Journey

tags: \[search-skills, iproute2]

## TL;DR

* iproute2 tools (`ip`, `ss`, `tc`, `bridge`) replace legacy `net-tools` for faster, unified Linux network management.&#x20;
* Google operators (`"exact phrase"`, `site:`, `filetype:`, `-`) slash noise and pinpoint sources for OSINT & research.&#x20;
* Use Shodan/Censys for exposed assets, VirusTotal & HIBP for malware and breach checks.&#x20;
* Track flaws with CVE IDs; hunt PoCs in Exploit-DB or GitHub for controlled testing.&#x20;
* Remember: `ss` supersedes `netstat`; on Windows, `netstat -b` maps ports to binaries (admin required). &#x20;

## Quick-Ref: Core search & tooling

| Command / Term   | What it is / Why you care                  | Example invocation → trimmed output                  |
| ---------------- | ------------------------------------------ | ---------------------------------------------------- |
| `ip`             | Unified interface/IP/route manager         | `ip addr show` → *eth0 192.0.2.10/24*                |
| `ss`             | Modern socket viewer (netstat replacement) | `ss -tulnp` → *LISTEN 0 128 0.0.0.0:22 sshd*         |
| `tc`             | Traffic shaping / QoS control              | `tc qdisc show` → *qdisc fq\_codel ...*              |
| `"exact phrase"` | Google operator for precise matches        | `"passive reconnaissance"` → only exact-phrase pages |
| `site:`          | Limit search to a domain                   | `site:tryhackme.com success stories` → THM blog only |
| `filetype:`      | Search specific file types                 | `filetype:pdf cyber warfare report` → PDF reports    |
| `-`              | Exclude a term                             | `pyramids -tourism` → ignores travel sites           |
| `Shodan`         | Engine for internet-facing devices         | `apache 2.4.1` → host list & geo stats               |
| `CVE-2024-3094`  | Standard ID for xz utils bug               | Lookup → summary + severity                          |
| `VirusTotal`     | Multi-AV hash / URL scanner                | Hash search → *BitDefender: Gen.Variant.*            |
| `netstat -b`     | Show owning EXE for each socket (Win)      | `netstat -anob` → *TCP 0.0.0.0:80 httpd.exe*         |
| `snake oil`      | Slang for bogus crypto                     | N/A                                                  |

## Gotchas

* `netstat -b` needs elevated prompt; otherwise executables won’t show.&#x20;
* Not all search engines honor every Google operator—verify support first.&#x20;
* Shodan data may lag; confirm findings with direct scans before action.&#x20;
* Exploit code from the internet can be unverified—test only on isolated labs.&#x20;
* iproute2 commands can break connectivity; double-check interface names & syntax.&#x20;

## References

* iproute2 man page: [https://linux.die.net/man/8/ip](https://linux.die.net/man/8/ip)
* Google advanced operators list
* Shodan & Censys docs
* CVE Program / NVD
* Exploit-DB, VirusTotal, Have I Been Pwned

### RAW NOTE

Source: `1.SAL1 Note_ Start Your Cyber Security Journey.pdf`
