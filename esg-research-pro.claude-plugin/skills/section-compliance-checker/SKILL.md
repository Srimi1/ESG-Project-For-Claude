---
name: section-compliance-checker
description: Check any drafted paper section for word-count compliance, structural completeness, and citation density against target ranges. Returns a scorecard with pass/fail and a prioritised fix list.
argument-hint: "<section name + pasted section text>"
---

# section-compliance-checker — Structural Compliance Audit

Runs on one or multiple sections. For a full draft use `/paper-audit` which spins one sub-agent per section in parallel.

## Agent File
→ `agents/compliance-agent.md`

## Execution Mode
- **Single section:** one agent
- **Multiple sections:** 1 sub-agent per section (max 6 parallel)

## Word-Count Targets

| Section | Min | Max | Critical floor |
|---|---|---|---|
| Abstract | 180 | 210 | 150 |
| Introduction | 480 | 520 | 400 |
| Literature Review | 700 | 900 | 600 |
| Methodology | 600 | 800 | 500 |
| Results | 1000 | 1200 | 900 |
| Discussion | 700 | 1000 | 600 |
| Conclusion | 300 | 400 | 250 |
| References | 20 refs min | — | 15 refs |

## Checks Applied Per Section

### 1. Word Count
- Count words in body text (exclude headings, tables, references)
- Status: PASS (within range) / WARNING (within 10% outside) / FAIL (below critical floor or >20% over max)

### 2. Structural Completeness
Check for required components per section:

**Abstract:** Background sentence | Objective/RQ | Method summary | Key finding | Implication
**Introduction:** Macro context with statistic | Problem narrowing to Indian MSMEs | RQ stated explicitly | Contribution bullets | Paper roadmap sentence
**Literature Review:** At least 3 themed sub-sections | Each theme has finding + contradiction + gap | Transition sentences between themes | Concluding paragraph with overall gap
**Methodology:** Research design justification | Sample description with MSMED Act 2020 definition | Data collection procedure | Measurement instrument description | Analysis method with software named
**Results:** Descriptive statistics paragraph | One narration paragraph per hypothesis tested | Hypothesis acceptance/rejection summary | APA-7 statistical values in-text
**Discussion:** One interpretation paragraph per finding | Theoretical implications | Policy implications | Limitations paragraph (min 3 limitations) | Bridge to Conclusion
**Conclusion:** Direct answer to RQ | Non-repetitive findings summary | Contribution restatement | Future research directions (min 3) | Policy call to action
**References:** Min 20 entries | All in-text citations have a reference entry | APA-7 or journal-required format consistent

### 3. Citation Density
- Introduction: min 8 citations
- Literature Review: min 20 citations
- Discussion: min 6 citations per 300 words
- Flag sections below threshold as ⚠️ CITATION-THIN

## Output Format

```
COMPLIANCE REPORT — [Section Name]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

WORD COUNT
Actual: [N] words | Target: [min]–[max] | Status: [PASS / WARNING / FAIL]

STRUCTURAL CHECKLIST
✓ [component present]
✗ [component missing — brief fix note]

CITATION DENSITY
[N] citations | Target: [min] | Status: [PASS / WARNING]

MISSING COMPONENTS
1. [specific missing element with suggestion]
2. ...

COMPLIANCE SCORE: [X]/10
VERDICT: Ready / Minor Fixes Needed / Major Gaps Present
```
