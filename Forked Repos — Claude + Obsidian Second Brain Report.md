---
title: "Forked Repos — Claude + Obsidian Second Brain Report"
created: 2026-04-24
status: complete
tags: [research, repos, second-brain, Claude, Obsidian, architecture]
---

# Forked Repos — Claude + Obsidian Second Brain Report

Five repos Dave forked from GitHub, each taking a different approach to the same problem: how do you give an AI agent persistent, structured memory using an Obsidian vault?

---

## 1. obsidian-mind (breferrari)

**"Vault-first memory for software engineers"**

### Approach
Gives AI coding agents persistent memory via an Obsidian vault. All durable knowledge lives in git-tracked markdown — Claude's MEMORY.md is just a thin pointer index. Built for software engineer performance tracking: brag docs, 1:1s, incidents, review cycles.

### Architecture
- **Vault-first**: agent memory is pointer-only; real content in `brain/`, `work/`, `org/`, `perf/`
- **Progressive disclosure**: ~2K tokens injected at session start (North Star excerpt, git log, open tasks). Full content via QMD semantic search on demand.
- **Hook pipeline**: 5 lifecycle hooks in TypeScript with 400+ unit tests. UserPromptSubmit classifies every message with multilingual regex patterns (EN/JA/KO/ZH).
- **vault-manifest.json** as single coordination point for hooks, MCP, CLI, and upgrades.
- **Multi-agent portable**: same hooks serve Claude Code, Codex CLI, and Gemini CLI.

### Skills & Commands
- **18 slash commands**: standup, dump, wrap-up, humanize, weekly, capture-1on1, incident-capture, slack-scan, peer-scan, review-brief, self-review, review-peer, vault-audit, vault-upgrade, prep-1on1, meeting, intake, project-archive
- **9 subagents**: brag-spotter, context-loader, cross-linker, people-profiler, review-prep, slack-archaeologist, vault-librarian, review-fact-checker, vault-migrator
- **6 skills**: obsidian-markdown, obsidian-cli, obsidian-bases, json-canvas, defuddle, qmd
- **QMD MCP server** for semantic search (query, get, multi_get, status)

### Context Tiering
**Best in class.** Explicit 5-tier system:
| Tier | Cost | What |
|------|------|------|
| T0 | ~6K | CLAUDE.md (always) |
| T1 | ~2K | SessionStart injection (North Star, git log, tasks) |
| T2 | ~100 | Per-message classification hints |
| T3 | Variable | QMD semantic search on demand |
| T4 | ~200 | Post-write validation warnings |

### Perspectives
- **Strength**: Most engineered hook pipeline of any repo. Progressive disclosure is genuinely token-efficient. Multi-agent portability is real.
- **Weakness**: Extremely opinionated for software engineer domain. Reusing for personal knowledge management requires gutting ~40% of structure. 23KB CLAUDE.md is heavy.
- **Novel**: UserPromptSubmit classification hook with compiled multilingual regex. PreCompact transcript backup. Vault-migrator with tiered heuristics.

---

## 2. claude-obsidian (AgriciDaniel)

**"Karpathy's LLM Wiki pattern — knowledge compounds like interest"**

### Approach
Based on Andrej Karpathy's gist: instead of ephemeral RAG lookups against a vector store, the LLM builds a persistent, structured wiki. Cross-references are pre-built, contradictions are pre-flagged, and synthesis reflects everything ever ingested. The wiki IS the product; chat is the interface.

### Architecture
- **Three layers**: `.raw/` (immutable sources), `wiki/` (LLM-generated knowledge), schema files
- **Hot cache pattern**: `wiki/hot.md` (~500 tokens) overwritten after every operation. Loaded at SessionStart, re-loaded after context compaction via PostCompact hook.
- **Master index**: `wiki/index.md` (~1000 tokens) catalogs all pages with one-line descriptions
- **Domain sub-indexes**: `wiki/<domain>/_index.md` for focused lookups
- **PostToolUse hook** auto-commits every Write/Edit to git
- **DragonScale** (opt-in): deterministic page addresses, semantic tiling via local embeddings, boundary-first autoresearch, fold operator for log compression

### Skills & Commands
- **11 skills**: wiki, wiki-ingest, wiki-query, wiki-lint, wiki-fold, save, autoresearch, canvas, defuddle, obsidian-bases, obsidian-markdown
- **4 slash commands**: /wiki (scaffold), /save (conversation to wiki), /autoresearch (autonomous research loop), /canvas (visual)
- **2 agents**: wiki-ingest (parallel batch worker), wiki-lint (vault health scan)
- **4 hooks**: SessionStart (load hot cache), PostCompact (re-read hot cache), PostToolUse (git auto-commit), Stop (update hot cache)
- **6 wiki modes**: Website, GitHub, Business, Personal, Research, Book/Course

### Context Tiering
**Excellent — explicit token costs documented:**
| Tier | Cost | What |
|------|------|------|
| Hot cache | ~500 | wiki/hot.md — persistent session cache |
| Master index | ~1000 | wiki/index.md — page catalog |
| Sub-indexes | 100-300 each | Domain-specific indexes |
| Pages | 100-300 each | Max 3-5 per query (hard rule: never 10+) |

### Perspectives
- **Strength**: The hot cache pattern is elegant — solves cold-start across sessions without conversation history. Cross-project composability (any Claude Code project can read the wiki). Token costs explicitly documented.
- **Weakness**: Context budget grows unbounded as wiki grows. Single-writer constraint limits batch ingestion throughput. No adaptive budget based on remaining context.
- **Novel**: DragonScale boundary-first autoresearch uses graph structure to suggest frontier topics. Fold operator for log compression. Six wiki modes with mode-specific schemas.

---

## 3. claudesidian (heyitsnoah)

**"PARA-organized thinking partner — Claude Code for knowledge work, not just code"**

### Approach
Uses Claude Code as a knowledge work engine, not just a coding tool. Vault follows PARA (Projects/Areas/Resources/Archive). Skills are behavior modules loaded on demand. The key innovation is applying the Claude Code agent paradigm to thinking, writing, organizing, and researching — not code.

### Architecture
- **PARA folders**: 00_Inbox, 01_Projects, 02_Areas, 03_Resources, 04_Archive, 05_Attachments, 06_Metadata
- **Agent-agnostic skills**: canonical in `.agents/skills/` with symlinks to `.claude/skills/` and `.pi/skills/`
- **CLAUDE.md is gitignored**: generated per-user via init-bootstrap wizard. Template ships; instance doesn't.
- **FIRST_RUN sentinel**: triggers setup wizard on first session
- **Gemini Vision MCP server**: 7 tools for image/video/document analysis via local Gemini

### Skills & Commands
- **20 skills**: thinking-partner, daily-review, weekly-synthesis, research-assistant, inbox-processor, add-frontmatter, de-ai-ify, download-attachment, obsidian-markdown, json-canvas, obsidian-bases, pragmatic-review, systematic-debugging, git-worktrees, pull-request, release, upgrade, init-bootstrap, install-claudesidian-command, skill-creator
- **7 MCP tools** (Gemini Vision): analyze_image, analyze_multiple, extract_text, compare_images, suggest_image_filename, analyze_video, analyze_document
- **2 hooks**: SessionStart (first-run detection + update check), UserPromptSubmit (skill discovery on keyword "skill")

### Context Tiering
**Minimal.** Skills load on demand (binary: loaded or not). No progressive disclosure, no token budgeting, no compression. The init-bootstrap skill alone is ~30KB. If multiple skills load in one session, they stack additively with no management.

### Perspectives
- **Strength**: Cleanest PARA implementation. Agent-agnostic skill format is future-proof. The de-ai-ify skill (remove AI voice patterns) is culturally sharp. Skill-creator includes an eval harness for iterative improvement.
- **Weakness**: No tiered context loading. Skill discovery only fires on literal word "skill" in prompt. No vector search or embeddings. Single MCP server (vision only).
- **Novel**: Using Claude Code for knowledge work, not just coding. De-ai-ify skill. Skill-creator with eval harness.

---

## 4. My-Brain-Is-Full-Crew (gnekt)

**"PhD whose memory was failing — chat is the only interface, human never touches the vault"**

### Approach
Built for overwhelmed people with cognitive overload. The core principle: the human NEVER touches the Obsidian vault manually. You just talk. A dispatcher routes to 8 specialized agents who handle all vault operations. "Crew" = coordinated multi-agent system with automatic chaining.

### Architecture
- **Dispatcher-first**: DISPATCHER.md is the system prompt (~22KB), routes to skills first, then agents
- **Agent chaining**: agents output `### Suggested next agent` sections; dispatcher orchestrates (max depth 3)
- **Cross-platform build**: source files use neutral placeholders, compiled to Claude Code / Gemini CLI / OpenCode / Codex CLI at install time
- **PARA + Zettelkasten hybrid**: 00-Inbox through 04-Archive plus 05-People, 06-Meetings, 07-Daily, MOC, Meta
- **"Post-it" state**: skills write state to `Meta/states/` for multi-turn resume
- **Agent self-extension**: `/create-agent` runs a 6-phase interview, generates agent file, updates registry

### Skills & Commands
- **14 skills**: /onboarding, /create-agent, /manage-agent, /defrag, /email-triage, /meeting-prep, /weekly-agenda, /deadline-radar, /transcribe, /vault-audit, /deep-clean, /tag-garden, /inbox-triage, /contact-sync
- **8 agents**: architect, scribe, sorter, seeker, connector, librarian, transcriber, postman
- **15 orchestra scripts** (permission-free bash): Hey.com email, tracker, contact lookup, vault stats
- **3 hooks**: protect-system-files (PreToolUse), validate-frontmatter (PostToolUse), notify
- **MCP servers**: Gmail, Google Calendar, Apple Contacts

### Context Tiering
**None.** The full dispatcher (~22KB) loads every message. 7-language trigger tables load even if you only speak one language. No lite mode, no progressive loading, no compression.

### Perspectives
- **Strength**: Dispatcher routing is well-designed (skills first, agents second). Agent chaining with max-depth-3 and no-duplicate rules prevents runaway loops. Agent self-creation is genuinely novel. Cross-platform compilation from single source.
- **Weakness**: 22KB dispatcher on every message is expensive. "Holistic" promise (knowledge + nutrition + mental health) is aspirational — no specialized health agents exist. No vector search at all.
- **Novel**: Agent self-extension at runtime. Cross-platform prompt compilation. "Post-it" state persistence for multi-turn skills.

---

## 5. mempalace (MemPalace)

**"Highest-scoring AI memory system ever benchmarked — verbatim always"**

### Approach
The anti-extraction philosophy: never summarize, never paraphrase, never lossy-compress. Store every word exactly as written. Search with hybrid BM25 + vector similarity. Created by Milla Jovovich for her AI partner "Lumi." 96.6% R@5 on LongMemEval with zero API calls.

### Architecture
- **Palace metaphor**: Palace → Wing → Room → Drawer (verbatim chunk) → Closet (AAAK compressed index)
- **AAAK compression**: lossy format for indexing (NOT storage) — entities, topics, key quotes, emotions, flags. Any LLM can read it natively.
- **Knowledge graph**: temporal entity-relationship graph in SQLite with valid_from/valid_to windows
- **Hybrid search**: vector similarity (0.6 weight) + BM25 keyword (0.4 weight) + optional LLM rerank
- **Cross-wing tunnels**: lateral connections between wings for serendipitous discovery
- **Local-first, zero API**: all embedding and extraction on your machine. Privacy by architecture.

### Skills & Commands
- **29 MCP tools**: search, add/delete/update drawers, diary read/write, knowledge graph CRUD, tunnel operations, taxonomy, status
- **13+ CLI commands**: init, mine, sweep, search, compress, wake-up, split, status, repair, migrate, mcp, hook, instructions
- **6 Claude Code skills**: search, init, help, status, mine, mempalace
- **Hooks**: stop (diary save), precompact (state save)

### Context Tiering
**Excellent — explicit 4-layer memory stack:**
| Layer | Budget | What |
|-------|--------|------|
| L0 | ~100 tokens | Identity (who am I?) |
| L1 | ~500-800 tokens | Essential story (top 15 drawers by importance) |
| L2 | ~200-500 each | On-demand wing/room retrieval |
| L3 | Unlimited | Deep semantic search |

Wake-up cost: ~600-900 tokens. Leaves 95%+ of context free.

### Perspectives
- **Strength**: Benchmark-proven retrieval quality. Verbatim storage preserves WHY, not just WHAT. Temporal knowledge graph knows WHEN facts are true. Privacy by architecture, not by policy.
- **Weakness**: Storage grows linearly (441GB HNSW bloat for large palaces). L1 generation is naive (importance defaults to 3, so most drawers are equally weighted). No forgetting/eviction strategy.
- **Novel**: Verbatim-only philosophy. AAAK compression as read-by-any-LLM index format. Temporal knowledge graph. Emotional coding in indexes. Cross-wing tunnels.

---

## The Harmonies

### Harmony 1: "The vault IS the memory"
All five repos reject ephemeral agent memory. Knowledge lives in structured, git-tracked markdown files. Claude's built-in memory is a pointer at best. **This is the consensus position.**

### Harmony 2: "Start with identity, load details on demand"
Three of five repos (obsidian-mind, mempalace, claude-obsidian) have explicit tiered context loading:
- **obsidian-mind**: North Star excerpt → QMD search
- **mempalace**: L0 identity → L1 essential story → L2 on-demand → L3 deep search
- **claude-obsidian**: hot cache → master index → sub-index → individual pages

**The pattern**: ~500-2K tokens always loaded (who am I, what matters now). Everything else on demand. This is the architecture Dave should adopt for DaveVault3.

### Harmony 3: "Hooks do the bookkeeping"
All five use hooks to keep the human out of system maintenance:
- SessionStart for context injection
- PostToolUse for validation/auto-commit
- Stop for cleanup/diary
- PreCompact for state preservation

**The consensus**: zero tokens spent on bookkeeping during conversation. Background always.

### Harmony 4: "Skills as behavior modules"
All five package behaviors as SKILL.md files loaded on demand. The separation is consistent: the vault structure is passive data; skills define what the agent DOES with it.

### Harmony 5: "PARA or PARA-adjacent"
Four of five use PARA or a variant. The exception is claude-obsidian (wiki structure). But even the wiki approach has the same intent: separate inputs from outputs, active from archived.

### Harmony 6: "Agent-agnostic aspiration"
Three repos (obsidian-mind, claudesidian, My-Brain-Is-Full-Crew) explicitly support multiple AI agents. The skill format is converging toward a portable standard.

### Harmony 7: "The human curates, the AI maintains"
All five separate human judgment (what matters, what's true, what resonates) from AI labor (filing, linking, searching, indexing). The human is the curator; the AI is the librarian.

---

## Dissonances (Where They Disagree)

| Question | obsidian-mind | claude-obsidian | claudesidian | My-Brain-Is-Full-Crew | mempalace |
|----------|--------------|-----------------|--------------|----------------------|-----------|
| Should AI summarize? | No — excerpts + pointers | Yes — AI writes wiki pages | No — human voice preserved | Yes — scribe refines | **Never** — verbatim only |
| Should the human touch the vault? | Yes, it's their vault | Yes, wiki is human-readable | Mostly no, AI organizes | **Never** | N/A (not a vault) |
| Domain-specific or general? | Eng performance | General knowledge | General knowledge | General knowledge | General memory |
| Vector search? | QMD (external) | No (wiki structure replaces it) | No | No | ChromaDB (built-in) |
| How to handle scale? | Progressive disclosure | Hot cache + index tiers | No strategy | No strategy | Hybrid BM25 + vector |

---

## Recommendation for DaveVault3

**Take the best from each:**

| From | Take |
|------|------|
| **mempalace** | L0-L3 concentric context rings with explicit token budgets. Verbatim storage philosophy. Temporal knowledge graph. AAAK as compact index format. |
| **obsidian-mind** | Hook pipeline architecture (SessionStart, UserPromptSubmit, PostToolUse, PreCompact, Stop). vault-manifest.json as coordination point. QMD-style semantic search. |
| **claude-obsidian** | Hot cache pattern for cross-session continuity. Wiki index as navigational layer. Auto-commit on every write. |
| **claudesidian** | PARA folder structure. Agent-agnostic skill format. De-ai-ify as a standard skill. |
| **My-Brain-Is-Full-Crew** | Dispatcher routing (skills first, agents second). Agent self-creation. Cross-platform compilation. |

**The concentric circle architecture (Dave's original vision):**

```
Ring 0 (10K):   Identity + Spark essence        ← mempalace L0+L1
Ring 1 (50K):   Threads + active context         ← obsidian-mind progressive disclosure  
Ring 2 (200K):  Packets + working knowledge      ← claude-obsidian wiki layer
Ring 3 (1M):    Full corpus + raw captures       ← mempalace L3 deep search
```

Each ring harmonizes with the one inside it. Self before team. Team before community. The innermost ring is who you are. The outermost ring is everything you've ever captured.
