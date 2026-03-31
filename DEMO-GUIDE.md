# Claude Code + Obsidian: Demo Guide

**Total time:** 10 minutes
**Audience:** Invoca colleagues (mixed engineers, PMs, designers)
**Goal:** Show that a personal Claude Code + Obsidian setup can act as a context-aware work assistant

---

## Pre-Demo Checklist (do this before you start)

- [ ] Open Obsidian with the `claude_code` vault (`~/Desktop/odyssey/claude_code`)
- [ ] Open a terminal and run: `cd ~/Desktop/odyssey/claude_code && claude`
- [ ] Confirm Granola MCP is live: ask Claude `list my meetings from last week` — should return real meetings
- [ ] Confirm Atlassian MCP is live: ask Claude `search Confluence for Consumer Profile` — should return results
- [ ] Do a dry run of Segment 2 and Segment 3 so you know what comes back
- [ ] Obsidian: have Graph View open in one pane, file explorer open in another

**Backup IDs (if live fetch is slow):**
- BiWeekly Product & UX Meeting (Mar 11) — Granola ID: `b8c27883-1317-4d05-b644-b89d4a9f7ca8`
- Consumer Profile docs — Confluence page IDs: `61173957239` (Part 3 Understanding), `61174513672` (Part 2 Creating)

---

## Segment 1: The Vault (2 min)

**What to say:**

> "Before I show you what Claude can do, I want to show you what it reads. This is my Obsidian vault. One folder on my laptop. Claude reads it at the start of every session."

Walk the file explorer in Obsidian:

**`CLAUDE.md`**
> "This one file is the entire instruction layer. It tells Claude who I am, what tools it has access to, and how I want it to behave. No setup wizard. No UI. Just a markdown file."

**`context/team.md`**
> "This is my team. Names, roles, what each person owns. I never re-explain my team to Claude. It already knows."

**`skills/meeting-ingest.md`**
> "Skills are reusable prompt templates. Instead of typing a long prompt every time, I just say the skill name. This one pulls a meeting from Granola, structures it, and saves it to the vault."

**`meetings/`** (point to the empty folder)
> "This folder will hold every meeting note I ingest. Right now it is empty. Let me fill it."

**Key point to land:**

> "I do not start from scratch. The vault carries the context. Claude knows me before I type a single word."

---

## Segment 2: Meeting Ingest via Granola (2.5 min)

**What to say:**

> "I had a cross-functional Product and UX biweekly on March 11. Half the R&D org was in the room. Instead of digging through notes, I will pull the transcript right now."

**In Claude Code terminal, type:**

```
Pull the BiWeekly Product & UX Meeting from March 11, 2026 from Granola and ingest it.
```

Claude will: fetch the transcript via Granola MCP, run the meeting-ingest skill, and produce a structured note with decisions, action items, and open questions. It will save the file to `meetings/`.

**While it runs:**
> "Claude is calling Granola via MCP — that is the meeting notes app I use. No copy-paste. No browser tab. Just one line."

**When the file appears in Obsidian:**
> "Decisions extracted. Action items called out. Saved as a linked note in my vault. Every meeting I run through this becomes searchable and connected to everything else."

**Key point to land:**

> "I did not paste anything. One line. Real data. Filed."

---

## Segment 3: Confluence Research via MCP (2.5 min)

**Setup line:**

> "That meeting had context I do not fully have. Consumer Profile came up as something several teams are building toward. Normally I would go to Confluence, do a few searches, read three pages, lose the thread. Let me do it differently."

**In Claude Code terminal, type:**

```
Consumer Profile came up in that meeting. Can you look up what it is in Confluence,
read the relevant pages, and give me a one-pager: what it is, how it works,
and what I need to know before my next conversation about it?
```

Claude will: search Confluence via Atlassian MCP, find the Consumer Profile series (Sam Reynolds, Nov 2025), and synthesize a summary covering:
- What a Consumer Profile is (Identifiers, Traits, Consents model)
- How profiles are created and updated (late-binding resolution)
- How data is accessed at read time
- Compliance structure (consent, PII isolation)

**While it runs:**
> "It is searching our internal Confluence right now. Not the public docs. The actual engineering wiki our team wrote."

**When summary appears:**
> "No browser. No reading four separate pages. I asked in plain English and got a grounded answer from our own documentation."

**Key point to land:**

> "The gap between 'I was in a meeting' and 'I understand what was discussed' just got a lot smaller."

---

## Segment 4: Build a New Skill Live (2 min)

**What to say:**

> "I want to make what I just did repeatable. Any time a new service comes up, I want one command that looks it up in Confluence and saves a context file to my vault. I am going to create that skill right now, while you watch."

**In Claude Code terminal, type:**

```
Create a new skill called create-context-file. It should: look up a service or topic
in Confluence, read the relevant pages, synthesize what it finds into a structured
context file, and save it to context/. Include the expected output format in the skill.
```

Claude will write `skills/create-context-file.md` live. Show it appearing in Obsidian.

**Then immediately use it:**

```
Use the create-context-file skill to create a context file for RingPool.
```

Claude will: search Confluence for RingPool, read the engineering pages (operational knowledge, filling procedures, incubation setup), and save `context/ringpool.md`.

Show the file appearing in Obsidian under `context/`.

**Key point to land:**

> "I just taught Claude a new skill in plain English. It wrote the skill itself. I used it immediately. The vault is self-extending — it grows with every session."

---

## Closing (1 min)

> "Everything you saw is: one markdown file, a skills folder, and Claude Code. The MCPs connect Claude to the actual tools I use at work — Granola, Confluence."

> "The vault started empty. Now it has a meeting note, a Consumer Profile one-pager, a new skill, and a RingPool context file. All from one 10-minute session. That compounds over time."

> "The whole thing takes an afternoon to set up. Happy to share the CLAUDE.md and skills files if anyone wants them."

---

## Backup Plans

| Risk | Backup |
|---|---|
| Granola MCP slow or wrong meeting | Say: `get the meeting with ID b8c27883-1317-4d05-b644-b89d4a9f7ca8` |
| Confluence returns sparse results | Say: `get Confluence page 61173957239` (Consumer Profile Part 3) |
| Claude Code not responding | Have pre-saved output files in `meetings/` and `context/` to show |
| Obsidian not refreshing | Cmd+R to force refresh, or point to terminal output directly |

---

## Timing Guide

| Segment | Target | Notes |
|---|---|---|
| Vault tour | 2:00 | Show CLAUDE.md briefly, read one or two lines aloud, move on |
| Meeting ingest | 2:30 | Talk over the MCP wait — explain what is happening |
| Confluence one-pager | 2:30 | Talk over the wait, point to output quality when it lands |
| Build a skill | 2:00 | Fast — one write, one use |
| Close | 1:00 | Short and punchy |
