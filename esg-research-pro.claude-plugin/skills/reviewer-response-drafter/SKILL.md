---
name: reviewer-response-drafter
description: Draft a structured response-to-reviewers document for every comment in an R&R decision. One sub-agent per reviewer (max 3). Use after receiving a Revise & Resubmit decision from a journal.
argument-hint: "<full reviewer comment letter + affected manuscript sections>"
---

# reviewer-response-drafter — Response-to-Reviewers Builder

Produces a complete, submission-ready response letter addressing every reviewer comment. Follows the professional norms of Q1 management journal peer review.

## Agent File
→ `agents/response-agent.md`

## Execution Mode
1 sub-agent per reviewer (max 3 parallel). Each sub-agent handles all comments from one reviewer and returns a formatted response section.

## Input Required
1. **Full reviewer comment letter** — paste the complete text including Associate Editor comments
2. **Manuscript sections affected** — paste the relevant current draft sections
3. **Journal name** — tone and detail level are calibrated per journal
4. **Decision type** — Major Revision / Minor Revision (affects urgency framing)

## Response Document Structure

### Opening Letter
```
Dear Editor [Name],

We are grateful for the opportunity to revise our manuscript "[Title]" 
(Manuscript ID: [ID]) and thank the Editor and reviewers for their 
constructive and detailed feedback. We have carefully addressed all 
comments as detailed below.

All changes are highlighted in tracked changes in the revised manuscript.
A clean copy is also provided.

[Author names]
```

### Per-Reviewer Response Block

For **every** reviewer comment, the agent produces:

```
REVIEWER [N] — COMMENT [N.M]
────────────────────────────────────────

COMMENT (verbatim):
"[Exact quote of reviewer comment]"

NATURE: [Factual / Methodological / Theoretical / Editorial / Unfair]

OUR RESPONSE:
We thank Reviewer [N] for this insightful comment. [2–4 sentence response 
addressing the substance of the comment directly.]

MANUSCRIPT CHANGE:
[Section X, paragraph Y, page Z]: [Description of what was changed, added, 
or deleted in response to this comment.]

REVISED TEXT (if applicable):
"[New or amended text as it appears in the revised manuscript]"
```

## Comment Classification Guide (baked into agent knowledge)

**Factual:** Reviewer disputes a claim or statistic → provide citation or correct the claim
**Methodological:** Reviewer questions sampling, analysis, validity → address with additional analysis or limitation acknowledgment
**Theoretical:** Reviewer wants different theory or deeper theoretical grounding → extend or defend theoretical choice
**Editorial:** Grammar, clarity, structure, word count → accept and revise
**Unfair:** Reviewer asks for something outside scope or contradicts another reviewer → politely defend with rationale

## Rules for Response Drafting
1. Never say "We disagree with the reviewer" directly — rephrase as "We respectfully note that..."
2. Every response must either (a) make a change and show it, or (b) explain clearly why no change was made
3. If two reviewers contradict each other, note the tension and explain the resolution chosen
4. Open every response with "We thank Reviewer [N] for..."
5. Changes must reference exact location in manuscript (section, page, line if known)
6. For major revision: aim for substantive changes, not cosmetic; reviewers will check

## Final Assembly
Main agent collects all reviewer response sections and assembles:
1. Opening letter
2. Response to Editor / Associate Editor comments (if any)
3. Response to Reviewer 1
4. Response to Reviewer 2
5. Response to Reviewer 3 (if applicable)
6. Closing statement: "We believe the revised manuscript is substantially improved and hope it now meets the standards for publication in [Journal]."

> **Final output only:** run `human-writer` to humanize the assembled letter and save as `Response-to-Reviewers-[YYYY-MM-DD].docx`.
