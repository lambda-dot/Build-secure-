# 🛡️ MarketHub — Secure Multi-Vendor E-Commerce Marketplace

> 🏆 **Build Secure Hackathon — Winning Project**  
> **Team ALPHA Q | Cybersecurity + E-Commerce**

MarketHub is a secure multi-vendor independent-bookstore marketplace where customers can discover products, manage carts and wishlists, place orders through a simulated checkout, submit verified-purchase reviews, and track orders. Approved vendors manage products and inventory, while administrators review vendor applications, marketplace metrics and security signals.

**This is a public project showcase/security-documentation repository. It intentionally does not publish private source code, credentials, secrets, environment variables or database details.**

## 🌐 Project

**Live application:** https://markethub-jrw8qgc.manus.space/

**GitHub profile:** https://github.com/lambda-dot

**Demo video:** Add your public GitHub Release/video URL here.

---

## 🏆 Hackathon

**ABHEDYA BUILD SECURE HACKATHON**  
Organized by ABHEDYA, the official Cyber Security Forum of VBIT.

### Team ALPHA Q
- **D. Praneeth Kumar** — Back-end Development
- **Riddhi Verma** — Front-end Development
- **S. Sumesh** — Documentation
- **Ranya Mishra** — Research

## 📌 Problem Statement

Build a multi-vendor marketplace where customers can discover products, manage carts, place orders and track purchases, while vendors can manage their own products and orders.

MarketHub applies this requirement to an independent-bookstore marketplace with customer, vendor and administrator workflows and security controls throughout the application architecture.

→ [Problem Statement](docs/problem-statement.md)

## 💡 Solution

MarketHub combines:
- Next.js / React storefront
- Next.js Route Handlers
- TypeScript service-layer business logic
- Prisma / PostgreSQL persistence
- Supported process-local mock mode
- Server-side sessions
- Role and ownership authorization
- Zod validation
- Bounded request bodies
- Origin checks for browser mutations
- Rate limiting for sensitive writes
- Audit events
- Privacy controls
- Browser security headers
- Server-authoritative checkout
- Transactional inventory/order operations
- Deterministic read-only shopping advisor
- MarketShield administrative security signals

## 🧩 Core Features

| Area | Functionality |
|---|---|
| Product Discovery | Search, filtering, pagination, categories, book/product details |
| Customer Accounts | Registration, login, logout, session lookup |
| Cart & Checkout | Customer-scoped cart, server-authoritative prices, inventory checks, simulated INR payment |
| Orders | Customer-scoped orders, cancellation and inventory restoration |
| Addresses | Owner-scoped address management |
| Wishlists | Customer-owned wishlists |
| Reviews | Qualifying verified-purchase reviews |
| Vendor Marketplace | Applications, approval/rejection, suspension, product/inventory management |
| Social Shopping | Friendships, privacy, shared lists, recommendations, reading progress |
| Shopping Advisor | Five allowlisted read-only deterministic tools |
| MarketShield | Administrative burst/cluster security signals |

# 🔐 Security Architecture

```text
Browser
  │
  ▼
Next.js / React UI
  │
  ▼
Next.js Route Handler
  │
  ├── Origin Check
  ├── Body Size Check
  ├── Zod Validation
  ├── Session Authentication
  ├── Role / Ownership Authorization
  └── Rate Limiting
  │
  ▼
Service Layer
  │
  ├── Prisma → PostgreSQL
  └── Supported Mock Store
  │
  ▼
Audit / Security Signals
```

→ [Security Architecture](docs/security-architecture.md)

## 🛡️ Implemented Security Controls

- Server-side session authentication
- HTTP-only, SameSite cookies
- Seven-day session expiry and logout invalidation
- bcrypt for new passwords
- Legacy scrypt verification and upgrade
- Server-side RBAC and ownership checks
- Zod strict schemas and bounded input
- 1 MB JSON request-body limit
- Origin validation for cookie-authenticated browser mutations
- Rate limiting for sensitive writes
- Content Security Policy
- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: DENY`
- Strict Referrer Policy
- Restrictive Permissions Policy
- Production HSTS
- Server-authoritative checkout prices
- Transactional inventory/order operations
- Privacy-aware service-layer filtering
- Audit records
- Administrator-only MarketShield signals

→ [Security Controls](docs/security-controls.md)

## 🏪 Multi-Vendor Isolation

```text
Vendor A → Vendor A products       ✅ ALLOW
Vendor A → Vendor A orders         ✅ ALLOW
Vendor A → Vendor B products       ❌ DENY
Vendor A → Vendor B orders         ❌ DENY
Customer A → Customer A orders     ✅ ALLOW
Customer A → Customer B orders     ❌ DENY
Customer → Admin endpoints         ❌ DENY
Vendor → Admin endpoints           ❌ DENY
```

## 🛒 Secure Checkout

```text
Cart
 ↓
Validate Products & Quantities
 ↓
Reload Authoritative Prices
 ↓
Inventory Check / Update
 ↓
Transactional Order Creation
 ↓
Simulated INR Payment
 ↓
Audit Event
 ↓
Order Confirmation
```

The payment is simulated and does not charge a real payment provider.

## 🤖 Shopping Advisor

The shopping advisor uses five allowlisted, deterministic, read-only tools. It has no direct database access and no write capability.

## 🛡️ MarketShield

MarketShield generates burst/cluster security signals for administrative review. Security telemetry is not returned in normal customer-facing responses.

## 🧪 Security Validation

The final recorded validation included:

| Validation | Result |
|---|---|
| `pnpm test` | **24 tests passed — Pass** |
| `pnpm typecheck` | **Pass** |
| `pnpm build` | **Pass** |
| `pnpm audit` | **Clean after dependency remediation** |
| `pnpm audit --prod` | **Clean after dependency remediation** |
| Prisma schema validation | **Pass** |
| Privacy/access-control regression | **Pass** |
| Telemetry non-disclosure | **Pass** |
| Dynamic penetration test | **Not run** |

Two initial HIGH dependency advisories were remediated: `effect` was upgraded through Prisma 6.19.3 to 3.21.0, and `deepmerge-ts` was constrained to 8.0.2. The final recorded audit reported no known vulnerabilities.

A privacy-scope defect involving friends-only reading completion was fixed and regression-tested.

> No dynamic penetration test was performed because no deployed target and required Docker/Strix prerequisites were supplied.

→ [Testing & Validation](docs/testing-strategy.md)

## ⚠️ Known Limitations

- Payment is simulated.
- Rate limiting is process-local and would require shared infrastructure for multi-instance production.
- The mock store is not a substitute for shared production persistence.
- A full independent penetration test has not been performed.
- A full production security audit remains recommended.

→ [Deployment & Limitations](docs/deployment.md)

## 📚 Documentation

- [Problem Statement](docs/problem-statement.md)
- [Solution](docs/solution.md)
- [Technical Architecture](docs/architecture.md)
- [Security Architecture](docs/security-architecture.md)
- [Threat Model](docs/threat-model.md)
- [Security Controls](docs/security-controls.md)
- [Testing & Validation](docs/testing-strategy.md)
- [Deployment & Limitations](docs/deployment.md)
- [Team Contributions](docs/team.md)
- [Demo Guide](demo/README.md)
- [Security Checklist](security/security-checklist.md)

## 👥 Contributions

### D. Praneeth Kumar — Back-end
Server-side architecture, APIs, database integration, authentication, authorization, business logic, cart, checkout, orders, vendor functionality and security controls.

### Riddhi Verma — Front-end
Next.js/React UI, page design, navigation, reusable components, product browsing, accounts, cart, checkout, orders, reviews, vendor features and front-end integration.

### S. Sumesh — Documentation
Technical documentation, architecture, implementation details, deployment, validation, limitations and final report.

### Ranya Mishra — Research
Technical/security research, relevant technologies, security practices and research support for design decisions.

## 🔗 Links

**Live Project:** https://markethub-jrw8qgc.manus.space/  
**GitHub:** https://github.com/lambda-dot

> **MarketHub treats security as an architectural requirement, not a final presentation slide.**
