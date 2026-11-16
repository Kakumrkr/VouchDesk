# VouchDesk — Forensic Support Investigation Engine & MCP Server

VouchDesk reconstructs why booking changes (reschedule, cancel, new booking) failed or diverged across state-overwriting booking systems, returning a verified **FactGraph**, explicit **CoverageGaps**, and human-reviewed drafts.

## Core Architecture & Stack
- **Monorepo:** Node.js 22 LTS + `pnpm` + Turborepo (`packages/*`, `apps/*`).
- **Language & Validation:** Strict TypeScript + Zod (`@vouchdesk/contract` is the single source of truth).
- **Primary Distribution (MCP-First):** `@vouchdesk/mcp` (Official `@modelcontextprotocol/server` v2, stdio first) exposes 4 read tools so developers/support investigate directly inside Claude Code, Cursor, or VS Code with zero LLM API keys required on our side.
- **Secondary Viewer (`apps/inspector-ui`):** Thin React 19 + Vite + Tailwind SPA served by Hono + PostgreSQL 17 (`Drizzle ORM` + `pg-boss` for durable runs/leases; no Redis). Uses **BYOK Cloud LLM APIs** via Vercel AI SDK (`ai`)—never optimize around local LLMs.
- **Reference Adapter (`packages/adapters/librebooking`):** LibreBooking API + dependency-free PHP 8.2+ `PDO` capture hook (`booking_attempt_logs` on MySQL/MariaDB).

## Non-Negotiable Invariants
1. **Read-Only Source Boundary:** VouchDesk NEVER mutates source booking records, sends customer emails, or processes refunds through v1.0.
2. **Deterministic FactGraph First:** Code constructs `facts[]`, `gaps[]`, `contradictions[]`, and `verdict` from tool outputs. The LLM only renders prose from the verified FactGraph.
3. **Never Conflate Errors/Gaps with Empty History:** Missing capture hooks, expired retention, or timeouts must return explicit `CoverageGap` / `error` envelopes—never `[]`.
4. **Tenant & Object Scope:** `workspaceId`, `operatorId`, and allowed `customerId` come strictly from server session/config—never trusted from model arguments.
5. **Large-DB Performance:** All source queries must be bounded, index-backed, and cursor-paginated (`OFFSET` is forbidden). See `.claude/rules/database-performance.md`.

## Commands (Update as packages are initialized)
- Install: `pnpm install`
- Typecheck: `pnpm typecheck`
- Unit & Contract Tests: `pnpm test:unit`
- Integration & Eval Suite (Testcontainers): `pnpm test:eval`

## Scope Left Open for Claude Code Planning
Before writing application code, inspect `docs/PLAN.md` and `docs/CASE-LEDGER.md`, then use Plan Mode to propose optimal designs for:
- Exact monorepo package boundaries and Drizzle PostgreSQL schema (with RLS).
- The LibreBooking PHP validation hook integration points and transactional outbox/rollback survival strategy.
- Fast keyset pagination cursors and batching strategies for multi-million-row `booking_attempt_logs` and reservation tables.
- Signed, short-lived, RBAC-checked deep links from MCP tool responses into `apps/inspector-ui`.