# Work-Unit Brief: Actual Direction and Future Task Template

This is a **curated public representation of agent direction**, not a verbatim private conversation, a complete prompt archive or active agent configuration. A brief is a concrete handoff from an approved task, not mandatory OpenCode or Gentle AI infrastructure. Return to the [Phase 4 delivery plan](../../PHASE4.md#2-how-would-you-split-the-work-of-building-the-service-between-you-and-your-agents).

## Direction used during this documentation work

I used AI to compare sources, challenge the proposal and organize the design. Earlier independent read-only roles checked research, tool guidance and cross-document coherence. One coordinated writer integrated overlapping material. I corrected the product direction, open MCP/private SaaS distinction, backend/model responsibilities, evidence claims and diagram readability. I performed the lab reads and supplied their captures; agents helped interpret and document them.

The current follow-up authorized one writer to review and rewrite only the four Phase 4 files, preserving all eight question headings and two matching diagram sources. It required clear professional English, actual past tense for authoring history, conditional language for proposed service work, and preservation of concurrent edits. It explicitly excluded README, earlier phases, real evidence, private prompts/configuration and credentials. Local documentation checks and bounded official-source verification were permitted; service implementation, installations, model/API/evaluation runs, staging, commits, pushes and PR updates were not. Independent review earlier does not imply new reviewers ran during this single-writer follow-up.

This account makes the task boundaries and substantive corrections reviewable without exposing personal configuration, raw AI logs or customer data. It does not claim every original prompt is included.

## Reusable handoff fields

For future implementation, I would populate these fields from the approved backlog item and inspected repository, then resolve ambiguity before giving write permission:

| Field | Required content |
|---|---|
| Approved source | Ticket/issue/task reference, human owner, priority and approval state. No unapproved idea becomes an implementation task. |
| Problem and requirements | User outcome, smallest change, acceptance criteria, failure cases and unchanged contracts. |
| Context and scope | Relevant source/docs and evidence, exact allowed paths, exclusions, dependencies and one designated writer. |
| Permissions and data | Read/write, execution and network authority separately. Only public, synthetic or approved redacted development material. No secrets or automatic product-trace ingestion. |
| Verification | Relevant unit/integration/contract tests and real commands after toolchain inspection. TDD where meaningful and runnable. Documentation-only checks where no code exists. |
| Evidence and review | Exact candidate/diff, commands/results, skipped checks, assumptions and unresolved findings for fresh read-only review. |
| Stop conditions | Missing requirements/authority, unexpected sensitive data, conflicting risk, repeated findings without progress, or agreed time/round/scope budget exhausted. |
| Delivery authority | Local changes only unless explicitly authorized otherwise. Separate permission before commit, push and PR creation/update for the exact scope. Never merge for the user. |

## Example: planned read-only `agents_list` task

**Template only.** `<APPROVED-TICKET-REFERENCE>` is a placeholder to replace with a real approved backlog reference. No GitHub issue, code paths, test harness or implementation is claimed to exist in this design repository. The owner would confirm the requirements below before work began.

### Approved task and outcome

- **Reference:** `<APPROVED-TICKET-REFERENCE>`, approved by `<HUMAN-OWNER>` before implementation.
- **Problem:** An investigation needs a bounded inventory of agents visible to the authenticated person, without exposing another deployment or giving the model arbitrary API access.
- **Outcome:** Add or correct the official MCP's read-only `agents_list` contract and Manager adapter for that authorized inventory. Hosted model orchestration, other tools and UI changes would be separate approved work.
- **Context:** The [Phase 3 integration design](../../../phase3/PHASE3.md) and [synthetic evaluation plan](../../../phase3/assets/evaluation/EVALUATION-PLAN.md) would supply design expectations, not evidence of working code. The writer would inspect the future repository before choosing paths or commands.

### Requirements and acceptance criteria

1. The server would authenticate the caller and derive tenant/deployment/effective-user scope from trusted authorization context. The model could not supply an arbitrary tenant, endpoint or credential.
2. The adapter would use authorized Manager reads only. It would enforce the approved typed schema, pagination and response limits, minimize returned fields and omit credentials. This task would not add Indexer access, Wazuh writes or shell execution.
3. Missing/invalid authorization, forbidden scope and malformed arguments would fail safely before an unauthorized backend read. A forbidden result would not become an empty successful inventory.
4. A valid empty result would be distinguishable from Manager outage, timeout, partial/failed items or incomplete pagination. Error output would exclude secrets and raw sensitive backend details.
5. Existing supported behavior would remain covered. Contract documentation and synthetic fixtures would change with behavior. Community clients could choose external models, but that would not weaken server-side checks or imply hosted privacy guarantees.

### Planned edit surface and authority

| Planned files, to confirm against the actual repository | Intended scope |
|---|---|
| `<MCP-REPO>/src/tools/agents-list.<ext>` | Typed tool contract and bounded read behavior. |
| `<MCP-REPO>/src/adapters/manager.<ext>` | Only the adapter changes needed for this inventory read. |
| `<MCP-REPO>/tests/agents-list*` | Synthetic unit, adapter integration and contract cases. |
| `<MCP-REPO>/docs/tools/agents-list.md` | Scope, schema, limits and failure behavior. |

These are illustrative planned paths, not local links or existing files. The human owner would approve actual paths before edits. Shared authorization changes, new dependencies, inference, UI, live deployment access, trace export and other tools would be out of scope and require a new decision. One writer would handle this work unit; a reviewer would inspect read-only.

The initial permission would cover local scoped edits and approved synthetic tests only. It would not permit installation, live customer API reads, external content transfer, staging, commit, push, PR creation/update, merge or release. If requirements could not be met within that authority, the writer would stop rather than expand it.

### Verification and return evidence

The writer would first inspect the actual test framework and confirm executable commands. Where practical, it would capture a failing behavior test, implement the minimum fix, then refactor with tests green. For a new test boundary, establishing useful fixtures and coverage would come first; no invented command or claimed execution would fill that gap.

Tests would cover permitted inventory and valid empty results; forbidden/cross-tenant/revoked scope; malformed or over-limit input; pagination/truncation; Manager timeout/partial/error envelopes; and credential exclusion in outputs and logs. Unit checks would cover mapping and validation, integration checks the adapter with a controlled Manager substitute, and contract checks the public tool schema and error semantics. Live integration would require separate approval, not silently replace synthetic tests.

The writer would return the local candidate, mapping from acceptance criteria to tests, exact observed commands/results, skipped coverage and doc changes. A fresh reviewer would examine that same candidate against the approved ticket. The human owner would set `<TIME-LIMIT>` and `<MAX-CORRECTION-ROUNDS>` before execution; ambiguity, scope expansion, sensitive data or no evidence-based progress would stop the task.

Only after candidate review and **explicit permission for that delivery scope** could an agent commit, push and open/update a PR. A changed scope would need renewed permission. My review, another human's review and current required checks would precede production. Humans would approve, merge and authorize release; an approved pipeline could execute deployment.
