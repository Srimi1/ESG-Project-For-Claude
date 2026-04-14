---
name: human-writer
description: Takes the fully assembled final output of any command, runs it through the cc-prose humanizer (24 AI-pattern categories, rhuss/cc-prose), then exports as a formatted Word (.docx) file. Runs once on the complete final output only.
argument-hint: "<complete final output to humanize and export>"
---

# human-writer — Humanize via cc-prose + Export to Word

Runs **once**, on the **complete final output** only — after all skills and steps in a command have finished.

Humanization is powered by the **`prose` humanizer skill** from [rhuss/cc-rhuss-marketplace](https://github.com/rhuss/cc-rhuss-marketplace) (`rhuss/cc-prose`), which removes 24 documented categories of AI writing patterns based on Wikipedia's "Signs of AI writing" reference.

---

## Step 1 — Detect Voice

Analyse the content type and announce the voice profile before rewriting:

| Content Type | Voice |
|---|---|
| Literature review / gap analysis | **analytical** |
| Methodology / results | **technical** |
| Discussion / conclusion / abstract | **reasoning** |
| Introduction / contribution framing | **pov** |
| Response-to-reviewers letter | **conversational** |

> Always announce: `Rewriting with **[voice]** voice.`

---

## Step 2 — Apply the 24 AI-Pattern Checklist (cc-prose humanizer)

Scan the full output and rewrite every instance of the following. Preserve all data, tables, scores, citations, headings, and technical terms (ESG, MSME, BRSR, GRI, SDG, SEM fit indices, β values, p-values) exactly.

### Content Patterns
1. **Significance inflation** — remove "pivotal", "testament", "underscores its importance", "marks a shift", "evolving landscape", "indelible mark"
2. **Notability claims** — replace vague media name-dropping with specific cited claims
3. **Superficial -ing phrases** — remove dangling "highlighting X", "underscoring Y", "showcasing Z" clause-endings
4. **Promotional language** — remove "groundbreaking", "nestled", "vibrant", "breathtaking", "must-visit", "commitment to excellence"
5. **Vague attributions** — replace "experts argue", "observers note", "industry reports suggest" with named sources and years
6. **Formulaic challenges sections** — rewrite "Despite challenges... continues to thrive" into specific factual statements

### Language & Grammar Patterns
7. **AI vocabulary** — replace: additionally → also/and · crucial → important/key · delve → examine · enhance → improve · foster → build · highlight (verb) → show/note · landscape (abstract) → field/sector · pivotal → important · tapestry → [delete or rewrite] · testament → [rewrite] · underscore → show · vibrant → active/growing
8. **Copula avoidance** — replace "serves as", "stands as", "functions as", "represents a" with plain "is"/"are"/"has"
9. **Negative parallelism** — simplify "Not only X but also Y" and "It's not just X; it's Y" constructions
10. **Rule of three overuse** — break up forced triads where only two points are needed
11. **Synonym cycling** — use consistent terminology; do not rotate synonyms for the same concept
12. **False ranges** — remove "from X to Y, from A to B" constructions where X/Y aren't on a meaningful scale

### Style Patterns
13. **Em dash overuse** — replace em dashes (—) with commas, semicolons, or sentence breaks; max one per paragraph
14. **Boldface overuse** — remove bold from inline phrases; keep only for table headers and section labels
15. **Inline-header bullet lists** — convert "**Term:** explanation" bullets into flowing prose sentences
16. **Title case headings** — convert Title Case headings to Sentence case (preserve proper nouns)
17. **Emojis** — remove all emojis from body text and headings
18. **Curly quotes** — replace curly/smart quotes ("...") with straight quotes ("...") if present

### Communication Patterns
19. **Chatbot artifacts** — remove "I hope this helps", "Let me know if", "Of course!", "Certainly!", "Great question!", "Here is a..."
20. **Knowledge-cutoff disclaimers** — remove "as of my training", "based on available information", "while specific details are limited"
21. **Sycophantic tone** — remove "excellent point", "you're absolutely right", "that's a great observation"

### Filler & Hedging
22. **Filler phrases** — remove: "in order to" → "to" · "due to the fact that" → "because" · "at this point in time" → "now" · "it is important to note that" → [delete] · "has the ability to" → "can"
23. **Excessive hedging** — simplify: "could potentially possibly be argued that" → "may" or remove
24. **Generic positive conclusions** — replace "the future looks bright" / "exciting times lie ahead" / "major step in the right direction" with a specific, factual closing statement

### Academic-Specific Rules (ESG research context)
- Maintain academic hedging where required: "suggests", "indicates", "appears to", "the data show"
- Preserve APA-7 citation format and statistical notation exactly
- Keep BRSR, MSMED Act, SEBI, SIDBI, GRI, SDG references with their official names
- Do not convert passive constructions in methods/results sections (passive is standard there)
- Reading level target: Flesch-Kincaid Grade ~16 (Q1 journal standard)

---

## Step 3 — Export to Word (.docx)

After humanizing, export using `/docx`:

| Command | Output filename |
|---|---|
| `/literature-review` | `Literature-Review-[YYYY-MM-DD].docx` |
| `/write-review` | `Draft-[Section-Name]-[YYYY-MM-DD].docx` |
| `/methods-check` | `Methods-Critique-[YYYY-MM-DD].docx` |
| `/pre-submission` | `Pre-Submission-Audit-[YYYY-MM-DD].docx` |
| `/full-pipeline` | `Full-Pipeline-Report-[YYYY-MM-DD].docx` |
| `/draft-section` | `Draft-[Section-Name]-[YYYY-MM-DD].docx` |
| `/paper-audit` | `Paper-Audit-[YYYY-MM-DD].docx` |

Formatting: Heading styles · 12pt Calibri · 1.5 line spacing · 1-inch margins · page numbers · header with document title

---

## Step 4 — Confirm & Save

```
✓ Humanized with [voice] voice (cc-prose · 24 patterns checked)
✓ Exported: [filename].docx

Save to:  [A] Download  [B] Google Drive  [C] Notion  [D] All
```

---

## Reference

AI pattern checklist sourced from:
- [rhuss/cc-prose humanizer skill](https://github.com/rhuss/cc-prose) — version 2.2.0
- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
