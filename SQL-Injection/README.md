# TryHackMe: SQL Injection

## Room Summary

This room introduces SQL Injection as a web application security vulnerability. It explains databases, SQL basics, different types of SQL Injection, authentication bypass concepts, blind SQL Injection, out-of-band SQL Injection, and remediation techniques.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | SQL Injection |
| Difficulty | Medium |
| Topic | SQL Injection, Web Security, Database Security |
| Status | Completed |

## Skills Practiced

- Understanding database fundamentals
- Learning SQL basics
- Understanding SQL Injection concepts
- Learning in-band SQL Injection
- Understanding blind SQL Injection
- Learning boolean-based blind SQLi concepts
- Learning time-based blind SQLi concepts
- Understanding out-of-band SQLi
- Understanding authentication security risks
- Learning SQL Injection remediation techniques
- Developing secure coding awareness

## Tools and Platforms Learned

- TryHackMe
- SQL concepts
- Database security concepts
- Web application security concepts
- OWASP concepts
- Secure coding concepts

## Key Takeaways

- SQL Injection happens when user input affects database query logic.
- Databases store important application data.
- SQL is used to communicate with relational databases.
- In-band SQLi returns results through the same application channel.
- Blind SQLi requires observing application behavior indirectly.
- Boolean-based blind SQLi relies on true or false behavior.
- Time-based blind SQLi relies on response delays.
- Out-of-band SQLi uses a separate communication channel.
- Authentication systems must be protected from injection risks.
- Parameterized queries are one of the strongest defenses against SQL Injection.
- Least privilege reduces the impact of database compromise.
- Safe error handling helps prevent unnecessary information exposure.

## Defensive Learning

- User input should never be trusted blindly.
- Developers should use parameterized queries.
- Applications should validate input properly.
- Database users should follow the least privilege principle.
- Detailed database errors should not be exposed to users.
- Web application logs should be monitored for suspicious request patterns.
- WAF alerts can help detect possible SQL Injection attempts.
- Secure coding practices should be followed from the beginning.
- SQL Injection prevention requires both development and defensive monitoring.

## Full Blog

Hashnode Blog: https://cybersecurity-learning.hashnode.dev/tryhackme-sql-injection-beginner-friendly-learning-guide
