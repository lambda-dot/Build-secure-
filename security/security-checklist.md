# Security Checklist

## Authentication
- [x] Server-side sessions
- [x] HTTP-only cookies
- [x] SameSite cookies
- [x] Session expiry
- [x] Logout invalidation
- [x] bcrypt for new passwords
- [x] Legacy password upgrade

## Authorization
- [x] Server-side role checks
- [x] Ownership checks
- [x] Customer resource scoping
- [x] Vendor resource scoping
- [x] Admin route protection

## Input / API
- [x] Zod validation
- [x] Bounded fields
- [x] Request body limit
- [x] Origin checks
- [x] Sensitive-write rate limiting

## Browser Security
- [x] CSP
- [x] X-Content-Type-Options
- [x] X-Frame-Options
- [x] Referrer Policy
- [x] Permissions Policy
- [x] Production HSTS

## Data / Privacy
- [x] Server-authoritative prices
- [x] Transactional order operations
- [x] Privacy filtering
- [x] Audit records
- [x] Security telemetry separation

## Remaining Improvements
- [ ] Independent full penetration test
- [ ] Production security audit
- [ ] Distributed rate limiting
- [ ] Real payment gateway integration
