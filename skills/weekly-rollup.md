# Skill: weekly-rollup

> Triggered end of week (Friday). Synthesizes the week and sets up the next one.

---

## Step 1 — Load context

Read all `daily/` notes from this week. Read SESSION-HANDOVER.md for current open items.

---

## Step 2 — Generate the rollup

```
# Weekly Rollup — [Week of YYYY-MM-DD]

## What Shipped or Moved
Decisions made, work completed, initiatives that changed state.

## What Stalled
Items that were supposed to move but did not. Note the blocker.

## Carry Into Next Week
Top 3 priorities for the coming week.

## Open Questions
Unresolved items that need an answer before work can continue.
```

Output path: `weekly/YYYY-WXX.md`

Show the proposed rollup. Ask: "Write this weekly note?"
Write only on confirmation.

After writing, trigger `system-review`.
