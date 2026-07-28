
## Wireshark: The Basics & Traffic Analysis - [06-29-2026]

### What This Covers
This covers the fundamentals of using Wireshark to investigate network traffic. It goes from basic packet filtering and reconstructing data streams to more hands-on, practical tasks like decrypting secure web traffic, finding hidden strings, and extracting actual files out of raw network packets.

### Key Concepts
* **Capture vs. Display Filters:** Understanding the difference between capturing specific traffic live and filtering through traffic that is already saved in a file.
* **Quick GUI Filtering:** Using the right-click menu to quickly apply filters, highlight specific conversations, and add custom columns without having to write complex search queries from scratch.
* **Following Streams:** Using the "Follow Stream" tool to put fragmented packets back together, allowing you to read the full, plain-text conversation between a client and a server.
* **Decrypting Secure Traffic:** Loading a browser's `ssl-key.log` file directly into Wireshark to unlock and read encrypted TLSv1.3 web traffic.
* **Targeted Searching:** Using `Ctrl + F` to easily search through packet details for specific keywords that might be hidden inside the web code.
* **Finding Hidden Data:** Looking into the Packet Comment window to uncover hidden instructions or data that are buried under thousands of lines of spam traffic.
* **Extracting Files:** Pulling a raw file (like an image) straight out of a packet capture and using the Linux terminal to verify its MD5 hash.

### Commands/Tools Used
```bash
md5sum extracted_image.png
tcp.port == 80
```
http
### What I Learned
I learned how to stop getting overwhelmed by massive packet capture files. By using simple display filters and the "Follow Stream" feature, I can easily cut through the noise and read the actual conversations happening over the network. I also learned practical ways to deal with complex real-world traffic—like decrypting secure TLS packets with a key log file, searching for specific hidden keywords, and pulling actual files right out of the packet data to analyze them in the Linux terminal. I now have a solid, hands-on understanding of how to find exactly what I am looking for instead of just guessing.


<img width="923" height="688" alt="image" src="https://github.com/user-attachments/assets/39ae2240-3d75-4e9d-891d-9932089b31c2" />
<img width="838" height="527" alt="image" src="https://github.com/user-attachments/assets/e2f8c499-11dd-48cf-b08c-fbfd6264f23f" />

