# Technical Architecture

## Technology

- Next.js
- React
- TypeScript
- Tailwind CSS
- Node.js
- Next.js Route Handlers
- Prisma
- PostgreSQL
- Zod
- bcryptjs
- Lucide React
- pnpm

## Layers

**Frontend:** Next.js App Router, React, TypeScript, Tailwind CSS, responsive components and accessible UI states.

**Backend:** Next.js Route Handlers, TypeScript service modules and centralized API/error helpers.

**Database:** PostgreSQL through Prisma when configured.

**Local mode:** Supported local flows can use a process-local mock store.

**APIs:** Internal REST-style `/api/*` endpoints.

**Payment:** Simulated INR payment; no external payment processor.

**Shopping advisor:** Deterministic, allowlisted, read-only tools.
