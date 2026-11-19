# Metasploit Meterpreter - [11-19-2026]

## What This Covers

This execution log documents the architecture, stealth mechanisms, and post-exploitation capabilities of the Metasploit Meterpreter payload. It covers selecting platform-specific payloads, navigating built-in command categories, migrating processes, harvesting credentials, and loading post-exploitation extensions.

## Key Concepts

*   Understanding Meterpreter's in-memory (RAM) execution model, which avoids writing files to disk to evade basic antivirus scans, alongside TLS-encrypted communication channels that help bypass uninspected network-based IDS/IPS solutions.
*   Selecting between staged and inline (stageless) Meterpreter payloads across supported platforms (Windows, Linux, macOS/OSX, Android, iOS, Java, PHP, and Python) based on the target OS, available components, and allowed network connection types.
*   Navigating Meterpreter's built-in command categories—including Core, File System, Networking, System, Elevate, and Password Database commands—which execute directly on the target without dropping extra scripts or executables.
*   Using process migration (`migrate`) to stabilize an active session or interact with specific user processes (such as capturing keystrokes), while accounting for the risk of losing elevated privileges if migrating into a lower-privileged process.
*   Extending post-exploitation capabilities for privilege escalation, credential harvesting, and lateral movement by dumping Windows SAM NTLM hashes (`hashdump`) and dynamically loading extensions like Python or Kiwi (Mimikatz).

## Commands/Tools Used

```bash
# Listing and selecting Meterpreter payloads:
msfvenom --list payloads | grep meterpreter
use exploit/windows/smb/ms17_010_eternalblue
show payloads

# Session reconnaissance and system enumeration:
help
sysinfo
getuid
getpid
ps

# Process migration and credential harvesting:
migrate 716
getsystem
hashdump

# File searching, system shell, and loading extensions:
search -f flag2.txt
shell
load python
python_execute "print 'TryHackMe Rocks!'"
load kiwi
creds_all
```

## What I learned

I learned how Meterpreter functions as an in-memory command-and-control agent within the Metasploit Framework to support stealthier post-exploitation engagements. By exploring payload listings with `msfvenom` and `show payloads`, I can match staged or inline Meterpreter versions to the target's operating system, installed components, and network restrictions. I also learned how to enumerate system context using `getuid`, `getpid`, and `ps`, stabilize or reposition a session via `migrate` without accidentally dropping privileges, and locate sensitive files with `search`. Finally, I learned how to pivot into deeper post-exploitation by dropping into a native `shell`, extracting NTLM hashes from the SAM database with `hashdump`, and loading external modules like `python` and `kiwi` to expand available credential-dumping commands.
