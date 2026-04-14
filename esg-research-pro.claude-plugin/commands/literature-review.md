# Command: /literature-review

## Trigger
Type `/literature-review` in Claude Co-work chat.

## Purpose
End-to-end literature processing pipeline: screen papers for relevance → synthesize into themed sections → identify research gaps. Runs three skills in sequence using parallel sub-agents.

## When to Use
- When you have a new batch of papers to process (10–50 papers)
- At the start of a new literature search round
- After a weekly automated literature scout delivers new papers

## Input Prompt to Show User
```
/literature-review activated.

Please provide one of the following:
  Option A: Upload a CSV with columns: Title | Authors | Year | Journal | DOI | Abstract
  Option B: Paste a list of paper titles and abstracts directly
  Option C: Type "use Zotero" to pull from your connected Zotero collection

How many papers are you processing today? [answer determines number of sub-agents]
```

## Execution Steps

### Step 1: SCREEN (paper-screener skill)
- Determine batch size: divide total papers by 10, round up = number of sub-agents
- Maximum 5 sub-agents (cap at 50 papers per run; for 50+ papers, run in multiple batches)
- Spin up sub-agents, each using screener-agent.md
- Each agent receives its batch of 10 papers
- Collect all results → merge into one master CSV

**Sub-agent launch message:**
```
You are a literature screener for an ESG-MSME India research paper.
Load your instructions from: agents/screener-agent.md
Process these [N] papers: [batch]
Return structured JSON for each paper.
```

### Step 2: SYNTHESIZE (literature-synthesizer skill)
- Take all papers scored 4–5 from screening results
- Spin up 5 sub-agents, one per theme, each using synthesizer-agent.md
- Each agent receives: all approved abstracts + its assigned theme
- Collect all 5 theme sections

**Sub-agent launch message:**
```
You are a literature synthesizer for an ESG-MSME India research paper.
Load your instructions from: agents/synthesizer-agent.md
Your assigned theme is: Theme [N] — [Theme Name]
Papers to synthesize: [filtered approved papers]
Return a 200–300 word themed synthesis paragraph with gap statement.
```

### Step 3: GAP-SPOT (gap-spotter skill)
- Single agent using gap-agent.md
- Input: all 5 synthesized theme sections
- Output: gap matrix + 3 contribution statements + positioning paragraph

**Agent launch message:**
```
You are a research gap analyst for an ESG-MSME India research paper.
Load your instructions from: agents/gap-agent.md
Input: the following synthesized literature review sections [paste all 5 themes]
Return: gap matrix table, three contribution statements, one positioning paragraph.
```

## Final Output Assembly (Main Claude)
After all steps complete, deliver to user:

```
LITERATURE REVIEW PIPELINE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SCREENING RESULTS
Total papers processed: [N]
Included (Score 4–5): [N] → Added to Zotero recommendation
Maybe (Score 3): [N] → Review these manually
Excluded (Score 1–2): [N]

[Attach: master screening CSV]

SYNTHESIZED LITERATURE REVIEW
[All 5 themed sections assembled in order]
Total word count: [N] words

RESEARCH GAPS IDENTIFIED
[Gap matrix table]

CONTRIBUTION STATEMENTS
[3 ready-to-use bullets]

POSITIONING PARAGRAPH
[ready to paste into Introduction]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS:
→ Type /write-review to edit any section of your draft
→ Type /methods-check to review your methodology
→ Save to Notion? Type "save to Notion"
→ Save to Google Drive? Type "save to Drive"
```

## Error Handling
- If fewer than 5 papers pass screening: warn user and ask if they want to broaden search criteria
- If Zotero connection fails: ask user to upload CSV instead
- If a sub-agent times out: retry that batch with a smaller size (5 papers)

## Token Budget Note
This command uses significant tokens. Recommended: Pro or Max plan.
For large batches (40+ papers), run screening first, confirm results, then proceed to synthesis.


---

> **Final output only:** when all steps above are complete, run `human-writer` to humanize the assembled result and save it as `Literature-Review-[YYYY-MM-DD].docx`.
