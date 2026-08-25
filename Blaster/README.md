# TryHackMe: Blaster

## Room Summary

This room provides a hands-on introduction to Windows target reconnaissance, web application enumeration, remote desktop protocol (RDP) credential brute-forcing, local privilege escalation using flawed executable binaries, and persistence mechanisms. It also explores host and network log artifacts from a SOC analyst and defensive security perspective.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Blaster |
| Difficulty | Easy / Medium |
| Topic | Windows Exploitation, Web Reconnaissance, RDP Access, Privilege Escalation |
| Status | Completed |

## Skills Practiced

- Conducting targeted web service enumeration and directory discovery
- Identifying potential credential clues and user vectors
- Understanding Remote Desktop Protocol (RDP) credential access mechanisms
- Analyzing low-privilege Windows user permissions
- Performing Windows local privilege escalation to `NT AUTHORITY\SYSTEM`
- Examining post-exploitation persistence concepts
- Analyzing event logs and network signatures for SOC detection
- Documenting offensive findings to improve defensive security posture

## Tools and Platforms Learned

- TryHackMe
- Nmap
- Gobuster / Directory Enumeration Concepts
- RDP / xfreerdp / Remote Desktop Utilities
- Windows Command Line & System Utilities
- Metasploit Framework (Persistence Concepts)
- Windows Event Logs (Event ID 4624, 4625, 4688)

## Key Takeaways

- Thorough web enumeration often reveals initial entry paths or user context.
- Exposed remote access protocols like RDP must be protected with strong authentication policies.
- Gaining initial user access is only the first step in host security analysis.
- Unquoted service paths and misconfigured local executables lead to privilege escalation.
- Post-exploitation actions leave distinct traces in host registries and event logs.
- Effective defense requires correlating web logs, authentication events, and process creation logs.

## Defensive Learning

- Web applications should avoid leaving user hints or default credentials in comments or pages.
- Account lockout policies should be configured to prevent RDP brute-force attempts.
- Multi-Factor Authentication (MFA) should be enforced on external-facing access protocols.
- Restrict write permissions on administrative applications and system directories.
- Monitor Windows Security Event IDs `4625` (Failed Logon) and `4624` (Successful Logon).
- Deploy EDR tools to detect anomalous process creation originating from web services or remote logins.
- Audit startup registry keys (`HKLM\Software\Microsoft\Windows\CurrentVersion\Run`) for unauthorized persistence artifacts.

## Hashnode Blog Link
[https://cybersecurity-learning.hashnode.dev/tryhackme-blaster-beginner-friendly-learning-guide](https://cybersecurity-learning.hashnode.dev/tryhackme-blaster-beginner-friendly-learning-guide)
