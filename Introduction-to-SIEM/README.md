# TryHackMe: Introduction to SIEM

## Room Summary

This room provides a foundational overview of Security Information and Event Management (SIEM) systems, exploring how security teams collect, correlate, and analyze log data from across an enterprise network to detect, investigate, and respond to threats in real time.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Introduction to SIEM |
| Difficulty | Very Easy / Info |
| Topic | SIEM, Log Management, Security Operations, Threat Detection |
| Status | Completed |

## Skills Practiced

- Understanding the core architecture and operational role of SIEM platforms in SOC environments
- Ingesting, parsing, and normalizing diverse log sources (event logs, network traffic, firewall logs)
- Writing and evaluating correlation rules to identify anomalous patterns and potential security breaches
- Analyzing security alerts and conducting initial incident triage within a SIEM dashboard
- Distinguishing between true positives, false positives, and benign system activity

## Hands-On & Command Reference

### Log Ingestion & Querying Syntax (Splunk / Elastic / Generic SIEM)

```text
# Generic SIEM search for failed authentication attempts from a single IP
sourcetype="winlogbeat" EventCode=4625 | stats count by TargetUserName, IpAddress | where count > 5

# Search for suspicious process executions spawned by command shell
Image="*\\cmd.exe" OR Image="*\\powershell.exe" ParentImage="*\\w3wp.exe"

# Query firewall traffic logs for outbound connections on non-standard ports
action="allowed" direction="outbound" dest_port!=80 dest_port!=443 dest_port!=53

```

### Log File Inspection & CLI Parsing

```bash
# Filter auth log for failed SSH login attempts on Linux
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c | sort -nr

# Inspect Windows Event Log EVTX files using PowerShell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4625} -MaxEvents 20 | Select-Object TimeCreated, Id, Message

```

## Tools and Platforms Learned

* TryHackMe
* SIEM Dashboards & Log Management Engines (Splunk / Elastic Stack / Generic SIEM)
* Log Analytics Utilities (`grep`, `awk`, PowerShell `Get-WinEvent`)

## Key Takeaways

* **Centralized Visibility:** A SIEM aggregates log data across endpoints, servers, firewalls, and network devices, eliminating blind spots across corporate infrastructure.
* **Correlation Rules:** Automated rules evaluate incoming log streams in real time to trigger alerts when specific sequences of events match known adversary behaviors.
* **Alert Triage:** Effective SOC workflows rely on tuned correlation rules to minimize false positives, allowing analysts to quickly isolate and investigate high-fidelity security alerts.

## Defensive Learning

* Continuously tune SIEM correlation rules to account for baseline network activity and reduce analyst alert fatigue.
* Ensure proper NTP/time synchronization across all log sources to maintain accurate event sequencing during forensic timeline creation.
* Ingest logs following the principle of defensive priority: prioritize authentication logs, domain controller logs, and perimeter security logs first.

```

```
