> V2 (2026-03-31). Demo vault for Claude Code + Obsidian presentation.

## Who I Am

Shohei Kato (skato@invoca.com). Staff Product Manager on the Data Platform team at Invoca.
Manager: Surbhi Rathore. Based in Toronto.
Org context and team directory: `context/org-context.md` | `people/`

---

## Writing Rules (hard, every output)

* No em dashes. Rewrite with commas, colons, or shorter sentences.
* Bullet lists use * not -.
* Terminology check: before any outbound message, verify product terms against `context/terminology.md`. Never use a synonym if the accepted term exists.

---

## Skill Triggers

| Trigger | Skill |
|---|---|
| "resume" / session start | `resume` |
| "compact" / context window warning | `compact-prep` |
| after a meeting ends | `meeting-ingest` |
| morning / start of day | `morning-brief` |
| end of day / EOD | `daily-summary` |
| end of week / Friday | `weekly-rollup`, then `system-review` |
| sprint planning | `jira-sprint-prep` |

Full skill index: `skills/INDEX.md`

---

## Session Operations

**Session naming:** `YYYYMMDD` format. Multiple same-day sessions: `20260331a`, `20260331b`.

---

## MCP Connections

| Service | Use for |
|---|---|
| Atlassian | Jira tickets, Confluence pages |
| Granola | Meeting transcripts (`get_meetings` over `query_granola_meetings`) |
| Slack | Channel history, threads, posting messages |

**Slack channel resolution:** Before calling any Slack tool requiring a `channel_id`, resolve the channel name using `context/slack-channels.md`. Never run `slack_list_channels` unless the channel is not in the map.

**Vault-first lookup:** Before querying any MCP, check the vault first. Write MCP-pulled data back to vault.

---

## Vault Conventions

* File naming: `YYYY-MM-DD-kebab-case.md`
* Frontmatter: always include `date`, `tags`, and relevant links
* Obsidian links: use `[[wikilink]]` for all internal references
* Quote pattern: `* **[DECISION]** What was decided > *"exact quote"*`
* `context/initiatives/` is the spine of active work
