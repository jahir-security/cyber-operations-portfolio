## Nmap: The Basics - [07-01-2026]

### What This Covers
This room covers how to use Nmap to discover live hosts, find open ports, and detect service versions. It focuses on the fundamental scan types, controlling scan timing, and managing output formats for reporting and analysis.

### Key Concepts
* **Host Discovery:** Using list scans and ping scans to identify active devices on a network without fully scanning their ports.
* **Port Scanning:** Understanding the difference between a TCP connect scan (which completes the three-way handshake) and a TCP SYN scan (which only performs the first step of the handshake).
* **Privilege Limitations:** Recognizing that if Nmap is run with local user privileges (without root/sudo), it defaults to a Connect Scan.
* **Service & OS Detection:** Extracting more information from target systems by utilizing OS detection, service version detection, and the aggressive scan flag.
* **Timing & Performance:** Controlling scan speed using timing templates ranging from `T0` (paranoid) to `T5` (insane), and understanding that `T4` equates to an "aggressive" scan.
* **Scan Delays:** Observing how different timing templates affect packet intervals, such as `T0` waiting 5 minutes between packets versus `T1` waiting 15 seconds.
* **Output Management:** Controlling what is seen on the screen using verbosity and debugging levels, and saving reports in Normal, XML, Grepable, or All formats.

### Commands/Tools Used
```bash
nmap -sn
Performs a ping scan for host discovery only.

nmap -sT
Executes a TCP connect scan that completes the full three-way handshake.

nmap -sS
Executes a TCP SYN scan, completing only the first step of the handshake.

nmap -sV
Enables service version detection on open ports.

nmap -T4
Applies the "aggressive" timing template to speed up the scan.

nmap -v
Increases the verbosity level to show real-time output during the scan.

nmap -oN <filename>
Saves the scan results in a normal, human-friendly output format.

```
### What I Learned
I learned the foundational mechanics of scanning networks using Nmap. I now understand that without administrative privileges, my scans will default to a louder TCP Connect scan rather than a stealthier SYN scan. I gained hands-on experience controlling how fast Nmap operates by using timing templates (like T4 for aggressive scanning) to either speed up the process or avoid overwhelming the network. Finally, I learned how to properly save my scan results into formats like XML or grepable files so the data can be analyzed later without having to run the scan twice.
