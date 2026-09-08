# TryHackMe: CyberChef: The Basics

## Room Summary

This room provides a practical introduction to CyberChef, the "Cyber Swiss Army Knife" developed by GCHQ. It covers essential operations for data manipulation, encoding/decoding, encryption/decryption, hashing, extractors, and crafting automated multi-step processing pipelines (recipes).

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | CyberChef: The Basics |
| Difficulty | Very Easy / Info |
| Topic | CyberChef, Data Transformation, Encoding, Decoding, Cryptography, Deobfuscation |
| Status | Completed |

## Skills Practiced

- Navigating the CyberChef interface (Input, Output, Operations, Recipe pipeline)
- Performing multi-stage data encoding and decoding (Base64, Hex, URL encoding, ROT13)
- Extracting artifacts from obfuscated text using built-in extractors (IPs, URLs, Email addresses)
- Utilizing cryptographic operations for hashing (MD5, SHA-256) and basic symmetric operations (XOR)
- Automating repetitive deobfuscation tasks using recipe chains, control flow, and Magic operation

## Hands-On & Command Reference

### Common CyberChef Recipe Operations

```text
# Base64 Decoding Pipeline
From Base64 -> Render Image / Save Output

# Deobfuscating XOR-encoded Payload
From Hex -> XOR (Key: 'THM') -> From Base64

# Extracting Network Artifacts from Raw Logs/Dumps
Extract IP addresses -> Extract URLs -> Unique

```

### CLI Alternatives for CyberChef Operations (Linux/Bash)

```bash
# Base64 decode string
echo "U2VjdXJpdHlPcHMgIQ==" | base64 -d

# Convert Hex to ASCII
echo "5472794861636b4d65" | xxd -r -p

# Generate SHA-256 hash
echo -n "password123" | sha256sum

# Extract IPv4 addresses using grep Regex
grep -E -o '(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)' input.txt

```

## Tools and Platforms Learned

* TryHackMe
* CyberChef (Web App / Offline Instance)
* Linux CLI Data Utilities (`base64`, `xxd`, `sha256sum`, `grep`, `awk`)

## Key Takeaways

* **Pipeline Power:** CyberChef allows complex, multi-layered deobfuscation to be executed sequentially through drag-and-drop operations without writing custom scripts.
* **Automated Detection:** The **Magic** operation analyzes data patterns to automatically detect and reverse common encodings/encryptions when the exact scheme is unknown.
* **SOC Efficiency:** Using regex extractors (`Extract IP addresses`, `Extract URLs`) drastically speeds up IOC extraction during alert triage and phishing analysis.

## Defensive Learning

* Leverage CyberChef recipes to quickly decode obfuscated PowerShell scripts or malicious email headers during initial phishing analysis.
* Use offline/self-hosted CyberChef instances when analyzing sensitive enterprise artifacts or proprietary code to prevent third-party data exposure.
* Standardize common deobfuscation recipes across your SOC team to ensure fast, repeatable analysis of recurring malware obfuscation techniques.

```

```
