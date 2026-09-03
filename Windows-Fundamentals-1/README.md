# TryHackMe: Windows Fundamentals 1

## Room Summary

This room provides a practical introduction to the Windows operating system, covering core structural components such as the Windows File System (NTFS), User Account Management, the Windows Registry, Task Manager, Control Panel, and System Settings.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Windows Fundamentals 1 |
| Difficulty | Very Easy / Info |
| Topic | Windows Architecture, User Management, Registry, Task Manager |
| Status | Completed |

## Skills Practiced

- Navigating and analyzing the Windows File System structure (`C:\Windows`, `C:\Program Files`, `C:\Users`)
- Managing Windows User Accounts, User Account Control (UAC), and group privileges
- Inspecting and querying the Windows Registry hives (`HKLM`, `HKCU`, `HKCR`, `HKU`, `HKCC`)
- Monitoring active processes, resource consumption, and startup applications via Task Manager
- Interacting with System Settings, Control Panel, and Administrative Tools for system configuration

## Hands-On & Command Reference

### Windows Command Line & System Inspection

```cmd
# View system information and OS build details
systeminfo

# Display logged-in user identity and privilege privileges
whoami /priv

# List local user accounts on the target machine
net user

# Inspect local group memberships
net localgroup Administrator

```

### Registry Query Operations (CMD)

```cmd
# Query specific registry run keys for persistence entries
reg query "HKLM\Software\Microsoft\Windows\CurrentVersion\Run"

# Query user-specific startup registry keys
reg query "HKCU\Software\Microsoft\Windows\CurrentVersion\Run"

```

### PowerShell System Diagnostics

```powershell
# Get active system processes sorted by CPU utilization
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10

# Inspect active system services and their current status
Get-Service | Where-Object {$_.Status -eq "Running"}

```

## Tools and Platforms Learned

* TryHackMe
* Windows GUI Diagnostics (Task Manager, Resource Monitor, Control Panel)
* Windows System Utilities (`regedit`, `lusrmgr.msc`, `services.msc`)
* Command Line Tools (`cmd.exe`, PowerShell, `net`, `whoami`, `systeminfo`)

## Key Takeaways

* **Windows Architecture:** Built around a centralized hierarchical database known as the **Windows Registry**, which dictates OS settings, driver behavior, and user preferences.
* **Access Control:** User Account Control (UAC) enforces security boundaries by prompting for elevated administrative privileges before allowing system-level alterations.
* **Process Visibility:** Task Manager and Resource Monitor serve as essential first-line tools for identifying anomalous process behavior and resource hijacking.

## Defensive Learning

* Audit startup registry keys (`HKLM` / `HKCU` Run keys) to detect persistence mechanisms planted by malicious software.
* Apply the principle of least privilege by running daily tasks under standard user accounts rather than local administrator accounts.
* Continuously monitor running services and binary file paths using `Get-Service` or Process Hacker to spot unquoted service paths and unauthorized execution.

```

```
