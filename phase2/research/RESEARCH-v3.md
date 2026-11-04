**Language note:** I normally communicate with coding agents in Spanish. Quoted exchanges are English translations, not messages originally written in English. Edited summaries are labelled separately.

# Phase 2 research: two needs to choose between

**A improves how known alerts are handled. B helps recognize an attack from signals that are not convincing on their own.**
At this stage, I wanted to compare user needs, not solution designs. I wanted either direction to reduce analyst fatigue rather than create more work.

## A. Organizing and following up security alerts

Security analysts need known alerts and findings to be prioritized, assigned, investigated, and followed through to closure without constant manual coordination. The desired support is ticket management and AI-assisted evaluation alongside Wazuh AI Analyst—not a confirmed native integration. Success means knowing what matters, who owns it, and what still needs attention.

**Example:** An alert is noticed, but nobody clearly owns it; the next shift repeats the investigation or leaves it unfinished.

**In favor**

- Public requests explicitly ask for assignment and closure [1], and selective escalation rather than forwarding everything [2].
- Clear ownership and follow-up could prevent dropped work and repeated investigations.
- AI-supported evaluation could reduce manual reading and help analysts explain findings; this benefit is not yet demonstrated.

**Risks and limits**

- Strong existing overlap: Wazuh Alert Manager documents assignments, cases, history, and optional AI [3]; Wazuh with Shuffle already demonstrates automation [4].
- Requests show a specific problem, not broad demand or willingness to pay.
- AI Analyst already offers periodic analysis and advisory recommendations [5]; this does not establish automatic ticket handling or the proposed connection.

## B. Recognizing an attack earlier from related weak signals

Security analysts need to recognize an attack already in progress when individual observations look harmless or inconclusive. The need is to understand related activity across users, devices, sources, and time before the attack becomes more obvious. This is not predicting a future attack, and a small anomaly is not automatically malicious.

**Example:** An unusual login, an administration command, and later access to another machine may each have a normal explanation; together they may deserve one investigation.

**In favor**

- Focuses directly on recognizing a developing attack, rather than only organizing alerts that have already been raised.
- Could turn scattered observations into one useful investigation instead of more isolated alerts; vendor examples illustrate this need [7].
- An academic paper supports relating attack signals [8], but does not demonstrate earlier detection, fewer false investigations, or reduced analyst workload.

**Risks and limits**

- Normal activity can look suspicious in combination: false connections could increase fatigue.
- Relevant evidence must be available and retained; missing context can hide relationships or make them misleading.
- Wazuh already correlates events [6], and AI Analyst already examines patterns [5]; extra value over the full existing toolset remains unproven.

## What the choice means

A is about **handling already identified work better**; B is about **recognizing a pattern that is not obvious from one event**.
If the main pain is lost ownership and manual follow-up, A fits—but only if existing plugins and automation do not already solve it.
If it is a missed developing attack despite available signals, B fits—but it must improve recognition without adding false investigations.
I did not treat either as an objective winner: I wanted to compare against Wazuh **and** the team's existing security tools, not Wazuh alone.

## Essential sources

- [1] Community discussion: requests to assign, investigate, and close alerts.
- [2] Wazuh issue: request for selective single/bulk escalation.
- [3] Third-party plugin README: overlapping workflow and AI features; not installed or validated here.
- [4] Official Wazuh example: reporting and response automation with Shuffle.
- [5] Official AI Analyst documentation: existing analysis and advisory recommendations.
- [6] Official Wazuh rules documentation: existing event correlation.
- [7] Logstail article: vendor illustration, not independent effectiveness or market evidence.
- [8] *Early-Stage Detection of Cyber Attacks*: academic method, not proven operational benefits or market demand.

[1]: https://groups.google.com/g/wazuh/c/-fNsty6bIUY
[2]: https://github.com/wazuh/wazuh/issues/33328
[3]: https://github.com/xrisbarney/Wazuh-alert-manager
[4]: https://wazuh.com/blog/automating-security-reporting-and-response-with-wazuh-and-shuffle/
[5]: https://documentation.wazuh.com/current/cloud-service/ai-analyst.html
[6]: https://documentation.wazuh.com/current/user-manual/ruleset/ruleset-xml-syntax/rules.html
[7]: https://logstail.com/blog/early-signs-of-a-cyber-attack-why-soc-teams-often-miss-them
[8]: https://doi.org/10.3390/info11120560

<!-- RESEARCH-PROCESS-CONTEXT -->

---

## Retrospective process context: how the short comparison was produced

I reconstructed this section after the original short comparison. Its source was a direct 67-line copy made before the community-restoration edit and subsequently hash-verified. I preserved the comparison's findings and historical stage while editing the narration into first person and adding the language note and process record. I labelled translated excerpts and edited summaries separately. This is an annotated editorial presentation, not a byte-exact historical copy; the later instructions below came after this comparison.

### My request

After the expanded catalog and a redundant decision brief, I asked the AI to consolidate the material into one research document and delete the brief. I then asked for a clearer comparison before deciding:

**My request — edited summary:**

I had questions about the tradeoffs and wanted the AI to help me compare the alternatives through their main advantages and drawbacks.

**My request — translated excerpt:**

> Do not focus on making something very long. I only want the main points for and against the proposed alternatives, of which there are two:

I wanted to compare alert management with AI-assisted evaluation and earlier recognition from related weak signals.

**My request — translated excerpt:**

> We should not focus on the solution for now, only on which need we are addressing.

I wanted the main arguments for and against each need so I could decide before discussing architecture.

### AI response

**AI response — translated excerpt:**

> I will leave a single short research document focused on those **two needs**, covering the problem each addresses, its main pros and cons, and the essential sources. No further research and no architecture details. Then I will delete the decision brief.

The AI agreed to simplify the existing evidence rather than start new research or select an implementation.

### Output produced

The AI produced a 67-line comparison: an explanation and example for each need, three advantages and three risks per option, and eight essential sources. It removed the separate brief. I kept existing workflow tools, native correlation, AI Analyst, and the paper's limited operational evidence in the comparison rather than present either alternative as an objective winner.

### My changes and permission limits

I authorized document simplification and consolidation, not new research, architecture, deployment, or autonomous response. I kept the full conversation private.

### Subsequent stage, not knowledge available to this comparison

**My request — translated excerpt; surrounding personal context omitted:**

> Let's take into account the community review we set aside. I want you to bring back the information collected from the community to see whether it also helps us open up a third direction or settle on one of the two options.

I asked to restore relevant community evidence and, in that same later request, authorized saving recoverable earlier states. I recovered this further cleanup instruction from the main conversation:

**My request — translated excerpt recovered from the main conversation:**

> Do not include me or my experience in the research. Do not generate any new history.

I asked to remove personal experience from the research and stop creating new historical versions automatically. The AI confirmed that it had removed those references and kept the research focused on needs and sources.

**AI response — translated excerpt recovered from the main conversation:**

> **I have not created any new version or modified the existing history.** No commit or push.

I recorded the later changes of direction in the [current research](RESEARCH.md). I authorized process notes inside the existing files, not another numbered version.
