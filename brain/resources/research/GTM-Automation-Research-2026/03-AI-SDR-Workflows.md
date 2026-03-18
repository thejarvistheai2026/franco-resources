# AI SDR & Agent Workflows

**Research Date:** February 2026  
**Purpose:** Copy-pasteable agent workflows and AI SDR implementations for production GTM automation

---

## 1. Quick Reference: Workflow Library

| Workflow Name | Trigger | Agent Action | Tools Used | Output |
|--------------|---------|--------------|------------|--------|
| **Pre-Construction Signal Hunter** | Company in target list | Scan for "coming soon" projects, recent announcements | Clay (Claygent + Apollo), Apollo Sequences | Qualified accounts with project details → Sequence |
| **Intent-Based Email Follower** | Email opened 2+ times | Auto-triggers second personalized email + LinkedIn connection | Apollo, Salesforce/HubSpot | Enriched follow-up sequence for warm leads |
| **LinkedIn → Email Pipeline** | LinkedIn search export | Extract → Enrich → Sequence | PhantomBuster, Apollo.io, Zapier | Validated email contacts in Apollo sequence |
| **CRM Lead Revival** | Stalled opportunity (30+ days) | Research company updates → Draft personalized revival email | Clay + HubSpot/Salesforce + AI | AI-drafted email with contextual hook ready to send |
| **Job Change Signal Capture** | Contact changes job (LinkedIn signal) | Enrich new company → Score ICP fit → Notify SDR | Clay, LinkedIn, HubSpot, Slack | Slack notification + CRM update with research summary |
| **Bi-Directional CRM Sync** | New contact in HubSpot | Enrich → Score → Update CRM → Route to rep | Clay + HubSpot + Make/n8n | Fully enriched, scored, assigned record |
| **Daily Cold Outbound Engine** | Scheduled (daily) | Pull ICP list → Waterfall enrich → AI personalize → Queue to Apollo | Clay + Apollo | 200+ enriched, personalized prospects in sequence |
| **Post-Call Research Sync** | Gong call ends | Extract insights → Update Apollo → Trigger follow-up sequences | Gong + Clay + Apollo + Salesforce | Updated records + triggered next-best actions |

---

## 2. Detailed Workflows

### Workflow 2.1: Pre-Construction Signal Hunter (Apollo/Clay)

**Use Case:** Identify construction companies with "coming soon" projects before competitors

**Complete Setup:**

**Step 1: Build Initial List in Apollo**
- Search: Construction companies in target regions
- Filters: Employee count 50-500, Verified email status
- Export to Clay

**Step 2: Claygent Research Prompt**
```
You are a research analyst focused on the real estate and construction industry. Your task is to identify "coming soon" projects, recent announcements, or general project developments for specified builders and developers. Today's date is {{now_day}}-{{now_month}}-{{now_year}}. Don't output any projects that are already completed.

<content_on_company>
Company: {{account.name}}
{{#if account.website_url}} Company Website: ```{{account.website_url}}``` {{#endif}}
{{#if account.description}} Company Description: ```{{account.description}}``` {{#endif}}
</content_on_company>

Search Scope:
Company Website:
- News or update pages
- Press releases
- Blog posts related to project announcements

External Sources:
- Real estate industry news sites
- Local news articles mentioning the builder or developer
- Trade publications related to construction or real estate
- City planning or zoning board meeting minutes and agendas
- Industry forums or project listing sites

Provide the output in the following format:
Project summary with location, expected completion date (if available), and key project details.
Date: Date of announcement or mention of the project (format: YYYY-MM-DD)
Description: Brief description of the project, including any notable aspects or unique features.

Important:
- Only include information directly confirmed to be about the specified builder or developer.
- Exclude any unrelated projects or news about companies with similar names.
- If no relevant projects are found, respond only with "No projects found."
```

**Step 3: Filter & Categorize**
- Create computed columns in Clay for:
  - Has Active Project (Yes/No)
  - Project Value Tier (High/Medium/Low)
  - Timeline (Imminent/6 months/2025+)

**Step 4: Push to Apollo Sequence**
- Filter to only "Has Active Project = Yes"
- Export to Apollo
- Enroll in "Pre-Construction Outreach Sequence"

**Tools & Roles:**
| Tool | Role |
|------|------|
| Apollo | Initial list building, sequence execution, email delivery |
| Claygent | AI research agent for project discovery |
| Clay | Data orchestration, filtering, enrichment waterfall |

**Source:** [Apollo Academy Template](https://www.apollo.io/academy/templates/identify-pre-construction-projects)

---

### Workflow 2.2: Intent-Based Email Responder (Apollo Workflows)

**Use Case:** Automatically follow up with engaged prospects based on email open behavior

**Complete Setup:**

**Step 1: Create Opening Sequence**
- Sequence: "Initial Cold Outreach"
- Step 1: Email (intro + value prop)
- No follow-up steps yet

**Step 2: Create Engagement Workflow**
```
Trigger: Email Opened (2+ times in 24 hours)

Actions:
1. Wait 2 hours
2. Add contact to "High Intent Follow-Up Sequence"
3. Create task: "LinkedIn profile view + connect request"
4. Send Slack notification: "🔥 {{first_name}} from {{company}} is hot - opened email {{open_count}} times"
```

**Step 3: Create Second Sequence**
- Sequence: "High Intent Follow-Up"
- Step 1: Email (more detailed value prop, case study)
- Step 2: LinkedIn message (3 days later)
- Step 3: Call task (5 days later)

**Step 4: Ruleset Configuration**
```
Finish on reply: Yes
Pause on OOO: Yes, resume after period
Finish on booked meeting: Yes
Remove on bounce: Yes
```

**Results:**
- 57%+ open rates (reported by Sean O'Brien using this exact setup)
- 6.7% reply rates
- Fully automated - no manual intervention required

**Source:** [Apollo Academy Template](https://www.apollo.io/academy/templates/engage-prospects-who-open-your-email)

---

### Workflow 2.3: LinkedIn → Email Full Stack (PhantomBuster + Apollo)

**Use Case:** Scale prospecting by extracting LinkedIn leads and automatically enriching + sequencing

**Complete Setup:**

**Step 1: PhantomBuster Configuration**
- Phantom: "LinkedIn Search Export" OR "Sales Navigator Search Export"
- Search criteria: Your ICP (title, company size, industry)
- Extract fields: Name, Title, Company, LinkedIn URL, Company Website

**Step 2: Zapier/Make Bridge**
```
Trigger: New CSV export from PhantomBuster
Action 1: Import to Google Sheet (backup)
Action 2: Send to Apollo via API
  - Map: First Name, Last Name, Company, Title, LinkedIn URL
```

**Step 3: Apollo Data Enrichment**
- Upload CSV to Apollo
- Use "Enrich People" feature
- Map fields: LinkedIn URL → Match score
- Output: Verified emails, phone numbers, additional contact data

**Step 4: AI Sequence Generation**
- Option A: Use Apollo's AI-assisted sequence (recommended for beginners)
- Option B: Custom sequence with AI prompts

**AI-Assisted Sequence Prompt (Apollo):**
```
Industry: {{industry}}
Company Size: {{employee_count}}
Pain Point: {{pain_point}}
Value Prop: {{your_value_prop}}

Generate a 5-step cold email sequence that:
1. Opens with relevance (not just "Hey {{first_name}}")
2. Hooks with industry-specific insight
3. Includes social proof from similar companies
4. Has clear CTAs (not "let me know if interested")
5. Breakup email at step 5 with soft re-engagement option
```

**Step 5: Launch & Monitor**
- Enroll enriched contacts
- Set mailbox rotation if using multiple domains
- Monitor: Open rates, reply rates, bounce rates

**Expected Results:**
- Time saved: ~2 hours 15 minutes per SDR daily
- Open rate improvement: Up to 45% with personalization
- Activity boost: 23% increase in calls/touchpoints

**Source:** [LinkedIn-to-Email Playbook](https://www.unkoa.com/linkedin-to-email-outreach-playbook-2025-automate-prospecting-with-phantombuster-apollo-io/)

---

### Workflow 2.4: Bi-Directional HubSpot + Clay + Make Integration

**Use Case:** Fully automated lead routing, enrichment, and research without manual work

**Complete Setup:**

**Step 1: HubSpot → Clay Trigger**
```
Make.com Scenario:
Trigger: New Contact Created in HubSpot
Action: Send contact data to Clay via API
Payload:
  - First Name
  - Last Name  
  - Email
  - Company
  - Title
  - Source (lead source property)
```

**Step 2: Clay Waterfall Enrichment**
```
Column 1: Email Verification (Dropcontact)
Column 2: Company Enrichment (Apollo)
Column 3: Person Enrichment (Apollo + LinkedIn)
Column 4: AI Research Summary (Claygent)
```

**Step 3: Clay AI Research Prompt**
```
Research {{company_name}} for sales context.

Task 1: What does this company do? (1-sentence summary)
Task 2: Who do they sell to? (Target market)
Task 3: What tools do they use? (Look for competitor/product mentions)
Task 4: Recent news (funding, hiring, product launches in last 90 days)
Task 5: ICP Fit Score (1-10) and reason

Output as JSON:
{
  "company_summary": "...",
  "target_market": "...",
  "tech_stack": [...],
  "recent_news": [...],
  "icp_score": number,
  "icp_reason": "...",
  "personalization_hook": "One sentence for email opener"
}
```

**Step 4: Scoring & Routing Logic**
```
Computed Columns:
- Lead Score = (ICP Score * 10) + (Engagement Score * 5) + (Company Size Score * 3)
- Route To = IF(Lead Score > 80, "AE - Enterprise", IF(Lead Score > 50, "SDR - Standard", "Nurture"))
```

**Step 5: Clay → HubSpot Sync**
```
Webhook from Clay:
- Update HubSpot Contact Properties: lead_score, customization_hook, company_summary
- Update Company Record: employee_count, funding_amount, tech_stack
- Trigger HubSpot Workflow: Create task for assigned rep based on Route To
```

**Step 6: Slack Notifications**
```
Make Scenario:
IF Route To = "AE - Enterprise":
  Post to #enterprise-leads:
  "🎯 *High Value Lead Enriched*
  Company: {{company}}
  Contact: {{first_name}} {{last_name}} ({{title}})
  Score: {{lead_score}}/100
  Hook: {{personalization_hook}}
  Assigned: {{assigned_owner}}"
```

**Tools & Roles:**
| Tool | Role |
|------|------|
| HubSpot | System of record, pipeline management, automation triggers |
| Clay | Data enrichment, waterfall logic, AI research |
| Make.com | Orchestration layer, conditional logic, webhooks |
| Slack | Team notifications, visibility |

**Source:** [Clay Community + HubSpot Integration](https://community.clay.com/x/content-and-events/5fahsjg8j0hb/)

---

### Workflow 2.5: Stalled Opportunity Revival Engine

**Use Case:** Automatically identify and revive stalled deals with contextual research

**Complete Setup:**

**Step 1: Identify Stalled Opportunities**
```
HubSpot Workflow Trigger:
- Deal Stage = "Proposal Sent" OR "Negotiation"
- Days in Stage > 30
- Last Activity Date > 14 days
```

**Step 2: Research Trigger (n8n/Make)**
```
Webhook sends to Clay:
  - Company Domain
  - Last Activity Notes
  - Deal Value
  - Primary Contact Info
```

**Step 3: Claygent Revival Research**
```
Research {{company_name}} for revival opportunity context.

This prospect went dark {{days_since_last_activity}} days ago after {{last_stage}}.

Research tasks:
1. Search for: Recent company news (funding, layoffs, acquisitions, product launches)
2. Search for: Competitor activities affecting them
3. Search for: Leadership changes (hiring, departures in C-suite)
4. Check: Any tech stack changes (new tool rollouts, migrations)
5. Look for: Trigger events that could restart the conversation

Output format:
Revival Angle: [One sentence - why NOW is the time to reach out]
Context Update: [What's changed since they went dark]
Soft CTA Options:
- Option A: If funding: Reference congrats + ask about scaling {{your_category}}
- Option B: If leadership change: Ask about new priorities
- Option C: If no news: Reference industry trend + how peers are solving it
Risk Flags: [Any negative signals to be aware of]
```

**Step 4: Draft Email (Clay or ChatGPT)**
```
Using the Revival Angle above, draft a 3-sentence email:
1. Reconnect context ("Wanted to reach out since {{event}} just happened")
2. Soft value reminder (1 sentence, not pushy)
3. Question that invites response (easy to answer, low friction)

Tone: Friendly, helpful, not desperate
```

**Step 5: CRM Update & Queue**
```
- Add email draft to HubSpot note on contact record
- Create task for owner: "Review AI revival draft and send"
- Log activity: "Revival research completed by Clay"
```

**Result:** SDR/AE spends 2 minutes reviewing vs. 15+ minutes researching manually

---

### Workflow 2.6: Job Change Signal Capture (LinkedIn → Slack → CRM)

**Use Case:** Instantly notify sales when target accounts have key personnel changes

**Complete Setup:**

**Step 1: Signal Source Options**
Option A (PhantomBuster):
- Phantom: "LinkedIn Profile Scraper" on target contacts list
- Schedule: Weekly
- Export: Current title, company

Option B (Clay + LinkedIn):
- Clay table of former prospects
- Scheduled enrichment: "Current Title" column
- Alert condition: Title changed OR Company changed

**Step 2: Determine ICP Fit at New Company**
```
Claygent Research:
"Research {{new_company_name}}. 
Is this company a fit for {{your_product_category}}?
- Employee count: 
- Industry: 
- Estimated revenue: 
- Tech stack: 
- ICP Match Score (1-10): 
- Reason: "
```

**Step 3: Routing Decision Tree**
```
IF: Previous relationship = "Closed Won" AND New Company ICP Score > 7
  → Alert: "Champion moved - expansion opportunity"
  → Route to: Customer Success + Account Manager
  → Action: Create task: "Welcome former champion to new role"

IF: Previous relationship = "Open Opp" AND New Company ICP Score > 7
  → Alert: "Prospect moved - land opportunity at new company"
  → Route to: SDR (new company) + Keep AE (old opp)
  → Action: Create sequence for new company

IF: Previous relationship = "Closed Lost" AND New Company ICP Score > 7
  → Alert: "Lost prospect moved - fresh start?"
  → Route to: SDR
  → Action: Research if previous objection still applies

IF: ICP Score < 4
  → No action (log only)
```

**Step 4: Slack Template**
```
🔄 Champion Alert
{{first_name}} {{last_name}} moved to {{new_company}}

Previous Context: {{last_deal_stage}} at {{old_company}}
New Role: {{new_title}}
New Company Fit: {{icp_score}}/10

Recommended Action: {{action}}
Research Summary: {{ai_research_summary}}

[View in HubSpot] | [Create Task] | [Enroll in Sequence]
```

---

### Workflow 2.7: Daily Outbound Engine (Full Stack)

**Use Case:** Fully automated daily prospecting that runs without human input

**Cron Schedule:** Weekdays at 6:00 AM

**Step 1: Pull Fresh Leads**
```
Source: Apollo saved search
Criteria:
  - Employee count: 50-500
  - Industry: Software, IT Services
  - Technologies: {{competitor}} (negative trigger)
  - Job titles: VP, Director, Head of, C-level
  - Last contacted > 90 days (Apollo dedupe)
Limit: 200 contacts/day
```

**Step 2: Clay Import & Validate**
```
Import to Clay table
Actions:
  - Remove domains on blocklist
  - Verify email (waterfall: NeverBounce → Dropcontact)
  - Validate: IF email = valid, THEN proceed
```

**Step 3: Waterfall Enrichment**
```
Column 1: Apollo Company Data (employee count, funding)
Column 2: Claygent Website Analysis
Column 3: LinkedIn Personal Insights (bio, recent posts)
Column 4: Tech Stack Detection (BuiltWith → technologies)
```

**Step 4: AI Personalization at Scale**
```
First Line Generator:
"Write a 1-sentence first line for {{first_name}} at {{company}} based on:
- Their LinkedIn: {{linkedin_summary}}
- Company: {{company_description}}
- Recent post: {{recent_post_topic}}

Make it specific (not 'love what you do at Acme').
Reference something real they've shared or done recently.
Tone: Friendly, professional, not salesy."
```

**Step 5: Score & Segment**
```
A Tier: ICP Score 8-10 + Enriched + Valid Email
  → Add to "High-Touch Outbound Sequence" (7 steps, multi-channel)

B Tier: ICP Score 5-7 + Enriched + Valid Email
  → Add to "Standard Outbound Sequence" (5 steps, email only)

C Tier: Low score OR Partial enrichment
  → Add to "Nurture List" (newsletter, monthly check-in)
```

**Step 6: Push to Apollo**
```
- Export A/B tiers to CSV
- Import to Apollo lists
- Auto-enroll in respective sequences
- Set to go live at 9:00 AM
```

**Step 7: Daily Report**
```
Slack to #sales-ops:
"📊 Daily Outbound Engine Complete
✅ 200 prospects pulled
🎯 142 passed validation
🌊 128 enriched via waterfall
💎 38 A-tier (high-touch seq)
📝 90 B-tier (standard seq)
❌ 14 bounced removed

Sequences active: 9:00 AM
Expected deliveries: 128"
```

---

## 3. CRM Integration Patterns

### Pattern 3.1: HubSpot + Clay Native Integration

**Architecture:**
```
HubSpot (Trigger) → Clay (Webhook) → Enrichment → HubSpot (Update) → Workflow (Action)
```

**HubSpot → Clay:**
```
Webhook URL: https://www.clay.com/api/v1/webhooks/ingest/xxx
Trigger Events:
  - Contact Created
  - Company Created
  - Deal Stage Changed
Payload:
  - All contact/company properties
  - Enrollment source
```

**Clay Operations:**
```
1. Receive webhook data
2. Run waterfall enrichment (Apollo → DropContact → LinkedIn)
3. Execute Claygent for AI research
4. Compute scores and routing logic
5. Prepare update payload
```

**Clay → HubSpot:**
```
Native Clay Integration:
  - Update Contact Property: Custom property mapping
  - Update Company Property: firmographic enrichment
Actions Available:
  - Update record
  - Create new record
  - Trigger workflow
  - Delete record
```

**HubSpot Workflow Triggers (post-Clay):**
```
IF: lead_score > 80
  → Assign to AE (round robin)
  → Create task: "High-value lead enriched - call within 2 hours"
  → Add to "Fast Track" list

IF: icp_score > 7 AND lead_score < 80
  → Assign to SDR
  → Add to outbound queue
  → Set "ICP Fit" lifecycle stage

IF: icp_score < 4
  → Set "Non-ICP" lifecycle stage
  → Remove from active sequences
  → Add to long-term nurture
```

---

### Pattern 3.2: Salesforce Bi-Directional Sync

**Via OutboundSync (recommended):**
```
OutboundSync provides true bi-directional sync vs. Salesforce's native one-way integration

Data Flow:
Outbound (Clay/Apollo) → OutboundSync → Salesforce
Salesforce → OutboundSync → Outbound (status updates)

Syncs:
- Email sends/replies
- Bounces
- Call outcomes
- Interest labels
- Lead stages
- Unsubscribes
```

**Setup:**
```
1. Connect Salesforce via OAuth in OutboundSync
2. Map custom fields:
   - Apollo Lead Score → Salesforce Lead Score
   - Clay Personalization Hook → Custom field "Email_Hook__c"
3. Configure sync frequency: Real-time or batch (hourly)
4. Set conflict resolution: Newest wins / Salesforce wins / Outbound wins
```

**Salesforce Process Builder Triggers:**
```
Trigger: Outbound_Activity_Lead_Score__c CHANGED
Condition: New value > 80
Action:
  - Create Task: "High-scoring lead - prioritize"
  - Move to Working status
  - Alert owner via Slack
```

---

### Pattern 3.3: Notion/Airtable as Data Warehouse

**Use Case:** Centralized reporting + team collaboration without CRM limits

**Clay → Notion:**
```
Make.com Scenario:
Trigger: Clay table updated
Action 1: Create Notion page
  - Database: "Prospect Research"
  - Properties:
    - Company (title)
    - ICP Score (number)
    - Research Summary (text)
    - Assigned To (person)
    - Clay Link (URL)
    - Status (select)
Action 2: Create child page for full Claygent research
```

**Airtable Alternative:**
```
Use Clay's native Airtable integration
Sync frequency: 15 minutes
Sync mode: Clay → Airtable (one-way)
Use case: Marketing team access without CRM licenses
```

---

### Pattern 3.4: n8n Advanced Orchestration

**Architecture:**
```
HubSpot → n8n → Clay → n8n → HubSpot + Slack + Email
         ↓
   (Decision Logic)
         ↓
   Branch A (High Score) → AE
   Branch B (Medium Score) → SDR
   Branch C (Low Score) → Nurture
```

**n8n Workflow Code:**
```javascript
// Scoring Logic Node
const lead = $input.first().json;
let score = 0;

// Add points for enrichment
core += lead.company_employee_count > 100 ? 20 : 0;
score += lead.funding_amount > 1000000 ? 25 : 0;
score += lead.email_verified ? 10 : 0;
score += lead.clay_research_complete ? 15 : 0;

// Tech stack matches
const targetTech = ['Salesforce', 'HubSpot', 'Marketo'];
if (lead.tech_stack.some(t => targetTech.includes(t))) {
  score += 20;
}

// Return
return {
  json: {
    ...lead,
    calculated_score: score,
    routing_decision: score > 80 ? 'AE' : score > 50 ? 'SDR' : 'NURTURE'
  }
};
```

---

## 4. Copy-Paste Prompt Library

### 4.1 Claygent Research Prompts

**Website Analysis:**
```
Analyze this company website: {{website_url}}

Task 1: What does this company do? (1 sentence, specific)
Task 2: Who do they sell to? (Target market, buyer persona)
Task 3: What's their value proposition? (How they win vs. competitors)
Task 4: What pain points do they likely have? (What problems they solve for their customers)
Task 5: Recent news or updates (last 90 days)

Output as bullet points. Be specific - no fluff.
```

**LinkedIn Profile Research:**
```
Analyze this LinkedIn profile for sales context:
Name: {{name}}
Title: {{title}}
Company: {{company}}
Bio: {{bio}}
Recent posts: {{recent_posts}}

Task 1: What's their role in buying decisions? (Decision maker, influencer, user)
Task 2: What likely matters to them in {{your_category}}?
Task 3: Any personal interests or background we can reference?
Task 4: One-sentence personalization hook for cold email
Task 5: Recommended value prop angle
```

**ICP Scoring:**
```
Score this company for {{your_product}} fit:

Company: {{company_name}}
Industry: {{industry}}
Employee Count: {{employee_count}}
Funding: {{funding_amount}}
Tech Stack: {{technologies}}

Scoring Criteria (1-10):
- Employee count: {{your_ideal_range}}
- Industry alignment: {{your_target_industries}}
- Tech stack maturity: Do they use similar tools?
- Growth indicators: Funding, hiring velocity

Output:
ICP Score: /10
Qualifier: YES/NO (need all criteria)
Reasoning: 2 sentences
Best outreach angle: 
```

### 4.2 Apollo AI Prompts

**Email Personalization:**
```
Write a personalized email to {{first_name}} at {{company}} based on:

Company Context:
- What they do: {{company_description}}
- Recent news: {{recent_news}}
- Pain points we solve: {{pain_points_addressed}}

Personal Context:
- Their title: {{title}}
- Likely responsibilities: {{role_functions}}

Email Requirements:
- Subject line: Make it specific, not generic
- First line: Reference something specific (not "saw you're at Acme")
- Value prop: One sentence, outcome focused
- CTA: One specific question (low friction)
- Length: Under 125 words
```

**LinkedIn Connection Note:**
```
Write a LinkedIn connection request for {{first_name}} at {{company}}.

Context:
- Their role: {{title}}
- Company focus: {{company_summary}}
- Shared connection (if any): {{shared_connections}}

Rules:
- Max 300 characters
- Specific, not generic
- No pitching
- Natural, conversational tone

Example good: "Hi {{first_name}}, noticed {{company}} just raised Series B - congrats! Working with similar teams on scaling their {{relevant_function}}. Would love to connect."
```

### 4.3 First Line Generators

**Version A - General:**
```
Write a one-sentence email opener for {{first_name}} at {{company_name}}.

Reference something specific from:
- Their LinkedIn activity: {{linkedin_posts}}
- Company news: {{recent_news}}
- Industry context: They compete in {{industry}}

Avoid:
- "Love what you're doing at {{company}}"
- "Saw your profile on LinkedIn"
- Generic compliments

Make it feel like I actually looked them up (because I did).
```

**Version B - Trigger Event:**
```
Write a one-sentence opener referencing their recent {{event_type}}.

Event: {{event_description}}
Date: {{event_date}}

Options:
- If funding: Congratulate + connection to scaling
- If hiring: Reference role + pain point
- If product launch: Comment on positioning
- If speaking engagement: Reference talk topic

One sentence only. Specific > clever.
```

### 4.4 Sequence Templates

**5-Step Cold Outreach Sequence:**

```
Email 1 (Day 1):
Subject: {{company}} + {{relevant_topic}}
Body:
{{first_name}},

{{ai_generated_first_line}}

{{one_sentence_value_prop}}

{{one_sentence_social_proof}}

{{soft_cta_question}}

Best,
{{sender_name}}

---

LinkedIn (Day 2):
[Manual task: View profile + Send connection request]
Note: "Hi {{first_name}}, noticed {{company}}'s work in {{area}} - interested in how you're handling {{pain_point}}.

---

Email 2 (Day 4):
Subject: Re: {{company}} + {{relevant_topic}}
Body:
{{first_name}},

Quick follow - {{competitor_or_peer}} saw a {{metric_improvement}} after implementing {{solution_category}} in {{timeframe}}.

Relevant given {{company}}'s recent {{company_context}}.

Worth a brief chat?

{{sender_name}}

---

Call (Day 7):
[Task: Call mobile, leave voicemail if no answer]
Script: "Hi {{first_name}}, this is {{sender_name}} from {{our_company}}. I sent you a note about {{topic}} - wanted to see if it was relevant for {{company}}'s {{department}} goals. I'll follow up via email too."

---

Email 3 - Breakup (Day 12):
Subject: Should I close the loop?
Body:
{{first_name}},

Tried to reach you a few times about {{topic}} but haven't connected.

Should I close the loop, or is {{pain_point}} still a priority for {{company}}?

{{sender_name}}
P.S. - If now's not the time, totally understand. I can check back in a few months.
```

---

## 5. Decision Trees

### 5.1 Lead Routing Decision Tree

```
INBOUND LEAD (HubSpot form, demo request, etc.)
     ↓
Is contact email valid?
 ├─ NO → Reject, add to invalid list
 └─ YES → Continue
     ↓
Company domain check:
 ├─ Is it a competitor? → Flag, alert security
 ├─ Is it existing customer? → Route to CSM
 ├─ Is it active opp? → Alert AE, update opp
 └─ NEW → Continue
     ↓
ICP Score calculation:
 ├─ Score 80-100 → AE Assignment
 │   └─ Task: "High-scoring lead - call within 2 hours"
 ├─ Score 50-79 → SDR Assignment  
 │   └─ Enroll in "Fast Track" sequence
 ├─ Score 25-49 → Automated Nurture
 │   └─ Add to newsletter, monthly touch
 └─ Score <25 → Reject / Low-priority list
     ↓
Slack notification (all tiers) with research summary
```

### 5.2 Engagement Response Decision Tree

```
PROSPECT ENGAGEMENT DETECTED
     ↓
Engagement Type:
 ├─ Email Opened 2+ times in 24h
 │   └─ Wait 2 hours
 │   └─ Send high-intent follow up
 │   └─ Create LinkedIn task
 │   └─ Alert rep: "Warm lead: {{first_name}}"
 ├─ Email Clicked
 │   └─ Priority: HIGH
 │   └─ Call within same day
 │   └─ Send related content
 ├─ Sequence Reply
 │   └─ Human takes over
 │   └─ Pause automation for this contact
 │   └─ Update CRM: "Engaged - reply received"
 ├─ LinkedIn Profile View (of your SDR)
 │   └─ Queue for connection request
 │   └─ Include personalized note
 └─ Website Visit (clearbit identified)
     └─ Enrich in Clay
     └─ IF ICP fit: Alert AE with visit summary
```

### 5.3 Data Quality Decision Tree (Clay)

```
NEW RECORD IMPORTED
     ↓
Email Validation:
 ├─ Valid → Continue
 ├─ Catch-all → Flag but proceed with caution
 └─ Invalid → Reject, don't use credits
     ↓
Company Enrichment:
 ├─ Found in Apollo → Pull firmographics
 │   ├─ Employee count matches ICP? → Continue
 │   └─ No match → Low priority
 ├─ Not found → Try LinkedIn
 │   ├─ Found → Continue
 │   └─ Not found → Manual research flag
     ↓
Personal Enrichment:
 ├─ LinkedIn match → Role analysis
 │   ├─ Decision maker? → High priority
 │   ├─ Influencer? → Medium priority
 │   └─ End user only? → Track for later
 └─ No match → Generic sequence
     ↓
Composite Score:
 ├─ A Tier (>80 points) → Human review queue
 ├─ B Tier (50-79) → Auto-enroll standard sequence
 └─ C Tier (<50) → Batch for later
```

### 5.4 Sequence Breakup Decision Tree

```
SEQUENCE COMPLETED (no reply after final touch)
     ↓
Any engagement? (opens, clicks)
 ├─ YES (opens > 2) → Move to nurture sequence
 │   └─ Quarterly soft touches
 │   └─ Continue monitoring for intent signals
 └─ NO engagement → Evaluate fit
     ↓
ICP fit = Strong?
 ├─ YES → Manual review
 │   └─ Different angle?
 │   └─ Different contact at company?
 │   └─ Wait 90 days, retry
 └─ NO → "Not Engaged" segment
     └─ Remove from active outreach
     └─ Annual check-in only
     ↓
Long-term nurture
 └─ Monthly newsletter
 └─ Trigger-based re-engagement (funding, leadership change)
```

---

## 6. Tool Stack Combinations

### Combo 1: Minimal Viable AI SDR

**Tools:** Clay (solo) + Apollo (solo) + HubSpot (solo)  
**Cost:** ~$300-500/month  
**Setup Time:** 1-2 weeks  
**Savings:** 15-20 hours/week manual work

### Combo 2: Enterprise Orchestration

**Tools:** Clay + Apollo + Gong + HubSpot + n8n/Mk + Slack  
**Cost:** $800-1500/month  
**Setup Time:** 3-4 weeks  
**Capabilities:** Full signal capture, post-call automation, complex routing

### Combo 3: Budget Bootstrap

**Tools:** PhantomBuster + Apollo + Notion (free tier) + Zapier  
**Cost:** $100-200/month  
**Setup Time:** 1 week  
**Limitations:** No bi-directional sync, manual review required

### Combo 4: Best-in-Class Pipeline

**Tools:** Clay + Instantly + SFDC + OutboundSync + n8n
**Cost:** $1000-2000/month
**Setup Time:** 4-6 weeks
**Best For:** High-volume outbound (10K+ touches/month)

---

## 7. Success Metrics & Benchmarks

### Apollo Sequence Benchmarks (2025/2026)

| Metric | Cold Email | Warm Lead | Intent-Based |
|--------|-----------|-----------|--------------|
| Open Rate | 25-35% | 40-50% | 55-70% |
| Reply Rate | 3-5% | 8-12% | 12-18% |
| Meeting Rate | 1-2% | 5-8% | 8-15% |
| Bounce Rate | <5% | <3% | <2% |
| Unsubscribe | <0.5% | <0.3% | <0.2% |

### Clay Enrichment Benchmarks

| Data Point | Single Source | Clay Waterfall |
|------------|--------------|----------------|
| Email Find Rate | 40-50% | 75-85% |
| Mobile Phone Rate | 20-30% | 45-60% |
| Firmographic Complete | 60-70% | 85-95% |
| AI Research Success | N/A | 90%+ |

### Time Savings (per SDR/month)

| Task | Manual | AI-Assisted | Savings |
|------|--------|-------------|---------|
| Lead Research | 40 hrs | 4 hrs | 36 hrs |
| Email Personalization | 20 hrs | 2 hrs | 18 hrs |
| List Building | 10 hrs | 1 hr | 9 hrs |
| CRM Data Entry | 8 hrs | 0.5 hrs | 7.5 hrs |
| **TOTAL** | **78 hrs** | **7.5 hrs** | **70.5 hrs** |

---

## Sources & References

1. **Apollo AI SDR Building Guide:** https://www.apollo.io/magazine/ai-sdr-how-to-build-your-own
2. **Clay + Apollo Integration:** https://www.clay.com/university/guide/apollo-io-integration-overview
3. **RevOps Supercharged with Clay:** https://ziellab.com/post/revops-supercharged-with-ai-how-clay-transforms-every-stage-of-your-revenue-engine
4. **Apollo Sequences Guide:** https://www.unkoa.com/apollo-io-sequences-the-ultimate-guide-to-automated-outreach-for-b2b-sales/
5. **LinkedIn-to-Email Playbook:** https://www.unkoa.com/linkedin-to-email-outreach-playbook-2025-automate-prospecting-with-phantombuster-apollo-io/
6. **HubSpot + Clay Integration:** https://www.hubspot.com/startups/tech-stacks/sales-csx/hubspot-clay-ai-stack-startups/
7. **Pre-Construction Template:** https://www.apollo.io/academy/templates/identify-pre-construction-projects
8. **Intent-Based Follow-Up Template:** https://www.apollo.io/academy/templates/engage-prospects-who-open-your-email

---

**Research compiled by:** Sub-agent for GTM Automation Research  
**Last Updated:** 2026-02-19
