# TryHackMe: Active Reconnaissance

## Room Summary

This room introduces active reconnaissance and basic network interaction. It explains how tools such as a web browser, ping, traceroute, telnet, and netcat can be used to gather information by directly interacting with a target system in an authorized lab environment.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Active Reconnaissance |
| Difficulty | Easy |
| Topic | Active Reconnaissance, Networking, Service Interaction |
| Status | Completed |

## Skills Practiced

- Understanding active reconnaissance
- Learning the difference between passive and active reconnaissance
- Using a web browser for information gathering concepts
- Understanding browser-based reconnaissance
- Learning ping for basic reachability testing
- Understanding traceroute for network path discovery
- Learning telnet for basic service interaction
- Understanding netcat for network communication
- Connecting reconnaissance activity with defensive monitoring
- Practicing responsible information gathering methodology

## Tools and Platforms Learned

- TryHackMe
- Web Browser
- Browser Developer Tools
- Ping
- Traceroute
- Telnet
- Netcat
- Active reconnaissance concepts
- Network troubleshooting concepts

## Key Takeaways

- Active reconnaissance directly interacts with the target system.
- Active reconnaissance should only be performed with authorization.
- A web browser can reveal useful web application information.
- Browser Developer Tools help inspect requests, responses, headers, cookies, and scripts.
- Ping helps check basic host reachability.
- Lack of ping response does not always mean the host is offline.
- Traceroute helps understand the path network traffic takes.
- Telnet helps demonstrate basic service interaction but is insecure for real administration.
- Netcat is useful for testing and understanding network connections.
- Active reconnaissance can be logged and detected by defensive systems.

## Defensive Learning

- Organizations should monitor unusual reconnaissance activity.
- Repeated ping requests may indicate basic reachability testing.
- Traceroute-like behavior may reveal network path discovery attempts.
- Unexpected service connections should be reviewed.
- Telnet should not be used for secure remote administration.
- Netcat-like activity may indicate suspicious network behavior if seen unexpectedly.
- Public-facing services should expose only necessary information.
- Server banners and verbose responses should be minimized where possible.
- Firewalls, IDS, IPS, and SIEM tools can help detect active reconnaissance.
- Active reconnaissance knowledge helps defenders understand what attackers may observe.

## Full Blog

Hashnode Blog: https://cybersecurity-learning.hashnode.dev/tryhackme-active-reconnaissance-beginner-friendly-learning-guide
