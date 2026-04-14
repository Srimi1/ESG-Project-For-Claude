# Command: /draft-section

## Trigger
Type `/draft-section` in Claude Co-work chat.

## Purpose
Build a first draft of any individual paper section from scratch using the appropriate builder skill. After drafting, automatically runs `section-compliance-checker` to verify word count and structure, then offers to pass to `draft-editor` for style refinement.

## When to Use
- When starting a new section that doesn't exist yet
- When an existing section scored below 6/10 in `/paper-audit` and needs a full rebuild
- When you want a structured starting point for Introduction, Results, Discussion, or Conclusion

## Input Prompt to Show User
```
/draft-section activated.

Which section do you want to draft from scratch?

  [1] Abstract (200 words) + Keywords
  [2] Introduction (500 words)
  [3] Results (1000–1200 words)
  [4] Discussion (700–1000 words)
  [5] Conclusion (300–400 words)
  [6] Hypothesis / Proposition Set
  [7] Data Analysis Techniques subsection

Type the number to continue.
```

## Execution Routing

| User selects | Skill | Agent | Input needed from user |
|---|---|---|---|
| 1 | `abstract-generator` | `abstract-agent.md` | Title, RQ, key findings, methodology, target journal |
| 2 | `intro-builder` | `intro-agent.md` | RQ, gap-spotter contribution statements, methodology type |
| 3 | `results-structurer` | `results-agent.md` | Raw statistical output, hypothesis list, descriptive stats |
| 4 | `discussion-builder` | `discussion-agent.md` | Results summary, hypotheses accepted/rejected, lit-synthesizer output |
| 5 | `conclusion-writer` | `conclusion-agent.md` | RQ, key findings, contribution statements, target journal |
| 6 | `hypothesis-builder` | `hypothesis-agent.md` | Conceptual framework, theory, variable list |
| 7 | `data-analysis-guide` | `analysis-agent.md` | Analysis type, sample size, software, constructs/indicators |

## Step-by-Step Execution

### Step 1: Route to Builder Skill
After user selects a number, ask for the required inputs listed above. Then launch the corresponding agent with those inputs.

### Step 2: Auto-Compliance Check
After the builder skill returns the draft, immediately run `section-compliance-checker` on the output.

Report compliance inline:
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COMPLIANCE CHECK — [Section Name]
Word count: [N] (Target: [min]–[max])  [✓ PASS / ⚠ WARNING / ✗ FAIL]
Structure:  [N/N components present]   [✓ / ⚠ / ✗]
Score: [X]/10 — [verdict]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Step 3: Present Draft
Display the full drafted section below the compliance check.

### Step 4: Offer Next Steps
```
DRAFT COMPLETE — [Section Name]

NEXT STEPS:
→ Type /write-review to refine this draft for academic style and citations
→ Type /draft-section again to draft the next section
→ Type /paper-audit to check how this section fits your full draft
→ When all sections are ready: type /pre-submission for a full audit
```

## Final Output Assembly

```
/draft-section — [SECTION NAME]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

COMPLIANCE
Word count: [N] | Target: [min]–[max] | [PASS / WARNING / FAIL]
Score: [X]/10 | [verdict]

[Missing components if any]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DRAFT: [SECTION NAME]

[Full drafted section text]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS: [as above]
```

> **Final output only:** when the draft is approved, run `human-writer` to humanize and save as `Draft-[Section-Name]-[YYYY-MM-DD].docx`.
