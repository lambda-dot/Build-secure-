# Security Architecture

```text
                    Browser
                       │
                       ▼
                Next.js / React
                       │
                       ▼
                Route Handlers
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
   Origin Check   Body Limit      Zod Validation
        └──────────────┼──────────────┘
                       ▼
              Session Authentication
                       ▼
              Role / Ownership Checks
                       ▼
                  Rate Limiting
                       ▼
                 Service Layer
                  │         │
                  ▼         ▼
               Prisma    Mock Store
                  │
                  ▼
              PostgreSQL
                  │
                  ▼
          Audit / Security Signals
```

Authentication uses opaque server-side sessions in HTTP-only, SameSite cookies. Sessions expire after seven days and token hashes are stored server-side.

Authorization is enforced at the route/service boundary. Customer and vendor resources are owner-scoped and administrative routes require ADMIN.

Zod provides strict validation, bounded fields, numeric constraints, enumerations, URL/HTTPS checks and safe defaults. JSON request bodies are capped at 1 MB.

Cookie-authenticated browser mutations check Origin values.

Sensitive writes use a bounded process-local rate limiter.

Security headers include CSP, X-Content-Type-Options, X-Frame-Options, strict Referrer Policy, restrictive Permissions Policy and production HSTS.

Checkout reloads authoritative prices and updates inventory transactionally. Prisma relations and unique constraints protect data integrity.

The report identifies the rate limiter and mock store as process-local and therefore not substitutes for shared production infrastructure in a multi-instance deployment.
