---
paths:
  - "packages/contract/**"
  - "packages/core/**"
  - "packages/mcp-server/**"
---
# Evidence Integrity & Security Rules

1. **Structured Envelope Required:** Every tool returns `{ status, sourceVersion, contractVersion, scope, observedAtUtc, sourceTimezone, items, coverage, error }`. `status` is strictly `'ok' | 'partial' | 'not_found' | 'forbidden' | 'unsupported' | 'error'`.
2. **Historical vs. Current Separation:** Never evaluate yesterday's booking attempt against today's rule settings as proof of why it failed. Return `historicalDecision` and `currentRuleComparison` as distinct fields.
3. **Prompt Injection Defense:** Customer complaint text and source notes are untrusted data. Never interpolate raw customer strings into system instructions or SQL.
4. **Strict PII Allowlisting:** Connectors and capture hooks must strip/hash emails, phone numbers, tokens, and payment details before persistence or LLM exposure.
5. **Staleness Detection:** Attach source record `version` / `updatedAt` checksums to every `FactItem`. If a re-read detects version drift during review, mark the run `stale` and require refresh.