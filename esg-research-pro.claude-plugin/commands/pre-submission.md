# Command: /pre-submission

## Trigger
Type `/pre-submission` in Claude Co-work chat.

## Purpose
Full pre-submission quality gate. Runs three skills in sequence: (1) full citation audit, (2) simulated peer review, (3) journal fit matching. Produces a submission-ready checklist and action plan.

## When to Use
- When your full draft is complete and you are preparing to submit
- When you want a comprehensive quality check before sharing with co-authors
- When you have changed your target journal and need to re-evaluate fit
- As a final pass 1–2 weeks before submission deadline

## Input Prompt to Show User
```
/pre-submission activated.

This command runs a full pre-submission audit. Please provide:

  1. Your full paper draft:
     → Upload as PDF, OR
     → Type "fetch from Drive [document name]", OR
     → Paste section by section when prompted

  2. Your complete reference list:
     → Upload as CSV from Zotero (File → Export → CSV), OR
     → Paste the formatted reference list

  3. Your target journal:
     [Type journal name — e.g., "Journal of Cleaner Production"]

  4. Your abstract and keyword list (paste below)

  5. Your primary contribution angle:
     A: ESG measurement/operationalization at MSME scale
     B: Regulatory gap — BRSR pressure without MSME support
     C: ESG as competitive enabler for Indian MSMEs

Estimated time: 15–25 minutes for a full paper review.
```

## Execution Steps

### Step 1: CITATION AUDIT (cite-verifier skill)
- Divide reference list into batches of 15
- Spin up sub-agents (1 per 15 references), each using citation-agent.md
- Collect all results → merge into audit report

**Sub-agent launch message:**
```
You are a citation integrity specialist for an ESG-MSME India paper.
Load your instructions from: agents/citation-agent.md
Verify these 15 references against CrossRef and Semantic Scholar.
Apply all 8 verification checks.
Return structured audit table.
References: [batch]
```

### Step 2: PEER REVIEW SIMULATION (peer-reviewer skill)
- Single agent using reviewer-agent.md
- Input: full paper draft + target journal
- If paper is very long (8,000+ words): split into two agents:
  - Agent A: Introduction + Literature Review
  - Agent B: Methodology + Results + Discussion + Conclusion
  - Main Claude integrates both into one report

**Agent launch message:**
```
You are a peer reviewer for [target journal].
Load your instructions from: agents/reviewer-agent.md
Write a formal peer review report for this ESG-MSME India paper.
Paper sections: [paste or fetch from Drive]
Return the complete review report including 5 response-to-reviewer questions.
```

### Step 3: JOURNAL MATCHING (journal-matcher skill)
- Single agent using journal-agent.md
- Input: abstract + keywords + method + contribution angle
- Output: ranked journal table + top 3 detailed recommendations + submission checklist

**Agent launch message:**
```
You are an academic publishing strategist.
Load your instructions from: agents/journal-agent.md
Evaluate fit for 7 target journals given:
Abstract: [paste]
Keywords: [paste]
Method: [method]
Contribution angle: [A/B/C]
Return the ranked journal table and top 3 detailed recommendations.
```

## Final Output Assembly (Main Claude)

```
PRE-SUBMISSION AUDIT COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SUBMISSION READINESS SCORE: [X/10]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PART 1: CITATION AUDIT
Total references: [N]
✓ Clean: [N] | ⚠️ Fix needed: [N] | ✗ Critical: [N]
[Full audit table]
[Priority fix list]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PART 2: PEER REVIEW REPORT
Simulated Journal: [target journal]
Recommendation: [Accept/Minor Revision/Major Revision/Reject]

[Full peer review report]

Pre-emptive Response-to-Reviewers Template:
[5 Q&A pairs ready to fill in]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PART 3: JOURNAL RECOMMENDATIONS
[Ranked journal table]

TOP RECOMMENDATION: [journal name]
Why: [3 specific reasons]
What to emphasize: [exact abstract/intro language]
Submission checklist: [full checklist]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MASTER ACTION LIST (before you submit)

MUST DO (submission blockers):
□ [item 1]
□ [item 2]
...

SHOULD DO (quality improvements):
□ [item 1]
□ [item 2]
...

INCLUDE IN COVER LETTER:
□ [item 1]
□ [item 2]
...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Save this report? Type "save to Drive" or "save to Notion"
```

## Submission Checklist Template (Journal of Cleaner Production)
```
JOURNAL OF CLEANER PRODUCTION — SUBMISSION CHECKLIST

MANUSCRIPT
□ Word count: within limit (max 12,000 words inc. references)
□ Abstract: 200–250 words, unstructured
□ Keywords: 5–8 keywords
□ Highlights: 5 bullet points, max 85 characters each
□ All sections present: Introduction, Literature Review, 
  Methodology, Results, Discussion, Conclusion
□ All figures: 300 DPI minimum, captioned
□ All tables: numbered, captioned, self-explanatory

REFERENCES
□ All DOIs verified and active
□ APA 7th edition format throughout
□ No predatory journal sources
□ All Indian regulatory citations include circular numbers

DECLARATIONS
□ Data Availability Statement present
□ CRediT Author Contribution Statement present
□ Declaration of AI Use present (if Claude was used in writing)
□ Conflict of Interest Statement: None declared / declared
□ Funding Statement present
□ Ethical Approval Statement (if survey-based research)

COVER LETTER
□ Addresses Editor by name
□ States research question and main finding in 2 sentences
□ Explains why JCP is the right venue
□ Confirms paper is not under review elsewhere
□ Lists suggested reviewers (optional but helpful)
```


---

> **Final output only:** when all steps above are complete, run `human-writer` to humanize the assembled result and save it as `Pre-Submission-Audit-[YYYY-MM-DD].docx`.
