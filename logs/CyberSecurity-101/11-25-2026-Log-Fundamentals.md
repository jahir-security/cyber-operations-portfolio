# Log Fundamentals - [11-25-2026]

## What this covers
This lab gives an overview of different types of logs and how useful they are from a security perspective, as well as for performance monitoring, troubleshooting, and more. It provides a basic understanding of how we can read Windows and web server access logs.

## Key concepts
* Understanding the various use cases of logs.
* Types of different logs, such as:
  * System logs
  * Audit logs
  * Security logs
  * Network logs
  * Access logs
  * Application logs
* Windows Event Log analysis
* Basic concepts of web server access logs

## Commands and tools used
```bash
# To get Windows Event Logs
Start -> Event Viewer -> Windows Logs

# To get web logs from Linux
ls /root/Rooms/logs

# Filtering logs
grep 'GET /contact' access.log
```

## What I Learned
I learned how different types of logs are useful in different scenarios. I also learned how to read and filter Windows Event Logs and basic web server access logs.
