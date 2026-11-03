# Network Traffic Analysis & Incident Response (NIST Framework)

## 📌 Incident Overview
In this project, I investigated and documented a Denial of Service (DoS) security incident that compromised internal network operations[cite: 27]. Using network packet analysis tools (`tcpdump`) and protocol log telemetry, I diagnosed the root cause, contained the threat, and designed a long-term remediation plan using the **NIST Cybersecurity Framework**[cite: 2, 27, 28].

## 🛠️ Tools & Technologies
* **Analysis Tools:** `tcpdump`, Network Log Analyzers
* **Protocols Investigated:** ICMP, UDP (Port 53 / DNS), TCP (SYN Flood), HTTP[cite: 1, 2, 31]
* **Framework:** NIST Cybersecurity Framework (Identify, Protect, Detect, Respond, Recover)[cite: 27, 28]

## 🔍 Incident Investigation Summary

### 1. DNS & UDP Communication Failure
* **Symptom:** Users reported being unable to reach external company web services[cite: 2].
* **Diagnosis:** Analysis of network packet captures revealed ICMP echo replies returning `udp port 53 unreachable`[cite: 2].
* **Root Cause:** The DNS software service listening on Port 53 was crashed, stopped, or blocked by firewall rules[cite: 2, 3].

### 2. SYN Flood / DoS Attack Triage
* **Symptom:** Web server connection timeouts occurred under abnormal request volume[cite: 1].
* **Diagnosis:** Server logs reflected a rapid influx of SYN requests without completing the TCP 3-way handshake[cite: 1].
* **Root Cause:** A malicious actor flooded the server with half-open TCP connections, rapidly draining system memory and preventing legitimate traffic[cite: 1].

---

## 🛡️ NIST Framework Response Strategy

* **Identify:** Uncovered that an unconfigured firewall allowed external malicious actors to flood the internal network via ICMP pings and unverified connection requests[cite: 27].
* **Protect:** Recommended implementing rate-limiting rules on ICMP traffic, enabling source IP address verification to block spoofing, and configuring Firewall Access Control Lists (ACLs)[cite: 27, 30].
* **Detect:** Deployed network monitoring software and an Intrusion Detection/Prevention System (IDS/IPS) to baseline normal traffic patterns and flag anomalous spikes[cite: 27, 28].
* **Respond:** Blocked incoming ICMP flood traffic at the perimeter firewall and temporarily took non-critical network services offline to isolate system impact[cite: 28].
* **Recover:** Priority-restored core operational services, established automated network configuration backups, and instituted out-of-band communication channels for real-time incident coordination[cite: 28].

## 🚀 Business Impact
Demonstrated structured incident triage using industry-standard frameworks, reducing system restoration time, securing perimeter firewalls against volume-based attacks, and maintaining operational continuity[cite: 27, 28, 29].
