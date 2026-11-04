**Language note:** I normally communicate with coding agents in Spanish. Quoted exchanges are English translations, not messages originally written in English. Edited summaries are labelled separately.

# Phase 2 research: evidence before solution selection

**At this stage, the AI suggested analyst-controlled investigation and case workflow as a strong candidate; I had not selected a service.** Repeated requests concern turning alerts into owned work, producing useful customer reports, maintaining detection content, and operating customer scopes reliably. Competitors provide reusable patterns; their presence alone does not prove Wazuh lacks an equivalent. Reporting and Google Workspace have broader observed engagement than the newer case-workflow evidence.

I used this report to compare needs, not as completed Phase 2 answers, a product specification, or market validation. MCP remained a possible integration foundation, not a business need by itself. I had not approved a service, and the research did not include interviews, lab runs, purchase-intent validation, or inter-agent consensus.

The AI originally recommended reporting first. I then resumed and expanded the research after an earlier pause, asking it to consider MCP and competitor patterns. The expansion added case-workflow requests, successful workarounds, four MCP projects, and six competitors, and the AI revised its recommendation. In the [process notes below](#retrospective-process-context-how-the-expansion-was-produced), I reconstructed that sequence with translated excerpts; I did not replace the earlier recommendation with a later choice.

## Contents

- [Assistant recommendation, not an approved choice](#assistant-recommendation-not-an-approved-choice)
- [Scope and collection method](#scope-and-collection-method)
- [Complete core inventory](#complete-core-inventory)
- [Recurring jobs and target users](#recurring-jobs-and-target-users)
- [Eight supplementary issue threads](#eight-supplementary-issue-threads)
- [Community evidence catalog](#community-evidence-catalog)
- [Native capabilities and API constraints](#native-capabilities-and-api-constraints)
- [Six competitor comparisons](#six-competitor-comparisons)
- [Existing alternatives before building](#existing-alternatives-before-building)
- [Four MCP foundations](#four-mcp-foundations)
- [Opportunity matrix and disproof criteria](#opportunity-matrix-and-disproof-criteria)
- [Evidence limits and unresolved selection](#evidence-limits-and-unresolved-selection)

## Assistant recommendation, not an approved choice

The AI suggested comparing a **narrow analyst-owned investigation workflow** against reporting and maintained integration/content services. I kept it as a candidate, not an agreed design. At this stage, the suggestion was optional grounded AI assistance to summarize cited evidence or draft case notes, not silently convert every alert into a case or take response actions.

| Candidate | Why it merits attention | Strongest challenge |
|---|---|---|
| Analyst-controlled cases, optionally AI-assisted | Explicit requests for investigation, assignment, acknowledgement, selective escalation, and closure; recurring competitor pattern | IRIS, TheHive, plugins, and Shuffle may already solve enough; public demand is narrower than reporting/Workspace |
| Customer-specific report packs | Repeated scheduling, pagination, module, branding, and per-agent needs | Wazuh reports, Cloud AI Analyst, and upstream reporting already exist |
| Maintained detection and coverage content | Sigma semantic friction, Workspace tuning, SCA rollout, and rule-editor pain | Configuration, existing rules, and upstream content may suffice; arbitrary conversion is unsafe |
| MSSP scope and evidence workflow | Agent-group metadata, DLS maintenance, and customer-reporting friction | Native RBAC/DLS, labels, tenants, and cross-cluster search may resolve the precise workflow |
| Maintained Workspace integration | Strong single-thread engagement plus separate community use and successful ingestion | Native GCP/Pub/Sub and community connectors already work for some users |
| Telemetry health and continuity | Metrics, full buffers, silent sources, and a recurring Filebeat interruption | Existing exporters, counters, Zabbix, and operating procedures may be sufficient |

I wanted to compare these needs rather than combine them into one broad SaaS proposition. I had asked to consider reusable competitor patterns, not novelty for its own sake. Service boundaries, adoption, pricing, and my choice remained open.

## Scope and collection method

I used the AI to consolidate the source findings; I did not personally inspect every source. Three original independent read-only AI workers covered core requests, non-core repositories, and communities/documentation. Six completed expansion roles covered GitHub, native capabilities, communities, MCP, Elastic/Security Onion/Graylog, and Splunk/Falcon/Sentinel. Three earlier expansion launches were cancelled without results and contribute no evidence. The main assistant synthesized the separate reports; workers did not reach a consensus.

| Evidence layer | Coverage | What it does not establish |
|---|---|---|
| Original GitHub census | 36 core feature bodies and all available comments; 4 package features | All issues across the organization, or all unlabeled requests |
| Original supplemental inventory | 180 enhancement issues; 23 selected non-core threads deeply reviewed | Deep review of all 180 discussions |
| Expanded issue search | 284 overlapping matches; 92 metadata records screened; 8 threads selected | Exhaustiveness, 284 independent needs, or 92 unique customers |
| Public communities | 21 primary sources: original 11 plus 10 additional threads | An independent-organization census or private-community coverage |
| Native/competitor documentation | Wazuh counterchecks and 6 named competitor families | Runtime parity, exact commercial entitlements where not verified, or benchmark results |
| MCP repositories | 4 third-party projects, documentation and code inspection | Execution, a security audit, dependency clearance, or production readiness |

The AI researchers collected GitHub data using CLI REST/GraphQL access, pagination, actual labels, and core `totalCount`/`hasNextPage` crosschecks. Public web fetching and Context7's `/websites/wazuh_current` corpus supported documentary checks. Search results were discovery aids, not corroboration. The main assistant also performed selected spotchecks. All counts are an **observed snapshot; may change**.

**Claim vocabulary:** **documented exists** means an official source describes a capability; **user-reported gap/outcome** attributes experience to a source; **comparative inference** is the assistant's interpretation; **runtime unverified** means this research did not reproduce behavior. Documentation of a competitor feature is not evidence of Wazuh-wide absence.

### Original label-bounded inventories

| Repository under `wazuh/` | Actual label | Open issues inventoried |
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

Dashboard-plugins, dashboard, and indexer total 132; all eight supplemental repositories total 180. These populations are separate from the 36 core and 4 package features. Labels are not interchangeable or a neutral sample of user demand. [The original core filter](https://github.com/wazuh/wazuh/issues?q=is%3Aissue%20is%3Aopen%20label%3A%22type%2Fenhancement%2Ffeature%22) remains the inventory boundary.

Package sources retained separately: [#1919](https://github.com/wazuh/wazuh-packages/issues/1919), [#1530](https://github.com/wazuh/wazuh-packages/issues/1530), [#794](https://github.com/wazuh/wazuh-packages/issues/794), and [#862](https://github.com/wazuh/wazuh-packages/issues/862). These were inventoried, not counted as four customer endorsements; internal implementation discussion is not a purchase signal.

### Expanded search boundary

Each base query below was run separately with `is:open` and `is:closed`, sorted by descending comment count, inspecting the first 10 results per query/state where available. All responses had `incomplete_results=false`; the first-page selection remains bounded and overlapping. The links expose reproducible discovery filters, not additional primary evidence.

| Base query, also constrained by `is:issue` | Open / closed matches | Discovery links |
|---|---:|---|
| `org:wazuh "agent.group" in:title,body` | 3 / 5 | [Open](https://github.com/search?q=org%3Awazuh+is%3Aissue+%22agent.group%22+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=org%3Awazuh+is%3Aissue+%22agent.group%22+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |
| `repo:wazuh/wazuh logcollector buffer in:title,body` | 12 / 87 | [Open](https://github.com/search?q=repo%3Awazuh%2Fwazuh+is%3Aissue+logcollector+buffer+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=repo%3Awazuh%2Fwazuh+is%3Aissue+logcollector+buffer+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |
| `org:wazuh prometheus in:title,body` | 4 / 5 | [Open](https://github.com/search?q=org%3Awazuh+is%3Aissue+prometheus+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=org%3Awazuh+is%3Aissue+prometheus+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |
| `org:wazuh rule editor in:title,body` | 8 / 64 | [Open](https://github.com/search?q=org%3Awazuh+is%3Aissue+rule+editor+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=org%3Awazuh+is%3Aissue+rule+editor+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |
| `org:wazuh alert acknowledge in:title,body` | 3 / 9 | [Open](https://github.com/search?q=org%3Awazuh+is%3Aissue+alert+acknowledge+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=org%3Awazuh+is%3Aissue+alert+acknowledge+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |
| `org:wazuh "alert management" in:title,body` | 9 / 69 | [Open](https://github.com/search?q=org%3Awazuh+is%3Aissue+%22alert+management%22+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=org%3Awazuh+is%3Aissue+%22alert+management%22+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |
| `org:wazuh alert dismiss in:title,body` | 0 / 6 | [Open](https://github.com/search?q=org%3Awazuh+is%3Aissue+alert+dismiss+in%3Atitle%2Cbody+is%3Aopen+sort%3Acomments-desc&type=issues) / [closed](https://github.com/search?q=org%3Awazuh+is%3Aissue+alert+dismiss+in%3Atitle%2Cbody+is%3Aclosed+sort%3Acomments-desc&type=issues) |

## Complete core inventory

All 36 rows were **open** under the actual `type/enhancement/feature` label. Display titles are shortened for readability, not represented as exact issue titles. `C` is REST comment count; `R` is issue-body thumbs-up, not people demanding a paid service. Context describes the discussion, not verified employment.

| Core source and display title | C | R | Observed context and underlying need |
|---|---:|---:|---|
| [#10776 Google Workspace / Google Suite integration](https://github.com/wazuh/wazuh/issues/10776) | 49 | 15 | Operations/community use; cloud coverage and useful detections; only 46 comments available |
| [#14446 User Behavior Analytics](https://github.com/wazuh/wazuh/issues/14446) | 2 | 5 | Community interest in behavior analysis |
| [#14452 Include detectree by default](https://github.com/wazuh/wazuh/issues/14452) | 1 | 0 | Community visualization suggestion; service value speculative |
| [#14461 Laurel for auditd](https://github.com/wazuh/wazuh/issues/14461) | 1 | 1 | Community context/integration need; attempted translation did not work |
| [#14756 Start agent automatically after installation](https://github.com/wazuh/wazuh/issues/14756) | 0 | 0 | Operations relay; deployment completion |
| [#14815 Multiple osquery log paths](https://github.com/wazuh/wazuh/issues/14815) | 0 | 0 | Community request; existing `localfile` workaround |
| [#14980 Agent-group XML label for custom rules](https://github.com/wazuh/wazuh/issues/14980) | 3 | 0 | Community group-aware alerts/rules |
| [#15020 Immutable indices](https://github.com/wazuh/wazuh/issues/15020) | 8 | 0 | Community author/vendor implementation discussion; evidence integrity |
| [#15039 Improve Wazuh audit logs](https://github.com/wazuh/wazuh/issues/15039) | 2 | 0 | Community administrative auditability |
| [#15148 Separate admin accounts](https://github.com/wazuh/wazuh/issues/15148) | 0 | 0 | Community service/human identity separation |
| [#15178 UNIX/TCP sockets and pipe input](https://github.com/wazuh/wazuh/issues/15178) | 7 | 0 | Community edge-ingestion flexibility |
| [#15215 Prometheus metrics](https://github.com/wazuh/wazuh/issues/15215) | 0 | 16 | Community operational health; exporter already referenced |
| [#15227 Update taxonomy, especially Group](https://github.com/wazuh/wazuh/issues/15227) | 7 | 0 | Community taxonomy and grouping |
| [#15233 Linux/Unix kill-process active response](https://github.com/wazuh/wazuh/issues/15233) | 0 | 0 | Engineering response-script request |
| [#15263 FIM remove-threat active response](https://github.com/wazuh/wazuh/issues/15263) | 0 | 0 | Engineering malicious-file removal script |
| [#15264 Linux/Unix shutdown active response](https://github.com/wazuh/wazuh/issues/15264) | 2 | 0 | Engineering endpoint shutdown script |
| [#15265 Windows shutdown active response](https://github.com/wazuh/wazuh/issues/15265) | 1 | 0 | Engineering endpoint shutdown script |
| [#15292 On-premises GitHub logs](https://github.com/wazuh/wazuh/issues/15292) | 0 | 0 | Operations connector request |
| [#15402 Exclusions in integrations](https://github.com/wazuh/wazuh/issues/15402) | 0 | 0 | Affiliation unresolved; selective routing |
| [#15430 Unify agent-manager connections](https://github.com/wazuh/wazuh/issues/15430) | 0 | 0 | Engineering; open despite a won't-fix label |
| [#15449 Data masking](https://github.com/wazuh/wazuh/issues/15449) | 0 | 0 | Community privacy requirement |
| [#15451 Sigma rules integration](https://github.com/wazuh/wazuh/issues/15451) | 5 | 7 | Operations/community semantic portability |
| [#15452 AWS log-collection CloudFormation](https://github.com/wazuh/wazuh/issues/15452) | 0 | 0 | Operations onboarding templates |
| [#15470 Windows wazuh-control](https://github.com/wazuh/wazuh/issues/15470) | 0 | 0 | Engineering endpoint control |
| [#15493 Avoid log loss under storage pressure](https://github.com/wazuh/wazuh/issues/15493) | 2 | 0 | Community operational health and evidence continuity |
| [#15586 Windows 11 Sandbox compatibility](https://github.com/wazuh/wazuh/issues/15586) | 6 | 5 | Operations/user compatibility need |
| [#15741 Check insecure configuration on service start](https://github.com/wazuh/wazuh/issues/15741) | 3 | 0 | Community hardening |
| [#15810 Split wazuh-analysisd](https://github.com/wazuh/wazuh/issues/15810) | 4 | 4 | Architectural dialogue; also 4 hearts, from the same 4 reacting accounts |
| [#15991 Configurable endpoint attribution](https://github.com/wazuh/wazuh/issues/15991) | 2 | 0 | Community attribution for integrations/remote syslog |
| [#16072 CloudWatch logStreamNamePrefix](https://github.com/wazuh/wazuh/issues/16072) | 1 | 0 | Community ingestion scope and cost |
| [#16226 macOS/BSD realtime FIM](https://github.com/wazuh/wazuh/issues/16226) | 2 | 0 | Engineering/user platform parity |
| [#16361 dnstap localfile input](https://github.com/wazuh/wazuh/issues/16361) | 7 | 0 | Community DNS ingestion |
| [#16424 Multiple daily syscheck scans](https://github.com/wazuh/wazuh/issues/16424) | 3 | 0 | Community timing and noise control |
| [#16886 Log filtering](https://github.com/wazuh/wazuh/issues/16886) | 0 | 0 | Relayed user filtering need |
| [#32193 agent.group/agent.label in state indices](https://github.com/wazuh/wazuh/issues/32193) | 6 | 8 | Community/MSSP/PCI; 5 distinct nonauthor commenters |
| [#35134 UDP socket collection](https://github.com/wazuh/wazuh/issues/35134) | 1 | 0 | Engineering implementation of an ingestion capability |

The inventory has 61 thumbs-up and 4 hearts: **65 reactions, not 65 users**. For #15810, adding 4 thumbs-up and 4 hearts would double-count the same 4 accounts as supporters. Twelve issues share one author. GitHub association `NONE` is not proof of outside employment, and engineering-origin items do not establish external demand.

REST totals sum to 125 comments; 122 were available. #10776 alone explains the numerical difference: 49 REST-reported versus 46 available, with REST/GraphQL disagreement confirmed. The cause remains unknown; no missing comments or identities are invented. Other core available-comment counts matched their REST counts.

## Recurring jobs and target users

These clusters group underlying work, not alleged common software root causes. A request's suggested mechanism is a hypothesis; a user's symptom or confirmed workaround is the evidence. Detailed sources and outcomes appear in the issue and community catalogs below.

### Analyst-controlled investigations

**Target/job:** a SOC analyst wants to decide which alerts deserve investigation, assign an owner, retain evidence, and record closure. The community explicitly asks to “investigate alerts, assign them mark them as closed.” ([C12](https://groups.google.com/g/wazuh/c/-fNsty6bIUY)). [#33328](https://github.com/wazuh/wazuh/issues/33328) requests single/bulk manual escalation because automatic forwarding over-escalates; [#3337](https://github.com/wazuh/wazuh/issues/3337) discusses acknowledgement/classification and an unfinished UI.

**Workarounds/counterevidence:** IRIS and an AlertManager plugin are suggested in C12; its author later reports a 4.14 plugin release, but no installation outcome is confirmed. Wazuh's [Shuffle reporting/response proof of concept](https://wazuh.com/blog/automating-security-reporting-and-response-with-wazuh-and-shuffle/) includes TheHive integration. The opportunity is a smoother controlled workflow, not a claim that Wazuh cannot integrate with case tools. Competitor cases make the pattern credible, not the market proven.

### Reporting workflow and completeness

**Target/job:** self-hosted operators and MSSPs need scheduled, complete, scoped evidence for customers and management, rather than a screenshot or first API page.

| Source | Observed signal | Requested work / counterevidence |
|---|---|---|
| [Plugins #1492](https://github.com/wazuh/wazuh-dashboard-plugins/issues/1492) | 11 comments; 0 reactions | Automatic reports in the UI |
| [Plugins #3813](https://github.com/wazuh/wazuh-dashboard-plugins/issues/3813) | 2 comments; 1 celebration | Customizable email reports; explicitly extends #1492 |
| [Plugins #4414](https://github.com/wazuh/wazuh-dashboard-plugins/issues/4414) | 2 comments; 0 reactions | Weekly vulnerability reports |
| [C01 reporting layer](https://groups.google.com/g/wazuh/c/-bYUdw0mqAI) | 52 views; 2 messages | Complete pagination, custom PDF/PNG/CSV, scheduling |
| [C02 module reporting](https://groups.google.com/g/wazuh/c/rPn3fO7yZlg) | 160 views; 8 messages | Scheduled dashboard reporting confirmed working; module equivalents requested |
| [C03 per-agent reporting](https://groups.google.com/g/wazuh/c/ajH6P920mlo) | 169 views; 4 messages | Monthly per-agent output |

Seven distinct nonauthor accounts that appeared external originated or endorsed requests across the three issue threads, not seven verified buyers. Native reports and Cloud AI Analyst directly challenge generic “AI reports” differentiation. Remaining hypotheses concern scope, completeness, repeatability, and useful customization, not absence of reporting.

### Customer grouping and authorization maintenance

**Target/job:** an MSSP operator wants customer-filtered searches, current-state inventories, and repeatable reports without hand-maintaining per-agent DLS or spreadsheets. [#32193](https://github.com/wazuh/wazuh/issues/32193), [#14980](https://github.com/wazuh/wazuh/issues/14980), and [#15227](https://github.com/wazuh/wazuh/issues/15227) address different metadata/taxonomy surfaces. [#14225's MSSP example](https://github.com/wazuh/wazuh/issues/14225#issuecomment-2118525042) adds a concrete operating workflow.

**Workarounds/counterevidence:** labels can work, but multi-group semantics can be ambiguous; see the supplementary table. Native RBAC, indexer DLS, saved-object tenancy, and cross-cluster search already exist. C04-C06 are historical, version-scoped isolation reports, not a current exploit finding. A grouping convenience must never be presented as proof of a customer authorization boundary.

### Maintained Workspace ingestion and detection quality

**Target/job:** a consultant or administrator wants useful Workspace security events, descriptions, severity, and dashboards without maintaining a fragile connector chain. [#10776's multi-client context](https://github.com/wazuh/wazuh/issues/10776#issuecomment-1327972118), [low-value ingested events](https://github.com/wazuh/wazuh/issues/10776#issuecomment-1449563822), and [rules/compliance tuning](https://github.com/wazuh/wazuh/issues/10776#issuecomment-1659662899) distinguish ingestion from maintained detection content.

The original review identified 19 nonmember/nonauthor accounts plus a deleted-account identity in #10776, not confirmed unique customers. C14 reports an unwanted GCP dependency; C15 confirms success with a [community connector](https://github.com/avanwouwe/wazuh-gworkspace); C16 already has ingestion working. These are counterevidence to impossibility. Broad Drive/Gmail/audit-event coverage and its licensing remain unproven.

### Telemetry continuity and operational health

**Target/job:** an operator wants to know which expected source stopped contributing, whether queues/drop counters are worsening, and whether recovery restored data. Metrics interest in [#15215](https://github.com/wazuh/wazuh/issues/15215) and storage concerns in [#15493](https://github.com/wazuh/wazuh/issues/15493) are complemented by buffer pressure in #11241, indexer metrics in #34601, per-source silence in C17, and a recurring Filebeat interruption in C18.

**Workarounds/counterevidence:** an exporter is already referenced, a custom indexer image worked for one reporter, and C18 confirms replay recovery plus a Zabbix systemd monitor. Existing counters/API checks are building blocks. A healthy cluster does not establish that all expected telemetry arrived; neither a monitor nor this report establishes zero loss.

### Maintained detections, rollout, and vulnerability context

**Target/job:** a detection engineer wants reusable content with explained semantics, test cases, and reliable rollout. [#15451](https://github.com/wazuh/wazuh/issues/15451) records Sigma conversion friction; [#14461](https://github.com/wazuh/wazuh/issues/14461) records an unsuccessful translation attempt. #13074 and C19 add deployment assurance, not merely an online YAML editor. #5666 shows a dashboard/CLI discrepancy, not proof every editor is broken.

Vulnerability operators instead need current asset/package context and useful prioritization: C07/C08 do not establish false positives merely because a newer kernel is running or a CVE requires local access. C20 confirms a configuration-based recovery for manager inventory/vulnerabilities. CTI already exists; EPSS/KEV field availability was not verified. An LLM cannot be assumed to preserve every detection rule's semantics or establish exploitability.

### Deployment and privacy constraints

| Deployment source | Observed signal | Boundary |
|---|---|---|
| [Kubernetes #576](https://github.com/wazuh/wazuh-kubernetes/issues/576) | 38 thumbs-up; 1 comment | cert-manager; includes the author, leaving 37 other reactors |
| [Kubernetes #35](https://github.com/wazuh/wazuh-kubernetes/issues/35) | 2 thumbs-up; 9 comments | DaemonSet; a separate ETA comment has 9 thumbs-up |
| [Docker #412](https://github.com/wazuh/wazuh-docker/issues/412) | 3 thumbs-up; 5 comments | Docker agent; 4 external-looking interested commenters, not verified customers |
| [Ansible #325](https://github.com/wazuh/wazuh-ansible/issues/325) | 11 thumbs-up; 7 comments | Galaxy distribution; not proof of a standalone SaaS market |

Complete current native coverage was not checked for every deployment request. Low-engagement [#16072](https://github.com/wazuh/wazuh/issues/16072), [#16886](https://github.com/wazuh/wazuh/issues/16886), [#15402](https://github.com/wazuh/wazuh/issues/15402), and [#15449](https://github.com/wazuh/wazuh/issues/15449) still expose cost, routing, filtering, and privacy constraints. Source-side masking and data minimization matter before security data is sent to SaaS or an external model; low reaction counts do not remove that obligation.

## Eight supplementary issue threads

These selected threads counter label bias and include closed issues. Status, comments, and issue-body thumbs-up are snapshots. They do not replace the complete core inventory or imply eight independent organizations.

| Source / status / C / thumbs-up | Findings, outcome, and limitation |
|---|---|
| [Core #14225: filter Security events by agent.group](https://github.com/wazuh/wazuh/issues/14225), open; 20 / 13 | 18 distinct nonauthor handles, not verified customers. [Concrete MSSP workflow](https://github.com/wazuh/wazuh/issues/14225#issuecomment-2118525042); [label workaround reported working](https://github.com/wazuh/wazuh/issues/14225#issuecomment-2412900965); [multi-group label ambiguity](https://github.com/wazuh/wazuh/issues/14225#issuecomment-1514488970). Accounts overlap #32193; do not sum them. |
| [Core #11241: pause logcollector when buffers are full](https://github.com/wazuh/wazuh/issues/11241), open; 1 / 0 | Bulk 50,000-line import and drop counters. [Maintainer discussion](https://github.com/wazuh/wazuh/issues/11241#issuecomment-989826193) explains stale-data, multiple-target, and rotation tradeoffs; pausing is not automatically zero-loss delivery. |
| [Core #34601: indexer Prometheus observability](https://github.com/wazuh/wazuh/issues/34601), open; 1 / 0 | A custom 4.14.2 image provides shard-capacity metrics for the reporter; another account supports the need. [Outcome](https://github.com/wazuh/wazuh/issues/34601#issuecomment-4271188489) suggests maintenance/packaging friction, not impossibility. |
| [Core #13074: online SCA document editing](https://github.com/wazuh/wazuh/issues/13074), open; 1 / 0 | A [4.5 deployment report](https://github.com/wazuh/wazuh/issues/13074#issuecomment-1098321857) says 450 of 1,000+ machines responded; this motivates rollout assurance as well as editing. One case is not broad demand. |
| [Core #3337: integrator SQLite plugin](https://github.com/wazuh/wazuh/issues/3337), open; 7 / 1 | SOC acknowledgement/classification; [proof-of-concept output works, UI unfinished](https://github.com/wazuh/wazuh/issues/3337#issuecomment-495991801). Author plus two project-side participants are not seven adopters. |
| [Core #33328: send selected alerts to case management](https://github.com/wazuh/wazuh/issues/33328), open; 0 / 0 | 4.14.1 Cloud request for single/bulk manual escalation and auditability; automatic forwarding over-escalates. Specific workflow evidence with no endorsement count beyond its author. |
| [Core #6726: rule criteria for every alert field](https://github.com/wazuh/wazuh/issues/6726), closed, not planned; 1 / 0 | Group/severity, IP metadata, and routing. [Closure points to a future Engine](https://github.com/wazuh/wazuh/issues/6726#issuecomment-1548107958), not delivery in 4.x. |
| [Plugins #5666: rule editor and ampersands](https://github.com/wazuh/wazuh-dashboard-plugins/issues/5666), closed, not planned; 4 / 0 | 4.4.4 CLI path works while dashboard editing fails. [Discussion](https://github.com/wazuh/wazuh-dashboard-plugins/issues/5666#issuecomment-1658247907); closure for inactivity is not fix evidence. |

## Community evidence catalog

All 21 primary sources below were read by the research workers. Original metrics are retained rather than represented as refreshed measurements. Views, replies, likes, and votes are exposure/activity, not unique buyers. Findings are attributed user reports or documentary suggestions, not experiments performed by the assistant.

### Original eleven sources

| ID and primary source | Observed discussion | Outcome and evidential limit |
|---|---|---|
| C01, [Reporting layer](https://groups.google.com/g/wazuh/c/-bYUdw0mqAI) | 52 views; 2 messages; pagination, output formats, scheduling | A proposed reporting layer expresses workflow need; no completed independent product validation |
| C02, [Module reports](https://groups.google.com/g/wazuh/c/rPn3fO7yZlg) | 160 views; 8 messages | Scheduled dashboard reporting confirmed working; equivalent module reports remain requested |
| C03, [Per-agent reporting](https://groups.google.com/g/wazuh/c/ajH6P920mlo) | 169 views; 4 messages; monthly per-agent reports | Request evidence, not a claim all native reporting is absent |
| C04, [Customer isolation](https://groups.google.com/g/wazuh/c/isfTPrB-Nnk) | 149 views; 7 messages | Isolation questions; historical/version-scoped, not a verified current vulnerability |
| C05, [Related isolation thread](https://groups.google.com/g/wazuh/c/dtSFAGhZwEs) | 37 views; 2 messages | Related concerns; original attachment was unread, so attachment-dependent assertions remain unconfirmed |
| C06, [Multitenancy](https://groups.google.com/g/wazuh/c/VvyIMqv5Qtg) | 69 views; 6 messages | Partial-isolation/tenancy concerns; saved objects and data authorization are different surfaces |
| C07, [Installed versus running kernels](https://groups.google.com/g/wazuh/c/HCtVl92gDbI) | 62 views; 2 messages | Old installed kernels remain; an updated running kernel does not prove installed vulnerable packages are false positives |
| C08, [Understanding vulnerability reports](https://forums.lawrencesystems.com/t/understanding-vulnerability-reports/21079) | 2 posts; local-access CVE context | Prioritization context matters; exploitability and remediation outcome not established |
| C09, [UniFi syslog](https://forums.lawrencesystems.com/t/process-unifi-syslog-messages-in-wazuh/25522) | 3 posts; 1 like on a reply | Setup/connector friction; not evidence that ingestion cannot work |
| C10, [TrueNAS and Wazuh](https://forums.lawrencesystems.com/t/truenas-and-wazuh/26562) | 4 posts; 2 likes on a workaround | Existing workaround is counterevidence to wholesale absence; broad compatibility not tested |
| C11, [SIEM and observability choices](https://forums.lawrencesystems.com/t/zabbix-or-graylog-or-any-seim/23558) | 7 posts; 9 likes across replies | Mixed observability/SIEM discussion; likes cannot be assigned to one Wazuh feature |

### Ten additional sources

| ID and primary source | Observed discussion | Outcome and evidential limit |
|---|---|---|
| C12, [Help me find the alerts tab on Wazuh](https://groups.google.com/g/wazuh/c/-fNsty6bIUY) | 6 readable messages plus 1 deleted placeholder; 2 interested users, one already in the first-pass report | “investigate alerts, assign them mark them as closed.” IRIS/AlertManager plugin suggested; initial compatibility warning followed by author-reported 4.14 release. No installation confirmation. |
| C13, [Silence false/positive alerts](https://groups.google.com/g/wazuh/c/YjV7_eO3c54) | 5 messages; one user's hundreds of Slack notifications for successful remote-logon events | Source filtering confirmed working; a second Sysmon question has no confirmed resolution. The alert's classification as a false positive was not independently verified. |
| C14, [Workspace / G-Suite integration](https://groups.google.com/g/wazuh/c/fqmc8OpNtIk) | 7 messages; Workspace without GCP, Wazuh hosted on AWS | Extra GCP dependency unwanted; routing proposed, no completed outcome reported. This is deployment friction, not proof native ingestion is impossible. |
| C15, [Workspace logs update](https://groups.google.com/g/wazuh/c/5mzmOEkDQzQ) | 4 messages; [community connector](https://github.com/avanwouwe/wazuh-gworkspace) | An adopter reports success; claims of all audit-event coverage were not verified. |
| C16, [Custom dashboard and user creation](https://groups.google.com/g/wazuh/c/uV5NYWYZiw8) | 3 messages; one endpoint; Workspace ingestion already works; management dashboard and SOC L1/L2 roles desired | Completion unconfirmed; a response describes an expected asset denominator, not proof that metric is implemented. |
| C17, [Alert on lack of logs](https://groups.google.com/g/wazuh/c/qXLFlUWyQMs) | 3 messages plus 1 deleted placeholder; `who` output from 40 servers; per-asset silence desired | API/script concept unconfirmed. Example filters active agents and has placeholder notification logic; offline-agent coverage cannot be claimed. |
| C18, [Missing events after Filebeat crash](https://groups.google.com/g/wazuh/c/2TC71StiLTg) | 8 messages; distributed Alma 9.7 / Filebeat 7.10.2 setup | User confirms replay restored data, interruption recurs, and Zabbix systemd monitoring was added. Root cause remains unproven; AI-generated diagnosis in a thread is not evidence. |
| C19, [Centralized SCA policy deployment](https://github.com/wazuh/wazuh/discussions/38418) | 2 comments; 3 participants; 1 displayed vote; config arrives but endpoint YAML missing | Security-setting and SCP proposals are unconfirmed; no proven root cause or successful deployment outcome. |
| C20, [Manager inventory/vulnerability visibility](https://github.com/wazuh/wazuh/discussions/38968) | 1 comment plus requester reply; 2 participants; 1 vote; 4.14.7 manager agent 000 | `disable_scan_manager=0` resolves the user's case. [Requester confirmation](https://github.com/wazuh/wazuh/discussions/38968#discussioncomment-18331513): “Both the vulnerability detection and the syscollector indices for the Wazuh Manager host are now working perfectly.” |
| C21, [pfBlockerNG logs to Wazuh](https://forum.netgate.com/topic/180605/how-to-send-pfblockerng-logs-to-remote-log-server-wazuh-siem) | 26 posts; 4 posters; workaround with 3 votes | [Closing report](https://forum.netgate.com/post/1109302) confirms upstream syslog routing, not Wazuh detection quality. Readable HTML also carries a deleted-topic banner; continued availability is uncertain. |

Additional discovery used Google Groups searches for `"false positive" rules`, `"case management"`, `"Google Workspace"`, and `"monitor" "manager" "health"`; site-scoped Lawrence/Netgate searches; and GitHub Discussions' latest listing. Search pages did not become primary sources. Reddit returned 403 or an HTML shell, including an older unsuccessful attempt, and is excluded. No private Slack/community data was accessed; public reports about Slack notifications are not private Slack access. Accounts may recur across sources.

## Native capabilities and API constraints

### Reporting and AI already exist

| Primary source | Documented capability | Constraint on any proposed addition |
|---|---|---|
| [Wazuh configured reports](https://documentation.wazuh.com/current/user-manual/reference/ossec-conf/reports.html) | Daily filtered reporting configured in XML | XML is the configuration format, not an output-format claim. The `group` filter denotes a **rule group/category**, not an authorized agent/customer group. |
| [Inventory reports](https://documentation.wazuh.com/current/user-manual/capabilities/system-inventory/generating-system-inventory-reports.html) and [branding](https://documentation.wazuh.com/current/user-manual/wazuh-dashboard/custom-branding.html) | PDF/CSV inventory output and dashboard/report branding capabilities | “Wazuh has no reports” is false. A specific missing module, schedule, scope, or completeness must be named. |
| [Cloud AI Analyst](https://documentation.wazuh.com/current/cloud-service/ai-analyst.html) | Periodic analysis of alerts, vulnerabilities, endpoints; recommendations and email/PDF output | Cloud capability is not automatically self-hosted entitlement; generic AI summaries/reporting already have a native alternative. |
| [Documented LLM enrichment](https://documentation.wazuh.com/current/proof-of-concept-guide/leveraging-llms-for-alert-enrichment.html) | An existing AI integration extension point | “Wazuh has no AI” is false; a proof of concept is not a general managed investigation service. |
| [OpenSearch 2.19 reporting](https://docs.opensearch.org/2.19/reporting/report-dashboard-index/) | Report scheduling and configurable CSV limits in 2.17+ | Upstream documentation is not proof the same plugin/version/configuration is bundled in Wazuh 4.x. |
| [OpenSearch reporting CLI](https://docs.opensearch.org/latest/dashboards/reporting/rep-cli-index/) and [cron](https://docs.opensearch.org/latest/dashboards/reporting/rep-cli-cron/) | Existing automation routes | Compare a configured existing workflow before asserting a new report service is necessary. |
| [Wazuh + Shuffle proof of concept](https://wazuh.com/blog/automating-security-reporting-and-response-with-wazuh-and-shuffle/) | 4.14.7 scheduled dual-API reporting, Slack and TheHive integration | Its bounded top-N queries and single agent page are not exhaustive totals or a production completeness guarantee. |

Cloud AI Analyst's FAQ asks “Can I customize the analysis parameters?” and answers: “Not currently. The service uses predefined parameters optimized for comprehensive security assessment.” This supports a customization hypothesis, not demand validation or proof of missing reporting.

### Server API, indexer API, and customer scope

- [Server API responses](https://documentation.wazuh.com/current/user-manual/api/requests-responses.html) can contain `failed_items` despite HTTP success; default collection size is 500 and `offset`/`limit` must be handled. A first page cannot be presented as an estate-wide total.
- [Indexer API use cases](https://documentation.wazuh.com/current/user-manual/indexer-api/use-case.html) expose indexed data; [OpenSearch pagination](https://docs.opensearch.org/latest/search-plugins/searching-data/paginate/) has different mechanics. Server and indexer credentials/permissions are separate; an MCP wrapper does not unify their authorization automatically.
- [RBAC's agent-group use case](https://documentation.wazuh.com/current/user-manual/user-administration/rbac.html#wazuh-rbac-use-case-agents-group) documents group-based server access and label-based alert filtering. Added labels affect **new alerts**, not an automatic historical rewrite. Server API agent-group authorization is distinct from indexer document-level security.
- [Dashboard multitenancy](https://documentation.wazuh.com/current/user-manual/wazuh-dashboard/multi-tenancy.html) concerns saved objects; [RBAC/DLS](https://documentation.wazuh.com/current/user-manual/user-administration/rbac.html) handles other boundaries. Neither “no tenancy” nor “tenant switch guarantees all-data isolation” is justified.
- [Cross-cluster search](https://wazuh.com/blog/managing-multiple-wazuh-clusters-with-cross-cluster-search/) already documents multi-cluster operations. Multiple cluster connections or a cluster selector are not, by themselves, principal-bound customer isolation.

### Workspace integration: native path and coverage limits

Wazuh documents [GCP Pub/Sub collection](https://documentation.wazuh.com/current/cloud-security/gcp/supported-services/pubsub.html). Google's [Workspace sharing guidance](https://support.google.com/a/answer/9320190) identifies baseline Admin, User, and Enterprise Groups events; additional OAuth/SAML events depend on eligible editions. This does not establish complete Drive/Gmail coverage.

[Workspace audit-log setup](https://docs.cloud.google.com/logging/docs/audit/configure-gsuite-audit-logs) includes super-admin enablement and an aggregated organization sink. [Cloud Logging IAM](https://docs.cloud.google.com/logging/docs/access-control) distinguishes Logs Viewer, which excludes Data Access logs, from Private Logs Viewer, which includes them; [Pub/Sub IAM](https://docs.cloud.google.com/pubsub/docs/access-control) governs consumption separately. A proposed maintained connector must account for this permission/dependency chain, not merely demonstrate one event arriving. No complete event-family/edition coverage was established.

### Health, detections, and vulnerability state

- [API RBAC reference](https://documentation.wazuh.com/current/user-manual/api/rbac/reference.html) covers permissions for manager/cluster health endpoints; [analysisd statistics](https://documentation.wazuh.com/current/user-manual/reference/statistics-files/wazuh-analysisd-state.html) expose received, processed, dropped, and queue metrics. Existing indexer API queries provide operational data; no whole-pipeline expected-source coverage follows from cluster health alone.
- [Custom rules](https://documentation.wazuh.com/current/user-manual/ruleset/rules/custom.html) and [ruleset testing](https://documentation.wazuh.com/current/user-manual/ruleset/testing.html) already support extension and logtest. Upstream OpenSearch Sigma capabilities cannot be assumed to be shipped Wazuh 4.x behavior.
- [Vulnerability detection](https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/how-it-works.html) uses inventory and CTI. Initial synchronization, restart, and content updates need not each produce every possible alert. Alerts are not interchangeable with the current vulnerability inventory: current state comes from `wazuh-states-vulnerabilities*` via the indexer, with manager API context as needed. EPSS/KEV field availability remains unverified.
- [Plugins #2063](https://github.com/wazuh/wazuh-dashboard-plugins/issues/2063) includes a maintainer report of UI upgrades shipped in 4.9.0. [Docker #1227](https://github.com/wazuh/wazuh-docker/issues/1227) has related merged [#2081](https://github.com/wazuh/wazuh-docker/pull/2081); secrets support must not be described as wholly absent.
- Future 5.x/6.x work in [security analytics #119](https://github.com/wazuh/wazuh-indexer-security-analytics/issues/119), [#276](https://github.com/wazuh/wazuh-indexer-security-analytics/issues/276), and [indexer #2028](https://github.com/wazuh/wazuh-indexer/issues/2028) is not evidence of delivery in 4.x. Conversely, an old open/closed issue does not prove the latest runtime still has its original gap.

## Six competitor comparisons

Official documentation is used for capability existence, with no product execution or competitive accuracy benchmark. The comparison asks what workflow can be reused, what Wazuh already provides, and what remains a hypothesis. **Hosted infrastructure is not necessarily managed SOC/MDR, and not every competitor capability is included in a base SaaS plan.**

| Product family | Product/deployment category | Entitlement boundary |
|---|---|---|
| Elastic Security | SIEM/XDR on self-managed Stack, Cloud Hosted, or Security Serverless | Deployment types and subscriptions differ; not all cloud/Stack features have parity |
| Security Onion | Self-deployed community network/host SOC platform; cloud images available | Pro adds commercial features/support; cloud image availability is not managed SIEM SaaS |
| Graylog | Open log management; Enterprise operations; licensed Security SIEM | Cloud and on-premises offerings; Open is SSPL source-available, not the same package as Security |
| Splunk Enterprise Security | Licensed security application over Enterprise or Cloud Platform | Essentials/Premier and SOAR/AI conditions vary; hosting alone is not MDR |
| CrowdStrike Falcon | Cloud EDR/XDR family plus a distinct Next-Gen SIEM offering | Sensor, SIEM, case, Charlotte AI, and SOAR entitlements must not be conflated |
| Microsoft Sentinel | Cloud SIEM/SOAR integrated with the Defender portal | Defender, Copilot, preview features, and Logic Apps have separate eligibility/permission/cost conditions |

### Elastic Security

[Deployment documentation](https://www.elastic.co/docs/deploy-manage/deploy#choosing-your-deployment-type) distinguishes Stack, Cloud Hosted, and Serverless. The [subscription page](https://www.elastic.co/subscriptions) extraction did not preserve entitlement checkmarks, so unverified minimum tiers below remain unknown rather than guessed.

| Documented pattern and source | Tier/version caveat | Wazuh comparison / bounded inference |
|---|---|---|
| [Create cases](https://www.elastic.co/docs/explore-analyze/cases/create-cases) / [manage cases](https://www.elastic.co/docs/explore-analyze/cases/manage-cases): assignee, status, attachments, activity, alert-status synchronization | Exact minimum entitlement for assignment/connectors not verified | Reusable analyst ownership pattern; Wazuh case requests and existing external tools must both be considered |
| [AI Assistant](https://www.elastic.co/docs/solutions/security/ai/ai-assistant) and [knowledge base](https://www.elastic.co/docs/solutions/security/ai/ai-assistant-knowledge-base#add-knowledge): private/global knowledge, indices/docs, citations, case comments | Enterprise Stack or EASE/Security Analytics Complete Serverless plus LLM privileges | Grounds an evidence-linked assistance hypothesis; Wazuh already has AI Analyst/enrichment, so “add AI” is not the gap |
| [Rule execution monitoring](https://www.elastic.co/docs/solutions/security/detect-and-alert/monitor-rule-executions) / [fill gaps](https://www.elastic.co/docs/solutions/security/detect-and-alert/fill-rule-gaps): warnings and execution gaps | Automatic gap-filling paid tier not established; scheduled detections differ from Wazuh stream rules | Inspiration for coverage/health explanation, not one-to-one engine equivalence |
| [Scheduled reports](https://www.elastic.co/docs/explore-analyze/report-and-share/automating-report-generation#schedule-report-generation) | Stack PDF/PNG/CSV; Serverless scheduled Discover CSV only; minimum commercial tier unknown | Scheduling is an established pattern, but native Wazuh/OpenSearch reporting is counterevidence to blanket absence |

[Agent Builder/workflows documentation](https://www.elastic.co/docs/solutions/security/ai/agent-builder/agent-builder) describes a 9.4 context, not a baseline capability of all Elastic deployments. Its relevant entitlement was not verified. No inference about Wazuh runtime absence follows from that documentation alone.

### Security Onion

The main comparison uses established **2.4** documentation. [Pro](https://securityonion.com/pro) adds commercial features/support and does not include higher Elastic licenses. Neither Pro nor deployable cloud images were verified as a hosted managed SIEM service.

| Documented pattern and source | Tier/version caveat | Wazuh comparison / bounded inference |
|---|---|---|
| [2.4 cases](https://docs.securityonion.net/en/2.4/cases.html): escalate, assign, status, comments, attachments, observables, history | Community capability; Pro time tracking is additional | Strong example of a usable case workflow without inventing a new concept; external Wazuh case integrations may already suffice |
| [2.4 detections](https://docs.securityonion.net/en/2.4/detections.html): status, tuning, history | Engine/content-specific; not arbitrary Wazuh-rule compatibility | Suggests maintained detection operations, not proof Wazuh lacks rules or testing |

**Separate 3.x examples:** Pro [Onion AI](https://docs.securityonion.net/en/3/main/onion-ai/) describes queries/cases/detections with interactive approval. [Agent Studio alert triage](https://docs.securityonion.net/en/3/main/agent-studio/#alert-triage) cannot acknowledge, escalate, or change alerts; do not portray every AI feature as autonomous response. Pro [reports](https://docs.securityonion.net/en/3/main/reports/) describe PDF case/productivity and CSV output, with scheduling not verified here. [Manager of Managers](https://docs.securityonion.net/en/3/main/manager-of-managers/) switches between grids rather than merging all their data. These 3.x sources are not attributed to 2.4.

### Graylog

[Pricing](https://graylog.org/pricing/) distinguishes free SSPL Open, commercial Enterprise, and licensed Security, which includes Enterprise. [Security prerequisites](https://go2docs.graylog.org/current/what_more_can_graylog_do_for_me/graylog_security.html#Prerequisites) matter: Open log management is not the complete SIEM. The Cloud product page returned 403; full cloud/on-premises parity was not verified.

| Documented pattern and source | Tier/version caveat | Wazuh comparison / bounded inference |
|---|---|---|
| [Investigations](https://go2docs.graylog.org/current/what_more_can_graylog_do_for_me/investigations.htm) / [alerts](https://go2docs.graylog.org/current/what_more_can_graylog_do_for_me/investigations_and_alerts.htm): team assignment, status, evidence, automatic attachment | Security feature | Reusable controlled-investigation workflow; auto-attachment should not be mistaken for the selective escalation Wazuh users request |
| [Reporting](https://go2docs.graylog.org/current/interacting_with_your_log_data/reporting.html): formats, scheduling, delivery history; [audit log](https://go2docs.graylog.org/current/interacting_with_your_log_data/audit_log.html#ViewAuditLogEntries) | Enterprise; optional audit signing disabled by default | Delivery/audit history can improve experience; history or signing is not blanket immutable evidence, and Wazuh reporting exists |
| [Agentic framework](https://go2docs.graylog.org/current/setting_up_graylog/graylog_agentic_framework.htm) and investigation reports | Framework Enterprise; AI investigation reports Security; external AI versus local Ollama paths differ | AI hosting/data egress must be explicit rather than treating all assistants as local/private |
| [Sigma rule events](https://go2docs.graylog.org/current/what_more_can_graylog_do_for_me/sigma_rule_events.htm): Git/file imports, schedules, streams, notifications | Security 7.2+; direct imports with `event_count`/`value_count` unsupported | Maintained rule lifecycle is transferable; Sigma does not imply universal semantic compatibility |

Graylog's official [MCP documentation](https://go2docs.graylog.org/current/setting_up_graylog/graylog_mcp.htm) says: “Use MCP only in controlled, non-production environments.” Existing user permissions and licensing still apply. This is an interoperability precedent, not a production recommendation or proof that third-party Wazuh MCP projects are equivalent.

### Splunk Enterprise Security

[ES editions](https://help.splunk.com/en/splunk-enterprise-security-8/enterprise-security-editions/overview-of-splunk-enterprise-security-editions) distinguish Essentials, with core cloud/on-premises security functions, from Premier, including SOAR/UEBA. Enterprise is the self-managed platform; Cloud Platform is hosted. Not every ES capability is a base platform feature.

| Documented pattern and source | Tier/deployment caveat | Wazuh comparison / bounded inference |
|---|---|---|
| [Investigations](https://help.splunk.com/en/splunk-enterprise-security-8/user-guide/8.8/mission-control/start-investigations-in-splunk-enterprise-security): selected findings, multiple findings per investigation, owner, status, disposition, history | ES application, not unlicensed base log collection | Closely matches selective escalation and accountable work; a mature pattern, not proof of unmet demand after Wazuh integrations |
| [Actions/playbooks](https://help.splunk.com/en/splunk-enterprise-security-8/user-guide/8.8/mission-control/automate-your-investigation-response-with-actions-and-playbooks-in-splunk-enterprise-security) | Integrated approval/playbook use requires SOAR Cloud | Human approval and backend authorization are separate concerns; compare with existing Shuffle integrations |
| [Risk-based alerting](https://help.splunk.com/en/splunk-enterprise-security-8/user-guide/8.8/mission-control/analyze-risk-with-risk-based-alerting-in-splunk-enterprise-security#ariaid-title2) | Asset/identity risk and intermediate risk findings, not merely per-alert severity | A context/prioritization pattern; not equivalent to relabeling Wazuh severity or proven accuracy |
| [Scheduled reports](https://docs.splunk.com/Documentation/Splunk/9.4.2/Report/Schedulereports) | Custom cron; `schedule_search` permission; execution as report owner matters | Scheduling and execution identity are established constraints, not a novel feature or permission-free export |

AI assistance has cloud/edition/regional conditions: Essentials Cloud availability differs from Premier Cloud Connect for on-premises use. Do not describe it as universally included. These sources do not establish independent gains in analyst accuracy or efficiency.

### CrowdStrike Falcon

Falcon's cloud EDR/XDR context differs from a Wazuh-based service; the vendor also describes [Next-Gen SIEM as a distinct offering](https://www.crowdstrike.com/en-us/platform/next-gen-siem/). Endpoint containment must not be attributed to case-management functionality or assumed to be included with every SIEM subscription.

| Documented pattern and source | Tier/evidence caveat | Wazuh comparison / bounded inference |
|---|---|---|
| [Official case API/MCP module](https://developer.crowdstrike.com/falcon-mcp/modules/cases/): owners/status, evidence, templates, custom fields, SLAs | Exact case bundle unverified; inspected scopes include Cases READ/WRITE and templates READ | Cases and an official MCP surface are reusable interoperability patterns; neither alone proves a missing Wazuh business need |
| Same module: create/update with optimistic versioning, evidence attachment | Tool/API description, not executed here | Controlled state transitions and auditability are more concrete than a generic chat interface |
| [Charlotte AI](https://www.crowdstrike.com/en-us/platform/charlotte-ai/): explained verdicts and triage confidence | Vendor claims, not verified accuracy; [pricing](https://www.crowdstrike.com/en-us/platform/charlotte-ai/agentic-soar/pricing/) separates Essentials from fuller agentic/SOAR entitlements | Grounded explanations are a pattern to evaluate; Essentials does not imply Detection Triage Response Agent or all connectors |
| [Fusion workflows](https://developer.crowdstrike.com/ngsiem/fusion-soar/): manual/scheduled/event triggers, branches, loops, queries, external APIs | Full Agentic SOAR conditions include credits/fair use; entitlement must be checked | Workflow automation is not the same product as EDR sensor action or a case record |

The official competitor MCP demonstrates a supported integration direction. It is not evidence that any particular third-party Wazuh MCP is endorsed, safe, or ready for the same deployment.

### Microsoft Sentinel

Sentinel is cloud SIEM/SOAR in the [Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-defender-portal), not a blanket entitlement to every Defender feature. Copilot requires [provisioned capacity and applicable eligibility](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot); it is not universally included with base Sentinel.

| Documented pattern and source | Tier/preview/operation caveat | Wazuh comparison / bounded inference |
|---|---|---|
| [Defender incident cases](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management): ownership, evidence, tasks, history | Incident cases are preview, Defender-portal-specific, with license conditions | Reusable case/accountability pattern; do not attribute unconditional availability to all Sentinel tenants |
| [Analytics incident creation/grouping](https://learn.microsoft.com/en-us/azure/sentinel/create-analytics-rules#configure-the-incident-creation-settings) | Defender correlation can override grouping | Grouping is not guaranteed deduplication or proof of better detection |
| [Incident-linked summaries](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-incident-summary) / [Sentinel Copilot integration](https://learn.microsoft.com/en-us/azure/sentinel/sentinel-security-copilot#integrate-microsoft-sentinel-with-copilot-in-defender) | Copilot provisioning/eligibility applies | Evidence-linked assistance is a candidate UX, not a reason to ignore Wazuh's existing AI |
| [Cross-workspace/tenant operations](https://learn.microsoft.com/en-us/azure/sentinel/extend-sentinel-across-workspaces-tenants) and [multitenant automation permissions](https://learn.microsoft.com/en-us/azure/sentinel/automate-incident-handling-with-automation-rules#permissions-in-a-multitenant-architecture) | Lighthouse delegation and explicit permissions; Logic Apps add costs/permissions | Customer scope must be enforced, not inferred from a selector; Wazuh already has RBAC/DLS and cross-cluster options |
| [Content hub](https://learn.microsoft.com/en-us/azure/sentinel/sentinel-solutions), [connector health](https://learn.microsoft.com/en-us/azure/sentinel/monitor-data-connector-health), [MITRE coverage](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage) | Named content maintainers/updates; health for selected connectors with SentinelHealth enabled; active/simulated coverage preview | Maintenance and telemetry-health patterns are relevant; ATT&CK mapping is not proof of effective detection coverage |

## Existing alternatives before building

The relevant comparison is not “custom SaaS versus nothing.” Existing native functions and integrations can invalidate the opportunity. No third-party case tool or plugin was installed or endorsed in this research; present licensing/compatibility must be checked rather than assuming every edition is free.

| Existing route | What evidence supports it | What remains open |
|---|---|---|
| IRIS / AlertManager plugin | [C12](https://groups.google.com/g/wazuh/c/-fNsty6bIUY) suggestions and author-reported plugin release | Integration completeness, permissions, maintenance, and actual user installation outcome |
| TheHive via Shuffle | [Official Wazuh proof of concept](https://wazuh.com/blog/automating-security-reporting-and-response-with-wazuh-and-shuffle/) | Whether selective escalation/ownership/audit needs are already met; edition and operational overhead |
| Native reporting / OpenSearch automation | [Inventory output](https://documentation.wazuh.com/current/user-manual/capabilities/system-inventory/generating-system-inventory-reports.html), [Cloud AI Analyst](https://documentation.wazuh.com/current/cloud-service/ai-analyst.html), [CLI cron](https://docs.opensearch.org/latest/dashboards/reporting/rep-cli-cron/) | Exact Wazuh bundle, module scope, authorization, pagination, and desired customization |
| Exporters, existing monitors, scripts | [#15215](https://github.com/wazuh/wazuh/issues/15215), [#34601](https://github.com/wazuh/wazuh/issues/34601), [C18](https://groups.google.com/g/wazuh/c/2TC71StiLTg) | Maintenance burden and expected-source coverage, not just process uptime |
| Community Workspace connector / native Pub/Sub | [Reported adopter success](https://groups.google.com/g/wazuh/c/5mzmOEkDQzQ), [native collection](https://documentation.wazuh.com/current/cloud-security/gcp/supported-services/pubsub.html) | Event-family/edition coverage, useful rules, credentials, and ongoing maintenance |

Free/community alternatives are especially important disproof candidates. A supported integration, better packaging, or clearer UX may be more appropriate than recreating a case engine, connector, or reporting system.

## Four MCP foundations

### What MCP adds, and what it does not

The [MCP specification](https://modelcontextprotocol.io/specification/latest#features) defines tools, resources, and prompts as integration primitives. A read-only Wazuh investigation surface could let an AI host fetch alerts, current state, and agent context consistently. MCP does not provide AI correctness, customer isolation, complete queries, or a business case by itself.

The following are **third-party repositories, not Wazuh-organization endorsements**. Counts exclude pull requests from open issues. Stars/forks are visibility snapshots, not market size or readiness. Inspection used source and documentation, not execution or a security audit. All have test sources; none were run in this investigation. Links to `main` are mutable.

| Candidate and root license | Visibility snapshot: stars / forks / open issues | Inspected interface and scope |
|---|---|---|
| [gensecaihq/Wazuh-MCP-Server](https://github.com/gensecaihq/Wazuh-MCP-Server), MIT | 262 / 68 / 2 | Python Streamable HTTP `/mcp`; `/sse` returns 410; 55 default tools: 41 reads, 14 writes; manager + indexer; additional multi-cluster listing tool |
| [lidless-labs/wazuh-mcp](https://github.com/lidless-labs/wazuh-mcp), MIT | 8 / 1 / 6 | TypeScript, 28 registrations; stdio/Streamable HTTP; manager read surface and indexer POST searches; no active-response tools |
| [0xFl4g/wazuh-mcp](https://github.com/0xFl4g/wazuh-mcp), MIT | 0 / 0 / 0 | Python stdio/HTTP; 27 registered tools: 18 reads, 9 writes; tenant policies/credential pools; README heading still says 17 |
| [socfortress/wazuh-mcp-server](https://github.com/socfortress/wazuh-mcp-server), AGPL-3.0-only in manifest | 94 / 26 / 3 | Python stdio/HTTP bearer secret; 10 registered tools versus README's 9; manager-only agents, inventory, rules, SCA; current registered tools nonmutating |

### Candidate-specific constraints

**gensecaihq:** inspected `src/wazuh_mcp_server/toolsets.py` and `server.py` support read/write scope checks; API keys default to read-only. Multi-cluster routing is not proof of tenant isolation: the inspected [dispatch path](https://github.com/gensecaihq/Wazuh-MCP-Server/blob/main/src/wazuh_mcp_server/server.py#L2931-L2983) takes a `cluster_id` from arguments and resolves it through the [registry](https://github.com/gensecaihq/Wazuh-MCP-Server/blob/main/src/wazuh_mcp_server/clusters.py#L93-L116), with no principal binding observed in that path. This is a scoped review concern, not a whole-project exploit finding. Compatibility documentation claims 4.8-4.14.7; older versions were not rechecked. [Issue #140](https://github.com/gensecaihq/Wazuh-MCP-Server/issues/140) reports external identity-provider/dynamic-client-registration incompatibility.

**lidless-labs:** the [manager client GET guard](https://github.com/lidless-labs/wazuh-mcp/blob/main/src/client.ts#L223-L235) is separate from authentication; indexer searches use POST without implying a write. HTTP bearer clients share an upstream identity, so per-user isolation does not follow from “read-only.” README reports least-privilege checks with 4.14.8, not a security certification. [Issue #37](https://github.com/lidless-labs/wazuh-mcp/issues/37) requests aggregations; the present 10,000-hit window is not proof of complete result totals.

**0xFl4g:** inspected `src/wazuh_mcp/server.py` registers 27 tools. Tenant context comes from a validated JWT/API key; session policies and credential pools default-deny unknown tenants. An empty write allowlist denies writes, but omitting it does not further restrict RBAC-allowed writes. A caller-supplied `confirm=true` is not proof of human approval. The [downstream API path](https://github.com/0xFl4g/wazuh-mcp/blob/main/src/wazuh_mcp/wazuh/server_api.py#L308-L382) adds a `run_as` query parameter after service-JWT authentication; that is not the official [authorization-context login](https://documentation.wazuh.com/4.14/user-manual/api/rbac/auth-context.html#authorization-context-login-method) at `/security/user/authenticate/run_as`. Effective human identity enforcement in Wazuh remains unverified. README testing with 4.9 does not prove latest-version support.

**SOCFortress:** [registered source](https://github.com/socfortress/wazuh-mcp-server/blob/main/wazuh_mcp_server/server.py) has 10 current nonmutating tools and read-only filtering; no registered alert-search, vulnerability, or active-response tool was found. Thus it is narrower than a full investigation backend, not a failed implementation of every possible tool. The [manifest](https://github.com/socfortress/wazuh-mcp-server/blob/main/pyproject.toml) marks Beta and AGPL-3.0-only; GitHub/root-license identification reports AGPL-3.0. A Wazuh version range was not verified.

### Licensing, transport, and security boundaries

Root MIT licenses do not clear dependencies, trademarks, or every commercial redistribution detail. AGPL review should consider modified network-served source obligations; it does **not** mean every surrounding SaaS component must automatically be open source. Dependency inventories and a deployment-specific legal review were not performed. No MCP candidate is selected for adoption.

| Boundary | Source-backed constraint / practical implication |
|---|---|
| Transport authorization | [MCP authorization](https://modelcontextprotocol.io/specification/latest/basic/authorization#protocol-requirements) is optional at the protocol level; HTTP implementations that implement it follow the specified OAuth 2.1 discovery/audience requirements. Stdio generally obtains credentials from the environment, not this HTTP authorization framework. Do not claim every MCP server must implement OAuth. |
| Token boundaries | [Token passthrough is forbidden](https://modelcontextprotocol.io/specification/latest/basic/security_best_practices#token-passthrough) in the specified authorization model. MCP-facing credentials and upstream Wazuh credentials have different audiences and authority. |
| Tool execution | [Tool security considerations](https://modelcontextprotocol.io/specification/latest/server/tools#security-considerations) require treating tool use as a security boundary. An annotation such as read-only, a confirmation field, or a UI approval does not replace backend authorization. |
| Untrusted log content | Attackers can influence logs and thereby prompt-inject an AI investigator. Apply the [tool security boundary](https://modelcontextprotocol.io/specification/latest/server/tools#security-considerations): retrieved event text is data, not instructions to invoke tools, reveal credentials, or change customer scope. |
| Data egress | A locally running MCP server does not mean local AI inference: the host can send security data to an external model. Minimize/redact data and clarify host/model retention and access before any sensitive use. |
| Customer scope | Manager API and indexer permissions are separate. Cluster routing, shared service credentials, and “read-only” still permit data disclosure if scopes are wrong; no cross-tenant safety claim was demonstrated here. |
| Completeness and provenance | Preserve source IDs/query scope, pagination, partial failures, time bounds, and citations. Do not report top-N hits or one API page as exhaustive findings, and do not silently turn missing access into “no risk.” |

A read-only, evidence-linked investigation foundation is meaningful, but it remains an enabler. Selecting it would not resolve which user problem deserves a service, nor establish readiness for active response.

## Opportunity matrix and disproof criteria

These are competing hypotheses, not numeric market/safety/readiness scores. A disproof criterion is a useful way to reject scope, not a requirement to invent extra assignment work. Evidence links point back to the underlying claims rather than counting competitors as buyers.

| Hypothesis / target job | Evidence and reusable pattern | Competing explanation or existing route | What would disprove the proposed value |
|---|---|---|---|
| Analyst-controlled cases with optional grounded assistance / SOC analyst | [C12](https://groups.google.com/g/wazuh/c/-fNsty6bIUY), [#33328](https://github.com/wazuh/wazuh/issues/33328); cases across six competitors | IRIS/plugin/TheHive + Shuffle already deliver the needed ownership, selection, evidence, and closure | The target workflow is adequately met with those tools; extra service adds switching cost without useful simplification |
| Reliable customer report packs / self-hosted operator or MSSP | [C01](https://groups.google.com/g/wazuh/c/-bYUdw0mqAI), [C02](https://groups.google.com/g/wazuh/c/rPn3fO7yZlg), [C03](https://groups.google.com/g/wazuh/c/ajH6P920mlo), [plugins #3813](https://github.com/wazuh/wazuh-dashboard-plugins/issues/3813); delivery/scheduling patterns | Native reports, Cloud AI Analyst, or existing OpenSearch automation | Existing authorized output already covers exact modules, complete data, schedule, and customization |
| Maintained detection/coverage content / detection engineer | [#15451](https://github.com/wazuh/wazuh/issues/15451), [#13074](https://github.com/wazuh/wazuh/issues/13074); content lifecycle/health in competitors | Existing rules, custom-rule tests, and configuration fix the observed pain | No meaningful maintenance/rollout gap remains, or translation cannot preserve the required semantics |
| MSSP customer-scope workflow / customer operations | [#14225](https://github.com/wazuh/wazuh/issues/14225), [#32193](https://github.com/wazuh/wazuh/issues/32193); delegated-scope patterns | Labels/RBAC/DLS/CCS solve scope and reports without another data store | Configuration already solves the intended workflow; safe scope cannot be maintained across the proposed APIs |
| Maintained Workspace coverage / consultant or administrator | [#10776](https://github.com/wazuh/wazuh/issues/10776), [C14](https://groups.google.com/g/wazuh/c/fqmc8OpNtIk), [C15](https://groups.google.com/g/wazuh/c/5mzmOEkDQzQ); maintained connectors/content | Native Pub/Sub or community connector plus current rules are sufficient | Required event families, useful detections, and maintenance are already covered for the target edition/deployment |
| Expected-telemetry health / platform operator | [#15215](https://github.com/wazuh/wazuh/issues/15215), [C17](https://groups.google.com/g/wazuh/c/qXLFlUWyQMs), [C18](https://groups.google.com/g/wazuh/c/2TC71StiLTg); connector-health patterns | Exporters, counters, Zabbix, and runbooks already suffice | They already detect the required silent sources and interruptions with acceptable maintenance |
| Vulnerability context / remediation owner | [C07](https://groups.google.com/g/wazuh/c/HCtVl92gDbI), [C08](https://forums.lawrencesystems.com/t/understanding-vulnerability-reports/21079); asset/risk context patterns | Current inventory/CTI plus asset metadata is enough | Existing workflow already produces useful prioritization, or proposed enrichment lacks reliable source fields |

Deployment automation remains another hypothesis, supported by individually strong requests but without a demonstrated standalone SaaS need. MCP is intentionally not a row: it can support several opportunities without proving any of them.

## Evidence limits and unresolved selection

- Counts are snapshots with filter and overlap bias. Open status is not proof of a current gap; closed/not-planned status is not proof of a fix. Twelve core issues share one author, and activity across linked threads can involve the same accounts.
- Comments include authors, maintainers, bots, and engineering dialogue. Reactions/views are not unique organizations, willingness to pay, independent adoption, or a measured market ranking. GitHub association `NONE` is not employment proof.
- The #10776 REST/available discrepancy is unresolved. The unread isolation attachment, deleted placeholders, Netgate banner, Reddit access failures, and unreviewed enhancement bodies remain gaps; inaccessible material did not become evidence.
- Official docs establish described capabilities, not successful execution in a relevant Wazuh deployment. Mutable repository branches, changing subscriptions, unknown entitlements, preview features, and separately versioned Security Onion documentation limit the comparisons.
- No lab reproduction, MCP test execution, penetration/security audit, independent AI-accuracy test, dependency/license clearance, interviews, or purchase-intent validation occurred. User-confirmed outcomes remain attributed reports, not assistant-run experiments.

Optional follow-up can examine one exact workflow against the relevant Wazuh version and existing alternatives, with server/indexer permission boundaries and complete-data semantics explicit. A focused demonstration, a configuration comparison, or direct user feedback could disprove a hypothesis; none is presented as an extra mandatory assignment stage. Avoid claiming customer isolation, zero loss, effective detection coverage, or AI accuracy without relevant evidence.

**I had not selected a service at this stage.** I kept the hypotheses open to reject, narrow, or choose in the next discussion. This report and the [process notes below](#retrospective-process-context-how-the-expansion-was-produced) record the evidence and AI recommendations, not a decision I had already made.

<!-- RESEARCH-PROCESS-CONTEXT -->

---

## Retrospective process context: how the expansion was produced

I reconstructed this section from retained task exchanges. The recovered source body was hash-verified before the editorial changes. I preserved its findings, chronology, and unresolved-selection status while editing the narration into first person, adding the language note and process record, and replacing two obsolete links with integrated process navigation. I labelled translated excerpts and summaries separately. This is an annotated editorial presentation, not a byte-exact historical file.

### My request

After the pause described in [V1](RESEARCH-v1.md#retrospective-process-context-how-this-draft-was-produced), I explicitly asked to resume research.

**My request (translated message):**

> Continue the earlier research. Expand it in detail and produce a report citing where you obtained the data.

I wanted a detailed expansion with sources. I then added integration foundations and competitor patterns:

**My request (translated message):**

> Add information about a possible MCP to the research too, because it could serve as a foundation for many AI integrations.

**My request (translated excerpt):**

> I also want you to add information about alternatives to Wazuh and which SaaS features they have that Wazuh lacks, based on Elastic, Security Onion, Graylog, Splunk, CrowdStrike Falcon, Microsoft Sentinel, and others.

I wanted to assess MCP as a possible foundation and compare established alternatives rather than require novelty. I had not established that every competitor feature was absent from Wazuh.

### AI response

**AI response (translated excerpt):**

> I will treat it as a possible integration foundation, not as an already selected solution.

In its expanded-report response, the AI revised its earlier reporting lead:

**AI response (translated excerpt):**

> In addition to reporting, we now have a concrete candidate: **helping the analyst move from an alert to an investigation with an owner, evidence, and closure**, with AI as support rather than a substitute for their decision.

I treated analyst-controlled investigations as another candidate, not my final choice. Existing case tools and native reporting/AI could still invalidate a new service.

### Output produced

The AI produced a 455-line catalog combining the original label-bounded inventories, eight supplementary issue threads, 21 public community sources, native-feature counterchecks, six competitor families, and four third-party MCP projects. The main assistant synthesized independent bounded reports; documentation/source inspection was not runtime validation or consensus. Reporting retained broader observed engagement than the newer case-workflow evidence. I kept licensing, permissions, version differences, and successful workarounds visible as counterevidence.

### My changes and permission limits

I authorized expanded public-source collection and local documentation, not a product choice, MCP adoption, installation, security certification, or response actions against systems. The research did not include interviews or purchase-intent validation. I kept these Phase 2 research files local and later permitted selected task excerpts here, not disclosure of the private conversation as a whole.

### Subsequent stage, not knowledge available to this report

A later decision summary duplicated the research. I questioned overlap with the existing security stack, explored earlier recognition, and then asked for one short comparison rather than another extensive catalog. The AI deleted the separate brief and produced [V3](RESEARCH-v3.md#retrospective-process-context-how-the-short-comparison-was-produced) to compare two needs. I kept those later simplifications and choices separate from this earlier research stage.
