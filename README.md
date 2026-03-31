# Claude Code + Obsidian Vault: Sample Setup

A working example of how to use Claude Code as a context-aware work assistant by pairing it with an Obsidian markdown vault.

The core idea: instead of re-explaining your context every session, you keep a folder of markdown files that Claude reads automatically. The vault carries the context so you don't have to.

---

## What's in this repo

```
.
├── CLAUDE.md                   # Claude's instruction layer — writing rules, skill triggers, MCP config
├── DEMO-GUIDE.md               # 10-minute walkthrough script
├── SESSION-HANDOVER.md         # Where Claude leaves a breadcrumb at the end of each session
├── _staging/                   # Drafts and outputs before they're moved to the vault
├── context/
│   ├── org-context.md          # Who's who and how the org is structured
│   ├── team.md                 # Your immediate team
│   ├── slack-channels.md       # Pre-encoded channel IDs (avoids API lookup latency)
│   ├── terminology.md          # Domain-specific terms Claude should know
│   └── initiatives/            # Active project context
└── skills/
    ├── INDEX.md                # Full skill index with triggers
    ├── meeting-ingest.md       # Pull a transcript, structure it, save it
    ├── morning-brief.md        # Start-of-day digest
    ├── daily-summary.md        # End-of-day wrap
    ├── weekly-rollup.md        # Week-in-review
    ├── jira-sprint-prep.md     # Sprint planning from Jira
    ├── resume.md               # Resume a session from SESSION-HANDOVER.md
    ├── compact-prep.md         # Compress context before hitting token limits
    └── system-review.md        # Periodic vault health check
```

---

## How it works

**CLAUDE.md is the entry point.** When Claude Code opens this folder, it reads CLAUDE.md first. That file defines:

* Writing rules (applied to every output)
* Which skill to run in which situation
* Which MCP connections are available and how to use them
* Vault conventions for file naming and structure

**Skills are reusable prompts saved as markdown.** Instead of typing the same instructions repeatedly, you write a skill once and trigger it by name. Claude reads the skill file and executes it. You can create new skills in plain English mid-session.

**Context files give Claude persistent memory.** Files in `context/` describe your team, your projects, and your organization. Claude reads them when relevant so you don't re-explain the same background every time.

**SESSION-HANDOVER.md keeps continuity across sessions.** At the end of each session, Claude updates a short "resume here" block. The next session picks up from that point.

---

## MCP integrations (configured in CLAUDE.md)

| Service | What it's used for |
| --- | --- |
| Atlassian | Read and write Jira tickets and Confluence pages |
| Granola | Pull meeting transcripts by ID |
| Slack | Read channel history, post messages, look up users |

Pre-encoding known IDs (like Slack channel IDs) in `context/slack-channels.md` eliminates runtime lookup latency.

---

## Getting started

1. Clone this repo and open the folder in Obsidian (File > Open Vault)
2. Open the same folder in Claude Code (`claude` in terminal from the folder root)
3. Replace the sample context files with your own: org, team, projects
4. Update CLAUDE.md with your name, role, and any MCP connections you have set up
5. Run `/resume` to let Claude orient itself, then start working

The DEMO-GUIDE.md walks through a 10-minute live demonstration if you want to show this to teammates.

---

## Customizing for your context

The sample files use placeholder content. To make this yours:

* `context/org-context.md`: describe your company and org structure
* `context/team.md`: your immediate team and their roles
* `context/terminology.md`: domain terms, product names, acronyms Claude should know
* `context/slack-channels.md`: channel names and IDs you use regularly
* `skills/`: keep, modify, or delete any skill; add new ones as you find patterns in your work

---

## Notes

* All files are plain markdown. No plugins, no proprietary formats.
* Claude Code reads the vault at session start. Changes you make to context files take effect next session (or mid-session if you tell Claude to re-read a file).
* The `.obsidian/` folder contains workspace settings for Obsidian. Safe to delete if you're not using Obsidian.
