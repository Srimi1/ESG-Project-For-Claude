# Command: /write-review

## Trigger
Type `/write-review` in Claude Co-work chat.

## Purpose
Edit one or more draft sections for academic style, precision, and terminology — then verify citations for the edited section. Runs draft-editor + cite-verifier in sequence.

## When to Use
- After drafting any section (Introduction, Lit Review, Methods, Results, Discussion, Conclusion)
- Before sharing a section with your supervisor
- After incorporating feedback — to clean up edits
- As a final polish pass before running /pre-submission

## Input Prompt to Show User
```
/write-review activated.

Please provide:
  1. Which section is this? 
     [Introduction / Literature Review / Methodology / Results / Discussion / Conclusion]
  2. Paste your section text below OR type "fetch from Drive" to pull from Google Drive
  3. Target journal? (default: Journal of Cleaner Production)
  4. Are you editing one section or multiple sections simultaneously?
     - One section: will use single agent
     - Multiple sections: will spin up one sub-agent per section
```

## Execution Steps

### Step 1: EDIT (draft-editor skill)
**Single section:**
- Single agent using editor-agent.md
- Input: section text + section type + target journal

**Multiple sections (2–4 at once):**
- Spin up 1 sub-agent per section (max 4), each using editor-agent.md
- Each sub-agent receives its own section + section type

**Agent launch message:**
```
You are an academic writing editor for an ESG-MSME India research paper.
Load your instructions from: agents/editor-agent.md
Section type: [section name]
Target journal: [journal name]
Apply all editing rules and return the full edit table.
Section text: [paste section]
```

### Step 2: CITATION FLAG REVIEW (cite-verifier skill, targeted)
After editing, extract all ⚠️ NEEDS CITATION flags from the editor's output.
Run cite-verifier on:
- All existing citations in the section (verify they are correctly formatted)
- All flagged sentences needing citations (suggest search terms)

**Note:** Full reference list verification is done in /pre-submission. This step only checks citations within the edited section.

## Final Output Assembly (Main Claude)

```
WRITE-REVIEW COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SECTION EDITED: [section name]
Original word count: [N] | Revised word count: [N] | Target: [N]
Overall quality: [rating]

EDIT TABLE
[full table: Original | Issue | Revised]

SENTENCES NEEDING CITATIONS ([N] found)
[numbered list with search suggestions]

CITATION CHECK
[status of existing citations in this section]

REVISED SECTION (clean version)
[Full revised section text, ready to copy back to your draft]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS:
→ Copy the revised section to your Google Drive draft
→ Resolve the [N] citation flags before moving on
→ Type /write-review again for the next section
→ When all sections are done: type /pre-submission
```

## Special Mode: Supervisor Feedback Integration
If you have received supervisor comments, use this mode:
```
"I have supervisor feedback to integrate. 
Please help me apply these comments to my [section] section.
Feedback: [paste comments]
Draft: [paste current section]"
```
Claude will: (1) categorize feedback as must-fix vs. optional, (2) apply edits, (3) track which comments were addressed.


---

> **Final output only:** when all steps above are complete, run `human-writer` to humanize the assembled result and save it as `Draft-[Section-Name]-[YYYY-MM-DD].docx`.
