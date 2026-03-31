---
date: 2026-03-31
tags: [slides, claude-code, obsidian, product-ux-biweekly, pkm]
type: slide-outline
---

# Slide Outline: Claude Code + Obsidian
Product UX Biweekly Presentation

---

## Slide 1 — Title

**Headline:** Your AI Work OS: Claude Code + Obsidian

**Subheadline:** How I set up a personal context layer that makes every session smarter

**Speaker / Date / Meeting:** Shohei Kato | March 2026 | Product UX Biweekly

---

## Slide 2 — What Is Claude Code + Obsidian?

### The one-sentence version
Claude Code runs in your terminal pointed at your Obsidian vault. It reads everything in that vault at session start. You never re-explain yourself.

### Why Obsidian (not Notion)

| Dimension | Obsidian | Notion |
|---|---|---|
| Storage | Local files on your machine | Cloud-hosted, API-accessible |
| Privacy | No data leaves your device | Notion servers + any AI feature calls external APIs |
| Security | Your vault, your keys, no account required | Notion AI sends your content to third-party models |
| Format | Plain markdown — Claude reads it natively | Proprietary blocks — requires export or API parsing |
| Cost | Free (dropped commercial licensing in 2025) | Business tier required for full AI features ($20/user/month) |
| Speed | Instant file reads, zero latency | API round-trips for AI features |

**The key point:** Because Obsidian is offline and local, Claude Code reads your vault as flat markdown files. No API. No export. No proprietary lock-in. From a security and privacy standpoint, your context stays on your machine.

**Obsidian's graph view is a bonus:** Obsidian visualizes how your notes link to each other. Claude reads those same connections. The mental model you build in Obsidian becomes the context Claude navigates.

### Why Claude Code + Obsidian beats GumLoop

GumLoop is excellent for shared, team-level workflow automation. Think: "everyone on the team runs this trigger and gets the same structured output." It is optimized for common patterns.

Claude Code + Obsidian is the opposite: it is deeply personalized. The value comes from:

* Your own context files (who your stakeholders are, what your active projects are, how you want outputs formatted)
* Your own skills (reusable prompt templates you write once, trigger forever)
* The combination of context + skills makes the assistant know *you specifically*, not just "a PM at a company"

GumLoop shares a workflow. Claude Code + Obsidian builds a working model of how you think.

### Resources (to include in slide notes)
* [Build Your Second Brain With Claude Code & Obsidian](https://www.whytryai.com/p/claude-code-obsidian) — WhyTryAI
* [Claude Code + Obsidian = AI Second Brain](https://agenticpm.substack.com/p/claude-code-obsidian-ai-second-brain) — The Agentic PM (directly PM-relevant)
* [Obsidian vs Notion vs Markdown Files: A 2026 PKM Comparison](https://dasroot.net/posts/2026/03/obsidian-vs-notion-vs-markdown-files-2026-pkm-comparison/) — published March 2026
* GitHub: [huytieu/COG-second-brain](https://github.com/huytieu/COG-second-brain) — most-cited public vault template (17 skills, 7 role packs)
* GitHub: [ballred/obsidian-claude-pkm](https://github.com/ballred/obsidian-claude-pkm) — starter kit with auto-git-commit hook

---

## Slide 3 — Anatomy of a Claude Code Vault

> Walk the folder structure on screen while presenting this slide.

### The core files

**`CLAUDE.md` — the instruction layer**

One file. Loaded every session, top to bottom. It tells Claude:
* Who you are
* What MCP tools are connected and how to use them
* Which skills exist and what triggers them
* Hard rules (writing style, vocabulary, what not to do)

Keep it under 150 lines of substance. If a directive is longer than two sentences, it belongs in a skill file. CLAUDE.md is navigation, not execution.

> Real example from my vault: "No em dashes. Never use the character in any output. Rewrite with commas, colons, or shorter sentences."

---

**`context/` — persistent knowledge**

Everything Claude should already know before you say a word:
* Your team roster (who each person is, what they own)
* Active initiatives (current status, key decisions, open questions)
* Org context (how your company is structured, vocabulary)
* Stakeholder files (how specific people communicate, what they care about)

Claude loads these selectively, not all at once. You configure which context loads for which task.

> Real example: When Surbhi is in a meeting, Claude automatically loads `meetings/_context/surbhi-weekly-sync.md` — which contains her evaluation rubric and communication style.

---

**`skills/` — reusable prompt templates**

Skills are executable instructions stored as markdown files. You trigger them by keyword.

| Skill | Trigger | What it does |
|---|---|---|
| `meeting-ingest` | "ingest meeting" | Fetches transcript from Granola, generates structured note, proposes initiative updates |
| `morning-brief` | "morning brief" | Pulls Jira, surfaces open action items, frames the day |
| `match-voice` | any draft request | Adjusts language to match how Shohei writes before sending |
| `prep-surbhi-sync` | "prep for 1:1" | Loads manager context, assembles talking points, flags risks |
| `daily-summary` | "EOD" | Captures what happened, what moved, what to carry forward |

Skills turn a 10-step mental workflow into a one-word command. Once written, they are permanent. They compound.

---

**`SESSION-HANDOVER.md` — anti-amnesia for context compaction**

Claude Code conversations have a context window limit. When the conversation gets long, Claude compacts earlier messages. If nothing is written down, context is lost.

SESSION-HANDOVER.md is a 30-line living snapshot:
* What was done this session
* Where open threads are in the vault
* Pending actions Shohei owns

Claude overwrites it after every significant action. When a new session starts (or after compaction), this is the first file Claude reads.

> Without this: "Hey Claude, we were working on the qualification pipeline prompt..." and you spend 5 minutes re-establishing context.
> With this: Claude opens the session already knowing where you left off.

---

**`_staging/` — confirm before you commit**

Any substantial output (meeting notes, drafts, analysis) is auto-saved here first. Nothing goes into the main vault without confirmation.

This prevents the most annoying failure mode: Claude writes something you don't want, it lands in your vault, and now you have to find and delete it.

Staging creates a one-step gate: review, then confirm or discard.

---

**`_meta/` — the system's own feedback loop**

| File | Purpose |
|---|---|
| `friction.md` | Real-time log of slowdowns, wrong outputs, re-explanations |
| `signal-log.md` | Implicit patterns in how you think and work |
| `context-routing.md` | Maps keywords to context files — gets smarter over time |
| `pkm-design-guidance.md` | The design rationale behind every vault decision |

The vault is not static. It has a feedback loop built in. Every time something goes wrong, it gets logged. Every week, the system reviews what broke and improves.

---

## Slide 4 — Four Practical Rules for Running This Well

> This slide covers the operational lessons from running Claude Code + Obsidian daily. These are not hypothetical best practices — each one maps to a real failure mode.

---

### Tip 1: CLAUDE.md instruction order = execution priority

Claude reads CLAUDE.md top to bottom. What appears first shapes behavior for the entire session.

Put the most critical instructions at the top. If your MCP health check is at line 100, Claude might run 20 minutes of work before discovering Granola is down. Put it at the top and Claude surfaces it on session start before anything else.

**Rule:** Performance-critical context at the top. Rarely-needed detail in separate files loaded on demand.

---

### Tip 2: Session handover protects you from compaction (and crashes)

Claude Code has a context window limit. When a conversation gets long, Claude compacts earlier messages. Without a written record, context is gone.

SESSION-HANDOVER.md is a 30-line living snapshot Claude overwrites after every significant action:
* What was decided this session
* Where open threads are in the vault
* What actions are pending

When compaction hits (or if Claude Code crashes or you close the terminal), you restart, Claude reads the handover file, and you are back in context immediately.

**The two failure modes this solves:**
* Compaction mid-session: Claude forgets what you were working on 45 minutes ago
* Session restart: you spend 5 minutes re-briefing Claude on where you left off

**The fix is one file, 30 lines, auto-updated.** Claude does the writing.

---

### Tip 3: Audit the vault or it turns against you

Context files accumulate. Old initiative files go stale. Two files start describing the same thing differently. A file written in Q4 contradicts what is actually true in Q1.

When Claude loads conflicting or outdated context, the output quality drops. In the worst case, it produces confident answers based on information that is no longer true.

**Signs the vault needs an audit:**
* Claude gives you a number or status you know is wrong
* Two context files describe the same initiative in different ways
* You have not reviewed a context file in 6+ weeks
* A skill produces output that needs heavy editing every time

**The fix:** A weekly `system-review` skill. It surfaces stale files, conflicting content, and skill drift — and proposes cleanup. The vault should have a feedback loop built in, not an audit you remember to run once a quarter.

---

### Tip 4: Encode your vocabulary — the Slack + terminology example

**Part A: The Slack channel ID problem**

Slack's API requires a `channel_id` (like `C012AB3CD`), not a channel name. When Claude has to look it up, it calls `slack_list_channels`, scans 200+ public channels, finds the match, then makes the actual call. That is 10 to 15 seconds of unnecessary latency on every Slack action.

The fix: a pre-built channel map in a context file.

```
context/slack-channels.md

| Channel name   | Channel ID  |
|----------------|-------------|
| #data-platform | C012AB3CD   |
| #product-ux    | C045EF6GH   |
| #odyssey-team  | C078IJ9KL   |
```

One line in CLAUDE.md: "Resolve channel names from `context/slack-channels.md` before calling any Slack tool. Never run `slack_list_channels` unless the channel is not in the map."

Result: Slack calls are instant.

**Part B: Terminology enforcement before every outbound message**

Invoca has a Confluence page with official product vocabulary. Before I send any Slack message or share any document, I want Claude to verify that every term matches the accepted standard, not a synonym I invented or a generic AI-generated alternative.

The instruction in CLAUDE.md:

> "Before producing any Slack message or document, check that every product term matches Invoca's official vocabulary. Source: [Confluence terminology page]. If a term does not match, replace it and note the substitution."

This catches the subtle drift: writing "lead pipeline" when Invoca calls it "qualification flow," or "data layer" when the accepted term is something more specific. The Confluence page is the source of truth. Claude enforces it automatically.

**The broader pattern:** Every time you re-explain something to Claude that you have explained before, that is a system design failure.

| What keeps coming up | Where to encode it |
|---|---|
| Vocabulary and terms | `context/` file or CLAUDE.md |
| MCP call patterns | CLAUDE.md |
| Recurring workflows | `skills/` file |
| Where you left off | SESSION-HANDOVER.md |

The vault's job is to eliminate the repeated briefing tax.

---

## Suggested Prompt for Claude.ai Slide Generation

> "Create a 4-slide presentation using the outline below. Slide 1 is a title slide. Slide 2 explains Claude Code + Obsidian and compares it to Notion and GumLoop — include the comparison table. Slide 3 walks through the anatomy of a Claude Code vault with 6 components. Slide 4 covers four practical operating rules: CLAUDE.md order, session handover for compaction protection, vault audits, and vocabulary enforcement with the Slack channel ID fix and Confluence terminology enforcement as concrete examples. Use a clean, minimal design. Each slide should be skimmable in under 10 seconds. Include tables and code blocks where specified."
