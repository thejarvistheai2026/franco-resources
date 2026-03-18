---
captured: 2026-03-14
source_url: https://www.youtube.com/watch?v=qb90PPbAWz4
category: transcript
author: AI Explained (YouTube channel)
source: YouTube
type: video
---

# Karpathy's "autoresearch" broke the internet

## Summary

Andrej Karpathy launched "auto research" — an AI system that runs experiments autonomously on AI models overnight while you sleep. It's being compared to the "Ralph loop" concept where AI does engineering 24/7. The video explains what it is, use cases, how to make money from it, and how to get started.

## What Is Auto Research?

**The concept:** A "super nerd robot intern" that runs science experiments on AI models all night without you doing the boring stuff.

### How It Works

1. **You set the goal:** e.g., "make this small AI model smarter"
2. **AI agent plans:** experiments with different settings and code changes
3. **Edits Python code** for you
4. **Runs training experiment** on GPU (~5 minutes)
5. **Reads results** and decides what to change next
6. **Repeats the loop** overnight

### Mental Model

Think of it as a **research boss you can boss around:**

| Step | Action |
|------|--------|
| 1 | Write clear task (improve model test score, research competitors, etc.) |
| 2 | Give bot access to code, GPU, internet, documents |
| 3 | Bot runs loop: plans → acts → reads results → updates plan |
| 4 | Come back later (6-20 hours) to find logged results, charts, metrics, written summary |

**Core value:** Tries lots of ideas fast and keeps only the winners.

## Key Insights

- **24/7 experimentation:** Like the "Ralph loop" for engineering — wake up to new work done
- **You define "better":** cheaper leads, more clicks, higher sales, better model scores
- **Only saves improvements:** Discards configs that don't work, keeps the winners
- **GPU required:** Needs Nvidia chip or cloud GPU (won't run on MacBook M1)
- **Toby's endorsement:** Shopify CEO posted auto research works great for optimizing any piece of software

## Business Ideas and Use Cases

### 1. Niche Agent-in-a-Box Products

**The play:** Package tiny auto research loops tuned for one painful niche

**Examples:**
- Amazon listing experimenter
- Email sequence tuner for realtors
- SaaS pricing optimizer

**Value prop:** "This thing runs experiments 24/7 and shows you the winner to click accept"

**Model:** Monthly subscription fee

**Workflow:**
1. Pick painful niche
2. Design tiny auto research loop
3. Run experiments automatically
4. See which setup works best
5. Turn best setup into simple agent product
6. Charge monthly subscription

### 2. Print Money with A/B Testing for Marketing

**Landing pages:** Agent writes variants of headlines, layouts, offers → pushes to traffic → measures conversions → keeps iterating

**Ads:** Auto test creatives, angles, audiences → keep combos that lower CAC or raise ROAS

**Monetization:**
- Use internally for your own products
- OR offer as retainer service to clients ($5K/month for "always-on experiment engine")

## Technical Requirements

### What You Need

- **Nvidia GPU chip** OR cloud GPU access
- **auto folder** with specific structure:
  ```
  auto/
  ├── program.md       # Markdown file with goal/spec
  └── bench script     # For measuring results
  ```
- **Git branch** — make a branch and "let it rip"

### The Auto Research Loop

```
Set Goal → Plan Experiment → Edit Code/Settings → Train on GPU (5 min)
    ↑                                              ↓
Plan Next ← Discard/Log ← Read Metrics ← Better Result?
```

## Key Quotes

> "It's like having a super nerd robot intern that runs science experiments on AI models for you all night without you doing the boring stuff."

> "If you've seen my video on the Ralph loop, where it basically would do engineering 24/7 and you'd wake up to new stuff happening, in simplest terms, that's what auto research is helping you."

> "You tell the AI what better means — cheaper leads, more clicks, higher sales, better model school — and then the AI keeps changing things, testing them, and it only saves the changes that improve."

> "Toby, who's the CEO and co-founder of Shopify: 'Auto research works even better for optimizing any piece of software.'"

> "Make an auto folder. Add a program MD that's just a markdown file... and a bench script, make a branch and let it rip."

> "Think of auto research as a research bot that runs experiments for you while you sleep, tries lots of ideas fast, and keeps the winners."

## Full Transcript

<details>
<summary>Click to expand full transcript</summary>

Andre Carpathy, I mean, one of the godfathers of AI, has just launched something called auto research. And auto research is a huge deal, and it's going viral on Twitter. And I just wanted to do an episode where I can explain to you in the clearest way possible what it is, what are the use cases, how to make money from it, how to be more productive with it, how to create impact with it. And by the end of this episode, I'm going to give you a bunch of different ideas, use cases for how to use auto research. I'm going to explain it to you in the most clear way possible and at the end I'm going to tell you how you can actually get started with it. Um, so let's go right into it. 

>> So what is auto research? Well, it's like having a super nerd robot intern that runs science experiments on a AI models for you all night without you doing the boring stuff. I mean, sounds intriguing, right? So how do you actually you know program it or get started with it? Well, the first thing is you got to give it a goal. So you can say something like make this small AI model smarter. That's the goal. And then an AI agent will actually plan what to do like different settings, code changes, edits the Python code for you, runs a short training experiment on a GPU um for about 5 minutes. it reads the results it and then it decides what to change next and to repeats the loop. So, in some ways, you know, if you've seen my video on the Ralph loop, where it basically would do engineering 24/7 and you'd wake up to new stuff happening, in simplest terms, that's what auto research is helping you. You know, it do. You give it a goal, the AI agent does a thing. You know, you tell the AI what better means. uh cheaper leads, more clicks, higher sales, better model school, and then the AI keeps changing things, testing them, and it only saves the changes that improve. So, what's really cool about it is you wake up, you grab the best version, and then hopefully you turn it into something you charge for or, you know, you give it away. I saw this tweet by Toby, who's the uh CEO and co-founder of Shopify. Auto research works even better for optimizing any piece of software. make an auto folder. Add a program MD that's just a markdown file which is really the foundation of what you know how you're going to be using auto research and a bench script make a branch and let it rip. So that's why I started paying attention to auto research right when Andre Carpathy Legend and Toby and and and more people you know started playing with it I'm like okay I got to pay attention. So I created this little visual for for how to think about what auto research is. So you set the goal. Uh the the AI plans an experiment. It edits and trains the code and settings. It runs a short training on a GPU. By the way, this is an important I should I should mention that you need a uh a Nvidia chip to actually run auto research or you can do it in the cloud. I'll talk about this at the end of the episode, but you you know you do need that. You can't just run it on, let's say you have a MacBook M1 or something like that. It reads metrics. It says, is it a better result? If it's if it's not, it's going to log the attempt and it's going to discard the config. If it's yes, it saves it to the config. Um, and then just plans a different experiment and it just, you know, hopefully gets better on your goal, whatever it is. So, um let's uh let's get into um we're going to get into some of the ideas, business ideas around it. But right before that, I just want to say here's a simple mental model for how I'm thinking about uh auto uh auto research. So, imagine you have a research boss you can boss around. Number one, you write, you know, a clear task. So, for code experiments, maybe it's improve this model test score. for business. Figure out the top five competitors for product XYZ and make a short report. Step two is you give the uh you give the bot um you know access to the code, a GPU for ML experiments. You obviously need to give it access to the internet and documents. If you're doing reading task, the bot then runs a loop. So it it plans, it acts meaning it might run code or search, it reads results, it updates the plan and then you just come back later you know uh it could be 12 hours, 20 hours, 6 hours and you see if it's logged everything charts and metrics and then it gives you a written sum summary in normal language. So you know think of auto research as a research bot that runs experiments for you while you sleep tries lots of ideas fast and keeps the winners.

[Transcript continues with business ideas section...]

</details>

## Related

- [Andrej Karpathy on Twitter/X](https://x.com/karpathy)
- [Toby Lutke (Shopify CEO) Tweet](https://x.com/tobi)
- [Nvidia GPUs](https://www.nvidia.com) - Required hardware
- "Ralph Loop" concept - 24/7 AI engineering
