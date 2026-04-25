---
title: "Proposal — Granularity Levels of Knowledge"
created: 2026-04-24
status: draft
tags: [architecture, knowledge-management, BASB, DaveVault3, granularity]
---

# Granularity Levels of Knowledge

## The Question

What is the smallest granular unit of an idea? And how does it stack upward through 3-5 levels to become an intermediate packet?

---

## Proposed Five Levels

### Level 0: THE SPARK (Atomic Claim)

**Size:** 1-3 sentences. A single assertion, insight, or observation.
**Token budget:** ~50-150 tokens
**What it is:** The irreducible unit of meaning. One idea that cannot be split further without losing its sense. It stands alone. It needs no preamble.

**Examples from Dave's corpus:**
- "I am the bottleneck until I put that capability out into the 2nd brain."
- "The quality of what you receive from AI will never exceed the depth of what you reveal to it."
- "A modern piece of work isn't created, it's assembled."
- "Fear dissolves every time I face it. But it regenerates."

**Properties:**
- Has a single subject and a single claim
- Can be true or false (testable)
- Has provenance (who said it, when, where)
- Has resonance (why it matters to you)
- May have a source tag: `mine` | `captured` | `derived`

**Analogs:**
- Zettelkasten: the atomic note
- Homunculus/ECC: the instinct
- MemPalace: the drawer
- Readwise: the highlight
- Tiago: the captured note (pre-distillation)

**Format:**
```yaml
type: spark
claim: "The bottleneck is always the human, not the system."
source: BASB Session 5 with Tiago (2021-06-02)
origin: captured  # mine | captured | derived
resonance: "This hit because I was living it — 847 notes and I was the blocker."
tags: [bottleneck, second-brain, agency]
confidence: 0.9
created: 2021-06-02
```

---

### Level 1: THE CLUSTER (Linked Sparks)

**Size:** 3-7 sparks that orbit the same idea. A handful of atomic claims that belong together.
**Token budget:** ~300-800 tokens
**What it is:** A gravity well. When sparks start repeating or rhyming across sources, they cluster. Not yet an argument — just a pattern.

**Examples from Dave's corpus:**
- Cluster: "The Bottleneck Problem"
  - "I am the bottleneck" (Tiago, Session 5)
  - "847 notes, no gardener" (Dave, 2022 Keep note)
  - "Mathias had 4,000 notes and the same problem" (Dave, 2025)
  - "The self never arrived" (Readwise highlight)
  - "How do you schedule maintenance time?" (Dave's cohort question, 2021)

**Properties:**
- Has a working title (can change)
- Contains 3-7 sparks with explicit links
- Shows a pattern but doesn't yet make an argument
- May span multiple sources and years
- Has tension — the sparks don't all agree

**Analogs:**
- Zettelkasten: a sequence / note thread
- MemPalace: a room query result
- Tiago: the bold + highlight layer of progressive summarization
- AI context: a retrieval chunk

---

### Level 2: THE THREAD (Narrative Arc)

**Size:** 1-3 paragraphs. A cluster given direction — beginning, middle, implication.
**Token budget:** ~500-2,000 tokens
**What it is:** The cluster gets a spine. You arrange the sparks into a sequence that makes an argument or tells a micro-story. This is where YOUR perspective appears. The sparks were raw material; the thread is distillation.

**Examples from Dave's corpus:**
- Thread: "How the Stirring-the-Soup Problem Got Solved"
  - Spark: Tiago's gardening concept
  - Spark: Dave's 847-note overwhelm
  - Spark: Three years of knowing better
  - Spark: Chroma vector index makes it searchable by meaning
  - **Perspective:** "The self never arrived — until I built one."

**Properties:**
- Has a thesis or narrative direction
- Arranges sparks in intentional order
- Contains Dave's voice (not just captured material)
- Can be spoken aloud in 60-90 seconds
- Is a TEACHING unit — could be a slide, a paragraph, a social post

**Analogs:**
- Tiago: the takeaway summary (level 5 of progressive summarization)
- Writing: the paragraph
- Speaking: the point
- Alpheus persona: a section of best-expression-index.md

---

### Level 3: THE PACKET (Intermediate Packet)

**Size:** 1-3 pages. Multiple threads woven into a self-contained deliverable.
**Token budget:** ~2,000-8,000 tokens
**What it is:** Tiago's intermediate packet. A module of completed thinking that can be reused, shared, dropped into a larger work. Has enough context to stand alone but is designed to compose with others.

**Examples from Dave's corpus:**
- Packet: "Act 2 — The Gap (2022-2025)" from the documentary script
- Packet: "The Irresistible Question" draft for Tiago
- Packet: "Alpheus Architecture Overview" — how the 3-layer context system works
- Packet: "10 BASB Pain Points with Evidence"

**Properties:**
- Has title, intro, body, conclusion
- Self-contained — makes sense without surrounding material
- Reusable — could appear in a talk, article, email, or deck
- Has clear audience (even if implicit)
- Represents 80%+ of the thinking done; only formatting/polish remains

**Analogs:**
- Tiago: the intermediate packet (explicitly)
- Journalism: the section or chapter
- Software: the module
- Speaking: the 3-5 minute segment
- Alpheus: a voice exemplar file

---

### Level 4: THE WORK (Published Artifact)

**Size:** 5-50 pages. Multiple packets assembled into a finished, audience-facing artifact.
**Token budget:** ~10,000-100,000 tokens
**What it is:** The thing you ship. A talk, an article, a documentary script, a course module, a book chapter. Assembled from packets, not written from scratch. This is what Tiago means by "assembled, not created."

**Examples from Dave's corpus:**
- Work: The full BASB Mini Documentary script
- Work: The Tiago pitch letter (when written)
- Work: "Are You Willing to Be Known?" essay
- Work: The Mystic Companion Workshop (8 modules)

**Properties:**
- Has a defined audience and purpose
- Assembled from packets (not written top-down)
- Has been through at least one feedback cycle
- Could be published / performed / shared as-is
- Generates derivative sparks (audience reactions become new sparks)

---

## The Stack Visualized

```
Level 4:  THE WORK          (ship it)
             ▲
Level 3:  THE PACKET         (reuse it)
             ▲
Level 2:  THE THREAD          (teach it)
             ▲
Level 1:  THE CLUSTER          (see it)
             ▲
Level 0:  THE SPARK             (capture it)
```

Each level is roughly 5-10x the token budget of the one below it.

---

## How This Maps to Concentric Context Rings (DaveVault3)

For the concentric-circle context architecture at different token budgets:

| Token Budget | What Fits | Content |
|-------------|-----------|---------|
| **10K** | 50-100 sparks | Core identity sparks + top 3 threads. "Who am I and what do I believe?" |
| **50K** | 25-30 threads | Full thematic portrait. All major threads + key clusters. Enough to have a real conversation. |
| **200K** | 20-30 packets | Complete working context. All intermediate packets + supporting threads. Enough to create. |
| **1M** | The corpus | Everything. All sparks, clusters, threads, packets, works, plus raw captures still awaiting distillation. |

The rings:
- **Inner ring (10K):** Essence. The sparks that define you. MemPalace: `persona` wing.
- **Second ring (50K):** Understanding. The threads that explain your thinking. MemPalace: `persona` + `alpheus` wings.
- **Third ring (200K):** Capability. The packets you can work with. MemPalace: + `output` + `planning` wings.
- **Outer ring (1M):** Memory. Everything you've captured. MemPalace: all wings.

---

## How This Connects to BASB CODE Framework

```
Capture  →  Level 0 (Spark)     — raw capture with provenance
Organize →  Level 1 (Cluster)   — sparks find their neighbors
Distill  →  Level 2 (Thread)    — your perspective appears
Express  →  Level 3-4 (Packet/Work) — reusable and shippable
```

**The distillation gap is the jump from Level 1 to Level 2.**

That's where most BASB practitioners get stuck. They have sparks (captures) and they can see clusters (tags, folders), but they never write the thread — the paragraph where their own voice arranges the sparks into meaning.

AI's role: help you see clusters you can't see (vector similarity), then draft threads you can refine. The human's role: choose which clusters matter and whether the thread is honest.

---

## Open Questions

- Should sparks have a confidence score (like instincts in Homunculus)?
- Should clusters be auto-generated by vector similarity, or manually curated?
- Is there a Level -1 below spark? (A raw fragment — a word, a feeling, a bookmark with no annotation?)
- How do sparks decay? If not referenced in 2 years, do they lose confidence?
- Should the DaveVault3 format enforce this structure, or allow organic emergence?

---

## Next Steps

1. Define the spark format as a YAML/markdown template
2. Extract 20-30 sparks from existing corpus to test the format
3. Map existing MemPalace drawers to spark/cluster/thread levels
4. Build the concentric ring context loader for DaveVault3
5. Test: can a 10K context ring produce a coherent conversation about Dave's BASB journey?
