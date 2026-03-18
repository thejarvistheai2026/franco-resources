---
captured: 2026-03-14
source_url: https://x.com/svpino/status/2029952780694352026
category: thread
author: Santiago Valdarrama (@svpino)
context: AI/LLM coding and software development
---

# What I Learned From 10,000 Hours of LLM Coding

## Summary

Santiago Valdarrama (@svpino) shares insights from extensive experience coding with Large Language Models (LLMs). He covers practical patterns for effective AI-assisted development, what works and what doesn't, and how to think about LLMs as coding partners rather than replacements for human judgment.

## Core Thesis

LLMs are incredibly capable coding assistants, but using them effectively requires understanding their limitations and strengths. The best developers treat LLMs as amplifiers of their own expertise, not replacements for it.

## Key Insights

### 1. Context is Everything

**The problem:** LLMs don't have implicit context about your codebase, your business logic, or your constraints.

**The solution:**
- Provide clear, structured context
- Use relevant file references
- Explain the "why" behind what you're asking
- Be explicit about constraints and requirements

**What works:**
- Pasting relevant code snippets
- Describing the architecture clearly
- Specifying edge cases
- Providing examples

### 2. Iteration Over Perfection

**The mistake:** Expecting perfect code on the first try.

**The reality:**
- LLMs generate plausible-looking code that may have subtle bugs
- The best workflow is iterative
- Generate → Review → Refine → Test

**The pattern:**
1. Ask for a draft
2. Review and identify issues
3. Provide specific feedback
4. Iterate until correct

### 3. LLMs are Great at Patterns, Bad at Novel Problems

**What LLMs excel at:**
- Common patterns (CRUD, API endpoints, standard algorithms)
- Boilerplate code
- Documentation
- Test generation
- Refactoring

**What LLMs struggle with:**
- Novel architectural decisions
- Complex business logic
- Performance-critical code
- Security-sensitive implementations
- Context that requires deep domain knowledge

### 4. Verification is Non-Negotiable

**The hard truth:**
- LLM-generated code looks correct but may not be
- Always verify, never assume
- Run tests, check edge cases, review security

**The workflow:**
- Generate code with LLM
- Review every line
- Run comprehensive tests
- Check for security issues
- Refine based on results

### 5. The Best Developers Use LLMs Differently

**Average developers:**
- Ask LLM to write entire features
- Copy-paste without review
- Blame LLM when things break

**Great developers:**
- Use LLM for exploration
- Generate starting points, not final solutions
- Know when to override the LLM
- Maintain ownership of the code

### 6. Prompt Engineering for Code

**Effective patterns:**

**Be specific:**
- Instead of: "Write a function to process data"
- Try: "Write a Python function that takes a list of dictionaries and returns a summary including count, average, and max values"

**Provide examples:**
- Show input/output pairs
- Demonstrate edge cases
- Include error handling patterns

**Specify constraints:**
- Time complexity requirements
- Memory limitations
- Framework/library preferences
- Coding standards

**Break it down:**
- Complex tasks into smaller steps
- One function at a time
- Build up incrementally

### 7. The Learning Loop

**What 10,000 hours taught:**

- LLMs speed up familiar tasks but don't replace learning
- The best developers know what questions to ask
- Understanding fundamentals matters more than ever
- LLMs are force multipliers, not skill replacements

> "The developers who will thrive are those who understand code deeply enough to guide LLMs effectively."

### 8. When NOT to Use LLMs

**Avoid for:**
- Mission-critical code without review
- Security-sensitive implementations
- Novel algorithmic challenges
- Code you don't understand
- Learning fundamentals (you learn by doing)

### 9. The Future of Coding

**The shift:**
- From writing every line to orchestrating solutions
- From syntax to architecture
- From implementation to verification
- From memorization to understanding

**What this means:**
- Junior developers need stronger fundamentals
- Senior developers focus on system design
- Everyone needs to be better at verification
- The gap between good and great widens

## The Verdict

LLMs are transformative tools that make developers significantly more productive when used correctly. But they're not magic. They require:
- Clear communication
- Careful verification
- Deep understanding of the problem
- Judgment about when to use them

The developers who will succeed are those who learn to work with LLMs while maintaining their own expertise.

## Key Stats

| Metric | Value |
|--------|-------|
| Hours of LLM coding experience | 10,000+ |
| Thread engagement | 85K+ views |
| Video views | 50K+ |

## What I'm Reading

For more on effective LLM coding patterns and AI-assisted development.

## Full Thread

<details>
<summary>Expand for complete thread text</summary>

After 10,000 hours of coding with LLMs, here are the patterns that actually work:

**Context is everything**

LLMs don't have implicit context about your codebase. You have to provide it. Clear requirements, relevant snippets, explicit constraints. The more context, the better the output.

**Iteration over perfection**

Don't expect perfect code on the first try. The workflow is: generate → review → refine → test. It's iterative.

**LLMs are pattern matchers**

They excel at common patterns: CRUD, APIs, refactoring. They struggle with novel problems, complex business logic, and security-critical code.

**Verification is non-negotiable**

LLM code looks correct but may not be. Always verify. Run tests. Check edge cases. Review for security issues.

**Great developers use LLMs differently**

Average devs: ask LLM to write features, copy-paste without review.

Great devs: use LLM for exploration, generate starting points, know when to override, maintain ownership.

**Prompt engineering matters**

Be specific. Provide examples. Specify constraints. Break complex tasks into steps.

**What 10,000 hours taught me**

LLMs speed up familiar tasks but don't replace learning. The best developers know what questions to ask. Fundamentals matter more than ever.

**When NOT to use LLMs**

- Mission-critical code without review
- Security-sensitive implementations
- Novel algorithmic challenges
- Code you don't understand

**The future**

Coding shifts from implementation to orchestration, from syntax to architecture, from writing to verification. The gap between good and great widens.

The developers who thrive understand code deeply enough to guide LLMs effectively.

</details>
