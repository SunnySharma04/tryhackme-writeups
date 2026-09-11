# TryHackMe: SOC Level 1 - Alert Triage

## Room Summary

This room provides a practical walkthrough of Security Operations Center (SOC) Level 1 alert triage workflows. It covers the initial response lifecycle for incoming security alerts, analyzing security telemetry, validating events, distinguishing True Positives from False Positives, and documenting investigative findings.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | SOC Level 1 - Alert Triage |
| Difficulty | Easy |
| Topic | SOC Operations, Alert Triage, True/False Positives, Incident Response |
| Status | Completed |

## Skills Practiced

- Performing initial triage and categorization of incoming SIEM and EDR security alerts
- Correlating alert metadata (timestamps, hostnames, IP addresses, process command lines) with baseline network behavior
- Differentiating between True Positive (TP), False Positive (FP), and Benign Positive security events
- Investigating common attack vectors including phishing, credential dumping, and suspicious process execution
- Structuring clear, professional incident tickets and escalation notes for Tier 2/3 analysts

## Hands-On & Command Reference

### Investigating Suspicious Process Execution & Parent-Child Relationships

```powershell
# Query process execution logs in Windows Event Viewer (Event ID 4688 / Sysmon Event ID 1)
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; Id=1} | 
    Where-Object {$_.Message -match "powershell.exe" -or $_.Message -match "cmd.exe"} | 
    Select-Object TimeCreated, Id, Message -First 10

```

### Network Artifact Analysis & IP/Domain Reputation Lookup

```bash
# Query active network sockets associated with suspicious process IDs (Linux/Windows)
netstat -ano | grep -E 'ESTABLISHED|SYN_SENT'

# Perform DNS resolution and basic WHOIS lookup on suspicious external domain/IP
nslookup suspicious-domain.com
whois 192.0.2.1

```

### Log Parsing & String Deobfuscation

```bash
# Extract and decode Base64 command strings passed to PowerShell
echo "aXBjb25maWcgL2FsbA==" | base64 -d

# Filter web server access logs for anomalous HTTP status codes and user-agents
grep -E ' 404 | 500 ' /var/log/nginx/access.log | awk '{print $1, $6, $7}' | sort | uniq -c | sort -nr

```

## Tools and Platforms Learned

* TryHackMe
* SIEM Platforms (Splunk / Elastic)
* EDR Telemetry & Event Viewer / Sysmon
* OSINT Threat Intelligence (VirusTotal, AbuseIPDB, Whois)

## Key Takeaways

* **Structured Workflow:** Alert triage must follow a standardized methodology: Verify -> Contextualize -> Determine Severity -> Document/Escalate.
* **Context is Everything:** An alert alone rarely gives the full picture; correlating parent process execution, user context, and network activity is required to confirm malicious intent.
* **Tuning Feedback Loop:** Consistently identified False Positives should be documented and communicated to SOC engineering teams to refine correlation rules and reduce alert fatigue.

## Defensive Learning

* Enforce Sysmon logging (specifically Event ID 1 for Process Creation and Event ID 3 for Network Connection) across endpoints to ensure rich telemetry during triage.
* Standardize incident escalation templates to include Indicators of Compromise (IOCs), host details, user impact, and initial triage steps taken.
* Establish clear operational baselines for standard administrative scripts and tools (e.g., administrative PowerShell usage) to accelerate False Positive identification.

```

```
