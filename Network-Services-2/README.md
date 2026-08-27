# TryHackMe: Network Services 2

## Room Summary

This room covers advanced network service enumeration and exploitation focusing on NFS (Network File System), SMTP (Simple Mail Transfer Protocol), and MySQL database servers. It explores misconfigurations such as NFS root-squashing flaws, SMTP user enumeration via VRFY, and remote database credential access.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Network Services 2 |
| Difficulty | Easy / Medium |
| Topic | Infrastructure Security, NFS, SMTP, MySQL, Privilege Escalation |
| Status | Completed |

## Skills Practiced

- Enumerating NFS shares using `showmount` and Nmap RPC scripts
- Exploiting `no_root_squash` misconfigurations to escalate local privileges to root
- Enumerating valid system accounts using SMTP command verbs (`VRFY`, `EXPN`)
- Conducting credential attacks using enumerated user lists
- Logging into remote MySQL databases and extracting structured records
- Auditing service configurations to prevent protocol-level abuse

## Tools and Platforms Learned

- TryHackMe
- Nmap (RPC scripts, MySQL scripts)
- Showmount / NFS Client Tools
- SMTP User Enum / Telnet / Netcat
- MySQL Command-Line Client

## Key Takeaways

- NFS `no_root_squash` configurations permit clients to create SUID root binaries, yielding local root access.
- SMTP user verification commands (`VRFY`) leak valid username lists without triggering lockouts.
- Databases must remain bound to localhost or isolated internal subnets to block external access.
- Service hardening is as crucial as maintaining software patch levels.

## Defensive Learning

- Always enable `root_squash` on NFS exported directories.
- Disable `VRFY` and `EXPN` in mail transport agent settings (e.g., Postfix/Sendmail).
- Bind MySQL and other internal database services strictly to `127.0.0.1`.
- Monitor host system logs for unauthorized mount activity or unusual SUID file creation.
