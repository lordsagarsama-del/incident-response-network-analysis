# Network Traffic Analysis & Incident Response

## Project Overview
Investigated two network security incidents using packet analysis and applied the **NIST Cybersecurity Framework** to contain, remediate, and prevent recurrence.

## Tools Used
- `tcpdump` (packet capture)
- Network log analysis
- NIST Cybersecurity Framework (Identify → Protect → Detect → Respond → Recover)

---

## Incident 1: DNS Service Failure

**Symptom**  
Users reported they could not access the company website (`yummyrecipesforme.com`).

**Investigation**  
- Packet capture showed a client sending a DNS query (UDP) to the DNS server (`203.0.113.2`).
- The server responded with an ICMP error: `udp port 53 unreachable` (timestamp 13:24:32).
- The same failure occurred three times in succession.

**Root Cause**  
The DNS service on port 53 was either crashed, stopped, or blocked by a firewall rule, preventing domain name resolution.

---

## Incident 2: SYN Flood (DoS Attack)

**Symptom**  
Website connection timeouts under abnormal traffic load.

**Investigation**  
- Logs showed a rapid influx of SYN packets with no completed TCP handshakes.
- The server was overwhelmed with half-open connections, exhausting system resources.

**Root Cause**  
A classic SYN Flood attack (a form of Denial-of-Service). The attacker sent large volumes of SYN requests but never completed the three-way handshake.

---

## NIST Framework Response

| Function | Actions Taken |
|----------|---------------|
| **Identify** | Determined that an unconfigured firewall allowed external ICMP and SYN flood traffic into the network. |
| **Protect** | Implemented rate-limiting on ICMP traffic, enabled source IP verification to block spoofing, and configured stricter firewall ACLs. |
| **Detect** | Deployed network monitoring tools and an IDS/IPS to baseline normal traffic and alert on anomalous spikes. |
| **Respond** | Blocked incoming ICMP flood traffic at the perimeter firewall and temporarily took non-critical services offline to contain impact. |
| **Recover** | Restored critical services first, established automated configuration backups, and set up an out-of-band communication channel for future incidents. |

---

## Business Impact
Demonstrated structured incident triage using industry-standard methodology. Reduced recovery time, hardened the network perimeter against volume-based attacks, and improved detection capabilities for future incidents.

## Related Documents
- [Cybersecurity Incident Report – Network Traffic Analysis](./Cybersecurity%20incident%20report%20network%20traffic%20analysis.pdf)
- [Cybersecurity Incident Report – SYN Flood](./Cybersecurity%20incident%20report.pdf)
- [Incident Report Analysis (NIST)](./Incident%20report%20analysis.pdf)
