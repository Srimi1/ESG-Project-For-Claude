---
name: human-writer
description: Post-processing skill that humanizes AI-generated research output and exports it to a formatted Word (.docx) file. Always runs as the final step after any ESG-Research-Pro command produces output.
argument-hint: "<output text to humanize and export>"
---

# human-writer — Humanize & Export to Word

This skill is the final stage of every ESG-Research-Pro pipeline. It takes structured AI output, rewrites it to sound natural and academic-human, then saves it as a formatted `.docx` Word file.

## When This Skill Runs

Automatically triggered at the end of:
- `/literature-review` → exports Literature Review Report
- `/write-review` → exports Edited Draft Section
- `/methods-check` → exports Methodology Critique Report
- `/pre-submission` → exports Pre-Submission Audit Report
- `/full-pipeline` → exports Full Research Pipeline Report

## Step 1: Humanize the Output

Apply the `/human` skill to the full output before writing to Word.

### Humanization Rules for Academic Research Writing

Transform AI-generated text to sound like a thoughtful, experienced researcher wrote it:

**Voice and Tone**
- Write in confident, measured academic voice — not robotic, not casual
- Use first person sparingly and purposefully ("This study argues...", "We find that...")
- Vary sentence length: mix short declarative sentences with longer analytical ones
- Avoid filler phrases: "It is worth noting that", "It is important to mention", "Needless to say"
- Remove meta-commentary: never say "As an AI..." or "Based on my analysis..."

**Word Choice**
- Replace AI-typical words: "utilize" → "use", "leverage" → "apply" or "draw on", "delve into" → "examine"
- Replace hollow intensifiers: "very significant" → "significant", "extremely important" → "critical"
- Use discipline-specific vocabulary naturally: ESG, MSME, BRSR, GRI, stakeholder theory, legitimacy theory
- Prefer active voice over passive where it strengthens clarity

**Structure and Flow**
- Ensure each paragraph has a clear topic sentence and concludes with a link to the next point
- Use transitions that signal argument progression: "However...", "Building on this...", "In contrast...", "This gap motivates..."
- Academic hedging where appropriate: "suggests", "indicates", "appears to", "preliminary evidence points to"
- Citation placeholders should read naturally: "as demonstrated by [Author, Year]"

**What to Preserve**
- All factual content, scores, tables, and data — do not change numbers or findings
- Section headings and structure
- All citation references exactly as written
- Technical terms and acronyms (ESG, MSME, BRSR, SDG, etc.)

**Output Check Before Exporting**
After humanizing, verify:
- [ ] No sentences starting with "Certainly", "Absolutely", "Of course", "Sure"
- [ ] No bullet points in prose paragraphs (prose should flow as sentences)
- [ ] No em-dash overuse (max 1 per paragraph)
- [ ] Reading level appropriate for a Q1 journal manuscript (Flesch-Kincaid Grade ~16)

## Step 2: Export to Word (.docx)

Use the `/docx` skill to export the humanized output as a formatted Word document.

### Document Structure by Command

#### /literature-review output → `Literature-Review-[YYYY-MM-DD].docx`
```
Title: Literature Review — ESG Practices and Business Performance in Indian MSMEs
Subtitle: [Date]

Section 1: Screening Summary (table)
Section 2: Synthesized Literature Review (5 themed sections)
Section 3: Research Gap Matrix (table)
Section 4: Contribution Statements
Section 5: Positioning Paragraph
```

#### /write-review output → `Draft-[Section-Name]-[YYYY-MM-DD].docx`
```
Title: Edited Draft — [Section Name]
Subtitle: Revision [N] | [Date]

Section 1: Revised Text
Section 2: Changes Made (summary)
Section 3: Citation Verification Results
Section 4: Remaining Issues (if any)
```

#### /methods-check output → `Methods-Critique-[YYYY-MM-DD].docx`
```
Title: Methodology Critique Report
Subtitle: [Date]

Section 1: Overall Validity Assessment
Section 2: Dimension-by-Dimension Analysis (9 dimensions)
Section 3: Critical Issues to Address
Section 4: Recommendations
```

#### /pre-submission output → `Pre-Submission-Audit-[YYYY-MM-DD].docx`
```
Title: Pre-Submission Audit Report
Subtitle: Target Journal: [Journal Name] | [Date]

Section 1: Peer Review Simulation
Section 2: Citation Audit Results
Section 3: Journal Match Assessment
Section 4: Submission Checklist
Section 5: Cover Letter Draft
```

#### /full-pipeline output → `Full-Pipeline-Report-[YYYY-MM-DD].docx`
```
Title: ESG Research Pipeline Report
Subtitle: Full Run | [Date]

Section 1: Literature Review
Section 2: Synthesized Review
Section 3: Gap Analysis
Section 4: Methods Assessment
Section 5: Pre-Submission Audit
Appendix: Screening CSV (as table)
```

### Word Document Formatting

Apply these styles when exporting via /docx:

| Element | Style |
|---|---|
| Document title | Heading 1, centered, 16pt |
| Section headings | Heading 2, 14pt |
| Sub-section headings | Heading 3, 12pt |
| Body text | Normal, 12pt, Times New Roman or Calibri, 1.5 line spacing |
| Tables | Table Grid style, header row shaded |
| Bullet lists | List Bullet style |
| Citation references | Italic inline |
| Page margins | 1 inch all sides |
| Header | Document title (short form) |
| Footer | Page number, centered |

## Step 3: Confirm and Offer Save Options

After the Word file is created, confirm with the user:

```
HUMANIZE & EXPORT COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Humanization applied: AI → Academic-human voice
Word file created: [filename].docx
File size: [N] KB | Pages: ~[N]

Where would you like to save it?
  [A] Download to local folder
  [B] Save to Google Drive → ESG-MSME-Paper/
  [C] Save to Notion as embedded document
  [D] All of the above

Type A, B, C, or D — or "skip" to keep in session only.
```
