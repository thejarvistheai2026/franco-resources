# Clay Deep Dive: GTM Automation Research (Nov 2024 - Feb 2025)

*Research Date: February 19, 2026*  
*Focus: AI Agents, Waterfall Enrichment, Claygent Updates, Templates & Integrations*

---

## Executive Summary

Clay has experienced explosive growth, reaching **$100M ARR** (from $1M to $100M in just 2 years) and achieving a **$5B valuation** by January 2026. The platform has evolved from a data enrichment tool into a comprehensive **GTM Engineering platform** powered by AI agents, waterfall enrichment, and deep integrations with ChatGPT and Claude.

**Key Milestones (Nov 2024 - Feb 2025):**
- **$100M ARR** reached (Dec 2025) - 8-year overnight success
- **$5B valuation** (Jan 2026) - second tender offer in 9 months
- **Claygent surpassed 1 billion runs** (Jun 2025)
- **Clay in ChatGPT** launched (Dec 2025)
- **Clay in Claude** launched (Jan 2026)
- **Sculptor Analyst Mode** released (Feb 2026)
- **6 major product launches** at Sculpt conference (Sep 2025)

---

## 1. AI Agents & AI-Powered Features

### Sculptor: Natural Language GTM Co-Pilot
**Launched:** September 2025 (Sculpt Conference)  
**Analyst Mode:** February 2026

Sculptor is Clay's AI co-pilot that allows GTM teams to build workflows and analyze data using natural language - no technical skills required.

**Key Capabilities:**
- **Workflow Building:** "Generate a list of healthcare companies in the US with 50-100 employees and find Heads of Sales with LinkedIn URLs and emails"
- **Data Analysis:** "Look at this list of customers and analyze why these accounts were lost"
- **Social Media Analysis:** "Analyze this table of social mentions and return (A) which subreddits talk most about our company, (B) top complaints, (C) top positives"

**Sculptor Analyst Mode (Feb 2026):**
Fine-tuned for business intelligence with four primary use cases:

1. **Define Market and ICP**
   - Example prompt: *"Generate a comprehensive ICP analysis document for [REGION] [SEGMENT] using this customer list. Define our ICP & top targeting filters to find more lookalikes of our best customers"*
   - Case Study: Ilze Nartise at Printify analyzed closed-won deals to identify ICP patterns never examined before

2. **Diagnose Revenue Performance**
   - Example prompt: *"Analyze closed/lost deals and summarize the top loss reasons"*
   - Clay's RevOps team used this to uncover core messaging gaps and adjust sales talk tracks

3. **Improve Data Reliability**
   - Example prompt: *"Audit this table's enrichment coverage and identify the biggest match-rate gaps + fixes"*
   - Sumair Shakir (Clayvengers agency) uses this as QC gate before expensive enrichments - saves 20-30% build time

4. **Size and Prioritize Markets**
   - Skydio (49-person sales team) used this for territory rebalancing across thousands of accounts
   - Analyzes: total locations, annual revenue, open opportunities

**Shared Templates:**
- [Sculptor for ICP Analysis](https://app.clay.com/shared-table/share_0t3xcbkFd5CWiJDQsQb)
- [Sculptor for Closed-Lost Analysis](https://app.clay.com/shared-table/share_0t4y5nkmQgNSpddmdNG)

### Claygent Builder
**Launched:** September 2025

A dedicated workspace for building, testing, and deploying AI prompts across organizations.

**Features:**
- Risk-free prompt development (no credit burn while iterating)
- Version control for prompts
- Natural language to structured prompt generation
- Cross-workflow deployment

**Workflow:**
1. Input: "find recent news articles about a company"
2. Builder generates fully structured prompt with detailed examples
3. Deploy across every workflow needing company research

### Claygent Connectors (MCP Connections)
**Launched:** September 2025 (Enterprise)

Extends Claygent's AI research beyond the web to **first-party data**:

**Supported Sources:**
- Salesforce records
- Gong transcripts  
- Google Docs
- Data warehouses
- Internal tools

**Example Use Cases:**
- *"Summarize all customer conversations from last quarter and identify common objections"*
- *"Research this Salesforce opportunity and suggest next steps based on deal history"*
- *"Write outreach copy using our brand voice guidelines from Google Docs"*

### Audiences (Coming Q4 2025)

Combines CRM data, signals, and enrichments into unified buyer journey view:

**Functionality:**
- Sync and enrich millions of CRM records in one click
- Segment by combining signals (website visits, social engagement, job changes) + enrichments + CRM fields
- Push enriched audiences back to CRM with engagement context

---

## 2. Waterfall Enrichment

### Core Waterfall Concept

Clay's waterfall enrichment searches **150+ databases** sequentially to maximize coverage:

**How It Works:**
1. Query Provider A for data point (email, phone, etc.)
2. If match found → pay for data, stop waterfall
3. If no match → move to Provider B
4. Continue until match found or all providers exhausted
5. **Only pay when data is found**

**Coverage Comparison:**
- Traditional providers (ZoomInfo): ~30% coverage
- Clay waterfall: ~80% coverage
- Anthropic achieved **3x enrichment rate** vs single provider

### Data Provider Strategy

**Clay's Approach vs. Traditional Vendors:**

| Aspect | Traditional (ZoomInfo, etc.) | Clay |
|--------|------------------------------|------|
| Data Source | Bundled, marked up | Direct from 50+ providers |
| Contracts | Annual, $50K-100K+ | Pay-as-you-go, no platform fee |
| Coverage | Single provider, ~30% | Waterfall, ~80% |
| Flexibility | Rigid filters | AI-powered custom qualification |
| Stale Data | Common | Real-time enrichment |

### Waterfall Data Types Available

- Work emails
- Personal emails  
- Mobile phone numbers
- Company phone numbers
- Fundraising data
- Technology stack data
- Firmographics
- Technographics

### Example Workflow

**Step-by-Step Email Waterfall:**
1. Create/import prospect list
2. Click "Enrich data" → Select "Work email" waterfall
3. Clay creates waterfall columns (each = different provider)
4. Run enrichment - only paying providers that return matches
5. Result: Near 100% coverage vs. 30% from single provider

---

## 3. Claygent Updates

### Claygent Navigator
**Launched:** August 20, 2025

Clay's most agentic model yet - inspired by OpenAI's Operator. Navigator can **interact with websites**, not just read them.

**Capabilities:**
- Human-style navigation: clicks, form fills, filter toggles, pagination, scrolling
- Works with pages, tables, PDFs, XML/CSV outputs
- Step-by-step Claygent Replay shows exactly what was clicked/filled

**Use Cases:**
- Search public databases (FINRA BrokerCheck, SEC filings)
- Check structured registries (liquor licenses, professional credentials)
- Navigate portals requiring filters/clicks

**Cost:** 6 credits per run (no private key support currently)

**When to Use Navigator vs Other Models:**
- **Navigator:** Multi-hop web research with actions, forms, visual content
- **GPT-4.1/Argon:** Deep research or text-only data synthesis

### GPT-5 in Claygent
**Launched:** August 7, 2025

GPT-5 is now available as a model option across Clay, bringing:
- Sharper research capabilities
- Stronger formula generation
- Better outbound writing

### Claygent Milestones

- **1 Billion Runs:** June 5, 2025
- **World's most loved AI research agent in GTM** (per Clay)

### Claygent Use Case Examples

**Social Listening Workflow (Jan 2026):**
1. Pull LinkedIn engagement data (reactors, commenters)
2. Enrich engagers with firmographic data
3. Match to CRM accounts
4. Identify tier 1 target account engagement
5. Route qualified leads to sales automatically

**Conversational Data Mining (Oct 2025):**
- Mine millions of call transcript pages (Gong, etc.)
- Extract implemented use cases
- Match product usage to specific use cases
- Calculate credit consumption/pacing
- Identify expansion opportunities

---

## 4. Templates & Playbooks

### Pre-Built Workflow Examples Found

#### 1. Automated Slide Deck Creation (Feb 2026)
**Purpose:** Generate QBR/pitch decks automatically

**Data Sources:**
- Product usage database (Snowflake, BigQuery)
- Salesforce (account info, use case tracking)
- Gong/call recordings (conversation intelligence)

**Generated Content:**
- Cover page with customer branding
- Account activity overview with metrics
- Implemented use cases with data
- Forward-looking roadmap
- Credit pacing/expansion recommendations
- Data citations for review

**Impact:** CS rep managing 15 accounts saves **90 hours per quarter** (2+ work weeks)

**Trigger:** Slack slash command → Deck generated in minutes

#### 2. Social Listening Pipeline (Jan 2026)
**Purpose:** Turn LinkedIn engagement into qualified pipeline

**Workflow:**
1. Native LinkedIn integration pulls post engagement
2. Set up one-to-many: one post → many reactions/comments
3. Match LinkedIn URLs to CRM accounts
4. Check named account list/tier definitions
5. Enrich with work emails via waterfall
6. Draft personalized emails based on comments
7. Queue in Clay Sequencer or route to HeyReach

**Metric Shift:** From "cost per engagement" to "cost per qualified engagement"

#### 3. Inbound Lead Automation (2024)
**Purpose:** Automate trial user conversion outreach

**Steps:**
1. Track trial sign-ups
2. Enrich with company data
3. Categorize by use case/ICP fit
4. Draft personalized conversion emails
5. Route to appropriate sales rep

#### 4. "Wake the Dead" Campaign (Feb 2024)
**Purpose:** Re-engage stalled opportunities

**Process:**
1. Export stalled CRM opportunities
2. Research current company state (hiring, funding, leadership changes)
3. Identify re-engagement triggers
4. Generate personalized revival emails
5. Targeted outreach to dormant accounts

#### 5. Warm Outbound Marketing Play (Jun 2024)
**Purpose:** Convert web visitors to leads

**Components:**
- Track website visitors
- Enrich visitor companies
- Identify ICP matches
- Trigger personalized outreach within 24 hours

#### 6. Local Business Prospecting (Oct 2025)
**Partnership:** Openmart + Clay Sequencer

**Use Case:** Find and outreach local businesses without manual research
- Salons, HVAC companies, small businesses
- Google Maps scraping + AI enrichment
- Automated personalized email campaigns

### Template Resources

**Clay University Guides:**
- [Claygent AI Web Scraper - Clay 101](https://www.clay.com/university/lesson/claygent-ai-web-scraper-clay-101)
- [Enrich: Build Complete Prospect Profiles with AI](https://university.clay.com/lessons/enrich-build-complete-prospect-profiles-with-ai)
- [Importing from Your CRM](https://university.clay.com/lessons/importing-from-your-crm-crm-enrichment)

**Shared Templates:**
- Sculptor ICP Analysis: `share_0t3xcbkFd5CWiJDQsQb`
- Sculptor Closed-Lost Analysis: `share_0t4y5nkmQgNSpddmdNG`

---

## 5. Integrations

### Major AI Platform Integrations

#### Clay in ChatGPT
**Launched:** December 17, 2025

**Capabilities:**
- Access Clay's research stack directly in ChatGPT
- Find contacts with verified emails/phone numbers
- Run detailed account research
- Draft contextual outbound emails

**Example Prompts:**
- *"Clay, find product execs who joined [Company] in the last 6 months"*
- *"Clay, find me [Name] at [Company]"* → *"Now find their thought leadership posts and email"*
- *"Clay, use the data collected to draft a personalized email"*

**Availability:** ChatGPT app directory, 500 free Clay credits for new users

#### Clay in Claude
**Launched:** January 26, 2026

**Five Core Use Cases:**

1. **Find ICP Contacts**
   - *"Find VP- and Director-level RevOps leaders at [company] who started in last 9 months"*

2. **Detailed Account Research**
   - *"What are [company's] top GTM priorities? Any recent executive changes?"*
   - *"Show me recent public posts from sales/product leaders mentioning AI"*

3. **Draft Contextual Outbound**
   - *"Write an email referencing [company's] recent product launches and their VP Engineering's comments on developer productivity, under 130 words"*

4. **Map Buying Centers**
   - *"Who are the key decision-makers in [company's] data infrastructure team? Show me economic buyer, technical evaluators, end users"*

5. **Multi-Thread Deals**
   - *"Find everyone at [company] involved in their data platform evaluation. I need contact info and context on what each person cares about"*

**Access:** [Claude Connectors page](https://claude.com/connectors/clay) - 500 free credits

### CRM & Data Warehouse Integrations

**Native CRM Connectors:**
- Salesforce (bi-directional sync)
- HubSpot
- **Bulk Enrichment** (Oct 2025): Enrich millions of Salesforce records at scale

**Data Warehouse:**
- Snowflake
- BigQuery
- Data warehouse connections for product usage metrics

**Website/Intent:**
- **Web Intent** (Oct 2025): Identify target accounts visiting your website
  - Track pages visited, time on site, engagement frequency
  - Open beta for Pro/Enterprise
- **Webflow** (Mar 2025): Scalable website personalization

### Conversation Intelligence

**Gong Integration** (Apr 2025):
- Turn call transcripts into automated workflows
- Extract implemented use cases from conversations
- Push to Salesforce, HubSpot, Notion, Slack, Google Sheets
- Summarize objections, next steps

### Outreach & Sales Tools

**Clay Sequencer** (Native, Sep 2025):
- Native email campaign engine
- Deliverability best practices baked in (inbox warming, account rotation, human-like pacing)
- Personalized content generation from Clay data
- Attribution tracking

**Third-Party Integrations:**
- **Apollo** (Feb 2026): Enrich data at scale, move from data to deals faster
- **HeyReach**: LinkedIn outreach automation
- **Sendoso**: Personalized direct mail at scale
- **Google Slides** (May 2025): Automated personalized presentations

### Other Notable Integrations

**HG Insights** (Jan 2025):
- Enterprise-grade technology intelligence
- Technology stack detection
- Corporate hierarchy mapping (parent-child relationships)
- Trusted by 90% of Fortune 100 Technology list

**Openmart** (Oct 2025):
- Local business lead generation
- Combined with Clay Sequencer for complete local outreach

**The Kiln Partnership** (Nov 2025):
- Large-scale data testing partnership
- Mobile phone verification methodology
- Work email verification methodology

---

## Key Workflows & Implementation Patterns

### Pattern 1: The Complete AI Outbound Funnel
1. **Find:** Use Sculptor/Claygent to identify target accounts
2. **Enrich:** Waterfall enrichment for contacts (80%+ coverage)
3. **Research:** Claygent Navigator for deep account research
4. **Qualify:** AI-powered ICP scoring
5. **Personalize:** Generate custom outreach based on research
6. **Execute:** Clay Sequencer for email campaigns
7. **Track:** Web Intent for visitor identification

### Pattern 2: CRM Hygiene at Scale
1. Import CRM data to Clay
2. Run waterfall enrichment for missing fields
3. Use Claygent to verify/update stale data
4. Research corporate hierarchy (HG Insights)
5. Push enriched data back to CRM
6. Set up Scheduling for ongoing maintenance

### Pattern 3: Signal-Based Outbound
1. Configure Custom Signals (funding, hiring, job changes)
2. Monitor with Audiences
3. Enrich signal data with company intelligence
4. Generate personalized outreach referencing specific signals
5. Execute via Sequencer within minutes of signal detection

---

## Resources & Links

### Official Clay Resources
- **Blog:** https://www.clay.com/blog
- **Clay University:** https://www.clay.com/university
- **Pricing:** https://www.clay.com/pricing
- **Sculptor:** https://www.clay.com/sculptor
- **Sequencer:** https://www.clay.com/sequencer
- **Audiences Waitlist:** https://www.clay.com/audiences

### Key Blog Posts (Nov 2024 - Feb 2025)
- Sculptor Analyst Mode (Feb 12, 2026): https://www.clay.com/blog/sculptor-analyst-mode
- Automated Slide Deck Creation (Feb 11, 2026): https://www.clay.com/blog/automated-slide-deck-creation
- Clay in Claude (Jan 26, 2026): https://www.clay.com/blog/clay-in-claude
- Social Listening Playbook (Jan 28, 2026): https://www.clay.com/blog/how-clay-uses-clay-social-listening
- $100M ARR Announcement (Dec 8, 2025): https://www.clay.com/blog/100m-arr
- Clay in ChatGPT (Dec 17, 2025): https://www.clay.com/blog/clay-in-chatgpt
- Sculpt 2025 Product Launches (Sep 17, 2025): https://www.clay.com/blog/sculpt-2025-product-launches
- Claygent Navigator (Aug 20, 2025): https://www.clay.com/blog/introducing-claygent-navigator
- Waterfall Enrichment Guide: https://www.clay.com/blog/data-waterfalls

### Community & Partner Resources
- **Clay Partner Program** (Aug 2025): For agencies and consultants
- **Clay Certifications** (Dec 2025): Credential program for Clay mastery
- **Clay Cup 2025:** Annual GTM engineering competition

---

## Strategic Takeaways

### For GTM Leaders
1. **GTM Engineering** is the new paradigm - technical/non-technical hybrid roles automating revenue workflows
2. **AI Agents** (Sculptor, Claygent) eliminate the execution bottleneck between ideas and live workflows
3. **Waterfall enrichment** provides 2-3x better data coverage at lower cost than traditional providers
4. **First-party data + AI** (Claygent Connectors) unlocks competitive advantage from your existing data

### For Operators
1. **Natural language interfaces** (Sculptor) make complex data workflows accessible to non-technical teams
2. **Native email sending** (Sequencer) with built-in deliverability reduces tool fragmentation
3. **Real-time signals** (Web Intent, Custom Signals) enable proactive rather than reactive outreach
4. **ChatGPT/Claude integrations** bring Clay's data layer into existing sales workflows

### For Technical Teams
1. **MCP connections** enable AI research across internal systems (Salesforce, Gong, data warehouses)
2. **Claygent Builder** provides proper prompt development environment with version control
3. **Claygent Navigator** handles complex web interactions traditional scraping can't reach
4. **API-first architecture** supports programmatic workflow deployment

---

*Research compiled from Clay blog posts, product announcements, and official documentation from November 2024 through February 2025.*
