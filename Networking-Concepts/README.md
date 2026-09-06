# TryHackMe: Networking Concepts

## Room Summary

This room provides a foundational overview of core networking principles, covering essential topics such as IP addressing, subnets, MAC addresses, routing fundamentals, the OSI & TCP/IP models, and key network protocols (DHCP, DNS, ARP, ICMP).

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Networking Concepts |
| Difficulty | Very Easy / Info |
| Topic | Networking Fundamentals, OSI Model, TCP/IP, IP Addressing, Routing |
| Status | Completed |

## Skills Practiced

- Differentiating between IPv4/IPv6 addressing models, private vs. public IP ranges, and CIDR notation
- Mapping protocols and network functions across the OSI 7-Layer and TCP/IP 4-Layer models
- Analyzing Layer 2 (MAC addressing, ARP) vs. Layer 3 (IP addressing, ICMP, Routing) communication
- Inspecting DNS resolution workflows and DHCP dynamic address allocation mechanics
- Conducting basic network troubleshooting and path analysis using CLI utilities (`ping`, `traceroute`, `arp`, `nslookup`)

## Hands-On & Command Reference

### IP Configuration & Interface Inspection

```bash
# Display IP address configuration and network interface states (Linux)
ip addr show

# View default gateway and routing table entries (Linux)
ip route

# Inspect Windows network adapter configuration
ipconfig /all

```

### Protocol Analysis & Resolution (DNS, ARP, ICMP)

```bash
# Query DNS A and MX records for a target domain
nslookup tryhackme.com
dig tryhackme.com ANY

# Inspect local Address Resolution Protocol (ARP) cache table
arp -a

# Test end-to-end host reachability via ICMP echo requests
ping -c 4 8.8.8.8

```

### Route Tracing & Path Diagnostics

```bash
# Trace network path and identify intermediate routers/hops (Linux)
traceroute tryhackme.com

# Trace network route using Windows Command Prompt
tracert tryhackme.com

```

## Tools and Platforms Learned

* TryHackMe
* Network Inspection Tools (`ip`, `ipconfig`, `arp`)
* Name Resolution Utilities (`nslookup`, `dig`)
* Path Diagnostics Tools (`ping`, `traceroute` / `tracert`)

## Key Takeaways

* **Layered Models:** The **OSI Model** (7 layers) provides a conceptual framework for network communication, while the **TCP/IP Model** (4 layers) maps directly to practical Internet protocol implementations.
* **Addressing Boundaries:** **MAC addresses** handle local hardware framing on Layer 2 (Data Link), while **IP addresses** facilitate global logical routing on Layer 3 (Network).
* **Core Infrastructure Protocols:** **ARP** maps IP addresses to MAC addresses; **DNS** translates domain names to IP addresses; **DHCP** automates dynamic IP distribution.

## Defensive Learning

* Audit ARP tables (`arp -a`) periodically to identify potential **ARP Poisoning / Man-in-the-Middle (MitM)** attacks.
* Implement DNS security extensions (**DNSSEC**) and DNS monitoring to detect domain spoofing, DNS tunneling, and unauthorized external exfiltration channels.
* Enforce network segmentation and VLAN boundaries to limit broadcast domains and restrict lateral movement across internal subnets.

```

```
