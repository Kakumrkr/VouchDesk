---
name: add-eval-case
description: Author or update a deterministic evaluation fixture and test assertion for a VouchDesk case (C01-C20) from docs/CASE-LEDGER.md.
---
# Add Evaluation Fixture Workflow

When asked to create or update an evaluation fixture for a case ID (e.g., `C01`–`C20`):

1. Read the case specification in `docs/CASE-LEDGER.md` and the current Zod schemas in `packages/contract`.
2. Create an independently authored fixture under `evals/fixtures/<case-id>.json` containing:
   - `caseId`, `title`, and `category`
   - `trustedContext` (`workspaceId`, `operatorId`, `allowedCustomerId`)
   - `complaintInput` (including timezone/locale context)
   - `mockSourceState` (account, booking, operation history, decision/policy records, and connector `CoverageManifest`—including intentional gaps, conflicts, clock skew, or prompt-injection strings where specified)
   - `expectedFactGraph` (exact `verdict`, `disposition`, required `factIds`, required `coverageGaps`, and `prohibitedClaims` strings/patterns)
3. Add or update the corresponding Vitest assertion in `evals/suite.test.ts` verifying both the deterministic engine (`@vouchdesk/core`) and MCP gateway (`@vouchdesk/mcp`) enforce authorization and produce the expected `FactGraph`.
4. Run `pnpm test:eval` and confirm the test passes without relaxing any schema constraint.