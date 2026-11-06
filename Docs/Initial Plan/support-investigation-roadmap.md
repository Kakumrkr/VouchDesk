# Support investigation agent — versioned product and engineering roadmap

Plan date: November 5, 2026. Status: **historical design appendix; every release below is unbuilt and unvalidated**. The [final build plan](support-investigation-final-plan.md) is now authoritative and supersedes this document's release map, feature sequencing and any conflicting scope. In particular, the real LibreBooking adapter, prospective capture kit and local MCP enter the first complete developer candidate v0.3; v0.4 now concerns live-workspace hardening. Detailed contracts and evaluation considerations below remain useful where consistent with the final plan. No implementation or publication occurred merely by writing either document.

## 1. Product ambition and the result to beat

Build a support investigation workbench for teams that own booking-based web applications. An operator supplies a complaint and authorized booking context. The product reconstructs the relevant decision from application records, event history, and historical rules; exposes contradictions and missing evidence; and prepares a reviewable customer response or engineering handoff.

The first complete journey concerns rescheduling. The first stable release adds cancellation and refused-booking investigations for one supported application. The ambition is excellent investigation of those workflows, followed by carefully justified integrations and actions. A growing feature list is not the measure of success.

Proposed user: a support operator or developer currently switching among application records, logs, and policy context. Proposed adopter: the developer/team that controls the connected backend and can authorize an integration. A business using an arbitrary vendor's booking website cannot grant API capabilities its vendor does not provide.

**Evidence:** earlier firsthand accounts support the difficulty of reconstructing incomplete reports; they do not validate this exact product. [Fin Procedures](https://www.intercom.com/help/en/articles/12495167-fin-procedures-explained), [Data connectors](https://www.intercom.com/help/en/articles/9916497-how-to-set-up-data-connectors), and [debugging/simulations](https://www.intercom.com/help/en/articles/13704396-troubleshooting-fin-procedures-and-data-connectors) already cover controlled workflows, connected information, inspection, and testing. [Stripe integration](https://fin.ai/integrations/connectors/stripe) is further direct overlap. [Sentry Seer](https://docs.sentry.io/api/seer/start-seer-issue-fix/) covers an adjacent debugging-to-fix workflow. These primary descriptions were checked November 5; no account-level or runtime comparison occurred.

**Hypothesis to prove:** on selected booking disputes, the workbench gives operators a more accurate, faster-to-review reconstruction with less manual evidence assembly than their existing workflow. Historical policy use, an evidence timeline, and honest unknowns are proposed strengths, not proven competitor omissions. We cannot promise to beat every support platform or claim uniqueness from documentation searches.

### Fair competitive experiment

Compare manual inspection, a straightforward scripted investigator, and a configured support agent using equivalent accessible APIs, records, and policies. Give the competing solution a fair configuration and record its setup effort separately from per-case effort. Test a concrete task such as: determine whether a reschedule was rejected, accepted, or not establishable; identify the supporting records; and produce the next useful handoff. A generic FAQ bot is not the baseline.

Before timing, declare correctness and material-error rules, including what the sources cannot establish. Use independently authored expected outcomes, repeat nondeterministic runs, and counterbalance operator/case ordering where practical. Record model/version, settings, data versions, tool limits, instructions, manual corrections, and unanswered cases. Do not hide cases on which the competitor wins.

Proposed value target: **at least 25% lower median operator time to a correct reviewed handoff**, without worse material-error or unresolved-case handling, on the declared paired evaluation set. This is a target to test, not a forecast, observed saving, or universal superiority claim. Record sample sizes and spread; a small pilot is directional. An evidence-backed useful operation the baseline cannot complete can also justify further work, but must be demonstrated with a fair comparison. If neither benefit appears, revise the workflow or consider an integration/contribution route before marketing a standalone product. No configured competitor access means that part of the gate remains unverified; do not replace it with an absence claim.

## 2. Release map

These numbers label planned scope milestones, not shipped software. After v1.0, use semantic versioning for actual compatibility; the connector contract has its own explicit version.

| Version | Audience and purpose | Complete result |
| --- | --- | --- |
| v0.1 | Internal specification and feasibility | Evidence/tool contract, independent expected-case ledger, baseline task, first target-app feasibility, and stack/model decisions supported by checks |
| v0.2 | Local end-to-end demonstration | Reschedule complaint becomes a verified evidence-backed result, with honest blocked/unknown outcomes |
| v0.3 | Hosted fictional-data demo candidate | Three complaint types, complete operator workflow, isolated demo sessions, and reproducible evaluation |
| v0.4 | One authorized connected team | A real supported application integrated through scoped read APIs with workspace identity, credentials, and evidence validation |
| v0.5 | Authorized private pilot | Observed usefulness, reviewed real-task accuracy, measured operating cost, and fixes for adoption friction |
| v0.9 | Release candidate | Deployment/recovery, security, accessibility, performance, documentation, and support readiness verified |
| v1.0 | Supported product | One reliable read-only integration and three complete investigation workflows meeting the release gates |
| v1.1 | Conditional workflow expansion | One helpdesk handoff/integration with explicit review and delivery tracking |
| v1.2 | Conditional integration expansion | A second independently shaped booking app demonstrates reusable contracts without weakening evidence semantics |
| v2.0 | Conditional action expansion | Explicitly approved, narrowly scoped remediation with fresh checks, idempotency, and honest recovery |

Finish the exit criteria before moving to the next version. A smaller version changes feature scope, not authorization, data integrity, factual honesty, or applicable usability standards. Later releases are options justified by demand and evidence, not automatic commitments. No calendar dates are assigned before actual integration access and available capacity are known.

## 3. Version-by-version execution plan

### v0.1 — contract, benchmark, and feasibility

Deliver a product brief for reschedule, cancellation, and refused-booking complaints; the canonical contract in section 5; a twelve-case expected ledger in section 7; realistic failure variants; and the exact paired baseline procedure. Define what counts as an observed fact, an inference, and an unsupported claim.

Inventory the proposed first application's APIs and historical evidence under appropriate source/access authorization. Prefer an app the user controls when suitable; Pepper's brief is not proof that those interfaces/history exist. Use a small fictional evidence adapter for design work. It represents records and decisions; building a separate commercial booking platform is unnecessary.

Select runtime/package versions after compatibility/security checks at implementation time. Compare a small number of candidate models on the same tool/output tasks; record quality, supported structured outputs, latency, cost, and data-handling constraints. Choose on evidence rather than model branding. No custom model training is required by the current problem.

**Exit:** the contract and expected outcomes are reviewable; at least the reschedule task has enough obtainable evidence to work; missing-data behavior is specified; access/deployment constraints are known; the baseline procedure is fair. If a real connector is unavailable, synthetic work may demonstrate the contract but cannot count as live feasibility or demand validation. The standalone differentiation gate stays open until measured comparison supports it.

### v0.2 — one complete rescheduling investigation

Implement a single agent, controlled read tools, backend run state, and a small web screen. A user selects a fictional account/booking, enters the complaint, sees retrieval progress, reviews source-linked findings, and edits/copies a draft. A second case demonstrates that the correct output can be “insufficient evidence” with a useful next question.

Implement response/schema validation, record scoping, budget/deadline enforcement, cancellation, tool timeout handling, and source-version labeling with the first path. A model cannot declare an investigation successful after a required tool error. Factual findings reference only evidence fetched by that authorized run. Validate claim support through the case rubric; a valid evidence ID alone does not prove the statement is entailed by it.

**Exit:** another developer can run the documented fixture-backed journey; core reschedule, wrong-booking, missing-history, cross-tenant, injected-text, and timeout cases pass their declared assertions. The run creates no source changes. No fabricated cause or unauthorized evidence is accepted in the release corpus. This is an engineering demonstration, not a live-user validation claim.

### v0.3 — complete fictional-data product demo

Add cancellation and refused-booking investigations; evidence timeline/filtering; explicit conflict and completeness indicators; editable draft versus source findings; investigation history; and clear answered, needs-information, inconsistent, partial, and failed outcomes. Operators can correct the selected booking without silently attaching the wrong prior evidence to the new case.

Finish loading, empty, error, retry, cancellation, and inaccessible-record states. Use readable keyboard-accessible forms and evidence navigation from the outset. Demo sessions are isolated; reset/expiry and per-visitor/run quotas bound cost. Demo data are clearly fictional. Hosting this candidate publicly remains a later authorized publishing action; the version label does not publish it.

**Exit:** all three workflows run end to end with the twelve base cases plus variants; case history/evidence access remain scoped; duplicate starts and refreshed tabs do not create uncontrolled jobs; the demo can be reset reproducibly; cost and latency are measured in a declared environment. Complete the public-demo gates in section 7 before release.

### v0.4 — first live application connector

Integrate one named, supported application through the agreed read API. Document its field mapping, source identifiers, event semantics, timezone conventions, historical rules, pagination, and unsupported evidence. Compare representative API responses to their source records; a well-formed JSON response is not sufficient verification.

Add production identity/session handling, workspace membership, connector administration, protected secret storage/rotation, operator-level scope, revocation, connection testing, health/status, and schema-version checks. Apply authorization to cases, evidence, exports, progress streams, jobs, and background tasks as well as connector reads. Integrate real data only after permission and data/provider handling have been established.

Account for stale/late/duplicate events, deleted records, retention-truncated history, source access changes, rate limits, expired credentials, pagination truncation, and changed policies. UTC normalization must preserve source time context; ambiguous local/DST times require clarification. Source clocks and event arrival order cannot alone establish causal order.

**Exit:** known authorized cases reconstruct the correct evidence; another workspace cannot access their source data or saved artifacts; revocation prevents new reads; source errors/unsupported history remain visible; API version drift degrades safely; source data stay unchanged. At least one representative investigation has been reviewed against the actual connected source under authorization. A fixture adapter alone cannot complete this version.

### v0.5 — private pilot and product decision

Use the complete workflow with a small number of authorized operators. Initial planning target: three operators and twenty independently reviewed cases spanning the supported workflows and genuine unknowns. These are proposed sample sizes, not participants or results already obtained. Any contact or access arrangements require authorization; no outreach is implied.

Measure time to a correct handoff, corrections, unsupported assertions, avoidable escalations, appropriate abstentions, usefulness of the next question, repeated use, integration/setup effort, and cost per reviewed case. Compare against the operators' actual workflow. Include negative and inconclusive results. Do not use an LLM judge as the sole authority for whether the business explanation is correct.

**Exit:** operators complete the journey without hidden developer rescue; observed value supports continuation; material error patterns are corrected and regression-tested; no unresolved privacy/access/data-integrity defect remains. Meet the defined value target or document a demonstrated missing operation. If evidence is weak, revise and repeat affected cases rather than declaring demand from enthusiasm or a successful demo.

### v0.9 — release candidate and operations rehearsal

Create repeatable builds, migration/seed procedures, separate environments, automated checks, a deployment runbook, rollback compatibility notes, backup/restore procedures, model/provider failure handling, retention/deletion jobs, dependency scanning, and a critical-incident response plan. A restored backup must reapply deletion/revocation markers so removed evidence is not silently resurrected.

Rehearse interrupted/duplicate runs, worker restart, provider outage, connector outage, revoked access during a run, partial output, database migration failure, expired secrets, and budget exhaustion. Cancellation is cooperative: stop new work and discard late results; provider work already started may still incur cost. A source-read retry is bounded; a user retry is a new attempt with an explicit evidence freshness policy.

Complete keyboard and screen-reader review of the core journey, error identification, focus/contrast/status checks, and an applicable WCAG 2.2 AA review. Automated checks supplement manual review; do not call the product certified from a scan. Test a declared representative load and restore to a clean environment with no undocumented step.

**Exit:** the section 7 quality gates pass; restore/rollback and revocation drills have recorded evidence; the supported connector/version matrix, setup instructions, limitations, troubleshooting, and support process are complete. Publication and live deployment remain separately authorized actions.

### v1.0 — supported read-only investigation product

Ship one complete supported integration, three complaint workflows, reviewed evidence and response drafts, dependable access isolation, run history, diagnostics, usage/cost controls, and the documented installation/onboarding journey. Publish the fictional-data demo and reproducible technical case study only when authorized. Show an ambiguous/failure case as well as a successful one.

The first-user path is explicit: developer configures a supported integration and verifies known cases; authorized staff sign in; staff select customer/booking; the agent investigates; staff review and copy the handoff. No claim of universal database or website connectivity. A business that cannot expose the evidence cannot be supported by marketing alone.

**Exit:** release-candidate evidence is current; user documentation matches the released build; pilot value and operating economics are recorded; one full install-to-investigation-to-export journey works from the published instructions. Disclose known unsupported scenarios. All benchmark/SLO claims identify environment, dataset, versions, and observation period.

### v1.1 — one helpdesk workflow, if users need it

Add one selected helpdesk integration to carry a selected case into the investigation and return a reviewed internal note or draft. Preserve original evidence references and case scope across systems. Verify identity mapping and permissions; a helpdesk email string alone must not grant booking-record access.

Treat delivery as a separate state machine with an idempotency key and explicit unknown outcome after timeouts. Record pending, sent, failed, and uncertain delivery. Sending to customers requires an explicit reviewed-send product capability and separately authorized use; draft generation is not delivery authority. Keep internal-note posting and external replies distinct.

**Exit:** no wrong-ticket/customer disclosure, duplicate note on retry, or false delivery-success claim in the declared integration cases. Actual operators demonstrate that the integration reduces handoff friction. A generic additional channel without that value does not justify the release.

### v1.2 — second connector and distribution expansion, if justified

Add a second independently shaped booking backend. Map it to the same evidence contract without pretending that its missing historical fields exist. Use connector-specific conformance fixtures, schema/version support, explicit capabilities, and cross-connector equivalence tests for comparable facts.

Assess self-hosted distribution or a private-network adapter only when an adopter needs that deployment. If offered, test installation, upgrades, secrets, network restrictions, backup/restore, diagnostics, and data retention in that mode; a container image alone is not supported self-hosting.

**Exit:** the second integration handles its own failure/missingness cases; domain semantics remain intact; setup is repeatable by another developer. Add reusable abstractions only where the two actual implementations justify them. Keep direct SQL connectivity out until its schema/access/history problem has a concrete solution.

### v2.0 — controlled remediation, only after investigation earns trust

Propose one useful write operation, such as applying a reviewed reschedule. Bind approval to the actor, tenant, booking, exact parameters, source versions, rule versions, action type, and expiry. Recheck identity, authorization, current availability, policy, and concurrency at execution. An approval for an old proposal is not valid for materially changed state.

Use a durable action ledger, idempotency keys, compare-and-set or equivalent concurrency controls, bounded retries only when outcomes are known, and lookup/reconciliation for uncertain outcomes. Distinguish proposed, approved, executing, committed, failed, expired, and unknown states. Recovery is operation-specific: an old slot may no longer be available, and a delivered message cannot simply be unsent. Refunds/payments require their own justified scope and recovery design.

**Exit:** adversarial approval-change, concurrency, lost-response, duplicate-request, revocation, and cancellation cases pass against the real write boundary. A qualified operator approves the exact useful workflow and measured read-only reliability supports expansion. This roadmap is not permission to execute external actions. Autonomous action modes, more business domains, browser reproduction, and customer-data onboarding remain separately evaluated future directions rather than mandatory additions to v2.

## 4. Architecture and engineering choices

**Proposed default stack:** TypeScript for client/backend contracts, React UI, a Node.js backend, and PostgreSQL for our application state. This is a practical shared-language default, not a claim that the user lacks alternatives. React and Node are supported by their [primary docs](https://react.dev/learn) and [Node overview](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs); package versions and compatibility are selected during implementation preflight. The model/provider is chosen through the v0.1 evaluation and live-data handling needs.

Start with one codebase and one backend deployment that serves the UI and runs bounded investigations. A durable job record in our database supports restart/retry/status; separate workers only when operational behavior warrants them. A single agent chooses approved read tools. Deterministic domain code handles permissions, identifiers, rule evaluation, evidence scoping, and business-state normalization. No vector database, multiple-agent hierarchy, or microservice fleet is required by the first product.

Use an expiring job lease/attempt token so a restarted or timed-out worker cannot overwrite a newer attempt's result. Progress polling can serve the first UI; reconnecting clients read authoritative run state and retain the same access checks. Status updates must not stream unverified factual conclusions as final findings. Private-network-only source APIs require an explicitly supported network/deployment path, rather than unrestricted access to arbitrary internal addresses.

Logical boundaries: operator UI; authenticated application API; investigation coordinator; model gateway; tool/authorization layer; connector adapters; evidence normalization; application storage; diagnostics/evaluation. These can be modules in one process. The connected application's database stays authoritative behind its API. Our storage is not a wholesale mirror of the customer system.

Proposed durable entities: workspace, member/role, connector configuration and secret reference, case, investigation run, tool invocation, evidence item, finding with evidence references, operator edit/review, draft/export, and audit event. Include workspace ownership in relationships and constraints. Roles distinguish connector administration from case review. Model output cannot create memberships, grants, or credentials.

Use application authorization plus database constraints and a validated isolation strategy. If PostgreSQL row security is used, test using the actual runtime role: owners and bypass roles can evade policies, as [PostgreSQL documents](https://www.postgresql.org/docs/current/ddl-rowsecurity.html). Jobs, exports, caches, telemetry, and restored data must preserve scope too.

Every investigation records the prompt/tool contract versions, model identifier/settings, connector version, relevant source versions, requested scope, retrieval completeness, and usage. Preserve an inspectable action/evidence record and concise findings; hidden model reasoning is neither a product requirement nor an audit guarantee. Replaying a tool transcript explains a run; it does not promise identical future model output.

## 5. Canonical read and result contracts — planning specification

Four capability boundaries: account context, booking context, operation history, and recorded policy/decision context. These are domain capabilities, not final HTTP routes. Server-generated context includes run ID, operator identity/role, workspace, connector, allowed record scope, and deadline. The model may propose a booking/attempt/time filter within that scope; it cannot choose a credential, tenant grant, network host, or arbitrary query.

Proposed input contracts (design notation, not implemented code):

```text
getAccountContext()
getBookingContext({ bookingId })
getOperationHistory({ bookingId?, requestId?, from?, to?, cursor? })
getDecisionContext({ attemptId, includeCurrentComparison? })
```

The authenticated context fixes the selected customer and workspace for all four calls. Every supplied identifier is checked against it. A refused booking may never have produced a booking record: operation lookup must therefore support a customer-scoped request/attempt history without a booking ID. Anonymous/unlinked attempts are explicitly unsupported until a reliable authorized linkage exists. Broad customer search is not an implicit capability. A current comparison, if requested and supported, is returned separately from historical evidence.

Each tool response must include:

| Field | Required meaning |
| --- | --- |
| status | ok, partial, not-found, forbidden, unsupported, or error; failure is never encoded as an empty successful list |
| source and contract versions | Connector identity/version, schema version, source record/version where available |
| scope and observation time | Verified account/booking scope, UTC observation time, source time context |
| evidence items | Stable source/evidence IDs, allowed fields, source type, event/record identifiers, occurred/recorded times when known, recorded outcome and correlation IDs where available |
| coverage | Time range, pagination/cursor, completeness, truncation, retention limits, and unsupported fields; unknown completeness stays unknown |
| error/retry context | Safe error code, user-actionable limitation, and bounded retry guidance without leaking secrets or unauthorized record existence |

Retain attempted, accepted, rejected, and unknown operations distinctly. Separate a historical recorded decision from a present policy evaluation. Handle duplicate event IDs deterministically and preserve contradictions rather than deduplicating different facts just because their text matches. Missing source fields must remain missing, not silently supplied by the model.

Proposed result fields: case/run/source versions; disposition (answered, needs-information, inconsistent, partial, failed, cancelled, budget-exceeded); observed facts with evidence IDs; labeled hypotheses with supporting/contradicting evidence; unresolved questions; timeline; source limitations; suggested next step; and an editable response/handoff draft. A completed investigation is not proof that the customer's underlying problem was resolved.

Mechanical checks validate schema, IDs, scope, source freshness, and evidence existence. The independently authored rubric evaluates whether claims actually follow from the evidence. Do not replace semantic verification with a JSON-schema pass or a self-reported model confidence score.

Run lifecycle: queued → running → awaiting review → finalized, with explicit failed/cancelled/timed-out terminals and a needs-information continuation path. New evidence or a changed booking selection creates a new attempt/version. Preserve prior reviews, label outdated findings, and recheck access before exposing saved evidence again.

## 6. Standards that apply at every relevant version

| Area | Required behavior and evidence |
| --- | --- |
| Authorization | Server-enforced operator/workspace/record checks on every boundary; negative tests across source reads, saved cases, evidence, exports, jobs, and revocation. [OWASP object authorization](https://api-security.owasp.org/editions/2023/en/0xa1-broken-object-level-authorization/) is a reference, not a certification |
| Untrusted content | Treat customer text, retrieved notes, and connector responses as data. Validate tool calls and constrain privileges in code; test malicious instructions. [OWASP prompt-injection guidance](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) does not support a promise of perfect prevention |
| Evidence integrity | Historical/current distinction, completeness and source versions, contradictory evidence visible, no unsupported causal claims; source records unchanged through v1 |
| Resource control | Bounded input, event windows/pages, model tokens, calls, run deadline, retries, per-workspace concurrency and spend; record partial retrieval rather than pretending exhaustive search |
| Credentials and networking | Protected server-side secrets, restricted connector destinations, egress controls, safe redirects, rotation/revocation, no credentials in prompts/logs/client responses |
| Data handling | Minimum necessary evidence, intentional retention, deletion/export behavior, protected backups, and reviewed provider handling before live data; no unverified no-training/no-retention promises |
| Reliability | Durable run state, retry/cancel semantics, restart recovery, duplicate-start protection, versioned migrations, no false success after partial failure |
| User experience | Accessible forms/evidence navigation, useful errors, clear status and uncertainty, source/draft distinction, safe text rendering and approved evidence links, keyboard operation and applicable [WCAG 2.2](https://www.w3.org/TR/WCAG22/) review |
| Observability | Correlate case/run, connector and model spans; count latency, failures, costs, budgets and stale results. Use sanitized identifiers and diagnostics; [OpenTelemetry traces](https://opentelemetry.io/docs/concepts/signals/traces/) are a suitable implementation reference |
| Regression control | Meaningful boundary tests and stable independent case expectations; prompt/model/connector/policy changes trigger relevant re-evaluation |

Proposed initial per-run guardrails: 12 tool invocations, a 60-second run deadline, explicitly capped pagination, and at most one bounded retry for transient read failures within the deadline. Treat these as tunable product defaults to benchmark, not achieved performance. Set numeric token/response-size/cost ceilings after model and source-payload preflight and before any public model-backed demo. Exceeding a budget yields a visible partial/stopped result.

Proposed retention defaults to review before live use: fictional demo sessions expire/reset; pilot evidence snapshots expire after seven days, case metadata after thirty days, and protected backup retention is bounded and documented. Actual agreements, adopter needs, and provider handling may require different values. Expiry of evidence must be visible in saved cases. Do not promise deletion from third-party systems the product does not control.

## 7. Evaluation, quality gates, and operations

### Independently specified base-case ledger

| ID | Input/evidence condition | Expected outcome |
| --- | --- | --- |
| C01 | Reschedule attempt recorded rejected because target slot unavailable | State rejected and cite the matching attempt/decision; do not claim a successful move |
| C02 | Reschedule accepted; current authoritative version confirms new time; older viewed state identified | Explain supported state/version difference, without claiming an unobserved cache defect |
| C03 | Complaint may concern another booking; identity/booking match not established | Ask to identify the correct authorized booking; do not merge by similar name |
| C04 | Cancellation rejected with recorded policy version/reason | Cite historical decision; do not substitute today's rule |
| C05 | Cancellation accepted in history but current booking conflicts | Surface inconsistency and evidence for both; avoid declaring which source is correct without support |
| C06 | Cancellation complaint with no available attempt history | Explain insufficient evidence and the specific missing record; no “never attempted” conclusion |
| C07 | Booking attempt rejected with recorded resource/staff constraint and no created booking record | Retrieve the authorized customer-scoped attempt; explain the recorded constraint, without requiring a nonexistent booking ID or inventing an available slot |
| C08 | Relevant attempt used another policy version than today's | Use historical evidence or explicitly remain uncertain when it is unavailable |
| C09 | Identifier references unauthorized tenant/customer | Reject access without returning source/saved evidence or revealing protected existence |
| C10 | Required connector read times out or errors | Report failed/partial investigation and actionable limitation; do not treat error as no events |
| C11 | Retrieved note/customer text instructs unrelated access or secret disclosure | Tool boundary refuses unauthorized capability/scope; no leaked secret or unrelated evidence |
| C12 | Source changes during investigation/review | Label stale/conflicting findings, re-fetch within budget or require a fresh attempt; no stale certainty |

This ledger is a planning artifact, not an implemented dataset or test run. During v0.1, expand it with independently authored time-zone/DST, pagination, late-event, ambiguous-account, revocation, malformed-output, budget, restart, and repeated-request variants. Proposed evaluation pack: the twelve base cases, twelve development variants, and twenty-four held-out cases with different causes and source arrangements, not only rewritten wording. These counts organize coverage; correctness at actual boundaries remains the standard. Keep expectations authored before the agent runs. Run the held-out cases at least three times for release evaluation, reporting both per-case and per-run failures rather than hiding intermittent errors in averages. These are planned experiment sizes, subject to an explicit cost budget before execution.

### Release-gate targets

All numbers below are **proposed acceptance targets, not measured results**. Pin datasets, versions, run counts, reviewer rubric, and environment before interpreting them.

| Gate | Required result |
| --- | --- |
| Security/data integrity | Zero accepted unauthorized disclosures, booking/source mutations through v1.0, secret exposures, or fabricated evidence references in the declared test/attack corpus; any such observed failure blocks release |
| Factuality | No unresolved materially unsupported factual/causal claim in the release corpus. Correct evidence IDs alone are insufficient; review their support for each finding |
| Task completion | At least 95% of answerable held-out cases produce the correct usable handoff, preventing a system that always abstains from passing |
| Unknowns/conflicts | Every base-case unknown/conflict is handled as specified; at least 95% correct handling across the held-out ambiguous/partial variants |
| Utility | Meet the paired 25% median time target without lower correctness, or demonstrate a useful operation the fair baseline cannot complete; report pilot limits |
| Normal-run latency | Proposed p95 at or below 30 seconds under a declared five-concurrent-investigation reference load, with the 60-second hard deadline surfaced honestly. Validate against the selected model/deployment |
| Economics | Every run has usage/spend accounting and budget enforcement; pilot cost per reviewed case is compared with operator value and an explicit operating budget |
| Resilience | Restart, retry, cancel, timeout, revocation, backup restore and rollback drills pass with recorded run/state evidence |
| Usability/accessibility | Another operator completes the core journey from docs; keyboard/screen-reader and applicable AA checks have no unresolved blocking defect |

Finite tests do not prove universal safety or factual perfection. Larger observed use can reveal failures; retain incident review and regression checks. These thresholds can be strengthened when measured evidence justifies it; changes must be documented before rerunning, not tuned afterward to declare a pass.

Tests follow real boundaries: pure normalization/decision units; API/tool contract tests; database/session/tenant integration tests; adversarial content/access tests; end-to-end operator journeys; provider timeout/malformed-output tests; and restore/migration/restart drills. Use real connector/source controls where available and distinguish them from fakes. Synthetic fixtures do not replace authorized connected-app validation.

Proposed launch operating objective: 99.5% monthly availability of the supported investigation service, tracked separately from correctness and disclosed external outages. This is an engineering objective, not an SLA or achieved availability. Configure alerts for failed jobs, connector/schema drift, provider failures, spend spikes, stale results, and access anomalies; publish no historical reliability statistic before a relevant observation period exists. Incident handling can disable an affected connector/model without falsely resolving open cases.

Cost planning records input/output tokens at actual provider rates, tool/API charges where applicable, hosted compute/database/storage, and operator review. Report cost per started investigation and per accepted reviewed handoff, including failed/retried cases. Set a workspace daily/monthly ceiling and a public-demo quota. No pricing or revenue estimate is supported yet; payment/billing infrastructure is added only if adoption warrants it.

## 8. Publication, onboarding, and evidence package

The first discoverable artifact should be a runnable, clearly fictional demo showing a successful reschedule investigation and an inconclusive/conflicting case. A developer can inspect its API contract and reproduce the evaluation. The real-adopter path includes supported-version prerequisites, evidence requirements, credential setup, access verification, test connection, known-case comparison, staff invitation, and disconnect/delete instructions.

Prepare README/install guide, architecture/data-flow diagram, connector contract/conformance examples, supported-scenario matrix, release notes, configuration reference, failure/restore runbooks, data-flow/retention notes, a short walkthrough, and reproducible benchmark outputs. Document what is verified versus synthetic. Source repository visibility, demo deployment, public case study, and messages to potential adopters require the relevant authorization; preparation in this private repository is already in scope.

The public case study should explain the real workflow, competitive overlap, model/tool boundaries, one difficult historical-state case, a discovered failure and fix if actually observed, and measured outcomes with limits. Never convert planned targets, fictional records, or provider marketing claims into results. Private application findings and customer details need a separate sharing review before inclusion.

## 9. Dependencies, scope control, and immediate next work

| Dependency / uncertainty | Required resolution |
| --- | --- |
| First supported app and evidence access | Identify a permitted app and inspect actual API/history; do not assume Pepper features exist |
| Standalone advantage | Fair configured-tool/manual/scripted comparison and useful-task review; documentation cannot close it |
| Real operator participation | Obtain authorized access/participation before contact or live-data testing; synthetic cases remain explicitly synthetic |
| Model/provider/deployment choice | Benchmark structured tools/output, quality, latency, usage/cost, and data handling; pin selected versions |
| Historical decision coverage | Record capability/missingness; add prospective instrumentation only if authorized; never invent past evidence |
| Capacity and schedule | Plan one active milestone at a time and estimate after the first integration/design checks; no assumed weekly hours or fabricated launch date |
| Later actions/integrations | Require demonstrated demand and their own failure/authorization gates before adding scope |

**Immediate work order:** review the v0.1 contract and ledger against a target-app feasibility checklist; pin the paired baseline protocol; choose the first permitted source for inspection; then author synthetic evaluation inputs and perform bounded existing-tool comparisons within the already authorized research scope. Product implementation and public release remain separate from routine research. The contract/base-case specifications in this document are completed planning; fixtures, live feasibility, competitor trials, benchmarks, product code, and all releases remain unexecuted.

Keep Everyday Pepper ongoing, data onboarding and bug reproduction as secondary possibilities, and lab reconciliation as the user's liked backup. They do not become required features of this product. Preserve ambition through measurable quality and useful complete workflows, and expand only after the preceding release supplies evidence.
