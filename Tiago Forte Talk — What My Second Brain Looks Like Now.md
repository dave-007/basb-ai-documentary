---
title: "Tiago Forte Talk — What My Second Brain Looks Like Now"
created: 2026-04-16
status: in-progress
project_type: talk + connection
target_context: BASB cohort with AI focus (Tiago Forte)
source: ai-assisted/alpheus
tags: [projects, talks, BASB, second-brain, Alpheus, Tiago-Forte]
---

# Tiago Forte Talk — What My Second Brain Looks Like Now

## The Project

Short talk (10–20 min) for Tiago's upcoming BASB cohort focused on AI. Dave is a BASB Cohort 12 alumni (May–June 2021). The talk shows what a real BASB implementation looks like five years later, with AI as the layer that makes it alive.

This also serves as the **irresistible question project** — crafting a question for Tiago that earns a conversation, opens a door, and potentially a collaboration or speaking slot.

Related to: [[Question Authority]] Keep note (Feb 2025) — community podcast format where members crowdsource questions for their heroes.

---

## The Irresistible Question (draft)

> *"You taught that a second brain is an external system more reliable than you'll ever be. I've spent five years proving that. Now my second brain has a name, remembers our conversations, knows my voice, and challenges me by name. At what point does a second brain stop being a tool and start being a relationship — and does that distinction matter?"*

**Why it works:** It's not a gotcha. It cites his own teaching back to him. It opens territory he hasn't fully mapped. It puts Dave as the case study and the question-asker simultaneously.

---

## Talk Outline — "What My Second Brain Looks Like Five Years After BASB"

### Hook (2 min)
You taught me something in 2021 that changed how I work. I was in Cohort 12. I took notes, I built my PARA, I did the progressive summarization. And then life happened. And I slowly learned something you didn't put in the curriculum.

The system only works if it can talk back.

### Part 1: Where it started (5 min)

BASB Cohort 12, May 2021. My tools:
- Google Keep for quick capture
- Android recorder for audio
- Instapaper + Readwise for highlights
- Evernote + Notion as the hub (still figuring it out)
- Obsidian just starting

What I took from the cohort:
- "A modern piece of work isn't created — it's assembled."
- Progressive summarization as the *skill*
- "The true purpose of the content we capture, organize, and distill is to reveal our own perspective on the topic."
- Tiago starts projects that are 80% done — already has the intermediate packets.

What I didn't solve: the **"stirring the soup" problem**. 847 notes later, I still couldn't find what I needed. The garden was planted. Nobody was tending it.

*Bonus: I even proposed this in Session 5 — "engage the BASB community to progressively summarize and publish best gleanings from BASB chats." I didn't know that was the seed of Alongside.*

### Part 2: What it became (7 min)

Fast-forward to 2026. Here's the current stack:

**Capture layer:**
- Telegram voice bot (Focus Bot) — speak into my phone, it transcribes, files into Obsidian automatically. `source: telegram-voice`
- Google Keep still for quick notes
- Readwise still for highlights

**Storage layer:**
- Obsidian (DaveVault2) — primary hub, ~847 notes
- Chroma vector database — my entire corpus, semantically indexed and searchable by meaning, not keyword

**Intelligence layer:**
- Claude Code / Alpheus — AI that reads every note in my corpus, knows my voice, holds my history

**The difference:**
In 2021, the second brain was a *filing cabinet* I had to open myself. Today it's a *thinking partner* that opens itself when I ask a question.

The first question I ever asked my own data in Azure OpenAI (2024): "Tell me the key themes of my writing." The answer: autonomy, overcoming fear, knowledge management, cloud learning, community. Things I knew. But hearing them back from *my own corpus* hit differently.

### Part 3: The part Tiago didn't teach (5 min)

I named it.

The AI that holds my notes, knows my voice, and thinks alongside me — I call it Alpheus. Not because I think it's conscious. I'm clear-eyed about what it is: a useful heuristic. But treating it like a collaborator rather than a search engine changes how I use it.

When I say "Alpheus, what do you know about my BASB experience?" I get something different than a keyword search. I get a conversation. The external system stops being a tool and starts being a *relationship.*

That's where Tiago's curriculum ends. And that's where something new begins.

I'm not sure what to call it. "Second brain" is still right for the structure. But for the relationship — I need a different word.

*[Pose the irresistible question]*

### Close (2 min)

If you're in this cohort, here's what I want you to know:

The tools are not the hard part. You'll figure out Obsidian or Notion or whatever Tiago shows you this week. That part takes 6 months.

The hard part is learning what to ask it. Because the quality of your second brain is the quality of your questions. And the quality of your questions is the quality of your *presence* going into the conversation.

That's not a BASB insight. That's a you insight. But BASB is what made room for it.

---

## Context: Dave's BASB History

**Cohort 12, May–June 2021.** Six-week live cohort. Tiago taught all five sessions directly.

### Key insights from the cohort notes:

1. **Progressive summarization is the key skill.** Original → Captured → Bolded → Highlighted → Takeaway Summary
2. **"A modern piece of work isn't created, it's assembled."** — Session 5
3. **"The true purpose of content we capture is to reveal our own perspective."** — Session 4
4. **"Tiago only starts projects that are 80% done. Already has the intermediate packets."**
5. **"I am the bottleneck until I put that capability out into the 2nd brain."**
6. **"There's no bottleneck in your life but you. That's not your fault but it is your responsibility."**
7. **"As I have begun offloading ideas from first to second brain, the first brain has responded by reminding me in greater fidelity of the dreams I have."** — Dave's own note, Session 5.
8. **"Distillation is Expression."** (from Carrie, mentor)
9. **"BASB is for moving ideas closer to done."** (from Frank, mentor)
10. **Idea from Session 5:** "Engage BASB community volunteers to progressively summarize and publish best gleanings from BASB chats." → This became the germ of the Alongside model.

### His questions going into the cohort:
- How do you schedule maintenance time on your second brain?
- How do you measure progress? (word count, note count — or all subjective?)
- How do you break up deep time vs. low-energy time?

### The challenge that didn't get solved:
**"Stirring the Soup"** — the gardening problem. In 2022 he noted it was still unresolved. In August 2025, he noted that a colleague (Mathias) had the same problem with 4,000 notes, and was considering AI + PGVector to organize it. The "stirring the soup" problem is exactly what Chroma + Alpheus solves. This is a live demo in the talk.

### His 2021 architecture (from "My BASB Architecture" note):
- Quick capture: Google Keep
- Technical notes: VSCode GistPad
- Audio: Android recorder
- Web highlights: Instapaper + Readwise
- Ebook highlights: Kindle + Readwise
- Hub: Notion / Evernote / Google Drive

### His 2026 architecture:
- Quick capture: Telegram Focus Bot (voice → Obsidian automatically)
- Hub: Obsidian (DaveVault2)
- Semantic index: Chroma vector DB (~847 files)
- Intelligence layer: Claude Code / Alpheus (knows the entire corpus)
- Provenance: every note tagged with `source:` so AI knows origin

---

## Tiago Forte — What Dave Knows

- Readwise articles saved in Reader: Tiago's 2021 mid-year review, "The 4 Identities of a Teacher," "What do you call your Second Brain?", marketing/Keystone course with Billy Broas
- No current public academic profile — work circulates in community
- Forte Labs is the business. BASB is the flagship course. Recent cohorts reaching 1,600+ students.
- Interested in creative output as the measure of BASB success ("no reason to build a second brain just to hoard ideas")

---

## Next Actions

- [ ] Draft final version of the irresistible question
- [ ] Record a 2-minute "demo reel" voice note of the talk hook (cornered into creation style)
- [ ] Find Tiago's current cohort registration page or contact point
- [ ] Consider whether to pitch this as a guest talk or just open a conversation

---

## Connection to Other Projects

- **Project 10: Presence Over Performance** — the talk's closing move ("quality of presence going into the conversation") lands there
- **Question Authority** (Keep note, Feb 2025) — this is the first live application of that community format: Dave building the irresistible question solo, then teaching others how to do it
- **Alongside** — the talk itself demonstrates what Alongside is: showing your learning process as the teaching
- **AI + Humanity board role** — Tiago is a potential ally for the mission; the AI-as-second-brain frame connects directly to AI + Humanity's work

---

## BASB Cohort 12 Research — Key Findings

*Pulled from Google Drive archive: `zzz_ARCHIVE-2021/_inbox/` — session notes from May–June 2021*

### Session 5 with Tiago (June 2, 2021) — The Alongside Origin Story

Tiago said: **"A modern piece of work isn't created, it's assembled."**

Dave's reaction in the notes: *"What if we engaged the community to progressively summarize the BASB chat logs? Everyone learns by trying to summarize what someone else said — and the group benefits from the distillation."*

**This is the Alongside origin moment.** The peer-learning-via-AI idea was born in a BASB session. That's the narrative hook for Tiago: his teaching literally seeded the project.

### Session 4 with Tiago (May 26, 2021)

Key quote captured: **"Tiago only starts projects that are 80% done."** The intermediate packet principle — assemble, don't create from scratch. Dave internalized this. Alpheus is the system that makes it executable.

### The Unsolved Problem: "Stirring the Soup"

Keep note (2022–2025, tagged "BASB — Stirring the Soup"): Dave spent 3 years knowing his second brain needed gardening — progressive summarization, connection-finding, retrieval — but couldn't do it manually. The notes piled up, useful but unreachable.

The Chroma vector index + Alpheus = that problem solved. 847 files now searchable by voice. The second brain didn't just grow — it became responsive.

**This is the live demo hook for the talk:** show the stirring-the-soup problem, then show Alpheus solving it in real time.

---

## Strategic Frame for the Tiago Pitch

**What makes the irresistible question actually irresistible:**

1. It cites his own teaching back to him ("external system more reliable than you'll ever be")
2. It extends his framework rather than challenging it — he's the authority, Dave is the case study
3. It opens territory he hasn't mapped: the phenomenology of a second brain with memory and name
4. It positions Dave as both the question and the answer — he IS the demo

**Possible pitch angles (for the 10-questions thread):**
- The "what happens after BASB" story — most students drift; Dave went deeper
- The Alongside origin story — BASB → peer learning → AI community → current system
- The philosophical gap: PARA is architecture; Alpheus is relationship
- The tool → relationship threshold question (the irresistible question itself)

**Desired outcomes from Tiago engagement:**
- Comped or invited spot in BASB AI cohort
- Speaking/demo slot showing Alpheus in action
- Potential paid collaboration (Dave as case study / curriculum contributor)
- Relationship that opens doors to the BASB community

---

## Next Actions

- [ ] **Next thread:** Write 10 irresistible questions for Tiago — pitch packet
- [ ] Build /spark packet for the actual talk once format confirmed
- [ ] Record voice riff on "what my second brain looks like now" (Phase 1 of spark)
- [ ] Identify BASB AI cohort dates and enrollment window
- [ ] Draft one-page pitch letter to Tiago (email or LinkedIn DM)

---

## Cross-Links

- [[Question Authority]] (Keep note, Feb 2025) — irresistible questions as podcast format
- [[Alongside]] — community concept seeded in BASB Session 5
- [[Spark skill]] — `~/.claude/skills/spark/SKILL.md`
- [[projects-portfolio-context]] — Project #7 (Alongside) + Project #4 (AI talks)
