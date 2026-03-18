---
category: article
type:
  - "#type/article"
tags:
source: https://x.com/levikmunneke/status/2026339787255537847
date: 2026-02-27
---
#### Key Insight
the key insight: once your decision-making is documented clearly enough for claude code to follow, you've cloned your operational judgment. it's not making strategic decisions. it's executing the decisions you already made, at scale, with zero variance.

#### Details
- real automation means the AI does the work while you sleep.
- this is why it works for outbound. outbound is 90% mechanical execution and 10% creative strategy. claude code handles the 90%.
- most people set up 5-10 inboxes and wonder why they're only booking 3 calls a month. volume is the game. infrastructure is what makes volume possible.
- the 3-channel system
	- single-channel outbound is dead. here's why running all three simultaneously works.
		- channel 1: cold email (the foundation)
			- 2 emails per prospect maximum
			- the data across millions of sends is clear. email 1 generates ~65% of positive replies. email 2 gets another ~25%. emails 3-7 combined account for ~10% while actively destroying your deliverability.
			- 90 days later, fresh copy, fresh angle, try again. different person at the same company if possible.
		- channel 2: twitter DMs (the arbitrage)
			- twitter is the most underrated B2B channel right now.
			- decision-makers get 50+ linkedin messages per day. they get 100+ cold emails per week. know how many B2B DMs they get on twitter? maybe 2-3.
			- scraping competitor followers filtered by bio keywords (founder, CEO, VP, director
			- analyzing recent tweets to find personalization hooks
			- sending DMs that reference something specific they posted
			- following up once if no response
			- routing interested replies to your qualification flow
		- channel 3: linkedin (the trust builder)
			- linkedin is saturated but still has the highest concentration of B2B buyers.
			- not for cold pitching. for creating familiarity.
			- the sequence:
				- view their profile (they see the notification)
				- engage with a post (like or thoughtful comment)
				- send connection request with a short personalized note
				- wait 48 hours after acceptance
				- send a value-first message, not a pitch
				- follow up once if no response
- when you hit the same prospect on email tuesday, twitter thursday, and linkedin the following week - they start recognizing your name.
- by the third touchpoint, you're not a stranger anymore. you're "that person i keep seeing everywhere." familiarity breeds trust. trust books calls.
- Daily breakdown/schedule:
	- claude code checks which campaigns need fresh contacts. for each one, it:
		- runs searches in apollo or scrapes linkedin/twitter based on targeting criteria
		- filters out anyone contacted in the last 90 days
		- enriches missing data points (email, company size, tech stack)
		- validates all emails
		- segments contacts into the right campaigns
		- loads everything into instantly

- when setting this up, you don't hand claude code a finished automation. you describe what you need
	- "build me a python script that connects to the apollo API, pulls contacts matching these criteria, checks them against our master database to avoid duplicates, validates emails through zerobounce, and loads qualified contacts into instantly via their API."
- this is the difference. you're not maintaining a brittle automation that breaks every time an API updates. you have an agent that adapts.



daily-outbound-operations.md:
schedule 
- 6:00 AM: build lists for campaigns needing fresh contacts 
- 8:00 AM: review performance, rotate copy variants 
- 9:00-5:00: monitor sending across all channels 
- 6:00 PM: process and categorize all replies 
- 10:00 PM: send daily summary via telegram 

list building rules 
- never contact anyone reached in last 90 days 
- validate all emails before loading 
- max 300 new contacts per campaign per day 
- always check master DB for duplicates 

email rules 
- 2 emails max per prospect per cycle 
- pause any variant under 15% open rate after 200 sends 
- pause any variant with 0 replies after 500 sends 
- scale variants above 2% reply rate 

twitter rules 
- max 150 DMs per account per day 
- personalize using last 5-7 tweets 
- one follow-up after 24 hours, then stop 
- flag any response mentioning interest
 
linkedin rules 
- max 25 connection requests per day 
- max 50 messages per day 
- view profile before connecting 
- wait 48 hours after acceptance before messaging 
 
response handling 
- hot: interested, mentions budget/timeline/need → telegram alert + CRM task 
- warm: positive but timing issue → 90-day re-queue 
- objection: declined with reason → log for analysis - negative: hard no → unsubscribe immediately 

escalation triggers 
- deliverability below 92% on any domain
- negative reply rate above 5% on any variant 
- any mention of legal/spam/lawsuit in a reply


