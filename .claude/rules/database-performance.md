---
paths:
  - "packages/adapters/**"
  - "packages/core/**"
  - "**/migrations/**"
  - "**/*.sql"
---
# Large-Database Performance & Query Guardrails

VouchDesk must stay fast (<200ms per tool read, <5s p95 investigation) even when connected to booking databases with tens of millions of historical reservations and attempt logs:

1. **Zero `OFFSET` Pagination:** Always use composite keyset/cursor pagination `(occurred_at, event_id)` or `(created_at, reservation_id)` encoded as opaque base64 cursors.
2. **Mandatory Time-Window Bounds:** `getOperationHistory` must enforce a bounded time window (default 30 days, hard cap 90 days) and hard page size (`limit <= 100`) so queries always hit partition/index ranges.
3. **Covering Composite Indexes:** Every query against `booking_attempt_logs` or source reservation tables must lead with `(workspace_id, source_instance, ...)` followed by lookup key (`booking_ref` or `actor_ref`) and `occurred_at DESC`. Never rely on full-table scans or unindexed JSON column filters (`JSON_EXTRACT` in `WHERE` clauses is forbidden; promote filterable fields to indexed columns).
4. **No N+1 Tool Loops:** Batch related resource, policy version, and conflict lookups in a single bounded query rather than issuing per-event round trips.
5. **Payload & Memory Caps:** Enforce byte ceilings on connector responses (e.g., max 256 KB per tool envelope) and stream/truncate oversized metadata with an explicit `truncated: true` coverage flag.
6. **Table Partitioning Readiness:** Design `booking_attempt_logs` DDL with `occurred_at` in the primary/unique key structure so adopters can apply monthly `RANGE` partitioning on MySQL/MariaDB or PostgreSQL without schema rewrites.