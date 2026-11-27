# Introduction to Snort - [11-27-2026]

## What This Covers

This room covers the fundamentals of Intrusion Detection Systems (IDS) and introduces Snort, an open-source network intrusion detection tool. It explains different IDS types and detection methods, Snort operating modes, rule structure, custom rule creation, and how to detect suspicious network traffic using live monitoring and PCAP files.

## Key Concepts

- **Intrusion Detection System (IDS):** Monitors network or system activities to identify suspicious or malicious behaviour and generates alerts for security administrators. Unlike an IPS, an IDS does not actively prevent detected threats.
- **Host Intrusion Detection System (HIDS):** Monitors activities on an individual host and provides detailed visibility into that system.
- **Network Intrusion Detection System (NIDS):** Monitors network traffic across multiple hosts and provides centralized visibility into network activity.
- **Signature-Based Detection:** Identifies known threats by matching traffic against previously defined attack patterns or signatures. It cannot reliably detect unknown zero-day attacks.
- **Anomaly-Based Detection:** Learns normal network or system behaviour and detects deviations from the established baseline. It can identify unusual activity but may generate false positives.
- **Hybrid IDS:** Combines signature-based and anomaly-based detection techniques.
- **Snort:** An open-source IDS that uses rules to identify suspicious network traffic.
- **Snort Modes:**
  - Packet Sniffer Mode – Captures and displays network packets.
  - Packet Logging Mode – Logs network traffic into PCAP files for later analysis.
  - Network Intrusion Detection System (NIDS) Mode – Monitors traffic and generates alerts based on matching rules.
- **Promiscuous Mode:** Allows a network interface to capture traffic beyond packets specifically addressed to its own host, subject to network visibility.
- **Snort Rule Structure:** Includes action, protocol, source IP, source port, direction, destination IP, destination port, and rule options.
- **Rule Metadata:**
  - `msg` – Defines the alert message.
  - `sid` – Identifies the rule with a signature ID.
  - `rev` – Specifies the rule revision number.
- **Custom Rules:** Rules can be created in `local.rules` to detect specific types of network traffic.
- **PCAP Analysis:** Snort can analyse previously captured network traffic to identify signs of intrusion.

## Commands/Tools Used

### Snort Directory

```bash
# List files and directories used by Snort
ls /etc/snort
```

### Editing Custom Rules

```bash
# Open the local custom rules file
sudo nano /etc/snort/rules/local.rules
```

### Custom ICMP Detection Rule

```snort
# Detect ICMP traffic directed to the loopback address
alert icmp any any -> 127.0.0.1 any (msg:"Loopback Ping Detected"; sid:10003; rev:1;)
```

### Running Snort for Live Detection

```bash
# Monitor traffic on the loopback interface and generate alerts
sudo snort -q -l /var/log/snort -i lo -A alert_fast -c /etc/snort/snort.lua
```

### Generating ICMP Traffic

```bash
# Send ICMP packets to the loopback address
ping 127.0.0.1
```

### Analysing a PCAP File

```bash
# Analyse previously captured network traffic using Snort
sudo snort -q -l /var/log/snort -r Task.pcap -A alert_fast -c /etc/snort/snort.lua
```

## What I Learned

I learned the difference between IDS deployment types and detection methods, including HIDS, NIDS, signature-based, anomaly-based, and hybrid detection.

I explored the three main operating modes of Snort and understood how it monitors network traffic using predefined rules. I also learned the structure of Snort rules and the purpose of important fields such as `msg`, `sid`, and `rev`.

In the practical exercise, I created a custom ICMP detection rule in `local.rules`, ran Snort on the loopback interface, and generated traffic using `ping 127.0.0.1` to trigger an alert. I also learned how Snort can analyse PCAP files to investigate previously captured network traffic and identify suspicious activities.
