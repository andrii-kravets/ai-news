
    **Claude Second Brain 2.0: Guide to Efficient Knowledge Retention**

    **Key Concepts**:
    - **Four Memory Layers**: Claude Code uses a structured system with four layers to retain knowledge:
      1. **`CLAUDE.md` (Map)**: Core rules, facts, and naming conventions (under 200 lines).
      2. **`.claude/rules/` (Reflexes)**: Context-specific rules (e.g., folder/file rules).
      3. **`.claude/skills/` (Playbooks)**: Multi-step procedures (loaded on demand).
      4. **Auto Memory (Diary)**: Claude-generated notes (learned preferences, corrections).

    **Why It Matters**:
    - Prevents re-teaching Claude every session.
    - Optimizes context usage by loading only relevant rules/skills.

    **Setup Steps**:
    1. **Create Folders**:
       - `notes/`, `people/`, `projects/`, `drafts/`, `decisions.md`.
    2. **`CLAUDE.md` (Map)**:
       - Define folder structure, naming rules, and how to answer prompts.
       - Keep under 200 lines; use HTML comments for human notes.
    3. **`.claude/rules/`**:
       - Example: `people.md` (paths: `people/**`) for person-specific rules.
    4. **`.claude/skills/`**:
       - Example: `weekly-review/SKILL.md` for automated workflows.
    5. **Auto Memory**:
       - Claude auto-generates notes; access via `/memory`.

    **Common Pitfalls & Fixes**:
    - **Huge `CLAUDE.md`**: Reduce adherence; split into rules/skills.
    - **Incorrect Rules**: Use `/doctor prompt-audit` to resolve conflicts.
    - **No Enforcement**: Avoid relying solely on `CLAUDE.md` for \"never do X\"; use **PreToolUse hooks**.

    **Audit Checklist**:
    - Does `CLAUDE.md` appear under \"Memory files\" in `/context`?
    - Is `CLAUDE.md` under 200 lines?
    - Is auto memory enabled and populated?

    **Actionable Takeaway**:
    - Implement the **One-Prompt Setup** to avoid manual errors.
    - Follow [@mojeskoqq](https://x.com/mojeskoqq) for advanced setups.
    
## Claude Second Brain 2.0: The Complete Guide

9 хв читання

Every session you start, Claude forgets you. Here's how to stop losing everything you taught it.

Be honest. How many times have you explained the same thing to Claude?

Your folder layout. Your naming rules. "No, not like that, like THIS." You fix it on Monday. On Tuesday you open a new session and it's gone. You fix it again. And again.

That isn't a bug. It's how it works: every Claude Code session starts with a fresh context window. Everything you said in chat, every correction, every "remember this" you never wrote down, disappears the moment the session ends.

You're not building anything. You're re-teaching the same intern every morning, and paying for the tokens every time.

The viral "second brain" guide tried to fix this. It got one thing right: you don't need Obsidian, Notion or another $20/month app. Plain Markdown files and one map file.

But it stopped at layer one. And two of its key lines are wrong.

Claude Code has four memory layers. Most people use one, stuff it until Claude stops listening, and then decide "AI memory doesn't work."

It works. You just set up a quarter of it.

Reading time: 6 minutes. Setup: about 10. After that you never explain the same thing twice.

****Bookmark it now. The copy-paste setup prompt is near the end, and you'll want it open when you build.****

---

### The Short Answer

A second brain in Claude Code is four layers, each loading at a different moment:

1. ****CLAUDE.md, the map.**** You write it. Loads every session. For rules and facts Claude needs every single time.
2. ****.claude/rules/, the reflexes.**** You write them. Load only when Claude touches matching files. For rules about one folder or one file type.
3. ****Skills, the playbooks.**** You write them. Load only when invoked or relevant. For multi-step procedures.
4. ****Auto memory, the diary.**** Claude writes it. Loads every session (first 200 lines / 25KB). For your corrections and preferences, learned automatically.
![](https://pbs.twimg.com/media/HV4qGQiaQAATtrR.jpg)

Every session you start, Claude forgets you. Here's how to stop losing everything you taught it.

****The golden rule: put each piece of knowledge in the layer that loads only when it's needed.**** That's how your brain stays big while Claude's context stays small.

---

### What You Need

- Claude Code. Some features below need a recent version; the version is noted where it matters.
- A folder. Any folder. Plain.md files.
- 10 minutes. You fill the rest in as you go.

No installs, no plugins, no database.

---

### First, the 2 Myths From the Viral Guide

That guide has 13 million views. Which means a lot of people built their setup on these two lines, and are now wondering why Claude still ignores them.

![](https://pbs.twimg.com/media/HV4qUBHbwAAPm8q.jpg)

Every session you start, Claude forgets you. Here's how to stop losing everything you taught it.

****Myth 1: "CLAUDE.md is loaded into the system prompt."**** The docs say: "CLAUDE.md content is delivered as a user message after the system prompt, not as part of the system prompt itself." Claude reads it and tries to follow it, but there's no guarantee of strict compliance, especially for vague or conflicting instructions.

****Myth 2: "If the info isn't there, the agent reports a failure instead of hallucinating."**** Nothing in the docs promises that. Anthropic is explicit: Claude treats memory files "as context, not enforced configuration." If something must never happen, don't write a polite sentence in CLAUDE.md. Use a PreToolUse hook, which runs as a shell command and applies no matter what Claude decides.

Translation: if your "never do this" lives only in CLAUDE.md, you're hoping, not protected.

Now let's build it properly.

---

### The Skeleton

```
second-brain/
├── CLAUDE.md            # Layer 1: the map (keep under 200 lines)
├── CLAUDE.local.md      # your private notes for this folder (gitignore it)
├── decisions.md         # log of choices and why
├── notes/               # one topic per file
├── people/              # one person or company per file
├── projects/            # status, where you paused, next step
├── drafts/              # writing in progress
└── .claude/
    ├── rules/           # Layer 2: load only when needed
    │   ├── people.md    # paths: people/**
    │   └── writing.md   # paths: drafts/**
    └── skills/          # Layer 3: playbooks
        └── weekly-review/
            └── SKILL.md
```

Layer 4 (auto memory) you don't create. Claude does. Open it any time with /memory.

The one-topic-per-file discipline from the viral guide still stands: tax-policy.md, not notes.md. ivan-petrov.md, not note-12.md. Lowercase, hyphens.

---

### Layer 1: CLAUDE.md, the Map (Under 200 Lines)

This is where everyone overdoes it. You get burned once, so you add a rule. Then another. Six months later your CLAUDE.md is a 600-line wall, and Claude follows less of it than when it was 50.

That's not paranoia, that's the docs. Their target: under 200 lines per CLAUDE.md. Longer files "consume more context and reduce adherence." In plain words: the bigger your map, the worse Claude follows it.

So the map holds only what Claude needs in every session: where things live, naming rules, how to answer.

```
# Second brain: map
<!-- For humans: last cleaned 2026-10-29. Keep this file under 200 lines. -->

## Where things live
- notes/: one topic per file, named after the topic
- people/: one file per person or company
- projects/: status, last stop, next step
- decisions.md: every choice I make, with the reason

## How to answer
- Look up the file before answering. Quote the file name you used.
- If no file covers it, say so and suggest which file to create.

## Naming
- lowercase-with-hyphens.md, one topic per file

## Always in focus
- Current priorities: @projects/now.md
```

****Three tricks hiding in that example:****

1. ****HTML comments cost zero tokens.**** Block-level <!--... --> comments are stripped before CLAUDE.md is injected into context. Leave notes for yourself or your team for free.
2. ****Imports organize, they don’t save.**** The import line in that example pulls projects/now.md into context, and imports can chain up to 4 hops deep. But the docs are clear: imports “don’t reduce its context cost.” Everything you import loads every session. Import only what truly must always be in focus.
3. ****Backticks turn an import off.**** Wrap the path in backticks and Claude reads it as plain text. Leave it bare after the @ sign and Claude imports the file.

Don't want to write it from scratch? Run /init and Claude drafts a starter CLAUDE.md. Set CLAUDE\_CODE\_NEW\_INIT=1 first and /init turns interactive: it asks whether to set up CLAUDE.md, skills and hooks, explores with a subagent, and shows you a proposal before writing anything.

****Personal layer:**** CLAUDE.local.md sits next to CLAUDE.md, loads the same way, and is meant for you only. Add it to.gitignore. ****Global layer:**** ~/.claude/CLAUDE.md applies to every project on your machine.

---

### Layer 2: Rules That Load Themselves

If all your rules live in CLAUDE.md, every one of them gets shoved into every single session. Your writing rules load when you ask about taxes. Your people rules load when you're fixing a typo. You pay for all of it, every time.

This layer ends that.

Put Markdown files in.claude/rules/. Add a paths: field and the rule loads only when Claude reads, writes or edits a matching file. The rest of the time it costs nothing.

****.claude/rules/people.md:****

```
---
paths:
  - "people/**"
---
# People cards
- Sections: Who, How we met, Last contact (date), Open threads
- Update "Last contact" every time you edit a card
- Never store passwords, card numbers or ID numbers here
```

****.claude/rules/writing.md:****

```
---
paths:
  - "drafts/**"
---
# Writing voice
- Short sentences. No filler openers.
- Every claim needs a source line under it
```

Ask about your dentist and the people rules switch on. Ask about your draft and the writing rules switch on. Ask about taxes and neither one loads.

Rules without paths load at launch, like CLAUDE.md. Personal rules in ~/.claude/rules/ apply to every project you open.

---

### Layer 3: Skills, the Playbooks

CLAUDE.md is for facts. Anything that is a procedure ("every Friday, do these 6 steps") belongs in a skill. The docs: skills "only load when you invoke them or when Claude determines they're relevant to your prompt."

****.claude/skills/weekly-review/SKILL.md:****

```
---
name: weekly-review
description: Use when I ask for a weekly review of my second brain.
---
1. Read every file in projects/.
2. List what moved this week, what is stuck, and the next step for each.
3. Check people/ for anyone with "Last contact" older than 30 days.
4. Append today's decisions to decisions.md with the reason.
5. Write the review to notes/weekly-review-YYYY-MM-DD.md.
```

Now "do my weekly review" runs the whole routine, and the other 6 days of the week those steps take zero context.

---

### Layer 4: Auto Memory, the Brain That Writes Itself

This is the part the viral guide never mentions, and the one that hurts most to miss.

Think about every time you corrected Claude and it said "got it." Without auto memory, "got it" lasted until the session closed. Every one of those corrections is gone. You taught it, and you lost it.

Claude Code keeps auto memory: notes Claude writes itself, based on your corrections and preferences. It loads every session (the first 200 lines or 25KB), it's per repository and shared across worktrees, and it's all plain Markdown you can read, edit or delete.

****How to feed it:****

- Say "remember that I always want sources under every claim" → Claude saves it to auto memory.
- Say "add this to CLAUDE.md" → it goes into your map instead.
- Run /memory → see every memory file, toggle auto memory on or off, open the auto memory folder.

Rule of thumb: ****you write the map, Claude writes the diary.****

Quick pause. If you just realized half your corrections never got saved, follow [****@mojeskoqq****](https://x.com/mojeskoqq). I break down Claude Code features like this one, checked against the official docs and explained in plain words.

---

### The One-Prompt Setup

Too lazy to build it by hand? Open Claude Code in an empty folder and paste this:

```
Set up a second brain in this folder, following the Claude Code memory docs:

1. Create folders: notes/, people/, projects/, drafts/.
2. Create CLAUDE.md under 200 lines: where things live, naming rule
   (lowercase-with-hyphens.md, one topic per file), and "look up the
   file before answering, quote the file name, say so if no file covers it".
   Add one HTML comment at the top for humans.
3. Create .claude/rules/people.md with paths: "people/**"
   (sections: Who, How we met, Last contact, Open threads;
   never store passwords, card or ID numbers).
4. Create .claude/rules/writing.md with paths: "drafts/**"
   (short sentences, a source line under every claim).
5. Create .claude/skills/weekly-review/SKILL.md with name and description
   frontmatter: review projects/, flag people with Last contact older
   than 30 days, log decisions, save the review to notes/.
6. Create decisions.md and projects/now.md, and import @projects/now.md
   from CLAUDE.md.
7. Create CLAUDE.local.md for my private notes and add it to .gitignore.

Show me the file tree when done. Don't invent content for my notes.
```

Then run /context and check that CLAUDE.md shows up under "Memory files".

---

### How Claude Actually Loads All This

Knowing the load order is what separates a second brain from a junk drawer.

1. ****At launch:**** every CLAUDE.md and CLAUDE.local.md from your working folder and every folder above it, ordered from the top of the drive down. Within each folder, CLAUDE.local.md comes after CLAUDE.md. Files are concatenated, not overridden.
2. ****Also at launch:**** rules without paths, plus your auto memory.
3. ****On demand:**** a CLAUDE.md inside a subfolder loads the first time Claude touches a file in that subfolder. Path-scoped rules load the same way.
4. ****After /compact:**** your project-root CLAUDE.md is re-read from disk and comes back. Instructions you only typed in chat do not. That rule you spent 20 minutes explaining an hour ago? Compacted away. If it matters, write it down.

One limit to know: on-demand files over a per-file size limit get cut (40,000 characters on a 200K context window). Claude gets the start plus a note to read the rest.

---

### The 5 Commands That Keep It Healthy

1. /init: drafts a starter CLAUDE.md (interactive with CLAUDE\_CODE\_NEW\_INIT=1).
2. /memory: lists and opens every memory file, toggles auto memory.
3. /context: shows what actually loaded, under "Memory files".
4. /doctor prompt-audit: finds outdated, broken or contradicting instructions and changes nothing until you approve (v2.1.283+).
5. "remember …": saves a preference straight into auto memory.

Run /context once after setup. If a file isn't listed under Memory files, Claude can't see it.

---

### Common Pitfalls

- ****A huge CLAUDE.md.**** Less adherence, more context burned every session. → Keep it under 200 lines, move the rest to rules and skills.
- ****Importing everything with @.**** Imports load every time, no savings. → Import only the always-on core.
- ****Two files that disagree.**** Claude "may pick one arbitrarily." → Run /doctor prompt-audit.
- ****"Never do X" written in CLAUDE.md.**** It's context, not enforcement. → Use a PreToolUse hook.
- ****An important rule typed only in chat.**** Gone after /compact. → Put it in CLAUDE.md.
- ****One giant notes.md.**** Claude can't find anything. → One topic per file.

---

### The 60-Second Audit: How Much Are You Losing Right Now?

Don't build anything yet. Open your current project and answer five questions. Every "no" is something leaking out of every session you run.

1. ****Does Claude even see your CLAUDE.md?**** Run /context and look under "Memory files". Not listed? Then every rule you wrote in there has never reached Claude. Not once.
2. ****Is it under 200 lines?**** Count. If it's longer, you're paying every session for a map Claude follows worse with every line you add.
3. ****Is anything in your auto memory?**** Run /memory and open the auto memory folder. Empty, or switched off? Then every "no, do it like this" you've ever typed is gone.
4. ****Where does your most important "never" live?**** If it's a sentence in CLAUDE.md, it's a wish. Docs: context, not enforcement. A PreToolUse hook is the only version that can't be ignored.
5. ****Do your files contradict each other?**** Run /doctor prompt-audit (v2.1.283+). If two files disagree, Claude "may pick one arbitrarily", and you'll never know which one it picked.

Three or more "no"? You don't have a second brain. You have a notes folder Claude glances at.

---

### Two Versions of Tomorrow Morning

****Without it:**** you open a new session. Claude doesn't know your folders, your naming, your "never do this". You type the same three paragraphs you typed yesterday. It makes the mistake you corrected last week. You correct it again. The tokens you spent teaching it last time? Gone with the session.

****With it:**** you open a new session and just ask. Claude already knows where things live, which rules apply to the file it's touching, and every correction you ever made. The playbook runs when you say its name. Nothing you taught it is lost.

Same Claude. Same price per token. The only difference is the 10 minutes you spend tonight.

Paste the One-Prompt Setup before you close this tab. Then do three things:

- ****Bookmark this.**** In a month you'll want to run the audit again.
- ****Follow**** [****@mojeskoqq****](https://x.com/mojeskoqq) for more Claude Code setups like this, tested and explained in plain words.
- ****Repost it**** for the friend who still re-explains their folder layout to Claude every morning.

And reply with your audit score. How many "no" did you get?

[12](https://x.com/compose/post?in_reply_to=2116176596466032817)

39

323

1 тис.