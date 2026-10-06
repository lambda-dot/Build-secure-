# Security Controls

## Authentication
- bcrypt for new passwords
- Legacy scrypt verification/upgrade
- Opaque server-side sessions
- HTTP-only + SameSite cookies
- Seven-day expiry
- Logout/expiry invalidation
- SHA-256 token hashes stored server-side

## Authorization
- Server-side role checks
- Ownership checks
- Customer resource scoping
- Vendor resource scoping
- Admin route protection

## Validation
- Zod strict schemas
- Bounded fields
- Numeric constraints
- Enumerations
- HTTPS URL checks
- 1 MB JSON body limit

## Browser/API Protection
- Origin checks for cookie-authenticated mutations
- Rate limiting for sensitive writes
- CSP
- X-Content-Type-Options
- X-Frame-Options
- Referrer Policy
- Permissions Policy
- Production HSTS

## Data Integrity & Privacy
- Server-authoritative checkout prices
- Transactional inventory/order operations
- Relational/unique constraints
- Privacy-aware service filtering
- Verified-purchase review constraints
- Audit records
- Administrator-only MarketShield signals
