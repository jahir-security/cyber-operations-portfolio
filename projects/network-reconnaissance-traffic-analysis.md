# Security Assessment Report: Network Reconnaissance & Traffic Analysis

**Date:** 08-11-2026

**Environment:** TryHackMe lab environment — AttackBox (`10.10.201.13`) and target lab machine (`10.10.155.84`), local network segment (`10.10.155.0/24`).

---

## Scenario

As part of a network security assessment, I was tasked with mapping active hosts and services on a target network segment, then capturing and analyzing the resulting traffic to identify any unencrypted protocols or data exposure that could pose a risk if intercepted by an attacker on the same network.

---

## Investigation

**Host Discovery**

Before scanning for services, I first needed to determine which hosts on the network were actually live, since scanning dead IP space wastes time and adds unnecessary noise. I used Nmap's ping scan (`-sn`), which discovers live hosts without attempting to enumerate services on them — a quieter first step before a full port scan. On the local network segment, Nmap discovers hosts via ARP requests rather than ICMP, since ARP is reliable on a directly connected Ethernet/WiFi segment and also reveals the responding device's MAC address, which can hint at the vendor/device type.

**Port Scanning**

Once live hosts (`10.10.155.84`) were confirmed active, I moved to port scanning to determine which services were listening. I chose a SYN scan (`-sS`) over a full TCP connect scan (`-sT`), since a SYN scan only sends the initial SYN packet and never completes the three-way handshake — this generates less logging on the target compared to a full connection, making it a more realistic approach to how a real assessment or attacker reconnaissance would be conducted with a lower footprint.

This scan identified 6 open TCP ports on the target system (21, 22, 80, 111, 139, 445), including an active web server. I combined this with `-sV` (version detection) and `-O` (OS detection) to identify not just that ports were open, but *what* was running on them and the underlying OS — this additional context matters because an open port alone doesn't tell you whether the service is outdated or misconfigured; the version string does.

**Investigating the Exposed Web Service**

Since the port scan revealed an active web server on port 80 (`Apache httpd 2.4.29`), I accessed it directly via a web browser to determine what it exposed. This confirmed the service was serving a login portal over unencrypted HTTP rather than HTTPS — a finding worth flagging in a real assessment, since transmitting an authentication mechanism over cleartext HTTP exposes any submitted credentials in transit, regardless of how strong the password itself is.

**Traffic Capture with tcpdump**

To validate what the port scan found and capture supporting evidence, I used tcpdump to capture live traffic to/from the target host, filtering specifically by host and protocol (`tcpdump host 10.10.155.84 -w capture.pcap`) rather than capturing the entire network's traffic indiscriminately — this keeps the capture focused and avoids drowning the analysis in unrelated packets. I also used protocol-specific filters (e.g., `icmp`, `port 53`) to isolate specific traffic types of interest, such as confirming ICMP reachability and DNS query behavior.

**Deep Packet Inspection with Wireshark**

With the `.pcap` captured, I moved to Wireshark for deeper protocol-level inspection than tcpdump's command-line output allows. Using the "Follow HTTP Stream" feature, I reconstructed the full application-layer conversation for the web traffic — this is a critical step, since it revealed the actual data being transmitted in cleartext, not just the fact that a connection existed.

Because HTTP (unlike HTTPS) transmits data unencrypted, anyone capturing this traffic on the same network segment could read the exact content being exchanged. I confirmed this directly by reconstructing a captured `POST /login.php` request, which exposed the transmitted credentials (`username=admin&password=password123`) in plain text, despite the login mechanism itself functioning as intended.

I also reviewed Wireshark's Expert Information panel, which automatically flags anomalies. It highlighted multiple "TCP Retransmission" and "Duplicate ACK" warnings — common in virtualized lab networks — useful as a fast triage step before manually inspecting packets.

---

## Commands/Tools Used

```bash
# Nmap - host discovery (local network)
nmap -sn 10.10.155.0/24

# Nmap - SYN scan with version and OS detection
sudo nmap -sS -sV -O 10.10.155.84

# tcpdump - targeted capture, host-filtered, saved for later analysis
sudo tcpdump host 10.10.155.84 -w capture.pcap

# tcpdump - protocol-specific filtering
sudo tcpdump icmp -n
sudo tcpdump port 53 -n

# Wireshark - opened capture.pcap for deep inspection
# Used Analyze > Follow > HTTP Stream to reconstruct application-layer data
# Used Analyze > Expert Information to review flagged anomalies
```

---

## Findings

- Host discovery via ARP-based ping scan confirmed the target host (`10.10.155.84`) was live on the local network segment without triggering a full port scan.
- SYN scan identified 6 open TCP ports on the target system (21/FTP, 22/SSH, 80/HTTP, 111/rpcbind, 139/netbios-ssn, 445/netbios-ssn).
- Version/OS detection identified the specific web service (`Apache httpd 2.4.29`) and underlying OS family (`Ubuntu Linux`), providing enough detail to cross-reference against known vulnerabilities in a real assessment.
- The web service's login mechanism operated over unencrypted HTTP rather than HTTPS. Reconstructing the HTTP stream in Wireshark confirmed that a submitted login request transmitted user credentials in cleartext, exposing them to anyone capturing traffic on the same network segment.
- Expert Information flagged a notable number of TCP retransmission warnings during the capture, indicating protocol-level anomalies worth manual follow-up in a real engagement rather than dismissing as noise.

---

## MITRE ATT&CK Mapping

*   **T1595.001 – Active Scanning: Scanning IP Blocks** (Nmap host discovery)
*   **T1046 – Network Service Scanning** (Nmap port/service/version detection)
*   **T1040 – Network Sniffing** (tcpdump/Wireshark traffic capture and cleartext data exposure identification)

---

## Analyst Notes

This assessment reinforced why network reconnaissance findings need to be paired with traffic analysis, not treated as separate exercises — a port scan tells you a service exists, but only packet-level inspection confirms *how* that service handles data in practice. The discovery of cleartext HTTP traffic carrying readable login credentials is a common and easily overlooked risk, since a working authentication mechanism can still leave data fully exposed if the underlying transport isn't encrypted. In a real environment, I would recommend enforcing HTTPS/TLS for all web-facing login services regardless of whether they're internal or external, and treating cleartext credential transmission as a priority remediation item rather than a low-severity finding.
