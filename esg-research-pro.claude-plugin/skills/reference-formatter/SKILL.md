---
name: reference-formatter
description: Reformat a raw or mixed-style reference list into the exact citation style required by your target journal (APA-7, Harvard, AMS, Chicago). Distinct from cite-verifier which validates existence — this skill handles formatting compliance only.
argument-hint: "<reference list (any format) + target journal name or citation style>"
---

# reference-formatter — Reference List Formatter

This skill formats references correctly. For validating that references exist and are accurate, use `cite-verifier` first, then run this skill on the verified list.

## Agent File
→ `agents/reference-agent.md`

## Execution Mode
- Single agent for up to 50 references
- 2 parallel sub-agents for 50+ references (split at midpoint alphabetically)

## Input Required
1. **Reference list** — in any current format (or mixed formats)
2. **Target journal or style** — e.g. "Journal of Cleaner Production" or "APA-7"

## Journal-Style Mapping (baked into agent)
| Journal | Required Style |
|---|---|
| Journal of Cleaner Production | APA-7 |
| Business Strategy & Environment | APA-7 |
| Sustainability (MDPI) | APA-7 (MDPI variant) |
| Journal of Small Business Management | APA-7 |
| Journal of Business Ethics | APA-7 |
| Asia Pacific Journal of Management | Springer Harvard |
| IIMB Management Review | APA-7 |

## APA-7 Formatting Rules (Primary Style)

### Journal Article
`Author, A. A., & Author, B. B. (Year). Title of article. *Journal Name*, *Volume*(Issue), Page–Page. https://doi.org/XXXXX`

### Book
`Author, A. A. (Year). *Title of book* (Edition). Publisher.`

### Book Chapter
`Author, A. A. (Year). Title of chapter. In E. Editor (Ed.), *Title of book* (pp. X–X). Publisher.`

### Government Report / SEBI Circular
`Ministry/Agency Name. (Year, Month Day). *Title of report/circular* (Circular No. XXXX/YYYY). Official URL`
Example: `Securities and Exchange Board of India. (2021, May 5). *Business Responsibility and Sustainability Reporting* (Circular No. SEBI/HO/CFD/CMD-2/P/CIR/2021/562). https://www.sebi.gov.in/...`

### MSME Ministry / MCA Notification
`Ministry of Micro, Small and Medium Enterprises. (Year). *Title*. https://msme.gov.in/...`

### Working Paper / Report (SIDBI, RBI, World Bank)
`Author, A. A. (Year). *Title of report* (Report No. if available). Organisation. URL`

### Online Source (only if no better version exists)
`Author, A. A. (Year, Month Day). Title. Site Name. URL`
— Flag if URL is a news article, press release, or Wikipedia (unacceptable sources)

## Checks and Flags Applied

For every reference:
- ⚠️ **Missing DOI** — add if findable via CrossRef; flag if not available
- ⚠️ **Missing issue number** — flag for journals that require it
- ⚠️ **Inconsistent author format** — "et al." used in reference list (not allowed in APA-7 refs)
- ⚠️ **Missing page range** — flag for journal articles
- ⚠️ **Italics missing** — journal names and book titles must be italicised
- ⚠️ **Year placement** — year must follow author names in APA-7
- ⚠️ **URL without access date** — APA-7 does not require access dates for stable URLs; remove if present

## Output Format
```
REFERENCE LIST — FORMATTED ([Style])
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Alphabetically sorted, fully formatted reference list]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FORMATTING ISSUES FOUND: [N]
⚠️ [Ref author, year]: [issue description]
...

COPY-READY: Paste the formatted list above directly into your manuscript.
```
