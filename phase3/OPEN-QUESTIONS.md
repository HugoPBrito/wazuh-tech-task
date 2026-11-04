# Phase 3: Before-Pilot Integration Checks

I would use this checklist when taking the [service proposal](PHASE3.md) toward a pilot. The three genuine C1-C3 responses are already included in the [evidence record](assets/evidence/EVIDENCE.md); these checks concern deployment integration, not missing assignment captures or a requirement to run model benchmarks now.

## Accepted MVP starting points and future scope

I accepted reuse of existing identity/effective human permissions, ephemeral working conversation context and a provisional 30-day security-audit baseline for the hosted-assistant simulation. The revised product-observability proposal would separately retain admitted application content in protected regional traces, not operational logs. Its proposed 30-day content retention would require its own purpose, disclosure, permission/access and policy review; the security-audit assumption would not approve it. None of these settings establishes a token contract or actual Wazuh/legal policy, and traces would not become persistent model memory.

## Design choices I would start with

| Area | Proposed starting choice |
|---|---|
| Product boundary | An official Wazuh-maintained open-source MCP project with published contracts, documentation and versioned releases. Community operators could choose logging and clients/models, including external providers outside the SaaS offering; the official server would not automatically send application payloads home to Wazuh. Authentication, scoped reads and credential protection would still apply. |
| Hosted deployment | One CPU API/orchestrator application, a private instance of the official read-only MCP server, private GPU serving and regional platform storage for separate TTL/admission state and encrypted product traces. No new broker or trace microservice. |
| Capacity and budgets | Hosted [request limits](PHASE3.md#proposed-request-budgets) and [bounded pilot capacity](PHASE3.md#bounded-pilot-capacity), with shared atomic accounting and fail-closed admission. Common MCP per-tool authentication, permissions, schema, page/rate and minimized-output protections would apply to every instance. |
| Hosted retention/access | Proposed 15-minute working-context/evidence TTL and separate 30-day content traces from admission, with no context/content-trace backups initially. Trace reads/exports would need explicit tenant/content-scoped product-data grants and access auditing, not default developer/operator access. These are not guarantees for independent clients or forks. |
| Trace lifecycle and scope | Persist bounded authenticated admitted input before model/tool work; append used messages, authorized tool context, output, versions, coverage and outcome within existing budgets. Exclude raw HTTP/auth/health bodies, credentials, known secret fields and hidden reasoning; pasted-secret filtering would be best effort, not a nonsensitivity guarantee. Required capture failure would stop/degrade explicitly, without plaintext fallback; an analytics-view outage alone would not block healthy capture. |
| Evaluation and cost | A private hosted-assistant promptfoo comparison and hypothetical SaaS operating budget, separate from comparison expenditure, open-source release work and community inference costs. |

## Before-pilot integration checks

| Priority | What I would confirm with the responsible platform owner | Required deployment evidence |
|---|---|---|
| 1 | Official MCP tool/client compatibility, supported authorized Manager/Indexer routes and the hosted internal read route. | Versioned contracts, exact scoped endpoint resolution, GET-body ingress handling, bounded pagination and native error-envelope behavior. Community use would not imply a new public SaaS endpoint or Cloud OAuth contract. |
| 2 | Actual hosted signed-token/delegation contract and each MCP deployment's caller/backend authentication and effective-user mapping. | Human restrictions enforced at every backend read; no credentials in model/tool responses. Hosted permission revocation invalidates old context and citations, and authorization/state outages fail closed. |
| 3 | Hosted `deployment_region`, infrastructure processor and residency/egress rules. | Regional SaaS inference, state, content traces, offline judges and observability, encrypted storage/transport, approved key/access policies and blocked external processing/telemetry. `eu-central-1` and `eu-west-2` remain alternatives, not approvals; the UK is not EU residency. Community processing/retention choices would follow operators' own policy without weakening MCP server security. |
| 4 | Separate content-retention purpose/disclosure/permission, deletion and credential/audit/product/operator access and backup policy. | Confirm the proposed 15-minute working TTL, separate 30-day trace expiry from admission, provisional 30-day security audit and absence of content backups. Verify deletion/erasure, tenant/content-scoped grants, audited trace access and explicitly authorized privileged investigations. Any later backup/restore must enforce original expiry/deletion. No automatic coding-agent, training or evaluation reuse; evaluation reuse would need approved purpose/permission, minimization and review. No legal/compliance approval is implied. |

## Measurements I would use to tune the pilot

| Priority | Measurement | How I would use it |
|---|---|---|
| 5 | Representative demand, GPU fit/startup/readiness, cancellation, trace volume/storage and cost. | Test one warm replica, maximum two, one active investigation per ready replica, the four-slot fair queue and the two-request tenant ceiling. Validate content storage/encryption/access audit/deletion within the existing hypothetical platform allowance; replace budgeting hypotheses with regional quotes and observed completions. |
| 6 | Human-reviewed task quality, groundedness, citations and false refusals. | Set semantic thresholds after a baseline; hard security assertions remain mandatory independently of quality scores. |
| 7 | Stage latency, token packing, backend/storage retries, trace capture faults and overload across CPU replicas. | Check the unchanged absolute 30-second budget, including admission wait, initial capture/stage appends/finalization. Verify refusal before expensive work when capture is unavailable, incomplete interrupted records, no plaintext/unapproved fallback and healthy capture during review-view outages; no SLA claim, expanded deadline or third model call. |

I would complete integration checks before exposing a pilot to customer data, then tune within the explicit budgets using controlled measurements. Additional restricted-principal or failure experiments (C4) would be optional lab preparation, not a fourth required capture or an unresolved assignment blocker.
