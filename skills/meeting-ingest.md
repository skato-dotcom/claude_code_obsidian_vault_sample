# Skill: meeting-ingest

> Triggered after a meeting ends. Fetches the transcript from Granola and produces a structured note.

---

## Step 0 — Identify the meeting

Parse the trigger for a meeting name, date, or participant signal.

* Named meeting or title → search Granola by title
* Date signal ("all my meetings today") → batch for that date
* Granola ID provided → fetch directly
* Ambiguous → ask: "Just that one meeting, or all meetings today?"

Show for each match: Title | Date | Participants

---

## Step 1 — Fetch and generate the note

Fetch full transcript via `get_meeting_transcript`.

Check `meetings/_context/` for a matching standing context file. Load if found.

Output path: `meetings/YYYY-MM-DD-[slug].md`

### Note structure

```
---
date: YYYY-MM-DD
participants: [names]
granola_id: [id]
tags: [meeting-type, initiative tags]
---

# [Meeting Title]
_[Date] | [Participants]_

## Summary
2-3 sentences. What was the meeting for? What was the outcome?

## Discussion Log
Key moments only. Format: `- **[Speaker]:** "exact quote or tight paraphrase"`

## Decisions
`- **[DECISION]** What was decided > *"quote if available"*`

## Action Items
- [ ] [Action] — [Owner] — [Due if stated]

## Open Questions
Unresolved items that need follow-up.
```

Show the full proposed note. Do not write it yet.
Ask: "Write this meeting note?"

---

## Step 2 — Write on confirmation only

Write the note only after explicit confirmation. Never auto-write.
