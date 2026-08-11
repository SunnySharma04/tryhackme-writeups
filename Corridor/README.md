# TryHackMe: Corridor

## Room Summary

This room introduces IDOR, which stands for Insecure Direct Object Reference. It explains how URL endpoints, object references, and hash-like identifiers can become security risks when proper server-side authorization checks are missing.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Corridor |
| Difficulty | Easy |
| Topic | IDOR, Broken Access Control, Web Security |
| Status | Completed |

## Skills Practiced

- Understanding IDOR concepts
- Learning broken access control basics
- Understanding object references
- Analyzing URL endpoints conceptually
- Understanding why hidden URLs are not enough for security
- Learning server-side authorization importance
- Understanding secure access control practices
- Connecting IDOR with OWASP Broken Access Control
- Developing defensive web security awareness

## Tools and Platforms Learned

- TryHackMe
- IDOR concepts
- Broken Access Control concepts
- Web application security concepts
- Access control concepts
- Authorization concepts
- OWASP Access Control concepts

## Key Takeaways

- IDOR stands for Insecure Direct Object Reference.
- IDOR is a type of broken access control vulnerability.
- Object references can appear in URLs, APIs, files, or parameters.
- Complex-looking or hash-like values do not replace proper authorization.
- Hidden pages are not automatically secure.
- Server-side access control is essential.
- Users should only access resources they are authorized to access.
- APIs must enforce authorization on every sensitive request.
- Security should not depend only on obscurity.
- IDOR should only be tested in authorized environments.

## Defensive Learning

- Applications should enforce authorization on the server side.
- Object ownership should be verified before returning sensitive resources.
- Hidden URLs should not be treated as security controls.
- Role-based access control should be implemented properly.
- Access should be denied by default unless explicitly allowed.
- Suspicious access attempts should be logged.
- APIs should validate authorization for every sensitive request.
- SOC teams can monitor unusual access patterns and repeated object reference attempts.
- Developers should test access control logic carefully.
- Broken access control issues can lead to serious data exposure if not fixed.

## Full Blog

Hashnode Blog: https://cybersecurity-learning.hashnode.dev/tryhackme-corridor-beginner-friendly-learning-guide
