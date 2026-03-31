# Skill: system-review

> Triggered weekly (after weekly-rollup) or on demand. Reviews the vault for staleness,
> conflicts, and design drift. Surfaces problems; Shohei makes the decisions.

---

## Step 1 — Audit context files

Scan `context/`. For each file, check:
* Last modified date — flag anything older than 6 weeks
* Does it conflict with another file on the same topic?
* Is it still accurate based on what happened this week?

Report: list of files with status (current / stale / conflicting).

---

## Step 2 — Audit skills

Scan `skills/`. For each skill, check:
* Does it produce output that needs heavy editing? (check friction.md)
* Is the output path still correct?
* Has the trigger drifted from how it is actually being used?

Report: list of skills with status (working / drifted / needs update).

---

## Step 3 — Audit CLAUDE.md

* Is it under 150 lines of substance?
* Are there directives that belong in a skill file instead?
* Are there skills listed that no longer exist?

---

## Step 4 — Propose changes

For each issue found, propose a specific fix. Do not auto-apply anything.
Ask: "Apply these changes?" for each batch.

---

## Step 5 — Append to friction log

Append a summary of what was found to `_meta/friction.md`:
`| [date] | system-review | [what was found] | [what was fixed] |`
