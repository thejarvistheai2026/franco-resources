---
category: article
type:
  - "#type/article"
tags:
  - ai
  - openclaw
  - project-links
source: https://x.com/code_rams/status/2025630269559185648
date: 2026-02-25
---

#### Key Takeaways
- Discipline > more files. Unused skills and bloated files are silent token killers.
- Memory is a storage + retrieval problem. Most setups only solve storage.
- Model switches wipe context completely without a handover protocol.
- `/context detail` is essential for finding overhead.
- The fix was removing bloat, not adding more infrastructure.

#### Summary
Ramya spent 5 days debugging her OpenClaw agent "Chiti" (handles customer support, drafts tweets, manages invoices) that kept forgetting context. Detailed breakdown of problems found and solutions implemented.

#### Day 1: Compaction Loss
- **Problem:** Long conversations lost earlier context due to compression (compaction) when context window fills up. Summaries capture gist but drop specifics (names, numbers, exact decisions)
- **Solution:** Enable memory flush before compaction (`memoryFlush.enabled: true` with `softThresholdTokens: 4000`). Agent writes durable facts to daily log before compression runs
- **Key insight:** Compaction isn't the enemy — unwritten context is. If it's only in the context window, it's temporary. If it's on disk, it survives.

#### Day 2: Search Backend Issues
- **Problem:** Built-in SQLite semantic search missed exact matches (client names, specific numbers, exact phrases)
- **Solution:** Switched to QMD backend — combines BM25 (keyword) + vector embeddings + reranker
- **Configured paths:** memory-root (MEMORY.md), memory-alt, memory-dir, learnings folder
- **Key insight:** Pure semantic search fails on proper nouns. Hybrid search (keywords + vectors + reranking) is significantly better.

#### Day 3: Retrieval Habits
- **Problem:** Information existed but agent wouldn't retrieve it — retrieval isn't automatic, agent must decide to search
- **Solution:** Added explicit retrieval instructions to boot sequence (search daily logs, check MEMORY.md, search client history)
- **Built retrieval test:** Plant marker in daily log, start new session, test if agent finds it
- **Key insight:** "Information exists" ≠ "agent uses information." Test both storage AND retrieval.

#### Day 4: Long Session Problems
- **Problem:** Memory flush only triggers once per compaction. Multi-compaction sessions lost subsequent context.
- **Solution:** Configured context pruning alongside compaction (cache-ttl mode, 6h TTL, keep last 3 assistant responses)
- **Added MARKER test protocol:** After config changes, plant marker and test retrieval across compaction boundaries
- **Key insight:** Long sessions are where memory systems get tested. Short conversations rarely hit compaction.

#### Day 5: The Big Cleanup
- **Root causes discovered:**
  - 11,887 tokens of system prompt (!) — 51 skills, never used 20 of them
  - 200 lines of company wiki loaded every session
  - Two competing boot sequences in files OpenClaw doesn't auto-read
  - Model switches = total context loss (no handover protocol)

- **Files that auto-load:** MEMORY.md, SOUL.md, USER.md, AGENTS.md, HEARTBEAT.md, CURIOSITY.md, SOP-WORKFLOW.md
- Everything else needs explicit read instruction in AGENTS.md

- **Cleanup results:**
  - System prompt: 11,887 → 8,529 tokens
  - Skills: 51 → 32
  - Session tokens: 18,280 → 14,627
  - 28% lighter, same agent

#### 10 Rules for OpenClaw Memory

1. **Only 7 files auto-load** — everything else needs explicit read in AGENTS.md
2. **Boot sequence at TOP of AGENTS.md** — first thing processed
3. **Write discipline > read discipline** — log decisions/outcomes/mistakes to disk
4. **Never write directly to MEMORY.md during tasks** — curate during periodic reviews only
5. **LEARNINGS.md is underrated** — every mistake becomes a one-line rule
6. **Test retrieval, not just storage** — plant markers, test across sessions
7. **Handover protocol for model switches** — dump current state before switch
8. **Run /context detail regularly** — find token waste
9. **Hybrid search beats pure semantic** — BM25 + vectors + reranking
10. **Compaction isn't the enemy** — unwritten context is

#### Final Workspace Structure
```
workspace/
├── AGENTS.md (boot + write discipline + handover)
├── SOUL.md (personality)
├── USER.md (owner info)
├── CURIOSITY.md (tool usage)
├── HEARTBEAT.md (check-in behavior)
├── MEMORY.md (~90 lines, curated)
├── PROTOCOL_COST_EFFICIENCY.md
├── learnings/LEARNINGS.md (rules from mistakes)
├── memory/ (daily logs: YYYY-MM-DD.md)
├── docs/ (reference docs)
└── skills/ (32 skills, down from 51)
```

**Final stats:** System prompt: 8,529 tokens. Session: 14,627/200,000 (7.3%).


