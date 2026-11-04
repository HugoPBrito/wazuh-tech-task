# Phase 3: Before-Pilot Integration Checks

I would use this checklist when taking the [service proposal](PHASE3.md) toward a pilot. The three genuine C1-C3 responses are already included in the [evidence record](assets/evidence/EVIDENCE.md); these checks concern deployment integration, not missing assignment captures or a requirement to run model benchmarks now.

## Accepted MVP starting points and future scope

I accepted reuse of existing identity/effective human permissions, ephemeral conversation history initially, and a provisional 30-day payload-free audit baseline for the hosted-assistant simulation. Those principles do not establish a token contract or Wazuh/legal policy. Persistent history would be future scope, with a separate purpose, encrypted store, access model and retention decision.

## Design choices I would start with

| Area | Proposed starting choice |
|---|---|
| Product boundary | An official Wazuh-maintained open-source MCP project with published contracts, documentation and versioned releases. Community developers could use it independently with authorized deployments and chosen AI clients/models, including external providers outside the SaaS offering. |
| Hosted deployment | One CPU API/orchestrator application, a private instance of the official read-only MCP server, private GPU serving and shared regional TTL/admission state, reusing platform facilities. |
| Capacity and budgets | Hosted [request limits](PHASE3.md#proposed-request-budgets) and [bounded pilot capacity](PHASE3.md#bounded-pilot-capacity), with shared atomic accounting and fail-closed admission. Common MCP per-tool authentication, permissions, schema, page/rate and minimized-output protections would apply to every instance. |
| Hosted retention | A proposed 15-minute context/evidence TTL and no payload backups, implementing the accepted ephemeral-context principle. These are not guarantees for arbitrary clients or forks. |
| Evaluation and cost | A private hosted-assistant promptfoo comparison and hypothetical SaaS operating budget, separate from comparison expenditure, open-source release work and community inference costs. |

## Before-pilot integration checks

| Priority | What I would confirm with the responsible platform owner | Required deployment evidence |
|---|---|---|
| 1 | Official MCP tool/client compatibility, supported authorized Manager/Indexer routes and the hosted internal read route. | Versioned contracts, exact scoped endpoint resolution, GET-body ingress handling, bounded pagination and native error-envelope behavior. Community use would not imply a new public SaaS endpoint or Cloud OAuth contract. |
| 2 | Actual hosted signed-token/delegation contract and each MCP deployment's caller/backend authentication and effective-user mapping. | Human restrictions enforced at every backend read; no credentials in model/tool responses. Hosted permission revocation invalidates old context and citations, and authorization/state outages fail closed. |
| 3 | Hosted `deployment_region`, infrastructure processor and residency/egress rules. | Regional SaaS inference, state, offline judges and observability, approved access and blocked external processing. `eu-central-1` and `eu-west-2` remain alternatives, not approvals; the UK is not EU residency. Community client processing/retention choices would follow their own configuration and policy without weakening MCP server security. |
| 4 | Retention, deletion, credential/audit/operator access and metadata backup policy. | Implement the accepted ephemeral context and provisional 30-day payload-free audit principles; validate the proposed 15-minute TTL and no-payload-backup approach with responsible policy owners. No legal/compliance approval is implied. |

## Measurements I would use to tune the pilot

| Priority | Measurement | How I would use it |
|---|---|---|
| 5 | Representative demand, GPU fit/startup/readiness, cancellation and cost. | Test one warm replica, maximum two, one active investigation per ready replica, the four-slot fair queue and the two-request tenant ceiling. Replace budgeting hypotheses with regional quotes and observed completions. |
| 6 | Human-reviewed task quality, groundedness, citations and false refusals. | Set semantic thresholds after a baseline; hard security assertions remain mandatory independently of quality scores. |
| 7 | Stage latency, token packing, backend retries and overload across CPU replicas. | Check the absolute 30-second budget, including admission wait, without treating it as a measured SLA or allowing a hidden third model call. |

I would complete integration checks before exposing a pilot to customer data, then tune within the explicit budgets using controlled measurements. Additional restricted-principal or failure experiments (C4) would be optional lab preparation, not a fourth required capture or an unresolved assignment blocker.
