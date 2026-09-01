# TryHackMe: The CIA Triad

## Room Summary

This room explores the core pillars of cybersecurity—Confidentiality, Integrity, and Availability—along with security mindset principles, threat model mappings (the DAD Triad), and control balancing.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | The CIA Triad |
| Difficulty | Easy |
| Topic | Cybersecurity Fundamentals, Security Mindset, Risk Management |
| Status | Completed |

## Skills Practiced

- Categorizing defensive controls under Confidentiality, Integrity, and Availability
- Analyzing real-world attack scenarios and identifying compromised security pillars
- Mapping security controls to the opposing DAD Triad (Disclosure, Alteration, Destruction)
- Evaluating the security mindset to balance strict security controls with operational usability
- Verifying file permissions, cryptographic hashes, and service availability using CLI tools

## Hands-On & Command Reference

### Confidentiality Inspection (Permissions & Encryption Verification)

```bash
# Check file access permissions and ownership on Linux
ls -la /etc/shadow

# Verify active TLS certificate details for a web domain
openssl s_client -connect tryhackme.com:443 -tls1_3

# Inspect current file permissions on Windows Command Prompt
icacls "C:\Sensitive\Financials.txt"

```

### Integrity Verification (Hashing & Signature Inspection)

```bash
# Generate SHA-256 hash to verify data integrity
sha256sum document.pdf

# Compare file checksums against known reference values
md5sum binary_file | grep "expected_hash_string"

# Check GPG signature verification for software packages
gpg --verify package.tar.gz.sig package.tar.gz

```

### Availability & Health Monitoring

```bash
# Test network connectivity and response time
ping -c 4 192.168.1.1

# Monitor active network connections and listening ports
netstat -tulpn

# Inspect system resource usage (CPU, RAM, load average)
top
htop

```

## Tools and Platforms Learned

* TryHackMe
* Cryptographic & Verification Tools (`sha256sum`, `md5sum`, `gpg`, `openssl`)
* System & Access Control Tools (`ls`, `icacls`)
* Network & Health Monitoring Tools (`ping`, `netstat`, `top`, `htop`)

## Key Takeaways

* **Confidentiality:** Protects sensitive data from unauthorized exposure using encryption (AES/TLS) and access control lists.
* **Integrity:** Ensures data accuracy and prevents unauthorized modifications using cryptographic hashing (SHA-256) and digital signatures.
* **Availability:** Guarantees timely and reliable access to assets using hardware redundancy, load balancing, and backups.

## Defensive Learning

* Use the **DAD Triad** (Disclosure, Alteration, Destruction) to categorize and triage incident response events.
* Apply CVSS impact metrics (Confidentiality, Integrity, Availability) to prioritize vulnerability remediation.
* Maintain a balanced security mindset where defensive controls mitigate risk without causing business downtime.

```

```
