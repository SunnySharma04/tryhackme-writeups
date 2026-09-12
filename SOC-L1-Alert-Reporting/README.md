# TryHackMe: SOC Level 1 - Alert Reporting

## Room Summary

This room focuses on the critical post-investigation phase of Security Operations Center (SOC) Level 1 workflows: crafting clear, accurate, and actionable incident reports. It details how analysts document triage findings, summarize timeline events, record Indicators of Compromise (IOCs), and provide remediation recommendations for SOC leads, Tier 2/3 responders, and non-technical stakeholders.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | SOC Level 1 - Alert Reporting |
| Difficulty | Easy |
| Topic | SOC Operations, Incident Documentation, Alert Reporting, Executive Summaries |
| Status | Completed |

## Skills Practiced

- Authoring structured, professional incident reports following standardized SOC templates
- Synthesizing complex technical findings into concise Executive Summaries for leadership
- Documenting chronological incident timelines using verified UTC timestamps and log events
- Cataloging and categorizing Indicators of Compromise (IOCs) such as SHA256 hashes, C2 IP addresses, and malicious domains
- Formulating actionable containment, eradication, and post-incident remediation recommendations

## Hands-On & Command Reference

### Timeline Generation & Log Artifact Extraction

```bash
# Extract and format timestamped events for chronologically ordered incident timelines
grep -E 'Failed password|Accepted password' /var/log/auth.log | awk '{print $1, $2, $3, $9, $11}'

# Parse Sysmon Event ID 1 (Process Creation) with UTC timestamps for inclusion in report tables
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; Id=1} | 
    Select-Object @{Name='TimeUTC'; Expression={$_.TimeCreated.ToUniversalTime()}}, 
                  @{Name='Process'; Expression={$_.Properties[4].Value}}, 
                  @{Name='CommandLine'; Expression={$_.Properties[10].Value}} | 
    Export-Csv -Path ./ProcessTimeline.csv -NoTypeInformation

```

### IOC Documentation & Formatting Standard

```text
[Network Artifacts]
External C2 IP: 198.51.100.45 (Port 443 / HTTPS)
Malicious Domain: update-service-check[.]com

[Host Artifacts]
Dropped Payload: update_installer.exe
File Hash (SHA-256): e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
Execution Path: C:\Users\Public\Downloads\

```

## Tools and Platforms Learned

* TryHackMe
* Incident Management & Ticketing Systems (Jira / ServiceNow / Generic ITSM)
* Sysmon / PowerShell Event Export
* Markdown / Text Documentation Workflows

## Key Takeaways

* **Clear Communication:** An investigation is only as effective as its documentation. Clear reporting prevents redundant work during escalation and speeds up incident response.
* **Audience Awareness:** Incident reports must balance technical granularity for Tier 2/3 analysts (process command lines, memory dumps, hashes) with concise summaries for management.
* **Standardized Timelines:** Always normalize timestamps to UTC across all reported log sources to ensure precise chronological accuracy across distributed system logs.

## Defensive Learning

* Standardize organizational incident report templates to guarantee consistent metadata capture across all shift handovers.
* Defensively defang all URLs and IP addresses (e.g., `example[.]com`, `192.168.1[.]1`) in documentation to prevent accidental link clicking in security tools.
* Include clear risk severity levels (Low, Medium, High, Critical) based on asset value and threat impact to prioritize remediation actions.

```

```
