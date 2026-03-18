---
category: article
type:
  - "#type/article"
tags:
  - ai
  - ai-gtm
  - project-links
source: https://x.com/alixqureshi/status/2025969857041465373
date: 2026-02-25
---
#### Related Core Pages
[[GTM AI Overview]]

#### Summary
- Individual prompts give one-off outputs; connected skills give a pipeline
- Most people use AI for one-off tasks — building a system is the differentiator
- The brain file turns every session from a cold start into a warm conversation
- Version control everything so work compounds instead of resetting

#### Details
- Ali Qureshi runs a $3M creative agency and built a complete marketing operating system inside Claude Code
- The system uses a single `SOUL.md` file (~500 lines) as the "brain" that tells Claude Code what tools exist, what skills are available, which brand is active, and how to route requests
- Architecture pattern: Brain (SOUL.md) → Skills (execution) → Tools (data) → Brands (context) → Agents (coordination)
- **Skills layer**: 14 skill files for repeated tasks (copywriting, creative strategy, content planning, email sequences, copy review). Each skill includes frameworks, voice markers, anti-patterns, and real examples
- **Tools layer**: MCP servers connecting to external data (YouTube Research for transcripts, YouTube Outlier for performance tracking, Thumbnail Generator, Reddit RSS Monitor)
- **Brand system**: Each brand gets its own directory with voice profile, positioning, audience, assets, and learnings files. Context matrix controls which files each skill loads
- **Agents layer**: Four specialist personas (strategist, copywriter, researcher, orchestrator) that share memory files persisting across sessions
- Key insight: Skills talk to each other — creative strategy produces structured briefs that copywriting consumes as input. Output of one skill feeds directly into the next
- System gets sharper over time through feedback logging — corrections become rules for future use
- Recommendation for starting: Create SOUL.md file first, then build one skill file for your most repeated task, then create one brand directory with voice, positioning, and audience files

