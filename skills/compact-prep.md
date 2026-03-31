# Skill: compact-prep

> Triggered when the context window is approaching its limit, or before a manual compact.
> Goal: preserve everything needed to resume without loss.

---

## Step 1 — Write SESSION-HANDOVER.md

Overwrite SESSION-HANDOVER.md with the current state. Max 30 lines.

```
# Session Handover

> Overwritten each session. Max 30 lines.

# RESUME HERE — Session [YYYYMMDD]

## What was done
* [Key actions taken this session]

## In progress
* [Work that was underway when compact triggered]

## Pending actions
* [Things Shohei or Claude still needs to do]

## Open staging files
* [Any files in _staging/ that have not been confirmed]
```

---

## Step 2 — Confirm staging files

List any files in `_staging/`. Ask: "Confirm or discard each before compacting?"

---

## Step 3 — Ready to compact

"SESSION-HANDOVER.md is current. Safe to compact."
