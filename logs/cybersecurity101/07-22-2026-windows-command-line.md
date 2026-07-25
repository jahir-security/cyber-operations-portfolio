# Windows Command Line - [07-22-2026]

## What This Covers

This execution log documents my hands-on practice with the default Windows command-line interpreter, cmd.exe. It covers fundamental system information retrieval, network troubleshooting, file and directory management, and process execution.

## Key Concepts

*   Utilizing the CLI for lower resource usage, task automation, and remote management (e.g., SSH) compared to GUI-based administration.
*   System Information Retrieval: Identifying the current operating system version, active environment variables (like the execution Path), and comprehensive system details using built-in utilities.
*   Network Troubleshooting: Checking local IP configurations, testing reachability via ICMP echo requests, tracing routing paths across network hops, and querying specific DNS servers.
*   Connection Mapping: Analyzing active network connections and listening ports, and correlating them directly to specific process IDs (PIDs) and executables.
*   File and Disk Management: Navigating the directory tree, viewing file contents directly in the terminal, and performing standard file operations (copy, move, delete) using command-line syntax.
*   Process Management: Listing all running tasks, applying strict filters to isolate specific image names, and forcefully terminating unresponsive or malicious processes using their PID.

## Commands/Tools Used

```bash
### System Information:
set
ver
systeminfo
driverquery | more

###Network Troubleshooting:
ipconfig /all
ping example.com
tracert example.com
nslookup example.com 1.1.1.1
netstat -abon

### File and Disk Management:
cd
dir /a
dir /s
tree
mkdir
rmdir
type
copy
move
erase
del

### Task and Process Management:
tasklist /FI "imagename eq sshd.exe"
taskkill /PID [target_pid]

### Maintenance:
chkdsk
sfc /scannow
shutdown /s
shutdown /r
shutdown /a
```

## What I learned

I learned how to navigate and manage a Windows environment entirely through cmd.exe without relying on the GUI. I gained practical experience pulling host configurations and utilizing pipeline operators to paginate long terminal outputs. For network triage, I mapped active connections to their underlying executables and PIDs, and used tools like tracert and nslookup to troubleshoot routing and DNS. Additionally, I practiced core file system operations and learned how to actively monitor, filter, and terminate specific processes directly from the prompt.
