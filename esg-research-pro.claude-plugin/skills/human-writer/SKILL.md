---
name: human-writer
description: Takes the fully assembled final output of any command, rewrites it into natural academic-human voice using /human, then exports it as a formatted Word (.docx) file using /docx.
argument-hint: "<complete final output to humanize and export>"
---

# human-writer — Humanize Final Output & Save to Word

Runs **once**, on the **complete final output** only — after all skills and steps in a command have finished and the full result is assembled.

## What It Does

1. **Humanize** — Pass the entire final output through `/human`:
   - Rewrite all prose to sound like a confident academic researcher wrote it
   - Remove AI-typical phrasing: "utilize", "leverage", "it is worth noting", "delve into"
   - Vary sentence rhythm; apply natural academic hedging ("suggests", "indicates")
   - Preserve everything unchanged: all data, tables, scores, citations, headings, and technical terms (ESG, MSME, BRSR, GRI, SDG)
   - No filler openers: never start with "Certainly", "Absolutely", "Of course"

2. **Export to Word** — Pass the humanized text to `/docx`:

   | Command | Output filename |
   |---|---|
   | `/literature-review` | `Literature-Review-[YYYY-MM-DD].docx` |
   | `/write-review` | `Draft-[Section-Name]-[YYYY-MM-DD].docx` |
   | `/methods-check` | `Methods-Critique-[YYYY-MM-DD].docx` |
   | `/pre-submission` | `Pre-Submission-Audit-[YYYY-MM-DD].docx` |
   | `/full-pipeline` | `Full-Pipeline-Report-[YYYY-MM-DD].docx` |

   Formatting: Heading styles · 12pt Calibri · 1.5 line spacing · 1-inch margins · page numbers

3. **Confirm** — Ask the user where to save:
   ```
   ✓ Humanized & exported: [filename].docx

   Save to:  [A] Download  [B] Google Drive  [C] Notion  [D] All
   ```
