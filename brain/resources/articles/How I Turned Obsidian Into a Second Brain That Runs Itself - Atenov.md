---
captured: 2026-03-14
source_url: https://x.com/Atenov_D/article/2032528386745315553
category: article
author: Atenov
source: x.com
type: x-article
---

# How I Turned Obsidian Into a Second Brain That Runs Itself

## Summary

Atenov shares a simple but powerful setup: combining AI agents with Obsidian by having them share the same folder. The result is a self-organizing knowledge system where agents read, update, and organize notes automatically.

## The Core Insight

**Most people use AI agents in one window and notes in another.** Copy-paste. Switch tabs. Lose context. Start over.

**The fix:** One folder. Both systems look at the same files.

## The Setup (20 Minutes)

### 1. One Folder to Rule Them All
- Create a folder (Workspace, Brain, whatever)
- Open AI agent terminal inside it
- Point Obsidian at that same folder (not a new vault)
- Result: Both systems see the same files instantly

### 2. Terminal Inside Obsidian
- Install Terminal plugin (Community Plugins)
- Open in integrated mode
- Agent lives as a tab inside your notes
- Same window, same context, zero friction

### 3. AGENTS.md — The Context File
Create AGENTS.md in root with:
- Who the agent is
- What it's supposed to do
- How to handle files
- What format to use

**Rule:** Store everything as Markdown. Cleanest format for LLMs. No conversion errors.

## What Becomes Possible

### Your Notes Become a Searchable Database
- Dump working materials (news, research, meeting notes)
- Ask agent: "What's the most recent update on X?"
- Agent scans directories, opens files, answers from your data

### The Graph That Thinks
- Enable Command line in Obsidian settings
- Agent gets direct access to Obsidian functions
- Ask it to read a note and find everything connected
- Follows backlinks, synthesizes across knowledge base

### The Kanban Board That Fills Itself
- Install Kanban plugin
- Paste messy text dump
- Tell agent to distribute across board
- Give it a strict card template for consistency

## The Shift

You stop:
- Opening apps manually
- Creating files manually
- Navigating folders

You just talk to the terminal:
- "Brainstorm angles and save as new note"
- "Find everything about X and summarize"
- "Turn this thread into a project board"

Agent generates, creates .md file, opens in Obsidian automatically.

## Three Mistakes That Break This

1. **No AGENTS.md** — Agent has no context, starts from scratch every session
2. **Non-Markdown formats** — PDFs, .docx work but Markdown is cleaner
3. **Agent and notes in different folders** — 90% of people do this. Two separate systems pretending to cooperate.

## Key Quote

> "Your notes are already there. Your agent is already there. The only thing missing was the folder they share."

## Related

- [Obsidian](https://obsidian.md)
- [Atenov on Twitter](https://x.com/Atenov_D)
