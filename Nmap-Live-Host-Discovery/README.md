# TryHackMe: Nmap Live Host Discovery

## Room Summary

This room introduces Nmap host discovery techniques used to identify active devices before performing detailed network scans.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Nmap Live Host Discovery |
| Difficulty | Easy |
| Topic | Nmap, Host Discovery, Networking |
| Status | Completed |

---

## Skills Practiced

- Understanding host discovery
- Working with subnetworks
- ARP scanning
- ICMP scanning
- TCP SYN Ping
- TCP ACK Ping
- UDP Ping
- Reverse DNS Lookup
- Basic network reconnaissance

---

## Topics Covered

- Introduction to Nmap
- Why Host Discovery Matters
- Subnetworks and CIDR
- Enumerating Targets
- ARP Discovery
- ICMP Discovery
- TCP Discovery
- UDP Discovery
- Reverse DNS Lookup

---

## Key Takeaways

- Host discovery identifies live systems before scanning ports.
- ARP is the fastest discovery method on local networks.
- ICMP probes can identify reachable hosts but may be blocked by firewalls.
- TCP and UDP probes help discover hosts when ICMP is filtered.
- Reverse DNS provides meaningful hostnames for discovered IP addresses.
- Efficient host discovery saves time and reduces unnecessary network traffic.

---

## Defensive Learning

- Limit unnecessary exposure of network services.
- Configure firewalls to control ICMP traffic based on organizational needs.
- Monitor network discovery attempts.
- Review DNS records regularly.
- Keep network devices updated and properly configured.

---

## Tools Used

- Nmap
- Terminal
- TCP/IP Networking Concepts

---

## Full Blog

Hashnode Blog:

https://cybersecurity-learning.hashnode.dev/tryhackme-nmap-live-host-discovery-beginner-friendly-step-by-step-learning-guide
