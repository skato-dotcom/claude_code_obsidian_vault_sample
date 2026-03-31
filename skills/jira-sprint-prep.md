# Skill: jira-sprint-prep

> Triggered at sprint planning or start of sprint. Pulls the current sprint from Jira
> and frames the week.

---

## Step 1 — Fetch sprint from Jira

Search Jira for tickets in the current active sprint assigned to Shohei or owned by the team.

Group by status: In Progress | To Do | Blocked | Done

---

## Step 2 — Generate the sprint overview

```
# Sprint Overview — [Sprint Name]

## In Progress
- [Ticket ID] [Title] — [status note if any]

## To Do This Sprint
- [Ticket ID] [Title] — [priority or dependency note]

## Blocked
- [Ticket ID] [Title] — [what is blocking it]

## Done
- [Ticket ID] [Title]

## Key Questions Before Sprint Starts
Things that need an answer before work can begin. One line each.
```

Show the overview. Ask: "Save this to working/?"
