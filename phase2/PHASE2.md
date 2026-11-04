# Phase 2: Finding a User Need

I chose a conversational AI investigation assistant for Wazuh Cloud. I wanted authorized users to query and understand their security data without manually exporting corporate context to unapproved tools. AI would be the main capability, not an optional addition to ticket management.

## 1. Which needs did you find, and where did each one come from?

I asked the AI to research open requests, comments, reactions, public discussions, documentation, and competitors within a defined scope. Labels varied between repositories; this was not a census of every Wazuh issue or organization. Not every idea came from a community request.

| Need | Where it came from |
|---|---|
| Alert ownership and follow-up | A [discussion](https://groups.google.com/g/wazuh/c/-fNsty6bIUY) asks to investigate, assign, and close alerts. [Issue #33328](https://github.com/wazuh/wazuh/issues/33328) requests selected manual escalation and an audit trail instead of forwarding everything. |
| Customer and management reports | Separate threads request [complete exports](https://groups.google.com/g/wazuh/c/-bYUdw0mqAI), [scheduled module reports](https://groups.google.com/g/wazuh/c/rPn3fO7yZlg), and [per-agent output](https://groups.google.com/g/wazuh/c/ajH6P920mlo). One requester confirms native dashboard scheduling works. |
| Earlier attack recognition | I supplied vendor articles from [Logstail](https://logstail.com/blog/early-signs-of-a-cyber-attack-why-soc-teams-often-miss-them) and [Labyrinth](https://www.labyrinth.tech/post/preemptive-security-the-missing-layer-in-modern-socs), then a [paper](https://doi.org/10.3390/info11120560), to explore related weak signals. These were not direct user requests. |
| Integration, source health, and customer scoping | [Workspace coverage](https://github.com/wazuh/wazuh/issues/10776), [metrics](https://github.com/wazuh/wazuh/issues/15215), and [MSSP metadata](https://github.com/wazuh/wazuh/issues/32193) exposed narrower operational needs, with existing alternatives to check. |
| Controlled AI investigation | This came mainly from my Prowler MCP/Lighthouse experience, public analogs, and corporate data-handling constraints. [Prowler MCP](https://docs.prowler.com/getting-started/products/prowler-mcp) and [Lighthouse](https://github.com/prowler-cloud/prowler/blob/master/docs/user-guide/tutorials/prowler-app-lighthouse.mdx) helped distinguish an integration interface from a user-facing assistant. |

The follow-up requests do not prove people asked for private chat. I kept the previous options in the [research account](research/RESEARCH.md) and [research history](research/RESEARCH-HISTORY.md); pending-choice statements there describe earlier stages.

## 2. Which ones did you discard, and why?

Before this choice, I favored alert follow-up: ownership, investigation states, and tickets. It had direct community support, and I had seen those workflows work well at Prowler. I used that experience as a qualitative reference, not adoption evidence. Existing alternatives mattered too: [Wazuh Alert Manager](https://github.com/xrisbarney/Wazuh-alert-manager) documents cases and optional AI; Wazuh publishes a [Shuffle automation example](https://wazuh.com/blog/automating-security-reporting-and-response-with-wazuh-and-shuffle/), and its [Integrator guide](https://documentation.wazuh.com/current/user-manual/manager/integration-with-external-apis.html) links a Jira issue-creation script. None proves a complete maintained follow-up service, but simply creating tickets was not enough.

Late in drafting, I paused and asked the AI to reread the assignment with me, especially Phase 3. I then recognized an implicit expectation that AI would be part of the service, not only used to build it. The introduction describes extending Wazuh with AI; Phase 3 asks about AI calls, answer quality and degradation, and model outages. I had not connected those questions to the selection criterion earlier, and the assistant had not flagged it either.

Had I accounted for that emphasis earlier, the selection would have been more focused and direct. AI could have fitted follow-up, reporting, or earlier recognition; those options were not invalid, but AI had not been central to how I framed them. Once it became a key criterion, I preferred to make the AI capability itself the useful service: assisted investigation within approved corporate data boundaries.

I remained interested in earlier recognition, but it needs suitable retained data and a credible comparison against false associations. The paper uses Snort and CICIDS2017, not Wazuh, and does not demonstrate operational lead-time or workload gains. Vendor examples are not independent validation; [native correlation](https://documentation.wazuh.com/current/user-manual/ruleset/ruleset-xml-syntax/rules.html) already exists. I put it aside because of scope and the cost of a credible argument, not because it is a bad idea.

Generic reporting overlaps native reports and AI Analyst. Connector maintenance, source health, and customer scoping remain useful, but gave me a less convincing AI-centered service to pursue here.

## 3. Which one did you choose, who would benefit from it and how do they handle it today?

I chose the need to query, understand, and investigate Wazuh security data with AI under organizational controls. The main users would be analysts and detection engineers who need context behind an alert or observation. Today they can use dashboards, documentation, APIs, and manual queries, or approved internal AI systems, business providers, and community tools. I considered those existing options rather than assuming nobody had an assistant.

I wanted to reduce the risk of someone copying logs, alerts, or configuration into an unapproved AI tool to get help. I did not measure how often that happens. Approved business providers can be legitimate under company policy; this is not a blanket warning against ChatGPT. A no-training policy alone does not settle processing location or retention, as the [API data controls](https://developers.openai.com/api/docs/guides/your-data) distinguish.

Wazuh's [AI Analyst](https://documentation.wazuh.com/current/cloud-service/ai-analyst.html) already provides periodic, multi-source analysis of alerts, endpoints, vulnerabilities, and patterns, with recommendations and email/PDF output. I framed the opportunity as on-demand contextual investigation, not another generic summary. Wazuh-owned repositories also contain [assistant integration examples](https://github.com/wazuh/integrations/tree/9639b046e8846d2fae482bd4173960fb235fc8ac/integrations/AI_assistant), offered as-is rather than proof of a supported product. The bounded research I requested did not verify a supported first-party Wazuh MCP service. That is not proof that Wazuh has no chat or MCP work.

I would propose a Wazuh-owned assistant operated by Wazuh, with a proposed Wazuh-maintained MCP interface for authorized evidence access and self-operated model inference inside Wazuh Cloud. In this baseline, prompts and evidence would not go to external AI services. I was proposing an assistant, not a proprietary foundation model trained for this task. This would be a platform proposal, not a claim that current Cloud customers can install models on managed nodes. The processing boundary would be the Wazuh-operated platform, not necessarily customer-owned infrastructure.

That boundary needs validation across the host application, MCP, model, backend permissions, tenant separation, logs, telemetry, retention, and egress. [MCP does not dictate model use](https://modelcontextprotocol.io/docs/learn/architecture). Self-operated inference would allow Wazuh to apply controls; neither that nor official MCP maintenance would automatically prove security or compliance. In Phase 3, I would explain those controls, how they would be evaluated, and their operational cost.

## 4. Which service ideas did you consider before reaching yours, and what made you drop them?

I considered a report generator, a complete case-management/SOAR replacement, earlier attack hunting, and a broader compromise-assessment service. Existing tools overlap the first two; the latter directions demand stronger evidence and wider scope. The [CrowdStrike assessment example](https://www.crowdstrike.com/content/dam/crowdstrike/marketing/en-us/documents/pdfs/data-sheets/compromise-assessment.pdf) describes a professional service, not proof of a missing automated Wazuh product.

I treated MCP as a component, not an end-user product. A chat that simply forwards context to an external model would not meet the processing boundary I chose, although external providers are not universally unsafe. I used Prowler's Lighthouse as a product analogy, not proof that every Prowler deployment runs inference locally.

My proposed assistant would start read-only: consult evidence, explain what supports an answer, distinguish uncertainty, and suggest further checks. It would not write or apply rules in Wazuh, trigger Active Response, block systems, or become an unrestricted agent. AI being central does not mean it decides authorization or performs every mechanical step. Backend controls would enforce access; people would judge the conclusions.

I also saw potential for a reusable foundation. Stable, controlled MCP interfaces and the AI capability could later support other approved Wazuh interfaces or agent workflows, including helping detection engineers understand, draft, or test rules. These would be future possibilities, not MVP commitments or broader execution permissions.

I chose a need and a service direction, not a model or implemented architecture. In Phase 3, I would develop the data flows, controls, and evaluation plan, including answer quality and model, API, and tool costs. Neither the controls' effectiveness nor commercial value has been demonstrated by this research.
