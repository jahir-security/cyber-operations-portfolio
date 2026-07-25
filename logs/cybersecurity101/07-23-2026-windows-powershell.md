# Windows PowerShell - [07-23-2026]

## What This Covers

This execution log documents the fundamentals of Windows PowerShell, emphasizing its object-oriented architecture. It covers the execution of core cmdlets for file system navigation, advanced object piping and filtering, system and network information retrieval, and real-time process analysis.

## Key Concepts

*   Understanding PowerShell's object-oriented nature (processing objects with properties and methods instead of plain text) and the Verb-Noun cmdlet naming convention.
*   Discovering cmdlets, aliases, and examples using built-in help and repository search functions.
*   Managing files and directories using unified item management cmdlets.
*   Utilizing the pipeline to pass objects between cmdlets, applying operators (e.g., -eq, -gt, -like) to filter data, sort outputs, and select specific properties.
*   Retrieving comprehensive system specifications, local user account details, and detailed IP/network interface configurations.
*   Conducting real-time system analysis by enumerating active processes, querying service statuses, mapping active TCP connections to their owning processes, and generating file hashes.
*   Viewing Alternate Data Streams (ADS) attached to files and executing commands on remote systems using script blocks.

## Commands/Tools Used

```bash
# Basic Cmdlets and Help:
Get-Command -CommandType "Function"
Get-Help Get-Date -examples
Get-Alias
Find-Module -Name "PowerShell*"
Install-Module -Name "PowerShellGet"

# File System Management:
Get-ChildItem -Path ".\Documents"
Set-Location -Path ".\Documents"
New-Item -Path ".\captain-wardrobe" -ItemType "Directory"
Remove-Item -Path ".\captain-boots.txt"
Copy-Item -Path .\captain-hat.txt -Destination .\captain-hat2.txt
Move-Item
Get-Content -Path ".\captain-hat.txt"

# Piping and Filtering:
Get-ChildItem | Sort-Object Length
Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"
Get-ChildItem | Where-Object -Property "Name" -like "ship*"
Get-ChildItem | Select-Object Name,Length
Select-String -Path ".\captain-hat.txt" -Pattern "hat"

# System and Network Information:
Get-ComputerInfo
Get-LocalUser
Get-NetIPConfiguration
Get-NetIPAddress

# Real-Time Analysis and Remote Execution:
Get-Process
Get-Service
Get-NetTCPConnection
Get-FileHash -Path .\ship-flag.txt
Get-Item -Path "C:\House\house_log.txt" -Stream *
Invoke-Command -ComputerName RoyalFortune -ScriptBlock { Get-Service }
```

## What I learned
I learned how to operate within PowerShell's object-oriented environment, manipulating data objects that contain properties and methods rather than parsing plain text. I gained practical experience discovering cmdlets and managing the file system. I utilized the pipeline to seamlessly pass objects between commands, applying strict comparison operators to filter, sort, and extract specific properties. For system enumeration, I executed cmdlets to retrieve deep system hardware configurations, local user statuses, and network adapter details. I also performed live system analysis by tracking active processes, auditing service states, and identifying active TCP connections along with their underlying process IDs. Finally, I learned how to check file integrity via hashes, expose hidden Alternate Data Streams, and remotely execute commands across network boundaries.
