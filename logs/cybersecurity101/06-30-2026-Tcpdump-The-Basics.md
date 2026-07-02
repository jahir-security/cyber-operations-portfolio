## Tcpdump: The Basics - [06-30-2026]

### What This Covers
This room covers how to capture and analyze network traffic directly from the command line using `tcpdump`. It focuses on running basic packet captures, applying both basic and advanced filtering expressions, and formatting the output to read packet contents effectively.

### Key Concepts
* **Command-Line Packet Capture:** Operating `tcpdump` to intercept and inspect raw network traffic directly from network interfaces, providing a lightweight, low-overhead alternative to GUI-based tools like Wireshark.
* **Display and Output Formatting:** Modifying how `tcpdump` prints packet data to the terminal. This includes extracting Layer 2 MAC addresses, reading cleartext application payloads using ASCII encoding, and viewing raw packet bytes in hexadecimal formats for deep-dive analysis.
* **Basic Filtering Expressions:** Utilizing standard Berkeley Packet Filter (BPF) syntax to narrow down captures by specific hosts, IP addresses, ports, or protocols to prevent terminal flooding.
* **Advanced Filtering via Byte Offsets:** Targeting specific byte locations within protocol headers (e.g., `ether[0]` or `ip[0]`). This allows analysts to isolate highly specific traffic, such as packets sent to a multicast MAC address or IP packets utilizing specific options, by applying bitwise AND (`&`) operations against hexadecimal values.
* **TCP Flag Isolation:** Referencing the `tcp[tcpflags]` field to filter traffic based on specific TCP states, including SYN (Synchronize), ACK (Acknowledge), FIN (Finish), RST (Reset), and PUSH.
* **Logical Filtering Constraints:** Understanding the critical difference between strict matching (e.g., `tcp[tcpflags] == tcp-syn` to find packets where *only* the SYN flag is set) versus bitwise masking (e.g., `tcp[tcpflags] & tcp-syn != 0` to capture packets where the SYN flag is present, regardless of what other flags are also active).

### Commands/Tools Used
```bash
tcpdump -q
