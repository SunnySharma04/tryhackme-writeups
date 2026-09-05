# TryHackMe: Windows Command Line

## Room Summary

This room provides a deep dive into the Windows Command Line (CMD), covering essential CLI navigation, file management, system information retrieval, process manipulation, network troubleshooting, and security-relevant utility execution.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Windows Command Line |
| Difficulty | Very Easy / Info |
| Topic | Windows CLI, Command Prompt, System Administration, Process & Network Inspection |
| Status | Completed |

## Skills Practiced

- Navigating the Windows filesystem, creating/modifying/deleting files and directories using native CMD tools
- Inspecting system configuration, hardware details, network interfaces, and environment variables
- Managing and terminating system processes directly from the command line (`tasklist`, `taskkill`)
- Troubleshooting local network connections, routing tables, and active sockets (`ipconfig`, `netstat`, `ping`, `tracert`)
- Executing administrative and utility commands to audit system posture and file attributes

## Hands-On & Command Reference

### Filesystem Navigation & File Operations

```cmd
# Navigate directories and display directory contents
cd C:\Users\Public
dir /a

# Create, move, and remove files/directories
mkdir Incident_Response
copy C:\Windows\System32\drivers\etc\hosts C:\Users\Public\hosts.bak
del C:\Users\Public\hosts.bak
rmdir Incident_Response

```

### System & Process Management

```cmd
# Display complete system configuration and OS patch level
systeminfo

# List active processes with associated PID and memory usage
tasklist /v /fo csv

# Terminate a process by Process ID (PID) or image name
taskkill /PID 4432 /F
taskkill /IM notepad.exe /F

```

### Network Diagnostics & Triage

```cmd
# Display detailed TCP/IP configuration and flush DNS cache
ipconfig /all
ipconfig /flushdns

# View active network connections, process ownership, and listening ports
netstat -ano

# Trace packet route and test connection latency
tracert 8.8.8.8
ping -n 4 127.0.0.1

```

## Tools and Platforms Learned

* TryHackMe
* Windows Command Prompt (`cmd.exe`)
* Native Windows CLI Utilities (`dir`, `copy`, `systeminfo`, `tasklist`, `taskkill`, `ipconfig`, `netstat`)

## Key Takeaways

* **CLI Efficiency:** Native command-line interfaces provide rapid environment triage without requiring GUI dependencies, essential during headless or low-bandwidth remote administration.
* **Process Oversight:** `tasklist /v` and `netstat -ano` are foundational commands for correlating running processes directly to open network sockets during initial host triage.
* **Network Troubleshooting:** Tools like `ipconfig` and `netstat` provide immediate visibility into network interface states and active external connections.

## Defensive Learning

* Use `netstat -ano` correlated with `tasklist` to locate unauthorized outbound connections and uncover rogue processes.
* Audit file creation and modification timestamps (`dir /T:C`, `dir /T:A`) when performing initial disk artifact triage.
* Monitor execution of powerful CMD binaries (`cmd.exe /c`) via process creation logs (Event ID 4688) to spot command-line abuse by malicious scripts or initial access vectors.

```

```
