# Threat Model

| Threat | Defense |
|---|---|
| SQL Injection | Parameterized/ORM database access |
| XSS | Output controls and CSP/security headers |
| CSRF | SameSite cookies and Origin checks |
| Broken Access Control | Server-side authorization |
| IDOR | Ownership checks |
| Mass Assignment | Strict validated fields |
| Brute Force | Rate limiting and authentication controls |
| Session Theft | HTTP-only/SameSite server-side sessions |
| Malicious Uploads | Validation and safe-storage requirements |
| Price Manipulation | Server-authoritative pricing |
| Privilege Escalation | Role enforcement |
| Race Conditions | Transactional operations |

## Tenant Isolation

```text
Vendor A → Vendor A resources   ALLOW
Vendor A → Vendor B resources   DENY
Customer A → own orders         ALLOW
Customer A → another's orders   DENY
Customer → Admin endpoints      DENY
Vendor → Admin endpoints        DENY
```

Client-supplied roles, prices, totals and ownership claims are not treated as authoritative.
