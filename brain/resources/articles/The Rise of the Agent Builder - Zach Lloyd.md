---
captured: 2026-03-14
source_url: https://x.com/zachlloydtweets/status/2029223875066687683
category: article
author: Zach Lloyd
source: x.com
type: x-article
---

## Summary

Zach Lloyd (Founder of Warp) introduces the concept of the "Agent Builder" — a full-time role dedicated to systematically replacing SaaS tools and manual workflows with AI agents. He shares real examples from Warp where they've already automated fraud detection, competitive intelligence, and enterprise POC summaries using their cloud agent platform "Oz."

## Key Thesis/Insights

- **Agent Builder**: A new full-time role for companies to systematically replace SaaS and manual workflows with agents
- **Prediction**: Within a year, every company over 50 people will have at least one Agent Builder
- **SaaS replacement is happening**: Warp is canceling SaaS subscriptions in favor of rolling their own agents
- **Old mandate**: "Start with a prompt" → **New mandate**: "See if the task can be automated by building an agent"
- **Agents can self-improve**: Future where agents look at past runs and change their own definitions

## Main Content Breakdown

### What is an Agent Builder?

A full-time role dedicated to:
- Replacing SaaS tools with custom agents
- Automating manual workflows
- Using cloud agent platforms (Warp uses "Oz")

**Warp's first Agent Builders:**
- **Emily**: Started building agents for Growth team automation
- **Dave**: Building agents for product intelligence

### Already Automated at Warp

1. **Fraud Detection**
   - Agent constantly looks for suspicious usage patterns
   - Creates PRs to block users
   - Identifies novel fraud patterns
   - **Impact**: Saving tens of thousands of dollars every day

2. **Competitive Intelligence**
   - Monitors competitor launches
   - Compares to Warp's launches
   - Posts weekly market summaries to Slack
   - **Impact**: Replaced what used to take product team half a day each week

3. **Enterprise POC Summaries**
   - Summarizes how individual enterprise pilots are performing
   - Notifies when Sales Engineer should step in
   - **Impact**: Helps ensure pilot success

### Why Coding Agents Make Great General Purpose Agents

Warp's platform "Oz" is built around coding agents, but it turns out:
- A great coding agent makes a great general purpose agent
- Don't need predefined "if this, then that" workflows
- Agent can use intelligence to decide the right workflow instantly

### Building Internal Agents: Challenges

- Up-front environment setup
- Data access grants
- Monitoring
- Prompt tuning (best served by dogfooding early, forgiving kinks, turning feedback into improvements)

### New Primitives for Agent Platforms

Warp is discovering new primitives for their Oz platform:
- **Orchestration** (early demo shared)
- High-quality auditing, steering, and tracking mechanisms
- Tooling to improve agents over time

### The Self-Improving Agent Future

> "It sounds like science fiction, but it's not – agents can look at their past runs, see what could be improved, and change their own definitions."

### Key Discussion Points

**On governance and security:**
- Working on baking identity into agents
- Granting permissions similar to employees
- Using Oz to extend primitives

**On change management:**
- Biggest bottleneck isn't building agents — it's getting teams to trust them enough to retire SaaS tools
- Need approach that bakes evals/verification in from the start

**On developers as early adopters:**
- Developers are first persona to adopt agents at scale
- Most devs have their own "agent" running on laptop
- Many using something out-of-the-box, some building custom (OpenHands SDK)

**On auditing and tracking:**
- Critical because agents don't throw errors when they fail
- Fraud detection agent flagging legitimate users won't crash
- Competitive intelligence agent missing a launch won't error
- They complete, look fine in logs, but output is wrong

## Stats Table

| Metric | Value |
|--------|-------|
| Replies | 15 |
| Reposts | 92 |
| Likes | 640 |
| Bookmarks | 1,765 |
| Views | 401,627 |
| Date | Mar 4, 2026 |

## Key Quotes

> "For companies to pull ahead this next year, they need to systematically replace SaaS tools and manual workflows with agents, and dedicate a full-time role to do exactly that. We call this the Agent Builder."

> "We weren't sure about this at first since Oz is built around coding agents… but it turns out that a great coding agent makes a great general purpose agent."

> "We've already automated: Fraud detection: an agent that constantly looks for suspicious usage patterns and creates PRs to block users (and also identifies novel fraud patterns). This is saving us tens of thousands of dollars every day."

> "Our old internal mandate was 'start with a prompt' to get help with a task. Now, the mandate is to see if the task can be automated on an ongoing basis by building an agent."

> "An agent, given the right capabilities and skills, can use intelligence to decide on the right workflow instantly. You don't need to predefine a series of 'if this, then that' steps."

> "It sounds like science fiction, but it's not – agents can look at their past runs, see what could be improved, and change their own definitions."

> "My prediction: within a year, every company over 50 people will have at least one person whose full-time job is building internal agents."

## Full Thread

<details>
<summary>Click to expand full thread content</summary>

**Zach Lloyd @zachlloydtweets (Mar 4, 2026):**

The rise of the Agent Builder

For companies to pull ahead this next year, they need to systematically replace SaaS tools and manual workflows with agents, and dedicate a full-time role to do exactly that. We call this the Agent Builder.

Our first Agent Builders are Emily, who started off building agents to automate work on the Growth team, and Dave, who was building agents for product intelligence. Their mandate is to use our cloud agent platform Oz to automate tasks.

We weren't sure about this at first since Oz is built around coding agents… but it turns out that a great coding agent makes a great general purpose agent.

These agents complete tasks that we might have purchased a SaaS for a few months ago – e.g. social listening and user feedback analysis. Indeed, we are cancelling SaaS subs we had for these tasks in favor of rolling our own agents.

We've already automated:
- Fraud detection: an agent that constantly looks for suspicious usage patterns and creates PRs to block users (and also identifies novel fraud patterns). This is saving us tens of thousands of dollars every day.
- Competitive intelligence: agents that monitor competitor launches, compare them to ours, and post weekly market summaries to Slack — replacing what used to take our product team half a day each week.
- Enterprise POC summaries: summaries of how our individual enterprise pilots are performing, notifying us where we might want to have a Sales Engineer step in and help so that the pilots are successful.

Everywhere we look, we see new use cases for agents. That's why we decided to make building them a full-time job.

Our old internal mandate was "start with a prompt" to get help with a task. Now, the mandate is to see if the task can be automated on an ongoing basis by building an agent.

Building these internal agents presents a bunch of challenges. There's up-front environment setup, data access grants, monitoring, and prompt tuning. That last point is best served by dogfooding with our team early, forgiving the kinks, and turning feedback into prompt improvements.

We are also discovering new primitives for our Oz cloud agent platform to enable these workflows.

Overall, it's never been easier to automate a tedious task without a structured, Zapier-like workflow. An agent, given the right capabilities and skills, can use intelligence to decide on the right workflow instantly. You don't need to predefine a series of "if this, then that" steps.

What you really need is high-quality auditing, steering, and tracking mechanisms to see how these agents perform. You need the tooling to improve them over time.

And in the future, these same primitives will allow agents to start improving themselves. It sounds like science fiction, but it's not – agents can look at their past runs, see what could be improved, and change their own definitions.

It's going to be a wild ride over the next year. To figure out the future, we'll need Agent Builders at every level to make the most of this technology.

My prediction: within a year, every company over 50 people will have at least one person whose full-time job is building internal agents.

---

**kehaya @afkehaya (Mar 5):**
Totally agree that this is going to be true. How are you thinking about policy, governance, and security for agent teams across departments and potentially between companies?

**Zach Lloyd @zachlloydtweets (Mar 5):**
Great question - we are working on baking identity into the agents and granting them permissions in a similar way we might to employees. We are using Oz (our own orchestration product - oz.dev) to extend the primitives here.

---

**Simon @uniqueHan0 (Mar 5):**
The biggest bottleneck isn't building the agents — it's getting teams to trust them enough to actually retire the SaaS tools they replace. This role is really change management in disguise.

**Zach Lloyd @zachlloydtweets (Mar 5):**
yeah, i think we need an approach that bakes evals / verification in from the start

---

**Noah @Noahhh1005 (Mar 5):**
the SaaS replacement angle is the sleeper hit here. half the tools companies pay for are just thin wrappers around "read data, apply rules, post summary somewhere" — exactly what coding agents do well. also interesting your agent builders came from growth/product, not

---

**Scott David Meyer @MrScottMeyer (Mar 5):**
Hard agree. Trying to build chipp to support these agent builders

---

**Robert Brennan @rbren_dev (Mar 4):**
Agreed! It's clear that developers are the first persona to adopt agents at scale--a majority of devs have their own "agent" running on their laptop, though most are using something out-of-the-box I recently built my own custom OpenClaw-esque dev workstation using OpenHands SDK

---

**Utibe Okodi @UBOkodi (Mar 5):**
The "auditing, steering, and tracking" piece is where it gets interesting. A fraud detection agent that starts flagging legitimate users won't throw an error. A competitive intelligence agent that misses a major launch won't crash. They complete, look fine in logs, and the

</details>

## Related

- [Oz: The Orchestration Platform for Cloud Agents](https://oz.dev)
- [Warp](https://warp.dev)
- [OpenHands SDK](https://github.com/All-Hands-AI/OpenHands)
- [Chipp](https://chipp.ai) - mentioned by Scott David Meyer
