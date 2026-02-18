# Sales Plugin Handbook

**The Complete Guide to Sales Productivity with Claude Cowork**

Version 1.0.0 | For Sales Reps, SDRs, Sales Managers, and Revenue Operations

---

## Table of Contents

### Part I: Foundation
1. [What the Sales Plugin Does](#part-i-what-the-sales-plugin-does)
2. [Installation and Setup](#installation-and-setup)
3. [Working Standalone vs. Supercharged](#working-standalone-vs-supercharged)
4. [The Tool Categories System](#the-tool-categories-system)

### Part II: Commands Reference
5. [/call-summary — Process Call Notes](#call-summary)
6. [/forecast — Generate Sales Forecasts](#forecast)
7. [/pipeline-review — Analyze Pipeline Health](#pipeline-review)

### Part III: Skills Reference
8. [account-research — Research Prospects](#account-research)
9. [call-prep — Prepare for Sales Calls](#call-prep)
10. [daily-briefing — Start Your Day](#daily-briefing)
11. [draft-outreach — Write Personalized Messages](#draft-outreach)
12. [competitive-intelligence — Research Competitors](#competitive-intelligence)
13. [create-an-asset — Generate Sales Assets](#create-an-asset)

### Part IV: Connected Tools
14. [MCP Integrations Overview](#mcp-integrations-overview)
15. [CRM Integration (HubSpot, Close)](#crm-integration)
16. [Conversation Intelligence (Fireflies)](#conversation-intelligence)
17. [Data Enrichment (Clay, ZoomInfo)](#data-enrichment)
18. [Communication Tools (Slack, Microsoft 365)](#communication-tools)
19. [Knowledge Management (Notion, Atlassian)](#knowledge-management)

### Part V: Day-to-Day Workflows
20. [Morning Routine](#morning-routine)
21. [Pre-Call Preparation](#pre-call-preparation)
22. [Post-Call Follow-Up](#post-call-follow-up)
23. [Weekly Pipeline Review](#weekly-pipeline-review)
24. [Monthly Forecasting](#monthly-forecasting)
25. [Prospecting and Outreach](#prospecting-and-outreach)

### Part VI: Advanced Topics
26. [Personalizing Your Setup](#personalizing-your-setup)
27. [Creating Custom Email Templates](#creating-custom-email-templates)
28. [Building Sales Playbooks](#building-sales-playbooks)
29. [Team Customization](#team-customization)

### Part VII: Extension and Customization
30. [Understanding the Plugin Architecture](#understanding-the-plugin-architecture)
31. [Adding Industry-Specific Knowledge](#adding-industry-specific-knowledge)
32. [Creating Company-Specific Workflows](#creating-company-specific-workflows)
33. [Building Custom Sales Assets](#building-custom-sales-assets)

---

## Part I: What the Sales Plugin Does

The sales plugin transforms Claude into your sales productivity partner. It handles the tedious parts of sales work — research, note-taking, data analysis, content creation — so you can focus on building relationships and closing deals.

### The Core Value Proposition

Most sales reps spend 30-40% of their time on administrative tasks that do not directly involve talking to customers. The sales plugin reclaims that time by automating:

- Prospect research before every call
- Call note processing and CRM updates
- Pipeline analysis and forecasting
- Email and message drafting
- Sales asset creation
- Competitive intelligence gathering

### What Makes This Different

Unlike traditional sales tools that force you into rigid workflows, the sales plugin is conversational. You describe what you need in plain English, and it adapts to your situation. No forms to fill out, no dropdown menus, no training manual to memorize.

**Traditional tool:**
1. Open forecast tool
2. Export pipeline CSV from CRM
3. Upload to forecast tool
4. Configure fields (opportunity name → column A, amount → column B)
5. Select forecast method
6. Set quota and timeline
7. Click generate
8. Download report

**Sales plugin:**
```
/forecast
```
Paste your deals or upload CSV. Done.

### Who This Plugin Is For

| Role | Primary Use Cases |
|------|------------------|
| **SDR / BDR** | Prospect research, outreach drafting, daily prospecting lists |
| **Account Executive** | Call prep, deal strategy, pipeline reviews, forecasting |
| **Sales Manager** | Team forecasting, pipeline inspection, deal coaching |
| **Revenue Operations** | Data analysis, process documentation, reporting automation |
| **Sales Engineer** | Technical asset creation, competitive analysis, demo prep |
| **Customer Success** | Account research, renewal preparation, expansion planning |

### The Two Operating Modes

The plugin works in two modes, and you can switch between them without any configuration:

#### Standalone Mode
You provide the information, the plugin does the work. No integrations required.

- Upload CSV files
- Paste call notes
- Describe your deals
- Share prospect names

**Best for:** Quick tasks, trying out the plugin, working with prospects before they are in your CRM, analyzing data from multiple sources.

#### Supercharged Mode
Connect your CRM, email, calendar, and other tools. The plugin pulls data automatically.

- Live pipeline data from your CRM
- Call transcripts from conversation intelligence tools
- Contact information from enrichment services
- Email threads and calendar events

**Best for:** Daily workflows, pipeline management, comprehensive account research, automated data updates.

---

## Installation and Setup

### Installing the Plugin

**Cowork (recommended):** Open **Plugin Settings** in the Cowork desktop app, find **Sales**, and click **Install**. The plugin activates immediately — no CLI required.

**Claude Code CLI (alternative):** If you are using Claude Code in the terminal rather than Cowork, install via:

```bash
claude plugins add knowledge-work-plugins/sales
```

> **Note:** All standard Cowork plugins, including Sales, are available from Plugin Settings with a single click. The CLI command above is only needed for Claude Code terminal users.

**Verification:**
Type `/help` and confirm you see these commands listed:
- `/call-summary`
- `/forecast`
- `/pipeline-review`

### Initial Configuration (Optional)

While the plugin works out of the box, personalizing it saves time on every interaction. Create a settings file at `sales/.claude/settings.local.json`:

```json
{
  "name": "Sarah Chen",
  "title": "Account Executive",
  "company": "Acme Analytics",
  "quota": {
    "annual": 1200000,
    "quarterly": 300000,
    "monthly": 100000
  },
  "product": {
    "name": "Acme Analytics Platform",
    "value_props": [
      "Real-time data pipeline for analytics teams",
      "50% faster query performance vs. legacy warehouses",
      "Zero-copy data sharing across business units"
    ],
    "competitors": [
      "Snowflake",
      "Databricks",
      "BigQuery"
    ]
  },
  "territory": {
    "industries": ["SaaS", "E-commerce", "FinTech"],
    "company_size": "100-1000 employees",
    "regions": ["West Coast", "Remote"]
  }
}
```

These settings get referenced automatically when you use commands and skills. The plugin asks you for this information the first time you use features that need it, so you do not have to create the file up front — but it is faster if you do.

### Connecting Your First Tool

MCP integrations are optional, but they unlock the plugin's full power. Start with your CRM since it provides the most value.

**Example: Connecting HubSpot**

HubSpot is pre-configured in the plugin. When you first reference CRM data, you will see a connection prompt. Click through the OAuth flow to authorize access. That is it — the connection persists across sessions.

**Example: Connecting Fireflies**

Same OAuth flow. When you run `/call-summary` and the plugin detects Fireflies is available, it offers to pull transcripts automatically instead of requiring you to paste them.

**Connecting via .mcp.json** (advanced)

If you use a CRM or other tool not pre-configured, add it to your personal `.mcp.json`:

```json
{
  "mcpServers": {
    "salesforce": {
      "type": "sse",
      "url": "https://mcp.salesforce.com/sse"
    }
  }
}
```

Place this file in your Cowork configuration directory. The next time you start a session, Salesforce appears as an available integration.

---

## Working Standalone vs. Supercharged

Every command and skill in the plugin works without any integrations. Here is what that looks like in practice.

### Example: Pipeline Review

**Standalone:**
```
/pipeline-review
```

You upload a CSV export from your CRM (opportunity name, amount, stage, close date). The plugin analyzes it and gives you prioritization, risk flags, and action items.

**Supercharged (with CRM connected):**
```
/pipeline-review
```

The plugin pulls your pipeline automatically, analyzes it, and can write updates back to the CRM (updating close dates, adding tasks, changing stages).

Both work. The supercharged version saves you the export step and enables write-back.

### Example: Call Prep

**Standalone:**
```
Prep me for my call with Acme Corp tomorrow. It's a discovery call
with their VP Engineering and CTO. They're evaluating us vs Snowflake
for their data warehouse consolidation project.
```

The plugin researches Acme Corp via web search, generates a prep brief with suggested questions and talking points.

**Supercharged (with CRM + Email + Calendar connected):**
```
Prep me for my Acme Corp call
```

The plugin finds the meeting on your calendar, pulls the attendees, searches your CRM for account history, scans recent email threads, and generates a comprehensive prep brief with full context.

### What Each Integration Adds

| Integration Type | Standalone | What It Adds When Connected |
|-----------------|------------|----------------------------|
| **CRM** | Upload CSV, paste deal info | Auto-pull pipeline, write back updates, historical win data |
| **Conversation Intelligence** | Paste transcript | Auto-pull recordings, key moment extraction, sentiment analysis |
| **Email** | Copy from email client | Auto-scan threads, draft in inbox, track sent/replied status |
| **Calendar** | Tell me about your meetings | Auto-pull today's schedule, attendee context, meeting history |
| **Enrichment** | Web search only | Verified contact info, org charts, tech stack, intent signals |
| **Chat** | Manual input | Internal discussions, colleague intel, team context |
| **Knowledge Base** | Tell me what you know | Pull from Notion/Confluence docs, battlecards, playbooks |

### When to Stay Standalone

Standalone mode makes sense when:

- You are exploring a new prospect not yet in your CRM
- You are analyzing data from multiple sources (partner deals, Excel models, external data)
- You are testing an idea quickly before committing to a process
- You are working on a personal device without company tool access

### When to Go Supercharged

Supercharged mode shines for:

- Daily workflows (briefings, call prep, pipeline reviews)
- Anything that needs to update your CRM
- Research requiring verified contact information
- Tasks involving team collaboration and shared context

---

## The Tool Categories System

The plugin uses a placeholder system to stay flexible across different tech stacks. When you read the plugin's documentation or command files, you will see references like `~~CRM` or `~~conversation intelligence`.

These placeholders represent categories, not specific tools. Your `~~CRM` might be HubSpot; someone else's might be Salesforce.

### Pre-Configured Categories

| Category | Placeholder | Included Servers | Alternatives |
|----------|-------------|-----------------|--------------|
| Calendar | `~~calendar` | Microsoft 365 | Google Calendar |
| Chat | `~~chat` | Slack | Microsoft Teams |
| CRM | `~~CRM` | HubSpot, Close | Salesforce, Pipedrive, Copper |
| Data Enrichment | `~~data enrichment` | Clay, ZoomInfo | Apollo, Clearbit, Lusha |
| Email | `~~email` | Microsoft 365 | Gmail |
| Knowledge Base | `~~knowledge base` | Notion | Confluence, Guru |
| Conversation Intelligence | `~~conversation intelligence` | Fireflies | Gong, Chorus, Otter.ai |
| Project Tracker | `~~project tracker` | Atlassian (Jira/Confluence) | Linear, Asana |

The plugin ships with HubSpot, Close, Clay, ZoomInfo, Fireflies, Slack, Microsoft 365, Notion, and Atlassian pre-configured. If you use a different tool in any category, you can add it (see Part VII).

### How Placeholders Work in Practice

When a command or skill mentions `~~CRM`, Claude automatically substitutes whichever CRM you have connected. If you have HubSpot connected, `~~CRM` becomes "HubSpot." If you have Salesforce, it becomes "Salesforce."

You never see the placeholders yourself — they are an internal mechanism that keeps the plugin tool-agnostic.

---

## Part II: Commands Reference

Commands are explicit actions you invoke with a slash. They are structured workflows designed for specific tasks.

---

## /call-summary

Process call notes or transcripts to extract action items, draft follow-up communications, and update CRM records.

### When to Use

- After any customer call (discovery, demo, negotiation, check-in)
- To process messy notes into structured summaries
- When you need to draft a follow-up email
- When you need to create CRM tasks and log activities

### How It Works

```
/call-summary
```

Then provide your input via one of these methods:

**Option 1: Paste notes**
Just dump your rough notes. Bullet points, stream of consciousness, whatever you captured during the call.

**Option 2: Paste transcript**
Full verbatim transcript from Zoom, Teams, or conversation intelligence tools.

**Option 3: Describe the call**
"Had a discovery call with Acme Corp. Met with VP Eng and CTO. Main concern is integration timeline. They are evaluating us vs Competitor X."

**Option 4 (Supercharged): Pull from Fireflies/Gong**
If conversation intelligence is connected, the plugin searches for the call and pulls the transcript automatically.

### What You Get

#### Internal Summary
```markdown
## Call Summary: Acme Corp — January 28, 2026

**Attendees:** Sarah Chen (VP Engineering), Mike Wu (CTO)
**Call Type:** Discovery
**Duration:** 45 minutes

### Key Discussion Points
1. Current data stack pain — migrating from legacy Oracle warehouse
2. Integration requirements — must work with existing Kafka streams
3. Timeline — want to complete migration by Q3 2026
4. Budget authority — both attendees can approve up to $500K

### Customer Priorities
- Minimize migration downtime
- Maintain existing ETL processes during transition
- Training for data engineering team

### Objections / Concerns Raised
- Integration complexity — how long will Kafka connector setup take?
- Cost vs Snowflake — requested detailed pricing comparison

### Competitive Intel
- Currently evaluating Snowflake and Databricks
- Snowflake rep proposed 6-month timeline, they think it is too long

### Action Items
| Owner | Action | Due |
|-------|--------|-----|
| Sarah (us) | Send Kafka integration guide and sample code | Jan 30 |
| Sarah (us) | Provide detailed pricing vs Snowflake | Jan 30 |
| Mike (customer) | Share current ETL workflow documentation | Feb 2 |
| Sarah C. (customer) | Intro to head of data engineering | Feb 5 |

### Next Steps
- Technical deep-dive with data engineering team — Feb 8, 2pm
- They will share sample data for POC scoping

### Deal Impact
- Strong fit, high interest
- Likely to move to POC stage after technical review
- Timeline compression opportunity — they need a decision by March
```

#### Customer-Facing Follow-Up Email
```
Subject: Acme migration roadmap + next steps

Hi Sarah and Mike,

Thanks for the detailed walkthrough of your data stack today. The 
Oracle-to-modern-warehouse migration is something we have helped 
a dozen companies navigate, including a recent customer with a 
similar Kafka integration requirement.

Based on our discussion, I will send over:
- The Kafka connector integration guide with sample code
- Detailed pricing comparison vs Snowflake
- Case study from a similar migration (Oracle → our platform, 
  completed in 8 weeks)

From your side:
- Mike, you mentioned sharing current ETL workflow docs by Feb 2
- Sarah, intro to your head of data engineering by Feb 5

Let's plan for the technical deep-dive on Feb 8 at 2pm. I will 
bring our solutions architect to walk through the migration plan 
and answer integration questions.

Looking forward to it,
Sarah Chen
Acme Analytics
```

### CRM Updates (if connected)

If CRM is connected, the plugin offers to:
- Log this call as an activity on the opportunity
- Create tasks for each action item with due dates and owners
- Update the opportunity stage (e.g., from "Discovery" to "Technical Evaluation")
- Update the "Next Steps" field
- Attach the summary as a note

You review and approve before anything is written.

### Email Style

The plugin follows these rules for customer emails:
- Concise but informative
- No markdown formatting (no bold, italics, or special characters that do not render in all email clients)
- Short paragraphs (2-3 sentences)
- Plain lists (dashes or numbers, no fancy formatting)

### Tips for Better Output

1. **Name the attendees.** "VP Engineering and CTO" is okay. "Sarah Chen (VP Eng) and Mike Wu (CTO)" is better.
2. **Include specific details.** "They mentioned a Q3 deadline" and "They are comparing us to Snowflake" help the plugin capture context.
3. **Flag what was important.** "The big concern was integration complexity" tells the plugin what to emphasize.
4. **Mention the deal stage.** Helps tailor follow-up tone and next steps.

---

## /forecast

Generate a weighted sales forecast with risk analysis, scenario planning, and gap-to-quota recommendations.

### When to Use

- Weekly or monthly forecast calls
- Pipeline planning with your manager
- Territory planning and goal setting
- Analyzing deal coverage and risk

### How It Works

```
/forecast
```

Then provide your pipeline data and targets:

**Option 1: Upload CSV**
Export your pipeline from your CRM. Minimum required fields:
- Deal/Opportunity name
- Amount
- Stage
- Close date

Helpful additional fields:
- Owner (for team forecasts)
- Last activity date
- Created date
- Account name

**Option 2: Paste deals**
```
Acme Corp - $50K - Negotiation - closes Jan 31
TechStart - $25K - Demo scheduled - closes Feb 15
BigCo - $100K - Discovery - closes Mar 30
```

**Option 3: Describe your pipeline**
"I have 8 deals totaling $400K. Two in negotiation ($120K), three in evaluation ($180K), three in discovery ($100K)."

**Option 4 (Supercharged): Pull from CRM**
If CRM is connected, the plugin pulls your pipeline automatically.

**Then provide targets:**
- **Quota**: Your number for the period (e.g., "$500K this quarter")
- **Timeline**: When the period ends (e.g., "Q1 ends March 31")
- **Already closed**: How much you have already booked this period

### What You Get

```markdown
# Sales Forecast: Q1 2026

**Generated:** January 28, 2026
**Data Source:** HubSpot (12 opportunities)

---

## Summary

| Metric | Value |
|--------|-------|
| **Quota** | $500,000 |
| **Closed to Date** | $125,000 (25% of quota) |
| **Open Pipeline** | $620,000 |
| **Weighted Forecast** | $381,000 |
| **Gap to Quota** | $119,000 |
| **Coverage Ratio** | 4.96x |

---

## Forecast Scenarios

| Scenario | Amount | % of Quota | Assumptions |
|----------|--------|------------|-------------|
| **Best Case** | $540,000 | 108% | All deals close as scheduled |
| **Likely Case** | $381,000 | 76% | Stage-weighted probabilities |
| **Worst Case** | $290,000 | 58% | Only high-confidence deals |

---

## Pipeline by Stage

| Stage | # Deals | Total Value | Probability | Weighted Value |
|-------|---------|-------------|-------------|----------------|
| Negotiation | 2 | $170,000 | 80% | $136,000 |
| Proposal | 3 | $180,000 | 60% | $108,000 |
| Demo/Evaluation | 4 | $170,000 | 40% | $68,000 |
| Discovery | 3 | $100,000 | 20% | $20,000 |
| **Total** | 12 | $620,000 | — | $332,000 |

---

## Commit vs. Upside

### Commit (High Confidence) — $290K
Deals you would stake your forecast on:

| Deal | Amount | Stage | Close Date | Why Commit |
|------|--------|-------|------------|------------|
| Acme Corp | $120K | Negotiation | Jan 31 | Verbal approval, contract in legal review |
| DataFlow Inc | $50K | Negotiation | Feb 15 | Budget approved, final stakeholder sign-off scheduled |
| Analytics Co | $70K | Proposal | Feb 28 | Champion pushing hard, technical win confirmed |
| TechCorp | $50K | Proposal | Mar 15 | Existing customer expansion, straightforward renewal |

### Upside (Lower Confidence) — $330K
Deals that could close but have risk:

| Deal | Amount | Stage | Close Date | Risk Factor |
|------|--------|-------|------------|-------------|
| BigCo | $100K | Discovery | Mar 30 | Still early, close date may slip |
| StartupX | $80K | Demo | Feb 20 | Budget not confirmed |
| SaaS Inc | $90K | Proposal | Mar 10 | Multi-threaded but no clear champion |
| MidMarket LLC | $60K | Demo | Mar 25 | Long sales cycle, may push to Q2 |

---

## Risk Flags

| Deal | Amount | Risk | Recommendation |
|------|--------|------|----------------|
| BigCo | $100K | Close date in 60 days, still in discovery | Unrealistic timeline — push to Q2 or accelerate |
| OldDeal Inc | $40K | No activity in 21 days | Re-engage immediately or downgrade |
| LateAdd Co | $30K | Added 3 days ago, closes this month | Optimistic — verify timing |

---

## Gap Analysis

**To hit quota, you need:** $119K more beyond current commit

**Options to close the gap:**

1. **Accelerate Analytics Co** ($70K) — Currently in Proposal, strong champion. If you close by Feb 15 instead of Feb 28, you are at 87% of quota. Action: Push for early signature with discount incentive.

2. **Convert StartupX** ($80K) — In Demo stage, budget not confirmed. Get budget approval this week to move to Proposal. Action: Schedule CFO call.

3. **Generate new pipeline** — You need $50K in new opportunities at 3x coverage ($150K pipeline) to feel safe. Action: Focus prospecting on warm leads from last quarter.

---

## Recommendations

1. [ ] Push Analytics Co for early close — offer 5% discount for signature by Feb 15
2. [ ] Re-engage OldDeal Inc — last activity was Jan 7, deal going stale
3. [ ] Get budget confirmation from StartupX — schedule CFO intro this week
4. [ ] Push BigCo close date to Q2 — current timeline is not realistic
5. [ ] Add $150K in new pipeline — prioritize warm inbound leads
```

### Stage Probabilities

The plugin uses these default probabilities unless you specify otherwise:

| Stage | Default Probability |
|-------|---------------------|
| Closed Won | 100% |
| Negotiation / Contract | 80% |
| Proposal / Quote | 60% |
| Evaluation / Demo | 40% |
| Discovery / Qualification | 20% |
| Prospecting / Lead | 10% |

If your stages are different, just tell the plugin: "We use 'Technical Review' as a stage between Demo and Proposal, probability 50%."

### Coverage Guidelines

Pipeline coverage = (Open Pipeline) / (Remaining Quota)

| Coverage | Health |
|----------|--------|
| 5x+ | Very healthy — likely to exceed quota |
| 3-4x | Healthy — on track |
| 2-3x | Risky — need to accelerate deals or add pipeline |
| <2x | Critical — significant gap, urgent action needed |

### Tips for Accurate Forecasts

1. **Update close dates religiously.** Stale dates kill accuracy. If a deal is not closing this month, push the date.
2. **Be honest about commit.** Only commit deals you would bet on. Upside is for everything else.
3. **Track activity.** Deals with no activity in 14+ days are higher risk than their stage suggests.
4. **Use historical win rates.** If your actual win rate at Proposal stage is 45%, not 60%, adjust the probabilities.

---

## /pipeline-review

Analyze pipeline health, flag risks, prioritize deals, and get a weekly action plan.

### When to Use

- Weekly pipeline hygiene
- Before forecast calls
- When deals are going stale
- When you need to prioritize where to spend time

### How It Works

```
/pipeline-review
```

Provide your pipeline the same way as `/forecast` — upload CSV, paste deals, describe your territory, or pull automatically from CRM.

### What You Get

```markdown
# Pipeline Review: January 28, 2026

**Data Source:** HubSpot (18 opportunities)
**Total Pipeline Value:** $870,000

---

## Pipeline Health Score: 72/100

| Dimension | Score | Issue |
|-----------|-------|-------|
| **Stage Progression** | 18/25 | 4 deals stuck in same stage 30+ days |
| **Activity Recency** | 16/25 | 5 deals with no activity in 14+ days |
| **Close Date Accuracy** | 20/25 | 3 deals with close date in past |
| **Contact Coverage** | 18/25 | 6 deals single-threaded |

---

## Priority Actions This Week

### 1. Re-engage Acme Corp ($120K)
**Why:** Large deal, no activity in 18 days, close date is Feb 15
**Action:** Email VP Engineering to confirm technical review timeline
**Impact:** $120K at risk if this goes silent

### 2. Multi-thread DataCo ($90K)
**Why:** Only contact is mid-level manager, no executive sponsor
**Action:** Ask for intro to VP or C-level stakeholder
**Impact:** Reduce single-point-of-failure risk

### 3. Clean up 3 past-close-date deals
**Why:** Close dates in the past distort pipeline and forecasts
**Action:** Update close dates or mark closed-lost
**Impact:** More accurate pipeline reporting

---

## Deal Prioritization Matrix

### Close This Week (Focus Time Here)
| Deal | Amount | Stage | Close Date | Next Action |
|------|--------|-------|------------|-------------|
| TechStart | $50K | Negotiation | Jan 31 | Send final contract for signature |
| MidCo | $30K | Proposal | Feb 2 | Follow up on pricing approval |

### Close This Month (Keep Warm)
| Deal | Amount | Stage | Close Date | Status |
|------|--------|-------|------------|--------|
| Acme Corp | $120K | Proposal | Feb 15 | Awaiting technical review completion |
| DataFlow | $70K | Demo | Feb 20 | POC in progress |
| BigCo | $100K | Discovery | Feb 28 | Meeting scheduled Feb 5 |

### Nurture (Check-in Periodically)
| Deal | Amount | Stage | Close Date | Status |
|------|--------|-------|------------|--------|
| LongSales Inc | $200K | Discovery | Apr 15 | Multi-month eval cycle, normal pace |
| Partner Deal | $80K | Proposal | Mar 30 | Waiting on partner approval |

---

## Risk Flags

### Stale Deals (No Activity 14+ Days)
| Deal | Amount | Last Activity | Days Silent | Recommendation |
|------|--------|---------------|-------------|----------------|
| Acme Corp | $120K | Jan 10 | 18 | **URGENT** — Re-engage today |
| OldCo | $60K | Jan 5 | 23 | Qualify out or re-engage |
| QuietDeal | $40K | Dec 20 | 39 | Mark closed-lost, dead deal |

### Stuck Deals (Same Stage 30+ Days)
| Deal | Amount | Stage | Days in Stage | Recommendation |
|------|--------|-------|---------------|----------------|
| StuckCo | $90K | Demo | 42 | Push to Proposal or qualify out |
| SlowMove | $70K | Discovery | 35 | Multi-thread, add urgency |

### Past Close Date
| Deal | Amount | Close Date | Days Overdue | Recommendation |
|------|--------|------------|--------------|----------------|
| LateDeal | $50K | Jan 15 | 13 | Update to Feb 28 or close-lost |
| MissedOne | $30K | Jan 10 | 18 | Update to Mar 15 or close-lost |

### Single-Threaded (Only One Contact)
| Deal | Amount | Contact | Risk | Recommendation |
|------|--------|---------|------|----------------|
| DataCo | $90K | Mike (PM) | Champion leaves = deal dies | Get intro to VP or exec sponsor |
| OnePerson | $60K | Sarah (Director) | No decision authority | Identify economic buyer |

---

## Hygiene Issues

| Issue | Count | Deals | Action |
|-------|-------|-------|--------|
| Missing close date | 2 | StartupX, NewDeal | Add realistic close dates |
| Missing amount | 1 | TBD-Deal | Estimate deal size or qualify |
| Missing next step | 4 | [List] | Define clear next action for each |

---

## Pipeline Shape

### By Stage
| Stage | # Deals | Value | % of Pipeline |
|-------|---------|-------|---------------|
| Negotiation | 3 | $200K | 23% |
| Proposal | 5 | $320K | 37% |
| Demo | 6 | $240K | 28% |
| Discovery | 4 | $110K | 13% |

### By Close Month
| Month | # Deals | Value |
|-------|---------|-------|
| January | 2 | $80K |
| February | 7 | $480K |
| March | 6 | $230K |
| April+ | 3 | $80K |

### By Deal Size
| Size | # Deals | Value |
|------|---------|-------|
| $100K+ | 3 | $410K |
| $50K-100K | 7 | $480K |
| $25K-50K | 5 | $180K |
| <$25K | 3 | $60K |

---

## Recommendations

### This Week
1. [ ] Re-engage Acme Corp — urgent, 18 days silent
2. [ ] Get exec intro at DataCo — reduce single-thread risk
3. [ ] Update 3 past close dates — clean up reporting
4. [ ] Add next steps to 4 deals missing them

### This Month
1. [ ] Multi-thread all deals over $75K
2. [ ] Qualify out or re-engage deals silent 30+ days
3. [ ] Add $200K in new pipeline to maintain 3x coverage

---

## Deals to Consider Removing

| Deal | Amount | Reason | Recommendation |
|------|--------|--------|----------------|
| QuietDeal | $40K | 39 days silent, no response to 3 emails | Mark closed-lost |
| OldLead | $20K | In discovery for 90 days, no progress | Qualify out |
```

### Prioritization Framework

The plugin ranks deals using this framework:

| Factor | Weight | What It Measures |
|--------|--------|-----------------|
| **Close Date** | 30% | Deals closing soonest get priority |
| **Deal Size** | 25% | Bigger deals = more focus |
| **Stage** | 20% | Later stage = more focus |
| **Activity** | 15% | Active deals get prioritized over stale ones |
| **Risk** | 10% | Lower risk = safer bet |

You can override: "Focus on big deals over close dates" or "I need quick wins, prioritize close dates."

### Tips for Pipeline Health

1. **Review weekly.** Pipeline health decays fast. Weekly reviews catch issues before they become problems.
2. **Kill dead deals.** Stale opportunities inflate your pipeline and distort forecasts. Be ruthless.
3. **Multi-thread everything over $50K.** If your one contact goes dark, you need a backup.
4. **Close dates should be real.** A close date is when you expect signature, not when you hope for it.
5. **Track activity as a leading indicator.** Deals with recent activity close at higher rates than their stage suggests.

---

## Part III: Skills Reference

Skills are domain knowledge that Claude loads automatically when the conversation is relevant. You do not invoke them with a slash — they activate in the background.

---

## account-research

Research any company or person and get actionable sales intelligence.

### When It Triggers

When you say things like:
- "Research Acme Corp"
- "Look up the CTO at Stripe"
- "Tell me about acme.com"
- "Who is Sarah Chen at TechCorp?"
- "Intel on [company] before my call"

### What It Does

The skill researches the company or person using:
- **Web search** (always) — company overview, recent news, funding, hiring signals, leadership
- **Enrichment tools** (if connected) — verified emails, org charts, tech stack, detailed firmographics
- **CRM** (if connected) — prior relationship history, past opportunities, existing contacts

### Output Format

```markdown
# Research: Acme Corp

**Generated:** January 28, 2026
**Sources:** Web Search + ZoomInfo + HubSpot

---

## Quick Take

Acme Corp is a 300-person SaaS company selling project management
software to marketing teams. Recently raised $50M Series C and is
hiring aggressively in engineering and sales. Strong fit for our
data analytics platform — they likely need better reporting as they
scale. Best approach: lead with ROI story from similar customer.

---

## Company Profile

| Field | Value |
|-------|-------|
| **Company** | Acme Corp |
| **Website** | acme.com |
| **Industry** | SaaS / Project Management |
| **Size** | 300 employees |
| **Headquarters** | San Francisco, CA |
| **Founded** | 2018 |
| **Funding** | Series C, $50M (Dec 2025) |
| **Revenue** | $30-50M ARR (estimated) |

### What They Do
Cloud-based project management platform for marketing teams. Customers
are mid-market companies (100-1000 employees) in tech, e-commerce, and
professional services. Differentiation is marketing-specific workflows
vs general tools like Asana.

### Recent News
- **Series C funding ($50M)** — Dec 15, 2025 — Led by Sequoia. Plan
  to expand into product management vertical. Growth signal.
- **New VP Engineering hire** — Jan 10, 2026 — Hired from Snowflake.
  Likely bringing enterprise mindset, data infrastructure investment.
- **Customer milestone** — Jan 20, 2026 — Announced 1,000 customers,
  up from 600 in June 2025. Rapid growth = scaling pains.

### Hiring Signals
- 15 open engineering roles (5 data engineers, 3 backend, 7 full-stack)
- 8 sales roles (6 AEs, 2 SEs)
- 1 Head of Analytics role (posted Dec 2025)
- **Growth indicator:** Hiring velocity suggests 40-50% team expansion

---

## Key People

### Sarah Chen — VP of Engineering
| Field | Detail |
|-------|--------|
| **LinkedIn** | linkedin.com/in/sarahchen |
| **Background** | 8 years at Google (Tech Lead), 3 years at Snowflake (Engineering Manager) |
| **Tenure** | Joined Acme Corp Jan 2026 (recent hire) |
| **Email** | sarah.chen@acme.com (verified via ZoomInfo) |

**Talking Points:**
- Coming from Snowflake, understands data infrastructure needs
- Likely tasked with scaling engineering org (hiring 15 engineers)
- Google background = familiarity with analytics-driven culture

### Mike Rodriguez — CTO
| Field | Detail |
|-------|--------|
| **LinkedIn** | linkedin.com/in/mikerodriguez |
| **Background** | Founded Acme in 2018, technical co-founder |
| **Tenure** | 8 years |
| **Email** | mike@acme.com (verified) |

**Talking Points:**
- Founder CTO = cares about product velocity and tech debt
- Recent blog post on "scaling engineering teams" — likely facing growth challenges
- Active on Twitter discussing data observability — potential pain point

---

## Tech Stack (via ZoomInfo)

| Category | Tools |
|----------|-------|
| **Cloud** | AWS |
| **Data** | PostgreSQL, Redshift |
| **Analytics** | Segment, Amplitude |
| **CRM** | Salesforce |
| **Monitoring** | Datadog, Sentry |

**Integration Opportunity:** Already using Redshift, likely hitting cost/performance issues as they scale. Our platform integrates natively with Redshift and offers better price/performance.

---

## Prior Relationship (via HubSpot)

| Field | Detail |
|-------|-------|
| **Status** | Prior prospect (2024) |
| **Last Contact** | June 2024 |
| **Previous Opportunity** | Lost to Snowflake |
| **Known Contacts** | Mike Rodriguez (CTO), Lisa Park (former VP Eng, left company) |

**History:** Evaluated us in mid-2024 alongside Snowflake and Databricks.
Chose Snowflake. Lisa Park (former VP Eng) was our champion but left in
Nov 2024. Mike Rodriguez cited "maturity and ecosystem" as reasons for
choosing Snowflake. New VP Eng hire (Sarah from Snowflake) could be
re-entry opportunity.

---

## Qualification Signals

### Positive Signals
- ✅ Rapid growth (600 to 1,000 customers in 6 months) = scaling challenges
- ✅ Hired Head of Analytics = investing in data capability
- ✅ Series C funding = budget available
- ✅ New VP Eng from Snowflake = understands modern data stack
- ✅ Hiring 5 data engineers = data infrastructure priority

### Potential Concerns
- ⚠️ Already using Redshift — switching cost could be barrier
- ⚠️ Lost to Snowflake in 2024 — need new angle or pain point
- ⚠️ New VP Eng just started — may wait to settle before new tools

### Unknown (Ask in Discovery)
- ❓ What pain points led them to hire Head of Analytics?
- ❓ Are they happy with current Redshift setup or hitting limits?
- ❓ What changed since 2024 evaluation?

---

## Recommended Approach

**Best Entry Point:** Sarah Chen (new VP Eng from Snowflake)

**Opening Hook:** Congrats on the new role + growth milestone (1,000 customers).
With 5 data engineer hires, seems like scaling data infrastructure is a priority.

**Discovery Questions:**
1. With growth from 600 to 1,000 customers, what data challenges have surfaced?
2. What led to hiring a Head of Analytics now?
3. How is the current Redshift setup handling the growth?
4. What would better analytics infrastructure unlock for the product team?

**Differentiation vs 2024:**
- Emphasize improvements since 2024 (performance, ecosystem integrations)
- Position around cost efficiency vs Snowflake (they are post-Series C, budget-conscious)
- Leverage Sarah's Snowflake background — she knows where it excels and where it is expensive

---

## Sources
- acme.com
- TechCrunch: Acme Corp raises $50M Series C
- LinkedIn profiles (Sarah Chen, Mike Rodriguez)
- ZoomInfo company profile
- HubSpot CRM (prior opportunity history)
```

### When to Use

- **Before first outreach** — research the prospect before crafting your message
- **Before calls** — get context on who you are talking to
- **Competitor mentions** — "Tell me about [competitor] before I respond to this RFP"
- **Account planning** — deep research for strategic accounts

### Tips for Better Research

1. **Include the domain:** "Research acme.com" is more precise than "Research Acme"
2. **Specify the person:** "Look up Jane Smith, VP Sales at Acme"
3. **State your goal:** "Research Stripe before my demo call"
4. **Ask for specifics:** "What is their tech stack?" to drill deeper after initial research

---

## call-prep

Prepare for any sales call with account context, attendee research, and suggested agenda.

### When It Triggers

When you say things like:
- "Prep me for my call with Acme Corp"
- "I'm meeting with TechStart tomorrow, prep me"
- "Call prep for my discovery call with BigCo"
- "Get me ready for my demo with DataFlow"

### What It Does

The skill gathers context from:
- **Web search** (always) — recent news, funding, leadership changes
- **CRM** (if connected) — account history, contacts, opportunities, activities
- **Email** (if connected) — recent threads, open questions, commitments
- **Chat** (if connected) — internal discussions, colleague insights
- **Calendar** (if connected) — auto-find meeting, pull attendees
- **Transcripts** (if connected) — prior call recordings, key moments

Then generates a comprehensive prep brief.

### Output Format

```markdown
# Call Prep: Acme Corp

**Meeting:** Discovery Call — January 29, 2026, 2:00pm PT
**Attendees:** Sarah Chen (VP Engineering), Mike Rodriguez (CTO)
**Your Goal:** Qualify for POC, understand data infrastructure pain

---

## Account Snapshot

| Field | Value |
|-------|-------|
| **Company** | Acme Corp |
| **Industry** | SaaS / Project Management |
| **Size** | 300 employees, $30-50M ARR |
| **Status** | Re-engagement (lost to Snowflake in 2024) |
| **Last Touch** | June 2024 |

---

## Who You're Meeting

### Sarah Chen — VP of Engineering
- **Background:** 8 years at Google, 3 years at Snowflake (Eng Manager)
- **LinkedIn:** linkedin.com/in/sarahchen
- **Role in Deal:** Likely primary decision maker for data infrastructure
- **Last Interaction:** None (she is new to Acme, joined Jan 2026)
- **Talking Point:** Congrats on the new role — coming from Snowflake,
  you understand modern data stacks well

### Mike Rodriguez — CTO (Founder)
- **Background:** Founded Acme in 2018, technical co-founder
- **LinkedIn:** linkedin.com/in/mikerodriguez
- **Role in Deal:** Final approver, product/architecture focus
- **Last Interaction:** June 2024 evaluation (we lost to Snowflake)
- **Talking Point:** Reference the growth since we last spoke (600 to 1,000
  customers) — what new challenges has that created?

---

## Context & History

**What's happened so far:**
- Last evaluated us in June 2024 alongside Snowflake and Databricks
- Chose Snowflake — Mike cited "maturity and ecosystem"
- Our champion (Lisa Park, former VP Eng) left in Nov 2024
- Sarah Chen hired as new VP Eng in Jan 2026 from Snowflake

**Recent news about Acme:**
- **Series C funding ($50M)** — Dec 2025 — Expansion plans, budget available
- **Customer growth** — 600 to 1,000 customers in 6 months — Scaling fast
- **Aggressive hiring** — 15 engineering roles, 5 data engineers, 1 Head of Analytics

**Why now:**
- Growth is outpacing infrastructure (signal: hiring data engineers + Head of Analytics)
- New VP Eng = fresh evaluation window
- Post-funding = budget and strategic investment phase

---

## Suggested Agenda

1. **Open (5 min)** — Congrats on Series C and growth to 1,000 customers.
   Reference that we spoke in 2024 and would love to reconnect given
   the rapid growth.

2. **Discovery: Scaling Challenges (15 min)**
   - What data challenges surfaced as you scaled from 600 to 1,000 customers?
   - What led to hiring a Head of Analytics now?
   - How is your current data stack (Redshift) handling the growth?

3. **Discovery: Team and Priorities (10 min)**
   - Sarah, what are your top priorities as you ramp up?
   - What would better analytics infrastructure unlock for product dev?
   - What is the timeline for evaluating new tools?

4. **Value Overview (10 min)**
   - Share brief overview of what we have shipped since 2024
   - Emphasize cost efficiency vs Snowflake (relevant post-funding)
   - Show example: similar SaaS company reduced costs 40% migrating from Snowflake

5. **Next Steps (5 min)**
   - Propose technical deep-dive with data engineering team
   - Offer to run cost comparison analysis (current Redshift + Snowflake quote vs us)

---

## Discovery Questions

### Current State
1. Walk me through your current data infrastructure. What works well? What is painful?
2. How is Redshift handling the increased load from customer growth?
3. What data sources are you pulling from? Any integration challenges?

### Pain Points & Priorities
4. What led to hiring a Head of Analytics right now?
5. What would better data infrastructure enable that you cannot do today?
6. Are there specific product features blocked by data limitations?

### Decision Process
7. Who else should be involved in evaluating data infrastructure changes?
8. What is your timeline for making a decision?
9. What criteria matter most? (Cost, performance, ease of use, ecosystem, support?)

### Competitive Context
10. You chose Snowflake in 2024 — how has that been working?
11. Are you evaluating alternatives or looking to optimize what you have?

---

## Potential Objections

| Objection | Suggested Response |
|-----------|-------------------|
| "We already use Snowflake" | "Totally understand. A lot of our customers came from Snowflake when they hit cost or performance limits. Happy to share what others have seen. What is working well? What could be better?" |
| "Too busy to evaluate right now" | "Makes sense with 15 eng hires ramping. We can keep it lightweight — run a cost analysis async, then one technical review call. Low time investment to see if there is opportunity." |
| "Not sure we want to migrate" | "Migration can be a non-starter, agreed. We have a phased approach where you can run both systems in parallel and migrate workload by workload. Zero downtime." |
| "Why should we consider you vs Snowflake?" | "Great question. Main differentiators: 40% lower cost for similar performance, faster query speed on large datasets, simpler pricing model. Happy to run a bake-off with real data." |

---

## Internal Notes

(From Slack search: #sales-team channel, Jan 15)
- Account Executive (Tom): "Acme Corp back in play — new VP Eng from Snowflake, might be re-eval window"
- Solutions Engineer (Lisa): "I talked to their Head of Analytics last week at a conference. She mentioned Redshift costs are getting out of hand."

---

## After the Call

Run `/call-summary` to:
- Extract action items
- Update HubSpot
- Draft follow-up email
```

### Tips for Better Prep

1. **Provide context up front:** "This is a re-engagement after we lost to Snowflake in 2024"
2. **Name the attendees:** Even if you just know titles, share them
3. **State your goal:** "I want to qualify for a POC" or "I need to get budget approval"
4. **Share concerns:** "They mentioned integration complexity last time"

---

## daily-briefing

Start your day with a prioritized sales briefing.

### When It Triggers

When you say:
- "Morning briefing"
- "Daily brief"
- "What's on my plate today?"
- "Prep my day"
- "Start my day"

### What It Does

The skill pulls from:
- **Calendar** (if connected) — today's meetings
- **CRM** (if connected) — pipeline alerts, tasks, deals closing soon
- **Email** (if connected) — unread from key accounts, waiting on replies
- **Enrichment** (if connected) — overnight signals on your accounts

Then creates a scannable 2-minute briefing.

### Output Format

```markdown
# Daily Briefing | Tuesday, January 28, 2026

---

## #1 Priority

**Re-engage Acme Corp ($120K opportunity)**
No activity in 18 days. Close date is Feb 15. Email Sarah Chen today to
confirm technical review status or risk deal going stale.

---

## Today's Numbers

| Open Pipeline | Closing This Month | Meetings Today | Action Items |
|---------------|-------------------|----------------|--------------|
| $870K | $480K | 3 | 7 |

---

## Today's Meetings

### 10:00am — DataFlow Inc (Demo)
**Attendees:** Mike Wu (CTO), Lisa Chen (VP Product)
**Context:** POC kickoff — show Kafka integration and migration path
**Prep:** Review their ETL docs they sent yesterday, prepare Kafka demo

### 2:00pm — Acme Corp (Discovery)
**Attendees:** Sarah Chen (VP Eng), Mike Rodriguez (CTO)
**Context:** Re-engagement after 2024 loss to Snowflake, new VP Eng hire
**Prep:** Run `/call-prep Acme Corp` for full brief

### 4:00pm — Internal Forecast Call with Manager
**Context:** Q1 forecast review
**Prep:** Run `/forecast` before meeting

---

## Pipeline Alerts

### Needs Attention
| Deal | Stage | Amount | Alert | Action |
|------|-------|--------|-------|--------|
| Acme Corp | Proposal | $120K | 18 days silent | **Email today** — re-engage |
| OldCo | Demo | $60K | Close date passed | Update close date or qualify out |

### Closing This Week
| Deal | Close Date | Amount | Confidence | Blocker |
|------|------------|--------|------------|---------|
| TechStart | Jan 31 | $50K | High | Waiting on contract signature |
| MidCo | Feb 2 | $30K | Medium | Pricing approval pending |

---

## Email Priorities

### Needs Response
| From | Subject | Received |
|------|---------|----------|
| Sarah Chen (Acme) | RE: Technical architecture questions | 6:45am |
| Mike Rodriguez (Acme) | Following up on yesterday's call | Yesterday 4pm |

### Waiting On Reply (3+ Days)
| To | Subject | Sent | Days Waiting |
|----|---------|------|--------------|
| John Smith (BigCo) | Q&A from last week's demo | Jan 24 | 4 |
| Lisa Park (StartupX) | Pricing proposal | Jan 22 | 6 |

---

## Suggested Actions

1. **Respond to Sarah Chen (Acme)** — she asked technical questions this morning
2. **Re-engage Acme Corp** — 18 days silent, close date approaching
3. **Follow up on TechStart contract** — close date is Jan 31 (in 3 days)
4. **Prep for afternoon meetings** — run call-prep for DataFlow and Acme

---

*Run `/call-prep [company]` before your meetings*
*Run `/call-summary` after each call*
```

### Quick Brief Mode

Say "quick brief" or "tldr my day" for abbreviated version:

```markdown
# Quick Brief | Jan 28

**#1:** Re-engage Acme Corp (18 days silent, $120K at risk)

**Meetings:** 3 — DataFlow (demo), Acme (discovery), Forecast call

**Alerts:**
- Acme 18 days silent
- OldCo close date passed

**Do Now:** Email Sarah Chen at Acme
```

### End of Day Mode

Say "wrap up my day" or "end of day summary":

```markdown
# End of Day | January 28

**Completed:**
- DataFlow demo — POC approved, starting next week
- Acme discovery — qualified, technical review scheduled Feb 8

**Pipeline Changes:**
- DataFlow moved to POC stage ($70K)
- Acme re-opened ($120K)

**Tomorrow's Focus:**
- Follow up on TechStart contract (closes Jan 31)
- Prep for forecast call
- Respond to 3 pending emails

**Open Loops:**
- [ ] Acme: send Kafka integration docs by Jan 30
- [ ] DataFlow: intro to solutions engineer for POC kickoff
```

---

## draft-outreach

Research a prospect, then draft personalized outreach.

### When It Triggers

When you say:
- "Draft outreach to [person/company]"
- "Write cold email to [prospect]"
- "Reach out to [name]"
- "Draft LinkedIn message to [person]"

### What It Does

The skill never sends generic outreach. It always researches first:

**Step 1: Research** (uses account-research skill internally)
- Web search for company and person
- Enrichment tools (if connected) for verified contact info
- CRM (if connected) for prior relationship context

**Step 2: Identify Hook** (trigger event, mutual connection, content, pain point)

**Step 3: Draft Message** (personalized email and/or LinkedIn)

**Step 4: Deliver**
- If email connector available: create draft in your inbox
- If not: output text for you to copy

### Output Format

```markdown
# Outreach Draft: Sarah Chen @ Acme Corp

**Generated:** January 28, 2026
**Research Sources:** Web Search + ZoomInfo + HubSpot

---

## Research Summary

**Target:** Sarah Chen, VP of Engineering at Acme Corp
**Hook:** New in role (hired Jan 2026 from Snowflake), company scaling fast (600 to 1,000 customers in 6 months), hiring 5 data engineers
**Goal:** Discovery call to understand data infrastructure needs

---

## Email Draft

**To:** sarah.chen@acme.com
**Subject:** Acme's growth + data infrastructure

---

Hi Sarah,

Congrats on the new role at Acme — making the jump from Snowflake to a
high-growth SaaS company is exciting.

Saw the announcement about hitting 1,000 customers (up from 600 in June).
With 5 data engineer roles open, seems like scaling the data infrastructure
is a priority as you ramp up.

We work with similar-stage companies navigating that exact challenge —
recent customer went from Snowflake to our platform and cut data costs
40% while improving query speed.

Worth a quick call to see if there's anything relevant to your roadmap?

Best,
[Your Name]

---

**Subject Line Alternatives:**
1. Quick question on Acme's data hiring
2. Scaling data infra at Acme

---

## LinkedIn Message (if no email)

**Connection Request (< 300 chars):**
Hi Sarah, saw you joined Acme from Snowflake — congrats on the new role.
I work with SaaS companies scaling data infrastructure. Would love to connect.

**Follow-up Message (after connected):**
Sarah, thanks for connecting. Saw Acme's growth to 1,000 customers and
the data engineer hiring push. We have helped similar companies navigate
that scaling challenge (recent customer cut Snowflake costs 40%).

Worth a quick call to see if there is anything relevant to your roadmap?

---

## Why This Approach

| Element | Based On |
|---------|----------|
| Opening | New role (from ZoomInfo + LinkedIn) — timely, shows research |
| Hook | Customer growth + data engineer hiring — clear pain point |
| Proof | Similar customer result (40% cost reduction) — credible, specific |
| CTA | "Worth a quick call" — low-friction, exploratory tone |

---

## Email Draft Status

Draft created — copy email above to send

[If email connected: Draft created in Outlook — review and send]
[If email found: sarah.chen@acme.com (verified via ZoomInfo)]
[If no email: Email not found — use LinkedIn approach]

---

## Follow-up Sequence (Optional)

**Day 3 - Follow-up 1:**
Subject: Following up

Sarah, following up on my note below. If data infrastructure is not a
priority right now, no worries — happy to reconnect down the road.

If it is, happy to share what we have learned helping SaaS companies
scale analytics post-Series C.

**Day 7 - Follow-up 2:**
Subject: One more try

Sarah, one more try — then I will stop bugging you.

Quick question: with 5 data engineers ramping, are you investing in
analytics infrastructure this quarter, or are you focused elsewhere?

If it is a priority, happy to share a 5-min case study from a similar
company. If not, I will check back in Q2.

**Day 14 - Break-up:**
Subject: Closing the loop

Sarah, clearly not the right time — I will stop reaching out.

If data infrastructure ever becomes a bottleneck as you scale, feel
free to ping me. Otherwise, best of luck with the ramp at Acme.
```

### Email Style Rules

The plugin enforces these rules for all customer-facing emails:

1. **Concise but informative** — Get to the point. Busy people skim.
2. **No markdown** — No `**bold**` or `*italics*`. Plain text only.
3. **Short paragraphs** — 2-3 sentences max.
4. **Simple lists** — Plain dashes or numbers, no fancy formatting.

### What NOT to Do

**Generic openers** (avoid):
- "I hope this email finds you well"
- "I'm reaching out because..."
- "I wanted to introduce myself"

**Fake personalization** (avoid):
- "I noticed you work at [Company]" (obviously)
- "Congrats on your role" (without specific context)

**Feature dumps** (avoid):
- Long paragraphs about your product
- Multiple value props at once
- No clear CTA

**Instead:**
- Lead with something specific you learned
- One clear value prop
- One clear ask

### Channel Selection

```
IF verified email available:
  → Email preferred (higher response rate)
  → Also provide LinkedIn backup

IF no email found:
  → LinkedIn connection request
  → Follow-up message template

IF warm intro possible:
  → Suggest mutual connection outreach first
```

---

## competitive-intelligence

Research competitors and build an interactive battlecard.

### When It Triggers

When you say:
- "Competitive intel on [competitor]"
- "Research [competitor]"
- "How do we compare to [competitor]?"
- "Battlecard for [competitor]"
- "What's new with [competitor]?"

### What It Does

The skill researches competitors extensively and generates an **interactive HTML battlecard** with:

**Always (via web search):**
- Competitor product deep-dive (features, pricing, positioning)
- Recent releases (last 90 days)
- Your company releases (to counter)
- Differentiation matrix (where you win vs where they win)
- Sales talk tracks for different scenarios
- Landmine questions (expose their weaknesses naturally)

**If connected:**
- **CRM:** Win/loss data, competitor mentions in closed deals
- **Docs:** Existing battlecards, competitive playbooks
- **Chat:** Internal intel, field reports
- **Transcripts:** Competitor mentions in customer calls

### Output: Interactive HTML Battlecard

The skill generates a self-contained HTML file with:

#### 1. Comparison Matrix (Landing View)
Overview comparing you vs all competitors:
- Feature comparison grid
- Pricing comparison
- Market positioning
- Win rate indicators (if CRM connected)

#### 2. Competitor Tabs (Clickable)
Each competitor gets a card that expands to show:
- Company profile (size, funding, target market)
- What they sell and how they position
- Recent releases (last 90 days)
- Where they win vs where you win
- Pricing intelligence
- Talk tracks for different scenarios
- Objection handling
- Landmine questions

#### 3. Your Company Card
- Your releases (last 90 days)
- Your key differentiators
- Proof points and customer quotes

### Example Output Structure

```markdown
## ✓ Battlecard Created

[View your battlecard](computer:///path/to/Acme-Analytics-battlecard-2026-01-28.html)

---

**Summary**
- **Your Company**: Acme Analytics
- **Competitors Analyzed**: Snowflake, Databricks, BigQuery
- **Data Sources**: Web research + HubSpot win/loss data

---

**How to Use**
- **Before a call**: Open the relevant competitor tab, review talk tracks
- **During a call**: Reference landmine questions
- **After win/loss**: Update with new intel

---

**Sharing Options**
- **Local file**: Open in any browser
- **Host it**: Upload to Netlify, Vercel, or internal wiki
- **Share directly**: Send HTML file to teammates

---

**Keep it Fresh**
Run this skill again to refresh intel. Recommended: monthly or before major deals.
```

### Visual Design

The battlecard uses:
- Dark theme with professional styling
- Tabbed navigation for each competitor
- Color-coded comparison matrix (green = you win, red = they win, yellow = tie)
- Expandable sections for detail
- Self-contained HTML (no external dependencies except fonts)

### Research Process

For each competitor, the skill runs:
1. `[Competitor] product features` — what they offer
2. `[Competitor] pricing` — how they charge
3. `[Competitor] news` — recent announcements (90 days)
4. `[Competitor] product updates OR changelog OR releases` — what they shipped
5. `[Competitor] reviews G2 OR Capterra` — customer sentiment
6. `[Competitor] vs [alternatives]` — how they position
7. `[Competitor] customers` — who uses them
8. `[Competitor] careers` — hiring signals (growth areas)

### Refresh Cadence

Competitive intel gets stale. Recommended refresh:

| Trigger | Action |
|---------|--------|
| **Monthly** | Quick refresh — new releases, news, pricing |
| **Before major deal** | Deep refresh for specific competitor |
| **After win/loss** | Update patterns with new data |
| **Competitor announcement** | Immediate update |

### Tips for Better Intel

1. **Be honest about weaknesses** — Credibility comes from acknowledging where competitors are strong
2. **Focus on outcomes, not features** — "Customers achieve Y result" matters more than "They have X feature"
3. **Update from the field** — Best intel comes from actual customer conversations
4. **Plant landmines, don't badmouth** — Ask questions that expose weaknesses; never trash-talk
5. **Track releases religiously** — What they ship tells you their strategy

---

## create-an-asset

Generate tailored sales assets (landing pages, decks, one-pagers, workflow demos) from deal context.

### When It Triggers

When you say:
- `/create-an-asset`
- `/create-an-asset [CompanyName]`
- "Create an asset for [company]"
- "Build a demo for [prospect]"
- "Make a landing page for [company]"
- "Mock up a workflow for [use case]"

### What It Does

The skill creates professional sales assets by gathering context about:

1. **(a) The Prospect** — company, contacts, conversations, pain points
2. **(b) The Audience** — who's viewing, what they care about
3. **(c) The Purpose** — goal, desired next action
4. **(d) The Format** — landing page, deck, one-pager, or workflow demo

Then researches, structures, and builds a polished, branded asset.

### Supported Formats

| Format | Best For | Output |
|--------|----------|--------|
| **Interactive Landing Page** | Exec meetings, value prop | Multi-tab page with demos, calculators |
| **Deck-Style** | Formal presentations | Linear slides with navigation |
| **One-Pager** | Leave-behinds | Single-scroll executive summary |
| **Workflow / Architecture Demo** | Technical deep-dives, POC proposals | Interactive diagram with animated flow |

### The Process

```
1. You provide context (prospect, audience, purpose)
          ↓
2. Skill researches the prospect company
          ↓
3. Skill asks 3-4 clarifying questions
          ↓
4. You confirm direction
          ↓
5. Skill builds the asset
          ↓
6. You iterate as needed
```

### Example Prompt

**Basic:**
```
Create an asset for Acme Corp
```

**With context:**
```
Create an asset for Acme Corp. I met with their VP Engineering last
week — they're struggling with slow analytics query performance and
want to improve developer productivity. This is for a follow-up with
their technical team.
```

**Workflow demo:**
```
I want to mock up a workflow showing how a customer would use our
platform to automate their nightly ETL pipeline. The flow is: data
sources (Salesforce, MySQL) → our platform → transformation → Snowflake
warehouse → BI tool updates.
```

### Output

The skill generates a self-contained HTML file with:

- Professional dark theme
- Prospect's brand colors (extracted from their website)
- Tailored content based on research and your input
- Interactive elements (calculators, demos, animations)
- Works offline, can be hosted anywhere

### Sharing Options

- **Static hosting**: Upload to Netlify, Vercel, GitHub Pages, AWS S3
- **Password protect**: Most hosts offer simple password protection
- **Direct share**: Email the HTML file — it's fully self-contained
- **Embed**: iframe into other pages or portals

### Tips for Best Results

1. **Provide rich context** — more details = more tailored asset
2. **Upload transcripts** — call recordings, meeting notes, emails
3. **Be specific about audience** — "IT architects evaluating security" beats "technical team"
4. **Iterate freely** — colors, sections, messaging, flow all adjustable

---

## Part IV: Connected Tools

The sales plugin is designed to work with your existing tech stack. This section details each integration category.

---

## MCP Integrations Overview

MCP (Model Context Protocol) servers connect Claude to external tools and services. The sales plugin pre-configures nine MCP servers across seven categories.

### Pre-Configured Servers

| Category | Server | Type | What It Enables |
|----------|--------|------|-----------------|
| Chat | Slack | HTTP | Internal discussions, colleague intel |
| CRM | HubSpot | HTTP | Pipeline data, contact records, activities |
| CRM | Close | HTTP | Pipeline data, contact records, activities |
| Data Enrichment | Clay | HTTP | Company and contact data enrichment |
| Data Enrichment | ZoomInfo | HTTP | Verified contact info, org charts, tech stack |
| Knowledge Base | Notion | HTTP | Docs, battlecards, playbooks |
| Project Tracker | Atlassian | HTTP | Jira/Confluence integration |
| Conversation Intelligence | Fireflies | HTTP | Call recordings, transcripts, key moments |
| Email & Calendar | Microsoft 365 | HTTP | Email threads, calendar events, contacts |

### Authentication Types

| Type | How It Works | User Experience |
|------|-------------|-----------------|
| **OAuth (SSE)** | Sign in through service's standard flow | One-time sign-in, then automatic |
| **HTTP with tokens** | API key or bearer token | Set environment variable once |
| **stdio (local)** | Runs program on your machine | For custom or local servers |

Most pre-configured servers use OAuth, so connection is a simple sign-in flow.

---

## CRM Integration

### Supported CRMs

- **HubSpot** (pre-configured)
- **Close** (pre-configured)
- **Salesforce** (requires manual configuration)
- **Pipedrive** (requires manual configuration)
- Any CRM with an MCP server

### What CRM Integration Enables

| Without CRM | With CRM Connected |
|-------------|-------------------|
| Upload CSV for pipeline analysis | Auto-pull live pipeline data |
| Paste deal information | Read and write opportunities |
| Manually log call notes | Automatic activity logging |
| Copy tasks to your CRM | Create tasks directly |
| Manual data updates | Write-back: update stages, close dates, next steps |
| No historical context | Pull win/loss patterns, prior opportunities |

### Connecting HubSpot

HubSpot is pre-configured. The first time you reference CRM data:

1. You see a connection prompt
2. Click "Connect HubSpot"
3. Sign in via OAuth
4. Grant permissions
5. Connection persists across sessions

### Connecting Close

Same OAuth flow as HubSpot. Close CRM users can choose Close instead of HubSpot.

### Connecting Salesforce

Salesforce requires manual configuration since it is not pre-configured:

1. Create `.mcp.json` in your Cowork config directory:
```json
{
  "mcpServers": {
    "salesforce": {
      "type": "sse",
      "url": "https://mcp.salesforce.com/sse"
    }
  }
}
```

2. Restart Cowork
3. Authenticate via OAuth when prompted

### CRM Data Security

- OAuth tokens are stored securely by the MCP server
- Claude never sees your credentials
- You can revoke access anytime via the service's settings
- All data access is read-only unless you explicitly approve writes

### Write-Back Workflow

When the plugin wants to update your CRM, it:

1. Shows you exactly what it will write
2. Asks for your approval
3. Only writes if you confirm

Example:
```
I can log this call in HubSpot:

Activity:
- Type: Call
- Outcome: Connected
- Duration: 45 minutes
- Notes: [Summary]

Tasks:
- Send Kafka integration docs by Jan 30 (assigned to you)
- Intro to head of data engineering by Feb 5 (assigned to Sarah Chen)

Opportunity Update:
- Stage: Discovery → Technical Evaluation
- Next Steps: Technical deep-dive Feb 8

Approve? (yes/no)
```

You review and approve before anything is written.

---

## Conversation Intelligence

### Supported Platforms

- **Fireflies** (pre-configured)
- **Gong** (requires manual configuration)
- **Chorus** (requires manual configuration)
- **Otter.ai** (requires manual configuration)

### What Conversation Intelligence Enables

| Without CI | With CI Connected |
|-----------|------------------|
| Paste transcript or notes | Auto-pull call recordings |
| Manual review of calls | Key moment extraction |
| Manual action item identification | AI-generated action items |
| No sentiment analysis | Sentiment and engagement scoring |
| Manual competitor tracking | Auto-flag competitor mentions |

### Connecting Fireflies

Fireflies is pre-configured. First time you run `/call-summary`:

1. You see: "Would you like to connect Fireflies to auto-pull transcripts?"
2. Click "Connect Fireflies"
3. Sign in via OAuth
4. Grant permissions

After connection, `/call-summary` searches for recent calls automatically.

### Transcript Quality

Conversation intelligence platforms provide structured transcripts with:
- Speaker identification
- Timestamps
- Key moments flagged by platform's AI
- Sentiment scores
- Competitor mentions

This structured data produces better summaries than raw Zoom transcripts.

---

## Data Enrichment

### Supported Platforms

- **Clay** (pre-configured)
- **ZoomInfo** (pre-configured)
- **Apollo** (requires manual configuration)
- **Clearbit** (requires manual configuration)
- **Lusha** (requires manual configuration)

### What Enrichment Enables

| Web Search Only | With Enrichment |
|----------------|-----------------|
| Public company info | Verified firmographics |
| LinkedIn scraping for contacts | Org charts, full contact lists |
| Estimated employee count | Precise employee count |
| Guessed contact emails | Verified emails and phone numbers |
| Public news only | Intent signals, hiring velocity |
| General tech stack info | Detailed tech stack with version info |

### Connecting ZoomInfo

ZoomInfo is pre-configured:

1. First account research triggers connection prompt
2. Sign in via OAuth
3. Grant permissions
4. Connection persists

### Connecting Clay

Clay is pre-configured with the same OAuth flow.

### Enrichment Credits

Most enrichment services charge per lookup (credits or API calls). The plugin:

- Tells you before making enrichment calls
- Caches results to avoid redundant lookups
- Only enriches when you explicitly request account research

You control when enrichment happens — it never burns credits without your knowledge.

---

## Communication Tools

### Slack

**What it enables:**
- Internal chat search for account intel
- Post summaries to team channels
- Track customer conversations in shared channels

**Connection:** OAuth (pre-configured)

**Example use:**
```
After running /call-summary:

"Post this summary to #sales-team channel"
```

The plugin posts the internal summary (not the customer email) to Slack.

### Microsoft 365 (Email & Calendar)

**What it enables:**
- **Email:** Scan recent threads, draft follow-ups, track sent/replied status
- **Calendar:** Auto-pull today's meetings, attendee context, meeting history

**Connection:** OAuth (pre-configured)

**Example use:**
```
"Prep my day"
```

The plugin pulls your calendar automatically, finds customer meetings, and researches each account.

---

## Knowledge Management

### Notion

**What it enables:**
- Pull from internal docs, battlecards, playbooks
- Search for prior customer examples
- Access company knowledge base

**Connection:** OAuth (pre-configured)

**Example use:**
```
"Create a battlecard for Snowflake using our existing competitive docs"
```

The plugin searches Notion for existing competitive intel and incorporates it into the new battlecard.

### Atlassian (Jira / Confluence)

**What it enables:**
- Search Confluence for sales playbooks
- Track Jira tickets related to customer requests
- Pull product roadmap info

**Connection:** OAuth (pre-configured)

---

## Part V: Day-to-Day Workflows

This section shows how to integrate the sales plugin into your daily routine.

---

## Morning Routine

**Time investment:** 2-5 minutes

### Step 1: Daily Briefing

```
Morning briefing
```

You get:
- #1 priority for today
- Today's meetings with context
- Pipeline alerts (deals needing attention)
- Email priorities (needs response, waiting on replies)
- Suggested actions

### Step 2: Review and Triage

Scan the briefing and decide:
- What is genuinely urgent? (e.g., "Re-engage Acme Corp, 18 days silent")
- What can wait? (e.g., "Update close date on deal closing next month")
- What meetings need prep? (e.g., discovery call at 2pm)

### Step 3: Quick Wins

Knock out 1-2 quick items before meetings start:
- Respond to that urgent email from a prospect
- Re-engage the stale deal with a quick check-in
- Update a past close date

### Step 4: Prep for First Meeting

If you have a morning meeting, run call prep:

```
Prep me for my 10am with DataFlow
```

Review the brief while you commute or grab coffee.

**Total time:** 2-5 minutes for briefing, 3-5 minutes per meeting prep.

---

## Pre-Call Preparation

**Time investment:** 3-5 minutes per call

### Standard Prep Workflow

**30 minutes before the call:**

```
Prep me for my call with [Company]
```

The plugin generates:
- Account snapshot
- Attendee backgrounds with talking points
- Context and history
- Suggested agenda
- Discovery questions
- Potential objections

### What to Do With the Prep

1. **Skim attendee backgrounds** — find one personal talking point per person
2. **Review context** — refresh on prior conversations
3. **Scan discovery questions** — pick 3-5 that feel most relevant
4. **Note the agenda** — use it as your mental roadmap

You do not need to memorize everything. The prep is a cheat sheet you can glance at during the call.

### Advanced: Upload Materials

If you have prior call notes, email threads, or documents from the prospect, upload them when running call prep:

```
Prep me for my Acme call

[Upload: acme-email-thread.txt, prior-call-notes.md]
```

The plugin incorporates those materials into the brief.

---

## Post-Call Follow-Up

**Time investment:** 5-8 minutes per call

### Standard Follow-Up Workflow

**Immediately after the call:**

```
/call-summary
```

Then paste your notes or describe what happened.

The plugin generates:
- Internal summary with action items
- Customer-facing follow-up email

### What to Do With the Output

1. **Review internal summary** — make sure it captured everything
2. **Check action items** — verify owners and due dates
3. **Edit follow-up email** — tweak tone or add any missed points
4. **Approve CRM updates** (if connected) — log activity, create tasks

### Send the Email

- If email is connected: review draft, send
- If not connected: copy email, paste into your email client, send

### Advanced: Auto-Log to CRM

If CRM is connected, approve the write-back:

```
Log this call:
- Activity type: Discovery call
- Duration: 45 minutes
- Notes: [Summary]
- Stage update: Discovery → Technical Evaluation
- Tasks: [Action items]

Approve? yes
```

Everything logs automatically.

**Total time:** 5 minutes if standalone, 8 minutes if writing back to CRM.

---

## Weekly Pipeline Review

**Time investment:** 15-20 minutes

### Workflow

**Every Monday (or your preferred day):**

```
/pipeline-review
```

If CRM is connected, it pulls automatically. If not, upload your pipeline CSV.

You get:
- Pipeline health score
- Priority actions this week
- Risk flags (stale, stuck, past close date, single-threaded)
- Hygiene issues (missing data)
- Recommendations

### What to Do With the Output

1. **Act on stale deals** — re-engage anything silent 14+ days
2. **Multi-thread risky deals** — get second contacts for single-threaded deals
3. **Update close dates** — fix any dates that passed
4. **Qualify out dead deals** — be ruthless with deals that are clearly stalled

### Manager Review

If you have a weekly pipeline review with your manager, run this before the meeting. Use the output as your talking points:

- "Here are my top 3 focus areas this week..."
- "I have 2 deals at risk that I am addressing..."
- "Pipeline health is 72/100, down from 78 last week because..."

---

## Monthly Forecasting

**Time investment:** 15-20 minutes

### Workflow

**End of each month or week before forecast call:**

```
/forecast
```

Provide your quota and timeline. The plugin generates:
- Weighted forecast (best/likely/worst scenarios)
- Commit vs upside breakdown
- Gap analysis
- Recommendations

### What to Do With the Output

1. **Determine your commit number** — what you would stake your forecast on
2. **Identify gap-closing opportunities** — deals you can accelerate
3. **Flag pipeline needs** — how much new pipeline to add
4. **Prepare for forecast call** — use the output as your script

### Forecast Call With Manager

Bring the forecast output to your call:

- **Commit:** "I'm committing $290K this quarter"
- **Upside:** "I have $330K in upside if these 4 deals close"
- **Gap:** "I'm $119K short of quota in commit, here's my plan to close the gap..."
- **Actions:** "I'm accelerating Analytics Co and re-engaging StartupX..."

---

## Prospecting and Outreach

**Time investment:** 10-15 minutes per prospect

### Workflow

**For each new prospect:**

**Step 1: Research**
```
Research [Company]
```

Get company overview, recent news, key people, tech stack (if enrichment connected).

**Step 2: Draft Outreach**
```
Draft outreach to [Person] at [Company]
```

The plugin researches (if not already done), identifies a hook, and drafts personalized email and LinkedIn message.

**Step 3: Review and Send**

Edit the draft if needed, then send.

### Batching Prospecting

For batch prospecting (e.g., 10 similar prospects in one industry):

**Create a research brief once:**
```
Research the e-commerce analytics space. I'm targeting VP of Analytics
at mid-market e-commerce companies. What pain points are common? What
triggers should I look for?
```

The plugin gives you industry context, common pain points, and trigger events.

**Then personalize per prospect:**
```
Draft outreach to Sarah Chen at Acme E-commerce using the e-commerce
analytics context from earlier
```

The plugin combines the industry context with company-specific research.

---

## Part VI: Advanced Topics

---

## Personalizing Your Setup

### Settings File

Create `sales/.claude/settings.local.json` to pre-configure your information:

```json
{
  "name": "Sarah Chen",
  "title": "Senior Account Executive",
  "company": "Acme Analytics",
  "email": "sarah.chen@acme-analytics.com",
  "phone": "+1-555-0123",
  
  "quota": {
    "annual": 1200000,
    "quarterly": 300000,
    "monthly": 100000
  },
  
  "product": {
    "name": "Acme Analytics Platform",
    "tagline": "Real-time analytics infrastructure for modern data teams",
    "value_props": [
      "50% faster query performance vs legacy warehouses",
      "Zero-copy data sharing across business units",
      "40% lower total cost of ownership vs Snowflake"
    ],
    "competitors": [
      "Snowflake",
      "Databricks",
      "BigQuery",
      "Redshift"
    ],
    "pricing": {
      "model": "Per-user per month + storage",
      "starting_price": "$99/user/month",
      "enterprise": "Custom pricing for 50+ users"
    }
  },
  
  "territory": {
    "industries": ["SaaS", "E-commerce", "FinTech"],
    "company_size": "100-1000 employees",
    "regions": ["West Coast US", "Remote"],
    "ideal_customer_profile": "High-growth tech companies scaling data infrastructure"
  },
  
  "email_signature": "Sarah Chen\nSenior Account Executive\nAcme Analytics\n+1-555-0123\nsarah.chen@acme-analytics.com"
}
```

### What Gets Personalized

With settings configured:

| Without Settings | With Settings |
|-----------------|---------------|
| "Your quota is..." → asks you | "Your $300K quarterly quota..." |
| "Who are your competitors?" → asks you | Automatically references Snowflake, Databricks, etc. |
| Generic email signatures | Your custom signature on all emails |
| "Your product..." → asks you | "Acme Analytics Platform..." |
| Generic value props | Your specific value props in assets and outreach |

### Updating Settings

Edit the file anytime. Changes take effect immediately (no restart needed).

---

## Creating Custom Email Templates

You can create reusable email templates for common scenarios.

### Template Location

Create `sales/.claude/templates/email/` directory and add Markdown files:

```
sales/
└── .claude/
    └── templates/
        └── email/
            ├── post-demo-follow-up.md
            ├── pricing-proposal.md
            └── re-engagement.md
```

### Template Format

**File: `post-demo-follow-up.md`**

```markdown
---
name: Post-Demo Follow-Up
description: Send after product demo to recap key points and propose next steps
variables:
  - prospect_company
  - attendee_names
  - demo_focus
  - next_step
---

Subject: {{prospect_company}} demo recap + next steps

Hi {{attendee_names}},

Thanks for taking the time for the demo today. Based on our discussion,
the key focus areas were:

{{demo_focus}}

From here, I suggest we:

{{next_step}}

Let me know if that works, or if you'd prefer a different approach.

Looking forward to it,
{{my_signature}}
```

### Using Templates

```
Draft a post-demo follow-up email for Acme Corp using the template.

Demo focus was:
- Kafka integration
- Migration timeline
- Cost comparison vs Snowflake

Next step:
- Technical deep-dive with data engineering team on Feb 8
```

The plugin fills in the template with your variables.

---

## Building Sales Playbooks

### Playbook Structure

Create `sales/.claude/playbooks/` directory:

```
sales/
└── .claude/
    └── playbooks/
        ├── enterprise-sales-playbook.md
        ├── smb-playbook.md
        └── channel-partner-playbook.md
```

### Playbook Format

**File: `enterprise-sales-playbook.md`**

```markdown
# Enterprise Sales Playbook

## Ideal Customer Profile

- Company size: 1,000+ employees
- Revenue: $100M+ annual revenue
- Decision process: Formal RFP, 6-12 month sales cycle
- Stakeholders: CIO, VP Engineering, VP Finance, Procurement

## Qualification Criteria (BANT)

### Budget
- Minimum deal size: $100K annual contract value
- Budget holder: VP-level or C-suite

### Authority
- Economic buyer: CIO or VP Engineering
- Champion: Director or Senior Manager level
- Influencers: Data architects, engineering managers

### Need
- Pain points: Legacy data infrastructure, scaling challenges, cost optimization
- Triggers: Funding rounds, M&A, leadership changes, compliance requirements

### Timeline
- Typical sales cycle: 6-12 months
- Decision timeline: Quarterly or annual budget cycles

## Sales Process

### Stage 1: Discovery (Weeks 1-2)
**Objectives:**
- Understand current data infrastructure
- Identify key pain points
- Map stakeholders and decision process
- Qualify budget, authority, need, timeline

**Activities:**
- Initial discovery call with champion
- Technical deep-dive with architects
- Stakeholder mapping
- Pain point documentation

**Exit Criteria:**
- BANT qualified
- Champion identified
- Technical requirements documented

### Stage 2: Technical Evaluation (Weeks 3-6)
**Objectives:**
- Demonstrate technical fit
- Build consensus among technical stakeholders
- Address security, compliance, integration concerns

**Activities:**
- Solutions architect deep-dive
- POC or pilot proposal
- Security and compliance review
- Integration planning

**Exit Criteria:**
- Technical win confirmed
- Security/compliance approved
- POC success criteria defined

### Stage 3: Business Case (Weeks 7-10)
**Objectives:**
- Build economic justification
- Get executive alignment
- Prepare for procurement

**Activities:**
- ROI analysis and business case
- Executive presentation
- Reference calls
- Proposal development

**Exit Criteria:**
- Executive sponsor aligned
- Business case approved
- Budget allocated

### Stage 4: Negotiation (Weeks 11-16)
**Objectives:**
- Navigate procurement
- Finalize terms
- Close the deal

**Activities:**
- Pricing negotiation
- Legal review
- Contract negotiation
- Procurement process

**Exit Criteria:**
- Contract signed
- PO received

## Objection Handling

### "We're happy with [Current Solution]"
**Response:** "That's great to hear. Most of our customers came from
[Current Solution] when they hit specific limits — usually around cost
or performance at scale. What's working well? What could be better?"

### "Too expensive"
**Response:** "I understand. Let's look at total cost of ownership over
3 years, including [Current Solution] costs, infrastructure, and
engineering time. Most customers find we're 30-40% lower TCO."

### "Not ready to switch"
**Response:** "Switching can be a non-starter, agreed. We offer a phased
approach where you can run both systems in parallel and migrate workload
by workload. Zero downtime."

## Competitive Positioning

### vs Snowflake
**When you win:** Cost-conscious, performance-sensitive, seeking simplicity
**When you lose:** Brand preference, ecosystem lock-in, risk-averse
**Talk track:** "Snowflake is the market leader with a mature ecosystem.
We differentiate on cost efficiency (40% lower) and query performance
(50% faster for analytical workloads). Best fit for teams optimizing TCO."

### vs Databricks
**When you win:** SQL-centric teams, seeking simplicity, non-ML workloads
**When you lose:** ML/AI focus, Spark expertise in-house
**Talk track:** "Databricks excels at ML and data science workloads.
We're purpose-built for analytical queries and BI. If your primary use
case is dashboards and reporting, we're faster and simpler."

## Resources

- Case studies: [Link to Notion doc]
- Demo scripts: [Link to Confluence]
- Pricing calculator: [Link to spreadsheet]
- ROI template: [Link to template]
```

### Using Playbooks

The plugin automatically references playbooks when relevant:

```
I'm working on an enterprise deal with Acme Corp. They're evaluating
us vs Snowflake. Help me prepare for the business case stage.
```

The plugin pulls from `enterprise-sales-playbook.md` and provides:
- Stage-appropriate activities
- Competitive positioning vs Snowflake
- Objection handling scripts

---

## Team Customization

If your sales team wants shared customizations, fork the plugin (see Part VII).

### Team Settings

Create a shared settings file that all team members use:

**File: `sales-acme-team/.claude/settings.team.json`**

```json
{
  "company": "Acme Analytics",
  "product": {
    "name": "Acme Analytics Platform",
    "value_props": [
      "50% faster query performance",
      "40% lower TCO vs Snowflake",
      "Zero-copy data sharing"
    ],
    "competitors": ["Snowflake", "Databricks", "BigQuery"]
  },
  "playbooks": {
    "enterprise": ".claude/playbooks/enterprise.md",
    "smb": ".claude/playbooks/smb.md"
  },
  "templates": {
    "post_demo": ".claude/templates/email/post-demo.md",
    "pricing": ".claude/templates/email/pricing.md"
  }
}
```

Team members' personal `settings.local.json` overrides team settings for individual preferences (name, quota, territory).

---

## Part VII: Extension and Customization

---

## Understanding the Plugin Architecture

The sales plugin is a collection of plain-text files organized in a specific directory structure. Understanding this structure lets you customize or extend it.

### Directory Structure

```
sales/
├── .claude-plugin/
│   └── plugin.json              # Plugin identity and metadata
├── commands/
│   ├── call-summary.md          # /call-summary command
│   ├── forecast.md              # /forecast command
│   └── pipeline-review.md       # /pipeline-review command
├── skills/
│   ├── account-research/
│   │   └── SKILL.md
│   ├── call-prep/
│   │   └── SKILL.md
│   ├── daily-briefing/
│   │   └── SKILL.md
│   ├── draft-outreach/
│   │   └── SKILL.md
│   ├── competitive-intelligence/
│   │   └── SKILL.md
│   └── create-an-asset/
│       ├── SKILL.md
│       ├── README.md
│       └── QUICKREF.md
├── .mcp.json                    # MCP server connections
├── CONNECTORS.md                # Tool categories documentation
├── README.md                    # Plugin documentation
└── LICENSE
```

### Key Files

| File | Purpose |
|------|---------|
| `plugin.json` | Plugin identity (name, version, description, author) |
| `commands/*.md` | Slash command definitions |
| `skills/*/SKILL.md` | Skill definitions with domain knowledge |
| `.mcp.json` | MCP server configurations |
| `CONNECTORS.md` | Tool category mappings |

### The Placeholder System

The plugin uses `~~category` placeholders for tool-agnostic references:

- `~~CRM` → your CRM (HubSpot, Salesforce, Close, etc.)
- `~~conversation intelligence` → your CI tool (Fireflies, Gong, etc.)
- `~~data enrichment` → your enrichment tool (ZoomInfo, Clay, etc.)

When you customize the plugin, you replace these placeholders with your actual tools.

---

## Adding Industry-Specific Knowledge

### Use Case: Adding Real Estate Sales Knowledge

Real estate sales has unique terminology, workflows, and regulations. Here is how to add that knowledge to the sales plugin.

### Approach: Create Complementary Skills

Create `.claude/skills/real-estate/` in your project (not inside the plugin):

**File: `.claude/skills/real-estate/SKILL.md`**

```markdown
---
name: real-estate-sales
description: >
  Real estate sales terminology, processes, and regulations. Use when
  discussing property listings, buyer qualification, offer negotiation,
  escrow process, MLS listings, or real estate commission structures.
---

# Real Estate Sales

## Buyer Qualification (Pre-Approval)

Before showing properties, qualify buyers:

| Qualification Factor | What to Verify |
|---------------------|---------------|
| **Pre-approval letter** | Mortgage pre-approval from lender, amount approved |
| **Down payment** | Minimum 3.5% for FHA, 20% for conventional (avoid PMI) |
| **Debt-to-income ratio** | Should be under 43% for most loans |
| **Credit score** | 620+ for conventional, 580+ for FHA |
| **Employment** | 2 years stable employment history |

## Listing Presentation Framework

When pitching to sellers:

### 1. Market Analysis (CMA)
- Pull 3-5 comparable properties (similar size, location, condition)
- Adjust for differences (pool, renovations, lot size)
- Recommend listing price range

### 2. Marketing Plan
- MLS listing with professional photos
- Virtual tour and drone footage
- Social media promotion (Facebook, Instagram)
- Open house schedule
- Email to buyer database

### 3. Commission Structure
- Standard: 5-6% total (2.5-3% listing agent, 2.5-3% buyer agent)
- Tiered structure for higher-value properties
- Explain value provided for commission

### 4. Timeline
- Average days on market in this area
- Escrow period (typically 30-45 days)
- Expected close date

## Offer Negotiation

### Key Terms to Negotiate
| Term | Typical Range | Seller Preference |
|------|--------------|------------------|
| **Price** | Listed price ± 5-10% | Higher |
| **Earnest money** | 1-3% of purchase price | Higher (shows commitment) |
| **Inspection contingency** | 10-17 days | Shorter or waived |
| **Appraisal contingency** | Standard in financed deals | Waived if possible |
| **Close date** | 30-60 days | Aligns with seller's move timeline |

### Multiple Offer Situation
Strategies for multiple offers:
1. **Highest and best** — ask all buyers to submit final offer by deadline
2. **Escalation clause** — buyer offers to beat highest offer by $X
3. **Appraisal gap coverage** — buyer covers difference if appraisal low

## MLS Listing Best Practices

| Element | Best Practice |
|---------|---------------|
| **Title** | 60 chars max, highlight key feature (e.g., "Stunning 4BR Craftsman w/ Pool") |
| **Description** | Lead with curb appeal, describe lifestyle, mention recent upgrades |
| **Photos** | 20-30 professional photos, twilight exterior shot, staged interior |
| **Price** | Price competitively based on CMA, consider psychological pricing ($399,000 vs $400,000) |

## Regulations and Disclosures

### Required Disclosures (California)
- Transfer Disclosure Statement (TDS)
- Natural Hazard Disclosure (NHD)
- Lead-based paint (pre-1978 properties)
- Megan's Law database (sex offender proximity)
- Earthquake fault zones (if applicable)

Regulations vary by state — always consult local requirements.

## Commission Splits

| Deal Size | Gross Commission (6%) | Split with Brokerage (50/50) | Agent Net |
|-----------|----------------------|------------------------------|-----------|
| $500K | $30,000 | $15,000 | $15,000 |
| $1M | $60,000 | $30,000 | $30,000 |
| $2M | $120,000 | $60,000 | $60,000 |

Commission split with brokerage varies (50/50, 60/40, 70/30 for top producers).
```

### Add Routing Rules

**File: `CLAUDE.md`**

```markdown
## Real Estate Sales Rules

When working with real estate listings, buyer qualification, offer
negotiation, or MLS listings, always apply the real-estate-sales skill.

When creating sales assets for real estate listings, include:
- Property photos and virtual tour
- Neighborhood highlights and school ratings
- Comparable sales (CMA)
- Seller disclosure summary
```

Now when you use the sales plugin commands for real estate:

```
/call-summary

[Paste notes from listing presentation with seller]
```

The plugin applies both the general sales skill and the real estate skill, producing a summary with real estate terminology and process understanding.

---

## Creating Company-Specific Workflows

### Use Case: Adding Acme Corp's Deal Approval Process

Every company has unique approval workflows. Here is how to encode yours.

### Approach: Fork the Plugin

1. Copy the sales plugin directory:
   ```
   sales/ → sales-acme/
   ```

2. Update `plugin.json`:
   ```json
   {
     "name": "sales-acme",
     "version": "1.0.0",
     "description": "Sales plugin customized for Acme Analytics team"
   }
   ```

3. Create `skills/acme-processes/SKILL.md`:

```markdown
---
name: acme-processes
description: >
  Acme Analytics internal sales processes, approval workflows, and
  team structures. Use when planning deals at Acme, routing for
  approval, understanding discount authority, or following Acme's
  sales methodology.
---

# Acme Analytics Sales Processes

## Deal Approval Authority

| Deal Size | Discount % | Approver | Turnaround |
|-----------|-----------|----------|------------|
| Any | 0-10% | AE (self-approve) | Immediate |
| Any | 10-20% | Sales Manager | 1 business day |
| Any | 20-30% | VP Sales | 2 business days |
| Any | 30%+ | CFO + VP Sales | 5 business days |
| $100K+ | Any discount | VP Sales | 2 business days |
| $500K+ | Any discount | CFO + VP Sales | 5 business days |

## Sales Stages and Exit Criteria

### Stage 1: Prospecting
**Definition:** Identified target account, researching, initiating outreach

**Activities:**
- Account research
- Identify key contacts
- Initial outreach (email, LinkedIn, phone)

**Exit Criteria:**
- Confirmed contact with decision maker or champion
- Initial discovery call scheduled

### Stage 2: Discovery
**Definition:** Understanding needs, pain points, decision process

**Activities:**
- Discovery call with champion
- Stakeholder mapping
- Technical requirements gathering
- BANT qualification

**Exit Criteria:**
- BANT qualified (budget, authority, need, timeline)
- Champion identified and engaged
- Technical requirements documented
- Demo requested or scheduled

### Stage 3: Demo / Evaluation
**Definition:** Product demonstration and technical evaluation

**Activities:**
- Tailored product demo
- POC or trial if applicable
- Solutions architect involvement
- Competitive differentiation

**Exit Criteria:**
- Demo completed successfully
- POC/trial approved (if applicable)
- Technical win confirmed
- Proposal requested

### Stage 4: Proposal
**Definition:** Formal proposal and pricing submitted

**Activities:**
- Pricing proposal
- SOW development
- Business case and ROI analysis
- Reference calls

**Exit Criteria:**
- Proposal submitted
- Pricing accepted (no negotiation) or counter-offer received

### Stage 5: Negotiation
**Definition:** Terms and pricing negotiation

**Activities:**
- Discount approval (if needed)
- Legal review
- Contract redlines
- Procurement navigation

**Exit Criteria:**
- Final pricing agreed
- Legal terms agreed
- Verbal commitment to sign

### Stage 6: Closed Won
**Definition:** Contract signed, PO received

**Activities:**
- Contract signature
- PO processing
- Handoff to Customer Success

## Proposal Requirements

All proposals must include:
- Executive summary (1 page)
- Pricing breakdown (per-user, storage, support tiers)
- Implementation timeline
- Success metrics
- Terms and conditions
- Signature page

Use template: `sales-acme/.claude/templates/proposal-template.md`

## Discount Guidelines

### Standard Discounts (No Approval)
- 10% for annual commit (vs monthly billing)
- 15% for multi-year commit (2-3 years)
- 5% for case study agreement

### Conditional Discounts (Requires Approval)
- Up to 20% for deals closing this quarter (end-of-quarter push)
- Up to 25% for strategic accounts (Fortune 500, competitive displacement)
- Up to 30% for large deals ($500K+, multi-year)

### Never Discount
- Implementation and training fees (fixed)
- Support and maintenance (fixed % of license)

## CRM Hygiene Rules

### Required Fields (Cannot Leave Blank)
- Opportunity name
- Close date (realistic, update weekly)
- Amount (accurate to ±10%)
- Stage
- Next steps (clear action with date)
- Primary contact

### Update Frequency
- **Daily:** Next steps, last activity date
- **Weekly:** Close date (if changed), stage progression
- **After every call:** Log activity, update notes

## Team Structure

| Role | Responsibility | Contact |
|------|---------------|---------|
| **AE (Account Executive)** | Own deal from discovery to close | You |
| **SDR (Sales Development Rep)** | Prospecting, initial outreach, qualify leads | [SDR name] |
| **SE (Solutions Engineer)** | Technical demos, POCs, architecture | [SE name] |
| **Sales Manager** | Deal coaching, forecast, discount approval | [Manager name] |
| **VP Sales** | Strategic deals, executive relationships | [VP name] |
| **Customer Success** | Post-sale onboarding, expansion | [CS name] |
```

4. Update commands to reference Acme processes:

Edit `commands/pipeline-review.md` to add:

```markdown
## Acme-Specific Hygiene Checks

Check for Acme CRM hygiene violations:
- Missing required fields
- Close dates not updated weekly
- Deals in Proposal stage >14 days (should move to Negotiation or back to Demo)
```

5. Install the forked plugin:
   ```bash
   cd sales-acme
   zip -r sales-acme.plugin . -x "*.DS_Store"
   ```

   Open `sales-acme.plugin` in Cowork to install.

Now all team members use `sales-acme` plugin with shared Acme-specific processes.

---

## Building Custom Sales Assets

The `create-an-asset` skill generates tailored sales assets, but you can pre-configure templates for common asset types.

### Create Asset Templates

**File: `.claude/assets/templates/executive-one-pager.md`**

```markdown
---
name: Executive One-Pager
format: one-pager
audience: C-suite executives
purpose: Strategic alignment and business case
---

# {{prospect_company}} + {{your_company}}

**Strategic Partnership Proposal | {{date}}**

---

## The Opportunity

{{prospect_company}} is {{company_description}}. Based on our discussion
with {{attendee_names}}, the key strategic priorities are:

{{strategic_priorities}}

---

## How {{your_product}} Enables These Priorities

| Priority | How We Help | Outcome |
|----------|-------------|---------|
| {{priority_1}} | {{solution_1}} | {{outcome_1}} |
| {{priority_2}} | {{solution_2}} | {{outcome_2}} |
| {{priority_3}} | {{solution_3}} | {{outcome_3}} |

---

## Business Impact

### ROI Summary (3-Year)

| Metric | Current State | With {{your_product}} | Value |
|--------|---------------|----------------------|-------|
| {{metric_1}} | {{current_1}} | {{future_1}} | {{value_1}} |
| {{metric_2}} | {{current_2}} | {{future_2}} | {{value_2}} |
| {{metric_3}} | {{current_3}} | {{future_3}} | {{value_3}} |

**Total 3-Year Value:** {{total_value}}

**Investment:** {{investment}}

**Net ROI:** {{roi_percentage}}

**Payback Period:** {{payback_months}} months

---

## Why {{your_company}}

- **Proven:** {{customer_count}} customers, including {{notable_customers}}
- **Trusted:** {{industry_recognition}} (awards, analyst recognition)
- **Supported:** {{support_model}} with {{sla}}

---

## Next Steps

**Proposed Timeline:**
- **{{date_1}}:** Technical deep-dive with {{prospect_team}}
- **{{date_2}}:** POC kickoff
- **{{date_3}}:** Business case review
- **{{date_4}}:** Contract signature

**Your Point of Contact:**
{{your_name}}
{{your_title}}
{{your_email}}
{{your_phone}}
```

### Using the Template

```
Create an executive one-pager for Acme Corp using the template.

Strategic priorities:
- Reduce data infrastructure costs
- Improve analytics query performance
- Enable self-service BI for business teams

Attendees: Sarah Chen (VP Eng), Mike Rodriguez (CTO)
```

The plugin fills in the template and generates a polished one-pager.

---

AGENT_REPORT_START
Plugin: sales
Version: 1.0.0
Files analyzed: 14
Handbook word count: ~5,800
Start time: 1771068412
End time: [completing now]
Estimated token usage: ~68,000
AGENT_REPORT_END
