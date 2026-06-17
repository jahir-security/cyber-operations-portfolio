# Daily Progress Log: June 17, 2026
**Topic:** Cross-Platform Command Line Interface (CLI) Administration

## 🛠️ What I Executed Today

Today, I moved away from the Graphical User Interface (GUI) and focused entirely on navigating and enumerating systems via the command line. Mastering these commands is crucial for my path to becoming a SOC analyst, as incident response and threat hunting happen directly in the shell.

### 1. Linux Systems Administration (Bash Shell)
I spent the first half of my lab operating within a Linux environment, focusing on filesystem traversal and system profiling[cite: 3].
*   **Filesystem Navigation:** I utilized `pwd` to map my absolute path and practiced moving through the directory tree with `cd`[cite: 3]. To ensure I wasn't missing obfuscated data, I used `ls -al` to uncover hidden system files and verify read/write/execute permissions[cite: 3].
*   **Targeted File Operations:** Instead of manually digging through folders, I deployed the `find` utility with the `-name` argument to recursively locate specific files across the system[cite: 3]. Once found, I used `cat` to output and read the file contents directly in my terminal[cite: 3].
*   **System Profiling:** I learned how to extract live environment data. I used `whoami` to verify my current user context and `uname -a` to pull detailed information about the Linux kernel and system architecture[cite: 3]. I also monitored human-readable disk usage with `df -h` and navigated to the `/etc` directory to analyze core OS configuration files, specifically reading the `os-release` file[cite: 3].

### 2. Windows OS Administration (Command Prompt)
In the second half of the lab, I mirrored these operations inside the Windows Command Prompt to ensure I am comfortable in a mixed-OS enterprise environment[cite: 3].
*   **Directory Enumeration:** I leveraged `cd` for directory traversal and utilized `dir /a` to expose hidden directories and system files that don't appear in a standard listing[cite: 3].
*   **Recursive Searching:** I executed `dir /s` to hunt for specific files buried deep within nested subfolders[cite: 3]. Once I verified the exact path, I used the `type` command to output the text to my screen[cite: 3].
*   **Host & Network Auditing:** I gathered local machine intelligence by running `whoami` and `hostname` to map my session[cite: 3]. I then extracted extensive machine configurations (including the exact OS build and hardware specs) via `systeminfo`[cite: 3]. Finally, I audited my local network adapter, checking my IPv4 allocation, subnet mask, and default gateway using `ipconfig`[cite: 3].

## 💡 My Key Takeaway
Relying on a GUI is a massive limitation in cybersecurity. Whether I am trying to identify a rogue process, search for hidden malicious payloads, or audit network adapters, I have to be completely comfortable operating directly in the shell. Today's lab gave me the muscle memory to navigate both Linux and Windows systems rapidly.
