---
name: abstract-generator
description: Draft a structured 200-word abstract and 6–8 ranked keywords from your completed paper. Outputs two versions — structured (IMRaD) and unstructured — for journal flexibility. Run after all sections are finalised.
argument-hint: "<title + research question + key findings + conclusion + target journal>"
---

# abstract-generator — Abstract & Keywords Generator

Run this skill **last**, after all paper sections are complete. The abstract must accurately reflect the final paper, not a draft.

## Agent File
→ `agents/abstract-agent.md`

## Execution Mode
Single agent.

## Input Required
1. **Paper title**
2. **Research question** (exact wording)
3. **Key findings** — 3–5 bullet points of main results (include one key statistic if available)
4. **Main conclusion / implication**
5. **Methodology** — one-line description (e.g. "survey of 287 Indian MSMEs, PLS-SEM analysis")
6. **Target journal** — determines whether structured or unstructured abstract is primary

## Output: Two Abstract Versions

### Version A — Structured Abstract (IMRaD, for JCP, BSE, Sustainability)
Five labelled paragraphs, ~40 words each:

**Background:** Why this topic matters; what gap exists
**Objective:** What this study does; the RQ stated in one sentence
**Methods:** Sample, data collection, analysis technique (one sentence each)
**Findings:** 2–3 key results stated plainly; include one statistical result if possible
**Implications:** Theoretical contribution + policy recommendation for Indian MSME ecosystem

**Hard cap: 200 words. Flag if over 210 or under 185.**

### Version B — Unstructured Abstract (for JSBM, JBE, APJM)
Single flowing paragraph, same content, no subheadings, ~200 words.
Opening sentence must answer the RQ or state the main finding directly — no background throat-clearing.

## Keywords: 6–8 Terms

Generate in this priority order:
1. **Core topic terms:** ESG, Indian MSMEs, business performance, sustainability
2. **Framework terms:** BRSR, GRI Standards, stakeholder theory, institutional theory
3. **Method terms:** PLS-SEM, survey research, emerging markets
4. **Specificity terms:** MSMED Act 2020, Udyam registration, SIDBI

Rules:
- Use terms that appear in the abstract or title
- Prefer multi-word phrases over single words
- Check alignment with Scopus/WoS subject headings for the target journal
- List in order: most specific to most general

## Output Format
```
ABSTRACT — VERSION A (Structured)
[200-word abstract with Background/Objective/Methods/Findings/Implications labels]
Word count: [N]

ABSTRACT — VERSION B (Unstructured)
[200-word single paragraph]
Word count: [N]

KEYWORDS
1. [term]   2. [term]   3. [term]   4. [term]
5. [term]   6. [term]   7. [term]   8. [term]

RECOMMENDATION: Use Version [A/B] for [target journal] — [one-line reason]
```
