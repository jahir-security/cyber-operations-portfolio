# Windows and Active Directory Fundamentals - [07-21-2026]

**What This Covers**

This execution log covers the foundational mechanics of the Windows operating system, including the NTFS file system, system configuration tools, and built-in security features. It also introduces Active Directory architecture, domain trust relationships, and the mechanics behind network authentication protocols like Kerberos and NetNTLM.

**Key Concepts**

*   NTFS file system features, including permissions, file compression, and Alternate Data Streams (ADS).
*   Windows core directories (System32) and the differentiation between Administrator and Standard User accounts.
*   System configuration and troubleshooting utilities, including MSConfig, Resource Monitor, Task Scheduler, Event Viewer, and Disk Management.
*   Built-in Windows Security features, including Defender, Firewall profiles (Domain, Private, Public), BitLocker, and the Volume Shadow Copy Service (VSS).
*   Active Directory domain architecture, including the hierarchical structure of Trees, Forests, and Trust Relationships.
*   AD object management, differentiating Organizational Units (for policy application) from Security Groups (for resource authorization), and the delegation of administrative control.
*   Windows domain authentication protocols, specifically comparing the Ticket Granting Ticket (TGT) and Ticket Granting Service (TGS) mechanics of Kerberos against the legacy challenge-response mechanism of NetNTLM.


**What I learned**

I learned how to navigate and manage core Windows OS components, utilizing advanced utilities like MSConfig, Resource Monitor, and Computer Management to analyze system performance and scheduled tasks. I gained a practical understanding of the NTFS file system, including how permissions are applied and the existence of Alternate Data Streams (ADS), which malware can abuse to hide data. I explored built-in Windows security defenses, configuring Firewall profiles based on network trust (Domain, Private, Public) and analyzing hardware-based security features like BitLocker and the Trusted Platform Module (TPM). Furthermore, I mapped the structural hierarchy of Active Directory, understanding how to segregate devices (Workstations vs. Servers) into Organizational Units (OUs) for targeted policy application. Finally, I broke down the exact authentication flow of Kerberos, understanding how Ticket Granting Tickets (TGT) and Ticket Granting Services (TGS) authenticate users across a network without repeatedly transmitting credentials, contrasting this with the legacy NetNTLM protocol.
