# TryHackMe: Intro to LAN

## Room Summary

This room covers fundamental Local Area Network (LAN) principles, physical and logical network topologies, IPv4 subnetting logic, Address Resolution Protocol (ARP) address mapping, and Dynamic Host Configuration Protocol (DHCP) allocation workflows.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Intro to LAN |
| Difficulty | Easy |
| Topic | Network Topologies, Subnetting, ARP, DHCP |
| Status | Completed |

## Skills Practiced

- Differentiating physical topologies (Star, Bus, Ring, Mesh) and logical traffic paths
- Calculating IPv4 subnet boundaries, host ranges, and `/24` CIDR bitmasks
- Inspecting Layer 2 MAC address resolution mechanics via ARP requests and replies
- Tracing the 4-step DHCP **DORA** sequence (Discover, Offer, Request, Acknowledge)
- Executing network interface and ARP table inspection commands on Linux and Windows systems

## Hands-On & Command Reference

### Linux & Windows Network Inspection Commands

```bash
# View active Network Interfaces and IP addressing (Linux)
ip addr show
ifconfig

# Display local ARP cache table (Linux & Windows)
arp -a

# Send targeted ARP requests to verify local IP-to-MAC resolution (Linux)
arping -I eth0 192.168.1.1

# Query active DHCP client lease details (Linux)
dhclient -v eth0

# Release and Renew DHCP IP leases (Windows Command Prompt)
ipconfig /release
ipconfig /renew
ipconfig /all

```

### Packet Analysis & ARP Inspection Syntax

```bash
# Capture raw ARP traffic on interface eth0 using tcpdump
sudo tcpdump -i eth0 -n arp

# Capture DHCP DORA traffic (UDP ports 67 and 68)
sudo tcpdump -i eth0 -n "udp port 67 or udp port 68"

# Filter ARP traffic in Wireshark
arp.opcode == 1  # ARP Request
arp.opcode == 2  # ARP Reply

```

## Tools and Platforms Learned

* TryHackMe
* Linux Networking CLI (`ip`, `arp`, `arping`, `dhclient`)
* Windows Networking CLI (`ipconfig`, `arp`)
* Packet Analyzers (`tcpdump`, Wireshark)

## Key Takeaways

* Star topology is the enterprise standard due to port isolation and centralized management via switches.
* ARP bridges Layer 3 IP addressing to Layer 2 MAC addresses through local unauthenticated broadcasts.
* DHCP automates network client bootstrapping using the 4-step broadcast/unicast **DORA** process.

## Defensive Learning

* Detect ARP cache poisoning and Man-in-the-Middle (MitM) attacks by monitoring duplicate MAC bindings.
* Enable Dynamic ARP Inspection (DAI) and DHCP Snooping on switches to block rogue DHCP servers.
* Use subnetting and VLAN boundaries to isolate critical internal assets from general user workstations.

```

```
