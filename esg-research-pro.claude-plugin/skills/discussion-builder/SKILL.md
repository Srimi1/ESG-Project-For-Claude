---
name: discussion-builder
description: Build a Discussion section (700–1000 words) by interpreting each finding against cited literature, adding theoretical and policy implications, and drafting a limitations paragraph. Uses literature-synthesizer output as the anchor for interpretations.
argument-hint: "<results summary + hypotheses accepted/rejected + literature-synthesizer output>"
---

# discussion-builder — Discussion Section Builder

The Discussion interprets results — it does not repeat them. Every finding must be anchored to prior literature (agree, contradict, extend) and connected to the Indian MSME context.

## Agent File
→ `agents/discussion-agent.md`

## Execution Mode
Single agent. Can spawn up to 3 sub-agents for large studies (theory / policy / limitations split).

## Input Required
1. **Results summary** — which hypotheses were supported/rejected + key β values
2. **Hypothesis list** — numbered with IV and DV labels
3. **Literature-synthesizer output** — the 5 themed sections (for anchoring interpretations to cited papers)
4. **Theory used** — Stakeholder Theory / RBV / Institutional Theory / Signaling Theory
5. **Unexpected findings** (if any) — results that contradict hypotheses or prior literature

## Section Structure (Target: 700–1000 words)

### Sub-section 1 — Findings Interpretation (~400 words)
One paragraph per hypothesis group:

**Paragraph structure per finding:**
1. Restate the finding in plain language (no statistics — those are in Results)
2. Compare to prior literature: "This aligns with [Author, Year] who found..." OR "This contradicts [Author, Year]'s finding that..."
3. Offer a context-specific explanation: why does this finding hold for Indian MSMEs specifically?
4. If the hypothesis was NOT supported: explain plausible reasons (measurement limitation, context specificity, moderating variable not captured)

**India-MSME anchoring required for each finding:**
- Reference BRSR regulatory pressure, MSMED Act 2020 definition, SIDBI financing, or sector context
- Do not generalise findings to "all firms" — scope to Indian MSMEs explicitly

### Sub-section 2 — Theoretical Implications (~150 words)
- Name the theory used and state how findings extend, support, or challenge it
- "This study extends Stakeholder Theory by demonstrating that... in the MSME context where stakeholder pressure operates through [mechanism] rather than [prior mechanism]"
- If multiple theories: one sentence per theory
- Avoid vague statements like "This study contributes to theory" — be specific about which aspect of which theory

### Sub-section 3 — Policy Implications (~150 words)
- Address three levels: firm-level, industry-level, regulatory/government-level
- **Firm level:** What should MSME owner-managers do based on these findings?
- **Industry level:** What do sector associations (e.g., CII, FICCI, SIDBI) need to know?
- **Regulatory level:** What does this mean for SEBI's BRSR extension roadmap, MCA's CSR policy, SIDBI green finance?
- Keep recommendations specific and actionable — not generic sustainability platitudes

### Sub-section 4 — Limitations (~150 words)
List 5 standard limitations with one sentence each:
1. **Cross-sectional design** — cannot establish causality; longitudinal follow-up recommended
2. **Self-reported data** — social desirability bias possible; archival validation suggested
3. **Common Method Bias** — mitigated by [test used] but cannot be fully ruled out
4. **Geographic scope** — sampled from [region/states]; may not generalise to all Indian MSMEs
5. **MSME tier representation** — if sample skews to micro or small, findings may not apply equally across tiers

### Bridge Sentence (~30 words)
End Discussion with a forward-looking sentence that flows naturally into the Conclusion:
"Notwithstanding these limitations, this study provides foundational evidence for... which is elaborated in the concluding section."

## Post-Build Check
Run `section-compliance-checker` automatically:
- Word count vs. 700–1000 target
- Check all 4 sub-sections present
- Citation density: min 6 citations per 300 words
