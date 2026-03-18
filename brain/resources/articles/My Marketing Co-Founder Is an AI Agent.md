---
category: article
type:
  - "#type/article"
tags:
  - ai
  - marketing
source: https://x.com/m_0_r_g_a_n_/status/2020594168242880611
date: 2026-02-27
---
#### Key Details
- Squad
	- Scout Finds topics with real keyword data - Every 6h 
	- Quill Writes 2000+ word SEO articles - Every hour 
	- Sage Reviews quality, plagiarism, readability 3x/day 
	- Ezra Publishes to production - Every 3h 
	- Herald Amplifies on social media - 2x/day 
	- Lurker Scouts Reddit for outreach Every 8h 
	- Archie Weekly analytics reports - Weekly
	- Morgan Project manager — unblocks bottlenecks - 3x/day
- Each agent reads from and writes to a shared Notion database. Articles flow through statuses: Backlog → To Do → In Progress → Review → Ready to Publish → Done
- Every agent reads and writes to the same Notion database. This means:
	 - Any agent can see what every other agent has done
	 - Status transitions are atomic and visible
	 - I can monitor the entire pipeline from one board
	 - No agent can skip a step
- Lessons:
	- 1. Agents need constraints, not freedom. The more specific the instructions, the better the output. Open-ended "write a good article" produces garbage. "Write 2000-2200 words, 60+ readability, 5+ internal links to published articles, keyword in first 100 words" produces consistent quality.
	- Always build quality gates. Without Sage rejecting 40% of first drafts, I'd have published a lot of mediocre content. The revision loop is what makes the pipeline actually work.
	- Race conditions are inevitable at scale. As soon as you have parallel agents touching shared state, you need locking. I learned this the hard way with 5 Quills writing the same article.
	- The PM agent is the secret weapon. Morgan catches problems before they compound — empty backlogs, stuck articles, publishing bottlenecks. Self-healing systems beat monitoring dashboards.
	- AI will hallucinate ymy product features. Always have explicit "this product does NOT do X" documentation. Always have an editor agent that checks for accuracy.
	- Start with isolated sessions. Main-session cron jobs are fragile. Isolated sessions run independently and reliably.