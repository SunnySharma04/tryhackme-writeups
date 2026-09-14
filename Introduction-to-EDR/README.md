# TryHackMe: Introduction to EDR

## Room Summary

This room provides a practical overview of Endpoint Detection and Response (EDR) solutions, detailing how modern security teams monitor endpoint activities, detect advanced malicious behaviors beyond traditional antivirus capabilities, investigate host-level telemetry, and execute real-time incident containment.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Introduction to EDR |
| Difficulty | Easy |
| Topic | EDR Systems, Endpoint Security, Telemetry Analysis, Behavioral Detection, Containment |
| Status | Completed |

## Skills Practiced

- Differentiating between Traditional Antivirus (AV) and Endpoint Detection and Response (EDR) platforms
- Analyzing host-level telemetry, including process trees, registry changes, memory modifications, and network sockets
- Detecting signature-less, fileless, and living-off-the-land (LotL) attack techniques
- Utilizing EDR console features for device isolation, process termination, and file quarantine
- Correlating endpoint alerts with threat intelligence frameworks like MITRE ATT&CK

## Hands-On & Command Reference

### Endpoint Telemetry & Process Investigation (CLI Alternatives)

```powershell
# Query Sysmon Process Creation events (Event ID 1) with command-line arguments
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; Id=1} | 
    Select-Object TimeCreated, @{N='Process';E={$_.Properties[4].Value}}, @{N='CommandLine';E={$_.Properties[10].Value}} -First 10

# Inspect active network connections mapped to running process IDs (Sysmon Event ID 3)
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; Id=3} | 
    Select-Object TimeCreated, @{N='SourceIp';E={$_.Properties[9].Value}}, @{N='DestinationIp';E={$_.Properties[14].Value}}, @{N='DestinationPort';E={$_.Properties[16].Value}} -First 10

```

### Live Host Response & Containment Simulation

```powershell
# Terminate suspicious parent/child process by PID via PowerShell
Stop-Process -Id <PID> -Force

# Isolate host from local network (Simulated local firewall rule blocking outbound traffic)
New-NetFirewallRule -DisplayName "EDR Isolation Rule" -Direction Outbound -Action Block -Profile Any

```

## Tools and Platforms Learned

* TryHackMe
* EDR Systems (Generic EDR / CrowdStrike / SentinelOne / Microsoft Defender for Endpoint)
* Sysmon / Windows Event Log Analysis
* PowerShell / Command-Line Incident Response Utilities

## Key Takeaways

* **Beyond Signature Detection:** Traditional AV relies primarily on file signatures, whereas EDR continuously monitors behavioral telemetry to detect zero-day and fileless attacks.
* **Deep Visibility:** EDR records host-level events (process creation, DLL loading, registry edits, network connections), providing full process tree context during investigations.
* **Rapid Response Capability:** Integrated response capabilities allow analysts to isolate compromised hosts from the network instantly and terminate malicious processes remotely.

## Defensive Learning

* Ensure host logging coverage is complete by deploying EDR agents across all enterprise endpoints, including servers and cloud workloads.
* Establish alert thresholds and automated response rules for high-confidence detections (e.g., automated network isolation upon LSASS memory dumping).
* Regularly review and update EDR behavioral detection rules against modern MITRE ATT&CK techniques.

```

```
