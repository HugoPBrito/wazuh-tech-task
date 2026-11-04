**Language note:** I normally communicate with coding agents in Spanish. Quoted exchanges are English translations, not messages originally written in English. Edited summaries are labelled separately.

# Phase 2 research: evidence before solution selection

**At this stage, I had not selected a need or service.** I asked the AI to consolidate findings from three independent research workers. This report records that research, not a new investigation during the write-up, a product decision, or market validation. Evidence is an **observed snapshot; may change**.

I kept the shortlist before the detailed evidence and native-feature counterchecks. In the [process notes below](#retrospective-process-context-how-this-draft-was-produced), I reconstructed my requests and the research setup using translated excerpts and labelled summaries. I had not specified a Phase 2 solution.

## Assistant recommendation, not an approved choice

| Priority hypothesis | Why investigate it | What could invalidate it |
|---|---|---|
| 1. Customizable, reliable reporting for self-hosted operations | Repeated requests for scheduling, complete exports, module coverage, and customer-specific output | Existing native reports or Cloud AI Analyst may already satisfy the target workflow |
| 2. Group-aware MSSP operations | Customer grouping, state-index metadata, and reporting/permissions friction recur | RBAC, DLS, tenancy, and cross-cluster search may solve the actual requirement with configuration |
| 3. Maintained Google Workspace detections | Broad discussion asks for useful detections, descriptions, severity, and dashboards beyond ingestion | Existing connectors and maintained rules may cover the intended scope |
| 4. Platform health visibility | Metrics and disk-exhaustion concerns affect reliable operation | Existing exporters and operational tooling may be sufficient |

The AI suggested this investigation order; I treated it as a set of options, not a measured market ranking. Deployment automation, detection reuse, and vulnerability prioritization remained competing hypotheses. I had not chosen a service name or architecture, and the research did not include interviews, purchase-intent validation, or lab experiments.

## Scope and collection method

I authorized three parallel, independent, read-only AI research roles covering core requests; non-core interface/deployment repositories; and external communities plus native documentation. They reported separately; they did not debate or produce an inter-agent consensus.

- Actual repository labels were checked before collection. Core used `type/enhancement/feature`, packages used `type/feature`, and supplemental repositories used `type/enhancement`; these are not interchangeable populations.
- GitHub REST issue endpoints were paginated with open-state and label filters. Core totals and pagination were crosschecked using GraphQL `totalCount` and `hasNextPage`. Search results served discovery, not independent confirmation.
- Core: all 36 scoped issue bodies and all available comments were inspected. There were 122 available comments against a REST aggregate of 125. Issue #10776 accounts for the discrepancy: REST reported 49, while 46 were available, with REST/GraphQL disagreement confirmed and cause unknown.
- Packages: four scoped feature issues. Supplemental inventory: 180 enhancement issues, with detailed body/comment review of 23 selected non-core issues. Do not read this as deep review of every enhancement.
- Eleven primary community threads were read across Google Groups and Lawrence Systems. Reddit returned blocked or empty responses and was not corroborated evidence. No Slack or private sources were used.
- The AI researchers used GitHub CLI REST/GraphQL access, web fetching, and Context7's `/websites/wazuh_current` documentation corpus. The main assistant also spotchecked selected sources.

### Scoped inventory

| Repository under `wazuh/` | Label | Open issues inventoried |
|---|---|---:|
| `wazuh` | `type/enhancement/feature` | 36 |
| `wazuh-packages` | `type/feature` | 4 |
| `wazuh-dashboard-plugins` | `type/enhancement` | 112 |
| `wazuh-dashboard` | `type/enhancement` | 15 |
| `wazuh-indexer` | `type/enhancement` | 5 |
| `wazuh-agent` | `type/enhancement` | 12 |
| `wazuh-docker` | `type/enhancement` | 12 |
| `wazuh-kubernetes` | `type/enhancement` | 5 |
| `wazuh-ansible` | `type/enhancement` | 9 |
| `wazuh-installation-assistant` | `type/enhancement` | 10 |

Supplemental dashboard-plugins, dashboard, and indexer inventories total 132; all eight supplemental repositories total 180. The 36 core features and four package features remain separate. These are complete inventories within the stated filters, **not an organization-wide census of all requests or unlabeled issues**.

[Core query](https://github.com/wazuh/wazuh/issues?q=is%3Aissue%20is%3Aopen%20label%3A%22type%2Fenhancement%2Ffeature%22). Core IDs: 10776, 14446, 14452, 14461, 14756, 14815, 14980, 15020, 15039, 15148, 15178, 15215, 15227, 15233, 15263, 15264, 15265, 15292, 15402, 15430, 15449, 15451, 15452, 15470, 15493, 15586, 15741, 15810, 15991, 16072, 16226, 16361, 16424, 16886, 32193, 35134.

Packages: [#1919](https://github.com/wazuh/wazuh-packages/issues/1919), [#1530](https://github.com/wazuh/wazuh-packages/issues/1530), [#794](https://github.com/wazuh/wazuh-packages/issues/794), [#862](https://github.com/wazuh/wazuh-packages/issues/862). Internal implementation discussion is not a customer vote.

## Evidence by underlying need

All issue records below were open when researched. Reactions refer to issue bodies unless explicitly stated otherwise; comments can include authors, maintainers, and bots. Metrics are not equivalent to customers or willingness to pay.

### 1. Reporting workflow and completeness

| Source | Observed signal | Need expressed |
|---|---|---|
| [Plugins #1492](https://github.com/wazuh/wazuh-dashboard-plugins/issues/1492) | 11 comments; 0 reactions | Automatic reports in the UI |
| [Plugins #3813](https://github.com/wazuh/wazuh-dashboard-plugins/issues/3813) | 2 comments; 1 celebration | Customizable email reports; explicitly extends #1492 |
| [Plugins #4414](https://github.com/wazuh/wazuh-dashboard-plugins/issues/4414) | 2 comments; 0 reactions | Weekly vulnerability reporting |
| [Reporting layer discussion](https://groups.google.com/g/wazuh/c/-bYUdw0mqAI) | 52 views; 2 messages | Complete paginated exports, custom PDF/PNG/CSV output, and scheduling |
| [Module reporting discussion](https://groups.google.com/g/wazuh/c/rPn3fO7yZlg) | 160 views; 8 messages | User confirms scheduled dashboard reporting works, then asks for module equivalents |
| [Per-agent reporting discussion](https://groups.google.com/g/wazuh/c/ajH6P920mlo) | 169 views; 4 messages | Monthly per-agent reporting |

Seven distinct nonauthor accounts that appeared external originated or endorsed requests across the three issue threads; this is not seven verified buyers. The defensible hypothesis is a gap in workflow, completeness, and customization, **not an absence of reporting**.

### 2. Customer grouping and permissions

| Source | Observed signal | Need expressed |
|---|---|---|
| [Core #32193](https://github.com/wazuh/wazuh/issues/32193) | 8 thumbs-up; 6 comments; 5 distinct nonauthor commenters | Missing `agent.group`/label metadata in state indices; MSSP and PCI reporting; manual per-agent DLS and spreadsheets |
| [Core #14980](https://github.com/wazuh/wazuh/issues/14980) | 3 comments; 0 reactions | Group-specific alerts and rules |
| [Core #15227](https://github.com/wazuh/wazuh/issues/15227) | 7 comments; 0 reactions | Group/taxonomy needs |
| [Isolation discussion](https://groups.google.com/g/wazuh/c/isfTPrB-Nnk) | 149 views; 7 messages | Customer-isolation questions |
| [Related isolation discussion](https://groups.google.com/g/wazuh/c/dtSFAGhZwEs) | 37 views; 2 messages | Related isolation concerns; original attachment unread |
| [Multitenancy discussion](https://groups.google.com/g/wazuh/c/VvyIMqv5Qtg) | 69 views; 6 messages | Partial isolation and tenancy concerns |

Community reports are historical and version-scoped; a current exploit or latest-version isolation failure was not established. Saved-object tenancy is not the same as all-data isolation. RBAC, DLS, and cross-cluster search already exist, so validate the specific workflow rather than claiming missing multitenancy wholesale.

### 3. Google Workspace detection quality

[Core #10776](https://github.com/wazuh/wazuh/issues/10776) has 15 thumbs-up and 49 REST-reported comments, of which 46 were available. Researchers identified 19 nonmember/nonauthor accounts plus a deleted-account identity; these are not confirmed unique customers.

- [Consultant handling multiple clients](https://github.com/wazuh/wazuh/issues/10776#issuecomment-1327972118): recurring operational context.
- [Ingestion without useful descriptions, severity, or dashboards](https://github.com/wazuh/wazuh/issues/10776#issuecomment-1449563822): integration quality beyond collecting logs.
- [Rules tuning and compliance](https://github.com/wazuh/wazuh/issues/10776#issuecomment-1659662899): maintained detection content matters.

Workarounds and community connectors exist. The hypothesis is maintained integrations and detections, not technical impossibility of ingestion.

### 4. Platform health and detection reuse

| Source | Observed signal | Interpretation and limit |
|---|---|---|
| [Core #15215](https://github.com/wazuh/wazuh/issues/15215) | 16 thumbs-up; 0 comments | Prometheus metrics requested; an exporter is already referenced |
| [Core #15493](https://github.com/wazuh/wazuh/issues/15493) | 2 comments; 0 reactions | Disk exhaustion and lost-log concerns; no zero-loss guarantee established |
| [Core #15451](https://github.com/wazuh/wazuh/issues/15451) | 7 thumbs-up; 5 comments | Sigma conversion and semantic mismatch; LLMs cannot be assumed to translate every rule correctly |
| [Core #14446](https://github.com/wazuh/wazuh/issues/14446) | 5 thumbs-up; 2 comments | UEBA interest; not a validated implementation or purchase signal |

### 5. Deployment automation

| Source | Observed signal | Interpretation and limit |
|---|---|---|
| [Kubernetes #576](https://github.com/wazuh/wazuh-kubernetes/issues/576) | 38 thumbs-up; 1 comment | cert-manager; 38 reactors include author, leaving 37 others |
| [Kubernetes #35](https://github.com/wazuh/wazuh-kubernetes/issues/35) | 2 thumbs-up; 9 comments | DaemonSet; a separate ETA comment has 9 thumbs-up |
| [Docker #412](https://github.com/wazuh/wazuh-docker/issues/412) | 3 thumbs-up; 5 comments | Docker agent; 4 distinct external-looking interested commenters |
| [Ansible #325](https://github.com/wazuh/wazuh-ansible/issues/325) | 11 thumbs-up; 7 comments | Galaxy distribution request |

These include strong individual endorsements, but do not automatically justify standalone SaaS. Complete current native support was not independently verified for every deployment request.

### 6. Vulnerability context, connectors, and privacy

| Community source | Observed signal | Interpretation and limit |
|---|---|---|
| [Installed versus running kernels](https://groups.google.com/g/wazuh/c/HCtVl92gDbI) | 62 views; 2 messages | Old installed kernels remain despite an updated running kernel; installed vulnerable packages are not necessarily false positives |
| [Understanding vulnerability reports](https://forums.lawrencesystems.com/t/understanding-vulnerability-reports/21079) | 2 posts | Local-access CVE context affects prioritization |
| [UniFi syslog](https://forums.lawrencesystems.com/t/process-unifi-syslog-messages-in-wazuh/25522) | 3 posts; 1 like on a reply | Connector/setup friction |
| [TrueNAS integration](https://forums.lawrencesystems.com/t/truenas-and-wazuh/26562) | 4 posts; 2 likes on a workaround | Workaround evidence, not proof no integration is possible |
| [SIEM and observability discussion](https://forums.lawrencesystems.com/t/zabbix-or-graylog-or-any-seim/23558) | 7 posts; 9 likes across replies | Mixed SIEM/observability conversation, not 9 endorsements of one feature |

Lower-engagement core requests: [#16072 CloudWatch filtering](https://github.com/wazuh/wazuh/issues/16072), 1 comment/0 reactions; [#16886 log filtering](https://github.com/wazuh/wazuh/issues/16886), [#15402 excluding integrations](https://github.com/wazuh/wazuh/issues/15402), and [#15449 data masking](https://github.com/wazuh/wazuh/issues/15449), each 0 comments/0 reactions. Source-side privacy must be considered before transferring security data to SaaS; low engagement does not eliminate that constraint.

## Native capabilities and counterevidence

These sources constrain the opportunity; they are not merely background references.

| Native source | Consequence for the hypothesis |
|---|---|
| [Cloud AI Analyst](https://documentation.wazuh.com/current/cloud-service/ai-analyst.html) | Already periodically analyzes alerts, vulnerabilities, and endpoints; provides email/PDF output and recommendations. Generic AI reporting is weak differentiation. |
| [Daily filtered reports](https://documentation.wazuh.com/current/user-manual/reference/ossec-conf/reports.html) | Reporting already exists in server configuration. |
| [System inventory reports](https://documentation.wazuh.com/current/user-manual/capabilities/system-inventory/generating-system-inventory-reports.html) | Native PDF/CSV generation exists. |
| [Dashboard multitenancy](https://documentation.wazuh.com/current/user-manual/wazuh-dashboard/multi-tenancy.html) | Saved-object tenants exist; do not confuse them with comprehensive data isolation. |
| [RBAC and DLS](https://documentation.wazuh.com/current/user-manual/user-administration/rbac.html) | Authorization controls already exist; verify remaining metadata/workflow gaps. |
| [Cross-cluster search](https://wazuh.com/blog/managing-multiple-wazuh-clusters-with-cross-cluster-search/) | Multiple-cluster/manager architectures are documented. |
| [Vulnerability detection](https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/how-it-works.html) | Inventory and CTI already support vulnerability analysis. |
| [Indexer API use cases](https://documentation.wazuh.com/current/user-manual/indexer-api/use-case.html) | Data queries exist; distinguish indexer access from server API access. |
| [Custom rules and logtest](https://documentation.wazuh.com/current/user-manual/ruleset/rules/custom.html) | Rule customization and testing are existing extension points. |
| [LLM alert enrichment](https://documentation.wazuh.com/current/proof-of-concept-guide/leveraging-llms-for-alert-enrichment.html) | LLM integration is already documented, not a new capability by itself. |

Cloud AI Analyst's FAQ asks “Can I customize the analysis parameters?” and answers: “Not currently. The service uses predefined parameters optimized for comprehensive security assessment.” This supports investigating customization, but does not establish demand for a separate product.

Additional counterchecks: [plugins #2063](https://github.com/wazuh/wazuh-dashboard-plugins/issues/2063) contains a maintainer report of UI upgrades shipped in 4.9.0. [Docker #1227](https://github.com/wazuh/wazuh-docker/issues/1227) has related merged [#2081](https://github.com/wazuh/wazuh-docker/pull/2081), so secrets support must not be described as wholly absent. Future 5.x/6.x plans are not delivered 4.x facts: [security analytics #119](https://github.com/wazuh/wazuh-indexer-security-analytics/issues/119), [#276](https://github.com/wazuh/wazuh-indexer-security-analytics/issues/276), and [indexer #2028](https://github.com/wazuh/wazuh-indexer/issues/2028).

## Evidence limits and next decision gate

- Twelve of the 36 core issues share one author. Repeated issues are not automatically independent demand, and GitHub association `NONE` does not prove someone is an outside employee or customer.
- Views measure exposure, not agreement. Reactions, commenters, and cross-thread account counts cannot be added into a customer total. Internal engineering churn is not market validation.
- Old open requests may already have partial or full solutions in current 4.x. Documentation and issue status alone do not prove runtime behavior.
- Access failures, unread attachments, unreviewed enhancement bodies, and the comment-count discrepancy remain explicit evidence gaps. No exhaustive market ranking is claimed.

Before choosing, I still needed to check the precise gap against the latest relevant 4.x capabilities, establish whether the server API, indexer API, or both would be needed, and define a target operator and workflow. Adoption or purchase intent remained unvalidated. For reporting, I would need to compare native self-hosted reporting and Cloud AI Analyst; for customer operations, I would need to test the authorization boundary before claiming isolation.

**I had not yet made a selection.** I kept these hypotheses open for the next discussion; neither this report nor the [process notes below](#retrospective-process-context-how-this-draft-was-produced) records my approval of a service at this stage.

<!-- RESEARCH-PROCESS-CONTEXT -->

---

## Retrospective process context: how this draft was produced

I reconstructed this section from actual task exchanges; it was not part of the original research. The recovered source body was hash-verified before the editorial changes. I preserved its findings, chronology, and pending-choice status while editing the narration into first person, adding the language note and process record, and replacing two obsolete links with integrated process navigation. I labelled translated excerpts and summaries separately. This is an annotated editorial presentation, not a byte-exact archive.

### My request

**My request — translated excerpt:**

> I want you to thoroughly research all open Wazuh issues that have a "feature request" label.

I also asked the AI to examine repeated requests, comments, reactions, public forums, and documentation, and I explicitly permitted delegation. Labels differed between repositories, so the resulting inventories were bounded, not a complete census of Wazuh demand.

I then clarified that I wanted the research trail as a deliverable, not just advice in the chat:

**My request — translated excerpt:**

> That is, what it says: sources, notes, prompts, conversations that have led me to choose that solution.

**My request — translated message:**

> Do not add dates. Create both documents in parallel, also including these prompts for setting up your work.

I asked for the sources and decision-making exchanges in two local artifacts, created in parallel and without dates.

### AI response

**AI activity — recorded summary, not a quotation or translation:** three independent, read-only readers returned core, non-core, and community/documentation findings. The main assistant synthesized them, initially favoring reporting and customer operations while checking existing native features. They did not reach an inter-agent consensus, and I had not made a choice.

I recovered this reply from the main conversation:

**AI response — translated excerpt recovered from the main conversation:**

> Yes, and **my reply in the chat does not replace that deliverable**.

The AI acknowledged that its chat answer did not replace the research deliverable I requested. My first three prompts remain verbatim in Spanish in the private record, but the initial AI activity survives only as a summary. I did not invent the unavailable wording.

### Output produced

The AI produced the 152-line initial research and a separate private conversation record. I had reporting, customer scoping, Workspace detections, and platform health to consider, each with counterevidence; I had not yet selected a need or service.

### My changes and permission limits

I authorized public-source research and local Markdown, not implementation or autonomous actions against systems. I did not authorize publication of these Phase 2 research edits. I kept the conversation record private and later permitted selected work excerpts here, not publication of the full conversation.

### Subsequent stage, not knowledge available to this draft

I later asked to pause research-document construction so I could continue the discussion:

**My request — translated excerpt:**

> But we will build the research document at the end, based on those logs.

I wanted to continue the conversation and reconstruct the document later. I subsequently asked to resume and expand the research, leading to [V2](RESEARCH-v2.md#retrospective-process-context-how-the-expansion-was-produced). Both instructions came after this original draft.
