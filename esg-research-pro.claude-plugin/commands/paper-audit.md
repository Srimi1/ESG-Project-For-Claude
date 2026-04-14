# Command: /paper-audit

## Trigger
Type `/paper-audit` in Claude Co-work chat.

## Purpose
Fast structural check of a full or partial draft. Checks every section simultaneously for word-count compliance, structural completeness, and citation density. Returns a scorecard table with pass/fail per section and a priority fix list.

Does NOT edit prose or verify citations. For those, use `/write-review` and `cite-verifier`.

## When to Use
- After drafting all sections, before starting the editing round
- When you want a quick health check on the current state of your paper
- Between `/draft-section` runs to track progress
- As the first step in `/full-pipeline` Stage 3 (before editing)

## Input Prompt to Show User
```
/paper-audit activated.

Please provide your current draft. Options:

  [A] Paste all sections below, separated by their headings
      (e.g. ## Abstract, ## Introduction, ## Literature Review...)
  [B] Type "fetch from Drive" to pull from connected Google Drive
  [C] Check one section only — type its name

Note: This audit checks structure and word counts only.
For citation errors, use /write-review or cite-verifier.
```

## Execution

Spin up 1 `compliance-agent` sub-agent per section present in the draft (max 6 parallel). Each sub-agent runs `section-compliance-checker` on its assigned section.

**Sub-agent launch message:**
```
You are a compliance auditor for an academic research paper on ESG practices 
in Indian MSMEs.
Load your instructions from: agents/compliance-agent.md
Your assigned section: [Section Name]
Section text: [pasted section text]
Return: word count, structural checklist, citation density, score (X/10), verdict.
```

## Output Assembly

Collect all sub-agent results and assemble:

```
PAPER AUDIT COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PAPER STRUCTURE SCORECARD

Section            | Words  | Target      | Status | Score
-------------------|--------|-------------|--------|-------
Abstract           | [N]    | 180–210     | [✓/⚠/✗] | [X]/10
Introduction       | [N]    | 480–520     | [✓/⚠/✗] | [X]/10
Literature Review  | [N]    | 700–900     | [✓/⚠/✗] | [X]/10
Methodology        | [N]    | 600–800     | [✓/⚠/✗] | [X]/10
Results            | [N]    | 1000–1200   | [✓/⚠/✗] | [X]/10
Discussion         | [N]    | 700–1000    | [✓/⚠/✗] | [X]/10
Conclusion         | [N]    | 300–400     | [✓/⚠/✗] | [X]/10
References         | [N]    | 20+ entries | [✓/⚠/✗] | [X]/10

TOTAL DRAFT WORD COUNT: [N]
(Typical full paper body: 4,100–5,030 words, excluding references)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MISSING COMPONENTS

[Section Name]: [missing element] — [one-line fix suggestion]
[Section Name]: [missing element] — [one-line fix suggestion]
(Only sections with missing components are listed here)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PRIORITY FIXES (Top 3)
1. [Highest-priority issue — section, what is missing, why it matters]
2. [Second priority]
3. [Third priority]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

OVERALL READINESS: [N]/10

[Ready for /write-review]           → All sections ≥ 7/10
[Needs /draft-section first]        → One or more sections < 6/10 or missing
[Major structural gaps present]     → Three or more sections < 5/10

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

RECOMMENDED NEXT STEPS
→ Sections scored below 6/10: type /draft-section to rebuild from scratch
→ Sections scored 6–8/10: type /write-review to polish prose and citations
→ All sections ≥ 8/10: proceed to /methods-check then /pre-submission
```

## Partial Audit Mode
If the user provides fewer than 8 sections:
- Run compliance check only on the sections provided
- Show "NOT SUBMITTED" for missing sections
- Still calculate overall readiness based on sections present
- Prompt: "Sections not yet drafted: [list]. Use /draft-section to build them."

## Error Handling
- If a section heading is ambiguous: ask the user to clarify before running sub-agent
- If text is too short to audit (< 50 words): note "Section too short to audit — provide more text"
