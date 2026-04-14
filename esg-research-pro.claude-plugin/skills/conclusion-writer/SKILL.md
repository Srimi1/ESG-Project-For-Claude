---
name: conclusion-writer
description: Write a concise Conclusion section (300–400 words) that answers the RQ directly, restates contributions without repeating the Discussion, identifies 3 specific future directions, and ends with a policy call to action.
argument-hint: "<research question + key findings + contribution statements + target journal>"
---

# conclusion-writer — Conclusion Section Writer

The Conclusion must answer the RQ, restate contributions, and point forward. It must NOT repeat statistics from Results or interpretations from Discussion.

## Agent File
→ `agents/conclusion-agent.md`

## Execution Mode
Single agent.

## Input Required
1. **Research question** — exact wording
2. **Key findings** — 3–5 plain-language findings (no statistics)
3. **Contribution statements** — from `gap-spotter` output (A: theoretical / B: policy / C: methodological)
4. **Theory used**
5. **Target journal** — adjusts tone of policy call to action

## Five-Part Structure (Target: 320–380 words, hard cap 400)

### Part 1 — Direct Answer to RQ (~50 words)
- First sentence answers the RQ without hedging: "This study demonstrates that ESG practices are significantly associated with business performance among Indian MSMEs..."
- Do not open with "In conclusion" or "To summarise"
- State the overall direction and magnitude of the relationship in plain language

### Part 2 — Findings Summary (~80 words)
- 2–3 sentences only — no statistics, no new content
- Synthesise what was found across all hypotheses in aggregate terms
- Use language like "Collectively, these findings suggest..." to signal synthesis not repetition
- If a hypothesis was not supported, acknowledge it: "Notably, [H#] was not supported, suggesting that..."

### Part 3 — Contribution Restatement (~90 words)
Three sentences, one per contribution angle:
- **Theoretical:** "Theoretically, this study extends [theory] by demonstrating [specific extension] in the underexplored context of Indian MSMEs..."
- **Policy:** "From a policy perspective, findings underscore the need for [specific regulatory action] — particularly given the BRSR mandate's current exclusion of MSMEs..."
- **Methodological:** "Methodologically, this study offers a validated [instrument/framework] for measuring [construct] at MSME scale, filling a measurement gap noted by [Author, Year]..."

### Part 4 — Future Research Directions (~80 words)
Three specific, cited future directions — NOT generic suggestions:
1. A longitudinal study to establish causal direction (cite a paper calling for this)
2. A sector-specific replication (e.g., textile or auto-component MSMEs) to test boundary conditions
3. A qualitative study exploring owner-manager ESG decision-making processes

Each direction must be: specific to this paper's findings, different from what was done, and actionable by a future researcher.

### Part 5 — Policy Call to Action (~60 words)
Close with a sentence addressed to Indian regulators or policymakers:
- Reference SEBI BRSR Phase 2, SIDBI ESG financing, or MCA CSR amendment
- Advocate for a specific action: "Policymakers should consider extending simplified BRSR reporting requirements to MSMEs with turnover above ₹50 crore, supported by SIDBI capacity-building grants..."
- Do not end with a vague "more research is needed" sentence

## Post-Build Check
Run `section-compliance-checker`:
- Word count vs. 300–400 target (FAIL if over 400)
- All 5 parts present
- No statistics included (flag any numbers found)
