# TryHackMe: Broken Access Control

## Room Summary

This room covers the OWASP Top 10 #1 vulnerability: Broken Access Control. It explores fundamental access control models (DAC, MAC, RBAC, ABAC), the difference between authentication and authorization, HTTP traffic interception using Burp Suite Proxy, parameter tampering, vertical and horizontal privilege escalation, and developer mitigation strategies.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Broken Access Control |
| Difficulty | Easy |
| Topic | Web Security, OWASP Top 10, Authorization Flaws, Burp Suite |
| Status | Completed |

## Skills Practiced

- Distinguishing between Authentication (AuthN) and Authorization (AuthZ)
- Understanding Access Control Models (DAC, MAC, RBAC, ABAC)
- Intercepting and analyzing HTTP requests using Burp Suite Proxy
- Identifying client-side parameter manipulation vulnerabilities
- Executing vertical privilege escalation to gain administrative access
- Analyzing IDOR and horizontal privilege escalation concepts
- Evaluating server-side vs. client-side authorization architecture
- Documenting remediation strategies based on the Principle of Least Privilege

## Tools and Platforms Learned

- TryHackMe
- Burp Suite Proxy
- Browser Proxy Configurations (FoxyProxy)
- Web Application Security Frameworks
- OWASP Top 10 Guidelines

## Key Takeaways

- Broken Access Control is an authorization issue, not an authentication issue.
- Client-side checks and hidden parameters must never be trusted for security decisions.
- Applications must validate user access permissions server-side on every request.
- UI restrictions alone do not secure backend administrative functionality.
- Deny-by-default policies are vital for preventing unauthorized endpoint access.

## Defensive Learning

- Enforce all authorization logic strictly on the server side using centralized middleware.
- Apply the Principle of Least Privilege to user account permissions.
- Implement a Default-Deny posture across all API routes and application paths.
- Log and monitor failed access attempts and abnormal parameter changes in SIEM tools.
- Avoid relying on editable client tokens or parameters (e.g., `is_admin=true`) for authorization.
