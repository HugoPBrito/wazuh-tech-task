**Language note:** I normally communicate with coding agents in Spanish. Quoted exchanges are English translations, not messages originally written in English. Edited summaries are labelled separately.

# Phase 2 research: governed AI investigation for Wazuh Cloud

**I chose the need to help authorized users query, understand, and investigate their Wazuh security data with AI under organizational controls.** I would propose a conversational investigation assistant, with a proposed Wazuh-maintained MCP interface and inference operated inside Wazuh's controlled Cloud platform. This matches my current [Phase 2 choice](../PHASE2.md). I explored alert follow-up and earlier attack recognition before reaching this decision.

## Why this need became the choice

Late in drafting, I paused and returned to the assignment with the AI to check the fit with Phase 3. I then identified the requirement for AI inside the service, not just AI used to prepare it. I had not identified that requirement earlier, and the assistant had not flagged it either. The assistant acknowledged that tickets, states, and assignments had pushed AI into a peripheral role. AI could have supported any earlier option; I changed my criterion rather than treating those options as invalid.

I treated this need as a hypothesis informed by experience and public analogs, not validated market demand. Analysts and detection engineers may want help understanding security evidence without copying corporate context into unapproved tools. I did not measure that behavior. Approved internal systems and business providers can already be legitimate alternatives under organizational policy.

## What the existing evidence supports

| Evidence | What it supports and what it does not |
|---|---|
| [Community request to investigate, assign, and close alerts](https://groups.google.com/g/wazuh/c/-fNsty6bIUY), and [selective escalation request #33328](https://github.com/wazuh/wazuh/issues/33328) | Direct evidence of follow-up friction, not proof that users requested private chat or would pay for it. |
| Requests for [complete exports](https://groups.google.com/g/wazuh/c/-bYUdw0mqAI), [module schedules](https://groups.google.com/g/wazuh/c/rPn3fO7yZlg), and [per-agent reports](https://groups.google.com/g/wazuh/c/ajH6P920mlo) | Reporting remains a credible alternative. One requester confirms dashboard scheduling works; reporting is not wholly absent. |
| [Prowler MCP](https://docs.prowler.com/getting-started/products/prowler-mcp) and [Lighthouse tutorial](https://docs.prowler.com/user-guide/tutorials/prowler-app-lighthouse) | Public examples distinguish an integration interface from a read-only assistant experience; they do not prove all inference runs locally. |

I retained the sources and original measurements rather than refreshing them. Labels, replies, reactions, and recurring accounts do not form a customer census. The [expanded catalog](RESEARCH-v2.md) preserves the broader evidence and its limits.

## Alternatives and counterevidence

**Alert follow-up** had clearer direct community support. I also considered [Wazuh Alert Manager](https://github.com/xrisbarney/Wazuh-alert-manager), [Shuffle automation](https://wazuh.com/blog/automating-security-reporting-and-response-with-wazuh-and-shuffle/), and the [Integrator guide's Jira example](https://documentation.wazuh.com/current/user-manual/manager/integration-with-external-apis.html) as challenges to the value of another workflow tool. I treated a Jira route as a variant of follow-up, not a separate need. Those documents do not establish compatibility or a complete maintained service.

**Earlier attack recognition** interested me as a way to relate weak signals without creating more alert fatigue. The [paper](https://doi.org/10.3390/info11120560) offers a correlation method using Snort/CICIDS2017, not demonstrated Wazuh lead-time or workload gains. I put this option aside because it would need suitable retained evidence and false-association evaluation; [native correlation](https://documentation.wazuh.com/current/user-manual/ruleset/ruleset-xml-syntax/rules.html) already exists.

**AI investigation also faces overlap.** [AI Analyst](https://documentation.wazuh.com/current/cloud-service/ai-analyst.html) already performs periodic, multi-source analysis with predefined parameters, advisory recommendations, and email/PDF output. I framed the opportunity as on-demand contextual investigation, not generic summaries. Wazuh-owned [assistant examples](https://github.com/wazuh/integrations/tree/9639b046e8846d2fae482bd4173960fb235fc8ac/integrations/AI_assistant) are community/as-is material, not proof of supported product status. The bounded research I requested did not verify a supported first-party Wazuh MCP service; the maintained interface remains a proposal, not a certified existing offering.

## Proposed boundary, not an implemented design

[MCP does not determine model location](https://modelcontextprotocol.io/docs/learn/architecture). Local or official MCP can still pass data to an external model. I clarified that I would propose Wazuh-operated inference: processing within the Wazuh platform, not necessarily customer-owned infrastructure or models installed on managed customer nodes.

Self-operated inference offers control, not automatic security or compliance. Permissions, tenant separation, retained conversations, telemetry, and egress still need validation. I would start the assistant read-only: it would explain supporting evidence and uncertainty and leave judgment to people. I chose a service direction, not a model or deployed architecture. API integration, model accuracy, and commercial value remain unverified; autonomous response is outside the proposed initial scope.

<!-- RESEARCH-PROCESS-CONTEXT -->

---

## Retrospective process: requests, replies, and corrections

**I reconstructed this account from retained task exchanges; it was not documented alongside the original research.** The stages below follow the order of the decisions. Each has a short account and an expandable record of the retained exchanges.

I labelled translated excerpts and edited summaries separately, including excerpts recovered from the main conversation. Where the initial AI wording was unavailable, I kept a labelled summary. Internal research-worker commentary is not a main-conversation reply. The full conversation remains private.

### 1. I began with community research, not a service choice

I asked for broad research into open Wazuh feature requests, repeated comments and reactions, forums, and documentation. Three bounded, independent AI readers checked the actual, nonuniform labels. This was not an organization-wide census, and I had not selected a need.

The AI recommended reducing the manual work needed to use Wazuh data. I then asked for sources and conversation evidence, no dates, and two local artifacts. [V1's process record](RESEARCH-v1.md#retrospective-process-context-how-this-draft-was-produced) retains those prompts.

<details>
<summary>Retained exchanges: research request and initial recommendation</summary>

**My request (translated excerpt):**

> I want you to thoroughly research all open Wazuh issues that have a "feature request" label.

**AI response (translated excerpt recovered from the main conversation):**

> **The best-supported needs are not about “adding AI to Wazuh,” but about reducing the manual work needed to turn its data into useful results.**

</details>

### 2. I resumed the research and added MCP and competitors

I paused research-document construction to continue the discussion, then explicitly resumed it and added MCP. I also requested comparisons with Elastic, Security Onion, Graylog, Splunk, Falcon, and Sentinel. The AI checked native reporting, AI, authorization, and existing integrations rather than assuming gaps.

The [expanded report](RESEARCH-v2.md#retrospective-process-context-how-the-expansion-was-produced) gave me reporting and case-workflow options to compare. MCP was a possible integration foundation, not the user need, and I had not approved a service.

<details>
<summary>Retained exchanges: MCP's role in the expanded research</summary>

**My request (translated excerpt):**

> Add information about a possible MCP to the research too, because it could serve as a foundation for many AI integrations.

**AI response (translated excerpt):**

> **MCP would be a reusable integration foundation, not the user's need or a differentiator in itself.**

</details>

### 3. I first chose earlier attack recognition

I initially selected earlier recognition using the vendor articles, with the condition that it should not increase alert fatigue. The AI accepted that direction while pointing out native overlap and fatigue risks. I later supplied the paper, which did not establish operational benefits.

<details>
<summary>Retained exchange: the initial choice and fatigue constraint</summary>

**My request (translated excerpt):**

> That will be the selected need, but we need to avoid increasing fatigue too much

</details>

### 4. I simplified the comparison, then restored its evidence

I still had questions about the tradeoffs. I asked for a shorter comparison of the two needs, with their main advantages and drawbacks, so I could choose a need before discussing solutions. The AI produced the [67-line comparison](RESEARCH-v3.md#retrospective-process-context-how-the-short-comparison-was-produced) and deleted the redundant brief.

I then asked to restore community evidence and save recoverable earlier states. After that, I asked to remove personal experience from the research and stop creating new historical versions automatically. The AI confirmed that it had removed those references and kept the research focused on needs and sources.

<details>
<summary>Retained exchanges: comparison scope and subsequent cleanup</summary>

**My request about the comparison (translated excerpt):**

> We should not focus on the solution for now, only on which need we are addressing.

**AI response (translated excerpt):**

> No algorithms, architecture, or technical decisions.

**My later cleanup request (translated excerpt recovered from the main conversation):**

> Do not include me or my experience in the research. Do not generate any new history.

**AI response (translated excerpt recovered from the main conversation):**

> **I have not created any new version or modified the existing history.** No commit or push.

</details>

### 5. I provisionally chose alert follow-up and authorized drafting

With the community evidence restored, I authorized English Phase 2 and partial Phase 4 drafts for alert follow-up. I briefly considered official MCP, then asked to set it aside and finish the write-up with choice A. This was an intermediate choice, not the current conclusion.

<details>
<summary>Retained exchanges: finish the alert-follow-up draft without MCP</summary>

**My request (translated excerpt):**

> Let's ignore this for now, then. Finish the write-up with choice A.

**AI response (translated excerpt):**

> I will finish the Phase 2 write-up with choice A and leave out this latest official-MCP alternative.

</details>

### 6. I stopped drafting after recognizing the in-product AI emphasis

Late in drafting, I noticed that the Phase 3 questions expected AI within the service, not only as a tool for preparing it. I stopped the work and asked the AI to reread the assignment. Its questions about AI calls, answer evaluation and degradation, and model outages concerned the service itself.

I had identified that requirement late, and the assistant had not flagged it earlier. It acknowledged that the alert-follow-up draft had centered on states, assignments, and tickets, leaving AI peripheral. AI could still fit the earlier ideas; this check changed my selection criterion rather than invalidating them.

<details>
<summary>Retained exchanges: the late requirement check and correction</summary>

**My request (translated excerpt):**

> Stop for a moment, because several Phase 3 questions indicate or imply that AI should be a central part of the new functionality.

**AI response (translated excerpt):**

> I have steered option A too far toward **states, assignments, and tickets**, leaving AI as a poorly defined supporting element.

</details>

### 7. I moved to chat and clarified the inference boundary

I then favored a chatbot for controlled investigation. The AI distinguished the chat experience from MCP's integration role and explained that official or local MCP alone does not protect data. Model location also matters.

I clarified that I meant inference operated within Wazuh Cloud. The boundary was the Wazuh-operated platform, not necessarily the customer's infrastructure. I kept it as a proposal, not a deployment fact or compliance guarantee.

<details>
<summary>Retained exchanges: chatbot direction and Wazuh-operated inference</summary>

**My request about the experience (translated excerpt):**

> I think it makes the most sense to move to a chatbot solution

**My clarification about inference (translated excerpt):**

> But if we support the AI models locally in our Wazuh Cloud deployment, then we could control security.

**AI response (translated excerpt):**

> The correct promise would be **“the data is processed within the platform operated by Wazuh”**, not necessarily “within the customer's infrastructure.”

</details>

### 8. I explicitly replaced the choice with the investigation assistant

I asked the AI to rewrite Phase 2 around the investigation assistant for Wazuh Cloud and record the correction in partial Phase 4. I also asked it to acknowledge the late discovery fairly. The AI rewrote Phase 2 around that choice, with proposed Wazuh-operated inference and authorized evidence access through MCP. It also recorded the corrections in partial Phase 4.

I kept unapproved corporate AI use as a risk hypothesis, not a measured practice. At that point, I had not completed Phase 3 or implemented the service.

<details>
<summary>Retained exchanges: authorization to replace the Phase 2 choice</summary>

**My request (translated excerpt):**

> Record this among the corrections I have had to make to you, and write Phase 2 based on this new choice.

**AI response (translated excerpt):**

> I will update Phase 2 with the new choice: the investigation assistant for Wazuh Cloud, with inference operated within its platform and authorized access through MCP.

</details>

### 9. I asked to reconstruct the process inside the existing research

I later authorized selected work exchanges inside the existing research files, not a separate log, the full private conversation, or new numbered versions. I preserved source findings and historical stages while editing the narration into first person and labelling translations and summaries. The [history metadata](RESEARCH-HISTORY.md) explains those presentation edits and retains reference checksums of the recovered source bodies.

This reconstruction did not authorize new source collection, publication, implementation, or actions against systems. Unrelated project permissions did not extend to publishing these edits.

<details>
<summary>Retained exchanges: retrospective reconstruction and editorial labels</summary>

**My request (translated excerpt):**

> not as a separate log and documents, but inside the research documents themselves: the prompts that led to those research documents, what I asked you to change, the main research, what I asked for and what I did not, and so on.

**AI response (translated excerpt):**

> I will mark those annotations as retrospective to avoid confusing them with the original text.

</details>
