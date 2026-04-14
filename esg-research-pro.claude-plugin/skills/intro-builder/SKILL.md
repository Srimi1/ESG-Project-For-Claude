---
name: intro-builder
description: Build a 5-paragraph Introduction section (~500 words) from your research question, gap-spotter output, and methodology type. Follows the macro-to-micro funnel structure required by Q1 management journals.
argument-hint: "<research question + gap-spotter contribution statements + methodology type>"
---

# intro-builder — Introduction Section Builder

Produces a first draft of the Introduction section. Pass the output to `draft-editor` for style refinement, then `section-compliance-checker` for word-count verification.

## Agent File
→ `agents/intro-agent.md`

## Execution Mode
Single agent — this is a sequential argument-building task.

## Input Required
1. **Research question(s)** — the precise RQ(s) the paper addresses
2. **Contribution statements** — from `gap-spotter` output (or write them manually)
3. **Methodology type** — e.g. survey-based quantitative, secondary data, mixed methods, case study
4. **Target journal** (optional) — adjusts framing emphasis

## Five-Paragraph Structure (Target: 480–520 words)

### Paragraph 1 — Macro Context (~80 words)
- Open with a global or Indian statistic on ESG/sustainability significance
- Cite SEBI BRSR mandate (2021), UN SDGs, or IPCC if relevant
- Establish why ESG matters at the corporate/national level
- End with a pivot: "However, this discourse has largely centred on large, listed firms..."

### Paragraph 2 — Problem Narrowing (~100 words)
- Narrow from global → India → MSMEs
- Cite MSME contribution to Indian GDP (~30%) and employment (~110 million) with source
- State the regulatory gap: BRSR applies to top 1000 listed firms, not MSMEs
- Name the specific problem: absence of empirical evidence on ESG–performance linkage at MSME scale in India post-MSMED Act 2020
- Signal the gap without repeating literature review details

### Paragraph 3 — Research Question & Objectives (~100 words)
- State the RQ directly: "This study asks: [RQ]"
- List 2–4 specific objectives in numbered or bulleted form
- If hypotheses exist, briefly indicate the directional expectation: "Drawing on [theory], this study hypothesises that..."
- Specify scope: Indian MSMEs, post-2020, cross-sectional / longitudinal / panel

### Paragraph 4 — Contributions (~120 words)
- Embed the gap-spotter contribution statements verbatim (A, B, C)
- Frame each as a distinct contribution: theoretical / methodological / policy
- Use language that signals novelty without overclaiming: "To the best of our knowledge..." / "This study extends..." / "Unlike prior studies that..."
- Maximum 3 contribution bullets

### Paragraph 5 — Paper Roadmap (~60 words)
- One sentence per section: "Section 2 reviews..." / "Section 3 outlines..." / "Section 4 presents..." / "Section 5 discusses..." / "Section 6 concludes..."
- Do not describe what the paper finds — only what each section contains

## Post-Build Check
After drafting, automatically run `section-compliance-checker` and report:
- Word count vs. 480–520 target
- Whether all 5 paragraphs are structurally complete
- Citation count (target: 8+ in Introduction)
