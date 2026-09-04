# TryHackMe: Windows Fundamentals 2

## Room Summary

This room dives deeper into administrative tools and system utilities built into Windows, focusing on Computer Management, System Configuration (msconfig), Task Scheduler, Event Viewer, System Information, and Command Prompt / PowerShell administration.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Windows Fundamentals 2 |
| Difficulty | Very Easy / Info |
| Topic | Windows Administration, System Utilities, Event Logs, Task Scheduling |
| Status | Completed |

## Skills Practiced

- Interacting with administrative consoles (`compmgmt.msc`, `eventvwr.msc`, `msconfig`)
- Analyzing Windows Event Logs (System, Security, Application) to identify operational and security events
- Managing scheduled tasks and analyzing automated triggers via Task Scheduler
- Performing system configuration audits and managing boot parameters using `msconfig`
- Utilizing command-line administration tools (`schtasks`, `wevtutil`, `sc`) for remote and local triage

## Hands-On & Command Reference

### Task Scheduler Management (CMD / PowerShell)

```cmd
# Query active scheduled tasks on the local system
schtasks /query /fo LIST /v

# Run a specific scheduled task on demand
schtasks /run /tn "TaskName"

```

```powershell
# Get scheduled tasks with detailed output using PowerShell
Get-ScheduledTask | Where-Object {$_.State -ne "Disabled"}

```

### Windows Event Viewer Triage (PowerShell & CLI)

```powershell
# Retrieve the last 10 Error events from the System log
Get-EventLog -LogName System -EntryType Error -Newest 10

# Query specific Security Event IDs (e.g., Event ID 4624 for successful logons)
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4624} -MaxEvents 5

```

```cmd
# Export Event Log via Command Prompt using wevtutil
wevtutil epl Security C:\Logs\Security_Backup.evtx

```

### Service Configuration & Control

```cmd
# View configuration and status of a Windows service
sc query "Spooler"

# Stop and start a Windows service via CMD
sc stop "Spooler"
sc start "Spooler"

```

## Tools and Platforms Learned

* TryHackMe
* Windows Management Consoles (`compmgmt.msc`, `eventvwr.msc`, `taskschd.msc`, `msconfig`, `msinfo32`)
* Windows Command Line Utilities (`schtasks`, `wevtutil`, `sc`)
* PowerShell Event & Task Cmdlets (`Get-WinEvent`, `Get-EventLog`, `Get-ScheduledTask`)

## Key Takeaways

* **System Diagnostics:** Event Viewer (`eventvwr.msc`) provides centralized logging across Security, System, and Application logs, serving as a primary artifact store during digital forensics and incident response.
* **Automation Oversight:** Task Scheduler (`taskschd.msc`) manages background system tasks but is frequently targeted by adversaries for persistence and scheduled execution.
* **Unified Management:** Computer Management (`compmgmt.msc`) centralizes System Tools, Storage (Disk Management), and Services into a single administrative snap-in.

## Defensive Learning

* Monitor Event ID `4624` (Successful Logon), `4625` (Failed Logon), and `4698` (A scheduled task was created) for indicators of unauthorized access.
* Audit Task Scheduler regularly to detect malicious persistence entries scheduled to run upon startup or user logon.
* Use `wevtutil` or PowerShell scripts to collect EVTX log files automatically for centralized SIEM ingestion.

```

```
