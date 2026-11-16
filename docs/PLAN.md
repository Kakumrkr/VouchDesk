# VouchDesk — Canonical Product & Technical Plan

> **Status:** Planning baseline (v0.1 ready). Supersedes historical drafts in `docs/archive/`.
> **Design Philosophy:** Concrete contracts and safety invariants are locked below; implementation architecture, schema optimizations, and UX details remain open for Claude Code to refine during planning and execution.

## 1. Product Positioning & Open-Source Strategy
VouchDesk is an **open-source, MCP-first forensic support investigation engine** for booking and scheduling applications.

- **The Problem:** Legacy and CRUD booking engines (e.g., LibreBooking, WooCommerce Bookings, custom PHP/Rails schedulers) overwrite state on updates and rarely persist rejected attempts or historical rule versions. When a customer says *"I rescheduled my appointment, why is it still at the old time?"*, frontline AI bots guess and engineers waste hours grepping logs.
- **Our Differentiator:**
  1. **Prospective Audit Capture Hook:** A lightweight, dependency-free sidecar hook (`booking_attempt_logs`) that captures validation rejections, rule versions, and race collisions at the persistence boundary—surviving business transaction rollbacks.
  2. **Deterministic FactGraph Engine:** Code reconstructs verified facts, coverage gaps, and state contradictions *before* any LLM generates prose.
  3. **Zero-Friction Distribution:** Developers connect `@vouchdesk/mcp` to Claude Code, Cursor, or VS Code in minutes with **zero LLM API keys** needed on VouchDesk's side. Teams wanting a standalone browser workflow use `apps/inspector-ui` with **BYOK Cloud LLM APIs** (Claude, OpenAI, Gemini via Vercel AI SDK).

## 2. System Architecture

```mermaid
flowchart LR
    subgraph ClientLayer["Operator / AI Client Layer"]
        MCPClient["Claude Code / VS Code / Cursor"]
        Browser["Inspector UI (React 19 + Vite)"]
    end

    subgraph VouchDesk["VouchDesk Core (TypeScript Monorepo)"]
        MCP["@vouchdesk/mcp (Stdio / Streamable HTTP)"]
        API["Hono Backend + pg-boss Worker"]
        Core["@vouchdesk/core (FactGraph, Gap Detector, PII Redactor)"]
        PG[(PostgreSQL 17: Cases, Runs, Snapshots)]
    end

    subgraph TargetApp["Connected Booking App (e.g. LibreBooking)"]
        Adapter["@vouchdesk/adapter-librebooking"]
        Hook["PHP Capture Hook (PDO)"]
        SourceDB[(MySQL / MariaDB: Reservations + booking_attempt_logs)]
    end

    MCPClient --> MCP
    Browser --> API
    MCP --> Core
    API --> Core
    API <--> PG
    Core --> Adapter
    Adapter --> SourceDB
    Hook --> SourceDB