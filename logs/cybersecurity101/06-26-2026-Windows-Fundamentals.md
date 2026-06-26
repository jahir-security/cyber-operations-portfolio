## Windows Fundamentals (Part 1, 2, and 3) - [06-26-2026]

### What This Covers
This series of rooms covers the essential foundations of the Microsoft Windows operating system from an administrative and security perspective. It introduces Windows architecture, core system utilities, built-in management tools, and native security configurations required to navigate, audit, and harden Windows environments.

### Key Concepts
* Core Windows editions and deployment options
* Navigating the Windows Graphical User Interface (GUI)
* Structure of the Windows File System and critical system directories like System32
* Differentiating file systems: NTFS as the modern system standard versus legacy FAT limitations
* User accounts management, profiles, and standard vs. administrator permissions
* Mechanisms of User Account Control (UAC) and privilege escalation prompts
* Managing Control Panel layouts and system settings applets
* Using System Configuration (msconfig) to audit startup applications and services
* Managing background tasks, triggers, and shared folders via Computer Management (compmgmt.msc)
* Aggregating hardware and software environmental variables using System Information (msinfo32.exe)
* Inspecting live network interfaces and detailed protocol settings using `ipconfig /all`
* Navigating registry keys, hives, and configurations via the Registry Editor (regedt32.exe)
* Monitoring, tracking, and installing Windows security and definition updates
* Hardening endpoint devices using Windows Security configurations and Real-time protection toggles
* Differentiating firewall network behaviors across Domain, Private, and Public connection profiles
* Hardware root-of-trust functionality using Trusted Platform Modules (TPM 2.0) vs. BitLocker external startup keys
* Conceptual understanding of the Volume Shadow Copy Service (VSS) for application-consistent snapshots

### What I Learned
I learned how the Windows operating system structures its file permissions, registry keys, and administrative utilities to manage a secure host environment. I understand how modern storage is organized using the NTFS file system to support advanced security permissions and large storage capacities, and why legacy architectures like FAT are no longer suitable for modern OS drives due to their strict file size limitations and complete lack of access control security features. I gained practical knowledge on using fundamental tools like Computer Management, System Information, and the Registry Editor to gather host metrics and troubleshoot system configurations. Additionally, I learned how native security mechanisms like User Account Control, BitLocker drive encryption, and Windows Defender Firewall profiles work together to enforce the principle of least privilege and protect endpoints against unauthorized access or tampering.
