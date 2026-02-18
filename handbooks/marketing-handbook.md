# Marketing Plugin Handbook

**The Definitive Guide to the Claude Cowork Marketing Plugin**

---

**Plugin Name:** marketing  
**Version:** 1.0.0  
**Author:** Anthropic  
**Description:** Create content, plan campaigns, and analyze performance across marketing channels. Maintain brand voice consistency, track competitors, and report on what's working.

---

## Table of Contents

- [Part I: Overview & Quick Start](#part-i-overview--quick-start)
- [Part II: Commands Reference](#part-ii-commands-reference)
- [Part III: Skills Deep Dive](#part-iii-skills-deep-dive)
- [Part IV: Connectors & MCP Servers](#part-iv-connectors--mcp-servers)
- [Part V: Customization & Extension](#part-v-customization--extension)
- [Part VI: File Reference](#part-vi-file-reference)
- [Part VII: Troubleshooting & FAQ](#part-vii-troubleshooting--faq)

---

## Part I: Overview & Quick Start

### What Is the Marketing Plugin?

The marketing plugin transforms Claude into a specialized marketing assistant capable of drafting content, planning campaigns, maintaining brand consistency, researching competitors, and analyzing performance. Rather than starting from scratch each time you need marketing deliverables, this plugin provides pre-built workflows, best-practice frameworks, and seamless connections to your marketing tools.

### Business Problems Solved

**For Marketing Directors and VPs:**
- **Campaign planning bottleneck**: Eliminate hours spent creating campaign briefs from scratch. Generate comprehensive plans with channel strategy, content calendars, and KPIs in minutes.
- **Brand inconsistency**: Ensure every piece of content aligns with your brand voice guidelines, reducing review cycles and brand erosion.
- **Competitive blindspots**: Get structured competitive intelligence on demand without manual research across dozens of sources.
- **Reporting overhead**: Build performance reports with actionable insights automatically instead of spending days wrestling spreadsheets.

**For Content Marketers and Copywriters:**
- **Writer's block and repetitive work**: Get publication-ready drafts for blog posts, email sequences, social media, landing pages, press releases, and case studies.
- **SEO integration gaps**: Ensure every piece of content follows SEO best practices without having to remember all the rules.
- **Multi-channel adaptation**: Create content variations optimized for different platforms without starting over each time.
- **Approval process friction**: Get content that already follows brand guidelines, reducing back-and-forth with stakeholders.

**For Demand Generation and Growth Marketers:**
- **Campaign execution delays**: Move from strategy to execution faster with pre-built frameworks for email sequences, nurture flows, and multi-channel campaigns.
- **Performance analysis paralysis**: Know what's working and what to optimize without getting lost in dashboards.
- **Channel selection guesswork**: Make evidence-based decisions about where to invest budget based on proven frameworks.

**For Small Marketing Teams:**
- **Expertise gaps**: Access specialized knowledge in areas like SEO, email marketing, and competitive analysis without hiring specialists.
- **Bandwidth constraints**: Accomplish in hours what normally takes days, letting a team of two or three punch above their weight.

### Target Users

This plugin is designed for:

- **Marketing Directors and VPs** who need strategic planning support, competitive intelligence, and performance reporting
- **Content Marketers** who produce blog posts, whitepapers, case studies, and thought leadership
- **Copywriters** who draft website copy, email campaigns, social media, and advertising creative
- **Demand Generation Managers** who plan and execute multi-channel campaigns
- **Growth Marketers** who optimize conversion funnels and run experiments
- **Social Media Managers** who create platform-specific content at scale
- **SEO Specialists** who need content gap analysis, keyword research, and technical audits
- **Product Marketers** who launch products and manage messaging and positioning
- **Marketing Operations** who build processes, maintain standards, and track performance
- **Small Business Owners** wearing multiple hats who need expert marketing support

### Quick Start Walkthrough

**Step 1: Install the Plugin**

**Cowork (recommended):** Open **Plugin Settings** in the Cowork desktop app, find **Marketing**, and click **Install**. The plugin activates immediately — no CLI required.

**Claude Code CLI (alternative):** If you are using Claude Code in the terminal rather than Cowork, install via:

```bash
claude plugins add knowledge-work-plugins/marketing
```

> **Note:** All standard Cowork plugins, including Marketing, are available from Plugin Settings with a single click. The CLI command above is only needed for Claude Code terminal users.

**Step 2: Verify Installation**

Type `/help` in Claude and verify that marketing commands appear in the list. You should see:

- `/draft-content`
- `/campaign-plan`
- `/brand-review`
- `/competitive-brief`
- `/performance-report`
- `/seo-audit`
- `/email-sequence`

**Step 3: Run Your First Command**

Let's draft a blog post. Type:

```
/draft-content
```

Claude will prompt you for inputs. Respond with:

```
Type: blog post
Topic: How marketing teams can measure ROI on content marketing
Audience: Marketing directors at B2B SaaS companies
Key messages: 
- Most teams track vanity metrics instead of business outcomes
- Attribution is imperfect but directional data beats no data
- Start with pipeline contribution and work backward
Tone: Authoritative but practical
Length: 1200 words
```

Claude will generate a complete blog post draft with headline options, SEO-optimized structure, and a clear call to action.

**Step 4: Connect Your Tools (Optional but Recommended)**

The plugin pre-configures connections to popular marketing tools. Connect the ones you use:

- **HubSpot**: For campaign data and contact management
- **Slack**: To share briefs and reports with your team
- **Notion**: To access your brand guidelines and campaign documents
- **Amplitude**: For product analytics and user behavior data
- **Canva** or **Figma**: To reference design assets
- **Ahrefs** or **Similarweb**: For SEO research and competitive analysis
- **Klaviyo**: For email marketing sequences

When you run a command that references one of these tools, Claude will prompt you to authenticate if you haven't already connected.

**Step 5: Explore Skills**

Skills activate automatically when you discuss relevant topics. Try asking:

```
What are the key elements of a strong brand voice?
```

Claude will draw on the `brand-voice` skill to provide a structured framework for defining and documenting brand voice attributes.

Or ask:

```
What metrics should I track for a lead nurture email campaign?
```

Claude will reference the `performance-analytics` skill to provide benchmarks and KPI definitions specific to email nurture.

### Component Architecture

The marketing plugin combines three types of components that work together:

**1. Commands (User-Triggered Actions)**

Commands are explicit actions you invoke by typing a slash followed by the command name. Each command follows a structured workflow:

- Accept inputs from you (campaign goal, target audience, content type, etc.)
- Apply domain knowledge from relevant skills
- Pull data from connected MCP tools if available
- Produce a specific deliverable (campaign brief, content draft, performance report, etc.)

Commands are deterministic workflows. Running `/campaign-plan` with the same inputs will produce consistently structured output.

**2. Skills (Background Knowledge)**

Skills are packages of marketing expertise that Claude loads automatically based on conversation context. When you discuss brand voice, the `brand-voice` skill activates. When you talk about SEO, the `performance-analytics` skill loads.

Skills provide:
- Frameworks (campaign planning models, attribution approaches, content structures)
- Best practices (benchmarks, guidelines, checklists)
- Templates (content type structures, reporting formats)
- Reference knowledge (metric definitions, channel strategies)

You never explicitly invoke a skill. They work in the background to make Claude more knowledgeable about marketing.

**3. MCP Servers (Tool Connections)**

MCP (Model Context Protocol) servers connect Claude to your actual marketing stack. When you run `/performance-report` and you have Amplitude connected, Claude can pull real performance data instead of asking you to paste it manually.

MCP servers enable Claude to:
- Read campaign performance from HubSpot or Klaviyo
- Search your Notion workspace for brand guidelines
- Post reports to Slack channels
- Pull keyword rankings from Ahrefs
- Access user behavior data from Amplitude
- Reference design files in Figma

**How They Work Together**

Here's what happens when you run `/campaign-plan` with HubSpot and Notion connected:

1. You invoke the command: `/campaign-plan`
2. Claude loads the `campaign-planning` skill for framework knowledge
3. Claude prompts you for inputs (goal, audience, timeline, budget)
4. Claude uses the HubSpot MCP server to check historical campaign performance for benchmark data
5. Claude uses the Notion MCP server to retrieve your target persona documents
6. Claude generates the campaign brief using the framework from the skill, enriched with data from your tools
7. Claude asks if you want to save the brief to Notion or share it in Slack

Without MCP connections, the process still works — Claude just asks you for any information it would have pulled from tools automatically.

---

## Part II: Commands Reference

### Overview of Commands

The marketing plugin includes seven commands, each designed for a specific marketing workflow:

| Command | Primary Use Case | Typical Output |
|---------|-----------------|----------------|
| `/draft-content` | Creating any marketing content from scratch | Publication-ready draft with headline options and SEO guidance |
| `/campaign-plan` | Planning a multi-channel campaign | Comprehensive campaign brief with timeline, budget, and metrics |
| `/brand-review` | Checking content against brand guidelines | Detailed review with severity-ranked issues and revision suggestions |
| `/competitive-brief` | Researching competitors | Structured competitive analysis with messaging comparison and positioning gaps |
| `/performance-report` | Analyzing marketing results | Report with metrics, trends, insights, and prioritized recommendations |
| `/seo-audit` | Evaluating SEO health and opportunities | Audit with keyword opportunities, technical issues, and action plan |
| `/email-sequence` | Designing multi-email flows | Complete email sequence with copy, timing, branching logic, and benchmarks |

---

### Command: `/draft-content`

**Syntax:** `/draft-content [content type and topic]`

**Description:** Draft blog posts, social media posts, email newsletters, landing pages, press releases, and case studies with channel-appropriate formatting, SEO optimization, and brand voice consistency.

**What It Produces:**
- Publication-ready content draft
- Multiple headline or subject line options
- SEO recommendations (for web content)
- Formatting appropriate to the channel
- Call-to-action suggestions

**Required Inputs:**
1. **Content type**: Blog post, social media post (specify platform), email newsletter, landing page, press release, or case study
2. **Topic**: The subject or theme
3. **Target audience**: Who this is for (role, industry, pain points)
4. **Key messages**: 2-4 main points to communicate
5. **Length**: Target word count or format constraint

**Optional Inputs:**
- **Tone**: Desired voice (if brand voice is not already configured)
- **SEO keywords**: Specific keywords to target (for web content)
- **Additional context**: Offers, CTAs, content assets to reference

**Business Scenario Walkthrough:**

**Scenario:** Sarah is a content marketer at a B2B SaaS company. She needs to write a blog post for their target audience of marketing directors, but she's juggling three other deadlines this week.

**Step 1:** Sarah invokes the command.
```
/draft-content
```

**Step 2:** Claude prompts for inputs. Sarah responds:
```
Type: blog post
Topic: Why most marketing attribution models fail and what to do instead
Audience: Marketing directors at mid-market B2B companies who are frustrated with attribution reporting
Key messages:
- Single-touch attribution oversimplifies the buyer journey
- Multi-touch attribution requires more data than most teams have
- Start with simple directional insights and iterate
- Focus on the decision that matters: where to invest next
Tone: Authoritative but empathetic—we've been there
Length: 1000-1200 words
```

**Step 3:** Claude generates a draft with:
- Three headline options ("The Attribution Trap: Why Marketing Teams Waste Time on Perfect Models" was the winner)
- An engaging introduction that connects with the audience's frustration
- Four clearly organized sections with descriptive subheadings
- Data points and examples supporting each message
- A conclusion with actionable takeaways
- SEO recommendations: primary keyword "marketing attribution," secondary keywords "multi-touch attribution," "attribution modeling"

**Step 4:** Sarah reviews the draft. The structure is solid and the tone matches their brand. She edits the introduction to reference a recent industry study and adjusts one example to match their product's specific value prop. Total time from command to publishable draft: 20 minutes instead of 3+ hours.

**Pro Tips:**

- **Be specific about audience pain points** in your input. "Marketing directors frustrated with reporting" produces better copy than just "marketing directors."
- **Include your desired CTA** in the additional context if you know where you want to drive readers.
- **For social media, specify the platform** — LinkedIn, Twitter/X, Instagram, and Facebook each have different conventions.
- **Request multiple variations** if you need A/B test options: "Give me two versions, one more data-driven and one more narrative."
- **Reference existing content** if this is part of a series: "This is the third post in our attribution series. Previous posts covered first-touch and last-touch models."

**Common Pitfalls:**

- **Vague audience descriptions** produce generic content. "B2B marketers" is too broad. "Demand gen managers at Series B SaaS companies struggling to justify paid spend" is specific enough to write compelling copy.
- **Too many key messages** dilutes the piece. Stick to 2-4 core points. If you have more, you probably need multiple pieces of content.
- **No brand voice configured** means Claude uses a neutral professional tone. Either configure your brand voice or specify tone each time.
- **Unrealistic length targets** for the content type. A LinkedIn post should be 150-300 words, not 1000. Claude will warn you if there's a mismatch.

---

### Command: `/campaign-plan`

**Syntax:** `/campaign-plan [campaign objective or product]`

**Description:** Generate a comprehensive marketing campaign brief including objectives, audience segmentation, messaging, channel strategy, content calendar, budget allocation, and success metrics.

**What It Produces:**
- Campaign overview with SMART objectives
- Target audience profile with pain points and motivations
- Core messaging hierarchy with proof points
- Channel strategy with allocation recommendations
- Week-by-week content calendar
- Content asset list with priorities
- Success metrics and KPIs
- Risk assessment and mitigation plan
- Next steps checklist

**Required Inputs:**
1. **Campaign goal**: Primary objective (drive signups, increase awareness, launch product, generate leads, re-engage users)
2. **Target audience**: Who the campaign targets
3. **Timeline**: Campaign duration and fixed dates
4. **Budget range**: Approximate budget (optional but recommended)

**Optional Inputs:**
- Product or service being promoted
- Key differentiators or value propositions
- Previous campaign learnings
- Brand guidelines or constraints
- Geographic focus

**Business Scenario Walkthrough:**

**Scenario:** Marcus is a demand generation manager planning a campaign to drive trial signups for a new product feature. His VP wants a full campaign brief by Friday, and it's Wednesday afternoon.

**Step 1:** Marcus runs:
```
/campaign-plan
```

**Step 2:** Claude asks for details. Marcus provides:
```
Campaign goal: Drive 500 free trial signups for our new workflow automation feature within 8 weeks
Target audience: Operations managers and rev ops leaders at mid-market B2B companies who currently use manual processes or multiple disconnected tools
Timeline: Launch February 15, run through April 15 (8 weeks). Product announcement at our user conference on February 20.
Budget range: $30,000-$40,000
Additional context: This feature has been in beta with 20 customers who saw 40% time savings on average. Main competitor just raised $50M and is marketing heavily.
```

**Step 3:** Claude generates a comprehensive brief including:

- **Campaign Overview**: "Launch & Learn: Workflow Automation" campaign with primary goal of 500 trials and secondary goal of generating 50 SQLs
- **Audience Profile**: Operations managers at 100-500 person companies, current pain point is spending 10+ hours/week on manual workflows, motivated by efficiency and team scalability
- **Key Messages**: 
  - Core message: "Automate what slows your team down"
  - Supporting messages addressing pain points, proof points from beta customers
  - Differentiation from competitor based on ease of setup vs. their enterprise complexity
- **Channel Strategy**: 
  - Paid: LinkedIn ads (60% of budget), retargeting (15%)
  - Owned: Email nurture to existing users (no cost), blog content series, in-app messaging
  - Earned: User conference announcement, beta customer case study PR
- **8-Week Content Calendar**: Week-by-week breakdown with 23 content pieces mapped to channels and milestones
- **Success Metrics**: Primary KPI is trial signups with target of 500, secondary KPIs include MQL generation (150 target), content engagement rate, and cost per trial (target under $80)

**Step 4:** Marcus reviews the brief. The channel allocation makes sense, and the content calendar is realistic. He adjusts the LinkedIn ad budget split (more to prospecting, less to retargeting since this is a new feature). He shares the brief with his VP, who approves it with minor feedback. Total time: 45 minutes instead of a full day.

**Pro Tips:**

- **Connect HubSpot or your marketing automation tool** before running this command. Claude can reference historical campaign performance to inform budget allocation and benchmarks.
- **Include previous campaign learnings** in your input to avoid repeating mistakes: "Our last launch campaign over-indexed on paid ads and underinvested in email nurture to existing customers."
- **Be specific about constraints**: "We can't sponsor podcasts or events due to budget limitations" or "Our content team can only produce one long-form asset per week."
- **Ask for variations**: "Show me this campaign plan with a $15K budget instead" or "What if we compressed this to 4 weeks?"
- **Request deep dives**: After reviewing the brief, ask "Create detailed targeting criteria for the LinkedIn ad campaigns" or "Draft the email nurture sequence for existing users."

**Common Pitfalls:**

- **Unrealistic goals for the budget and timeline**: 500 trials in 8 weeks on a $5K budget requires magic, not marketing. Claude will flag mismatches but won't refuse to plan—just be aware of feasibility.
- **Vague campaign goals**: "Increase awareness" is not specific enough. "Increase unaided brand awareness among our target segment from 15% to 25%" gives Claude a concrete target to plan against.
- **No differentiation context**: If you don't explain how you're different from competitors, the messaging will be generic.
- **Ignoring seasonality**: Launching a B2B campaign the week of Thanksgiving will underperform. Mention timing constraints.

---

### Command: `/brand-review`

**Syntax:** `/brand-review [content to review]`

**Description:** Review marketing content against brand voice, style guidelines, and messaging standards. Flag deviations, assess compliance risk, and provide specific improvement suggestions.

**What It Produces:**
- Overall assessment summary
- Detailed findings table with severity ratings
- Before/after revision examples for high-priority issues
- Legal and compliance flags
- Recommended next steps

**Required Inputs:**
1. **Content to review**: Paste content directly, provide a file path, share a URL, or reference a Notion page (if connected)

**Optional Inputs:**
- **Brand guidelines source**: If not configured, Claude will ask if you have guidelines to reference

**Two Review Modes:**

**Mode 1: With Brand Guidelines Configured**

When brand guidelines are configured (via local settings file or Notion), Claude evaluates against:
- Voice and tone attributes
- Terminology preferences and avoided terms
- Messaging pillar alignment
- Style guide compliance (grammar, formatting, punctuation)
- Legal and compliance flags (always checked)

**Mode 2: Generic Review (No Guidelines)**

Without brand guidelines, Claude evaluates for:
- Clarity (message clear, sentences concise, structure logical)
- Consistency (tone, terminology, formatting)
- Professionalism (grammar, appropriate tone, substantiated claims)
- Legal and compliance flags (always checked)

**Business Scenario Walkthrough:**

**Scenario:** Jessica is a marketing manager reviewing a landing page draft from a freelance copywriter. Her company has detailed brand guidelines, and she needs to ensure the copy is on-brand before sending it to design.

**Step 1:** Jessica copies the landing page copy and runs:
```
/brand-review
[pastes the landing page copy]
```

**Step 2:** Claude detects that brand guidelines are configured in her Notion workspace (connected via MCP) and automatically loads them. The review begins.

**Step 3:** Claude returns a detailed review:

**Summary:**
> The content is well-structured and clearly communicates the product benefits, but there are 8 voice/tone deviations and 3 terminology violations that need correction before publication. Most issues are medium severity and easily fixed.

**Detailed Findings:**

| Issue | Location | severity | Suggestion |
|-------|----------|----------|------------|
| Using "easy" instead of preferred "straightforward" | Headline and benefit section | Medium | Replace to match voice guide preference for inclusive language |
| Exclamation mark usage (4 instances) | Throughout | Medium | Brand guideline limits exclamation marks to once per page maximum |
| "e-mail" with hyphen | CTA section | Low | Style guide specifies "email" (no hyphen) |
| Unsubstantiated claim "best" | Feature description | High | Remove or qualify with evidence; compliance risk |
| "customers" instead of preferred "clients" | Testimonial section | Medium | Update terminology per brand guide |

**Revised Sections:**

Original headline:
> "The easiest way to automate your workflows! Get started today!"

Suggested revision:
> "The straightforward way to automate your workflows. Get started today."

**Legal/Compliance Flags:**
- Superlative "best workflow tool" in subheadline needs qualification or removal (high risk)
- Testimonial quote lacks attribution details; add name, company, role for credibility

**Step 4:** Jessica reviews the findings. She agrees with all medium and high-severity issues and quickly makes the edits. The low-severity items she'll batch-fix in a second pass. Total review time: 10 minutes instead of 30-45 minutes manually comparing against the brand guide.

**Pro Tips:**

- **Configure brand guidelines once** in a local settings file or Notion. Every review after that is automatic.
- **Review early in the process** before design work begins. Changing "customers" to "clients" in finalized designs is costly.
- **Batch review similar content**: "Review all five of these social posts for brand consistency" works well.
- **Use this for vendor work**: Reviewing agency or freelancer deliverables ensures quality before accepting.
- **Don't ignore low-severity issues**: They compound over time and erode brand consistency.

**Common Pitfalls:**

- **No brand guidelines configured but expecting specific feedback**: Without guidelines, Claude can only do a generic quality review.
- **Overly detailed brand guidelines**: If your guide is 50 pages, put the most critical rules in a summary document for faster reviews.
- **Treating this as a final approval**: Brand review catches guideline deviations, but you still need human judgment on strategy, positioning, and whether the content actually works.
- **Not reviewing legal flags seriously**: "Best" and "only" claims can create real legal risk. Investigate every compliance flag.

---

### Command: `/competitive-brief`

**Syntax:** `/competitive-brief [competitor name or market segment]`

**Description:** Research competitors and generate a structured competitive analysis comparing positioning, messaging, content strategy, and market presence. Includes messaging matrix, content gap analysis, and actionable recommendations.

**What It Produces:**
- Executive summary with key opportunity and threat
- Detailed competitor profiles (positioning, messaging, product emphasis, content strategy, strengths, weaknesses)
- Messaging comparison matrix
- Content gap analysis
- Opportunities and threats assessment
- Recommended actions (quick wins and strategic moves)

**Required Inputs:**
1. **Competitor name(s)**: One or more competitors to analyze

**Optional Inputs:**
- Your company/product context (positioning, value prop, differentiators)
- Focus areas (messaging, product, content, pricing, recent news)

**Business Scenario Walkthrough:**

**Scenario:** David is a product marketing manager preparing for a quarterly business review. His VP asked him to present competitive positioning and identify messaging gaps. He has three main competitors.

**Step 1:** David runs:
```
/competitive-brief
```

**Step 2:** Claude prompts for details:
```
Competitors: Acme Workflows, CompeteBot, FlowMaster
Your company context: We're BuildRight, a workflow automation platform for mid-market B2B companies. Our positioning: "Automation without the complexity." Key differentiator: We focus on ease of setup (competitors require IT/dev resources).
Focus areas: Messaging and positioning, content strategy, recent announcements
```

**Step 3:** Claude researches each competitor via web search, gathering:
- Homepage messaging, product positioning, pricing pages
- Recent press releases and funding announcements (last 6 months)
- Blog topics, content frequency, thought leadership themes
- Social media presence
- Review site themes (G2, Capterra)

**Step 4:** Claude generates the competitive brief:

**Executive Summary:**
> Acme Workflows leads on brand awareness but is perceived as complex and enterprise-focused, creating an opportunity for BuildRight to own the "ease of use" positioning in the mid-market. Main threat: CompeteBot just raised $30M and is investing heavily in content marketing and SEO.

**Competitor Profiles:**

For each competitor, detailed sections on:
- **Positioning**: Acme positions as "Enterprise-grade automation," CompeteBot as "AI-powered workflows," FlowMaster as "Developer-first automation"
- **Messaging Analysis**: Core value props, key themes, tone characterization
- **Content Strategy**: Acme publishes daily (heavy SEO investment), CompeteBot focuses on video tutorials and webinars, FlowMaster targets technical audiences with API documentation and dev content
- **Strengths**: Where they excel and why
- **Weaknesses**: Customer complaint themes from reviews, positioning vulnerabilities

**Messaging Comparison Matrix:**

| Dimension | BuildRight | Acme | CompeteBot | FlowMaster |
|-----------|-----------|------|------------|------------|
| Primary tagline | Automation without the complexity | Enterprise workflow automation | AI workflows that adapt to you | Automation for developers |
| Target buyer | Operations managers | IT/enterprise buyers | Marketing ops, rev ops | Engineering teams |
| Key differentiator | Ease of setup | Scale and security | AI/intelligence | API-first flexibility |
| Tone | Approachable, practical | Authoritative, corporate | Innovative, modern | Technical, precise |

**Content Gap Analysis:**
- BuildRight is not covering "integration how-tos" (all competitors have this)
- BuildRight has no video content (CompeteBot and FlowMaster invested heavily here)
- Opportunity: None of the competitors are targeting "non-technical ops teams" explicitly

**Opportunities:**
1. Own the "no-code ops automation" positioning—none of the competitors explicitly target non-technical users
2. Create integration content to match competitors while emphasizing ease vs. their complexity
3. Invest in video content showing 5-minute setup vs. competitors' multi-day implementations

**Recommended Actions:**

Quick wins:
- Publish "BuildRight vs. [competitor]" comparison pages highlighting ease of setup
- Create case study featuring non-technical operations team

Strategic moves:
- Launch video content series: "5-minute automation setups"
- Develop thought leadership on "automation democratization" theme

**Step 5:** David uses the brief to prepare his QBR presentation. He focuses on the "ease for non-technical users" positioning gap and proposes a content strategy to own that space. Total research and synthesis time: 1 hour instead of a full day of manual competitor research.

**Pro Tips:**

- **Run this quarterly** to track competitor momentum and messaging shifts.
- **Include your own positioning context** so Claude can identify gaps and opportunities specific to you.
- **Connect Ahrefs or Similarweb** for deeper SEO and traffic insights (the brief will automatically incorporate this data).
- **Ask for battlecard creation** after the brief: "Create a sales battlecard for Acme Workflows based on this analysis."
- **Monitor new competitors**: When you hear about a new player, run a quick brief to understand their positioning before they become a major threat.

**Common Pitfalls:**

- **Analyzing too many competitors at once**: Start with your top 2-3. You can always run additional briefs for secondary competitors.
- **Not providing your own context**: Without knowing your positioning, Claude can describe competitors but can't identify specific opportunities for you.
- **Ignoring indirect competitors**: If your product solves a problem that customers currently solve manually or with spreadsheets, "manual processes" is a competitor worth analyzing.
- **One-time analysis**: Competitive landscapes shift. Quarterly updates keep you ahead of changes.

---

### Command: `/performance-report`

**Syntax:** `/performance-report [time period or campaign]`

**Description:** Build a marketing performance report with key metrics, trend analysis, insights, and optimization recommendations. Supports campaign reports, channel reports, content performance, and overall marketing summaries.

**What It Produces:**
- Executive summary (headline metric, key win, area of concern)
- Key metrics dashboard (table with current period, prior period, change, target, status)
- Trend analysis (performance over time, inflection points, patterns)
- What worked (top 3-5 wins with data and hypotheses)
- What needs improvement (bottom 3-5 with recommendations)
- Insights and observations
- Prioritized recommendations (impact vs. effort matrix)
- Next period focus

**Required Inputs:**
1. **Report type**: Campaign, channel (email, social, paid, SEO, content), or overall marketing
2. **Time period**: Last week, last month, last quarter, or custom date range

**Optional Inputs:**
- **Data source**: If product analytics (Amplitude) or marketing automation (HubSpot, Klaviyo) is connected, Claude pulls data automatically. Otherwise, you can paste data or describe key numbers.
- **Comparison period**: Prior period or year-over-year for context
- **Stakeholder audience**: Executive summary vs. detailed analyst view

**Business Scenario Walkthrough:**

**Scenario:** Elena is a demand generation manager who needs to present monthly performance results to her VP. She has HubSpot and Amplitude connected.

**Step 1:** Elena runs:
```
/performance-report
```

**Step 2:** Claude prompts for inputs:
```
Report type: Overall marketing report
Time period: Last month (January 2025)
Comparison period: December 2024
Stakeholder audience: VP Marketing (executive summary style)
```

**Step 3:** Claude pulls data from HubSpot (email and campaign metrics) and Amplitude (product usage and conversion data). It analyzes the data and generates the report.

**Step 4:** The report includes:

**Executive Summary:**
> January performance exceeded lead generation targets (+15% vs. plan) but conversion rates from MQL to SQL declined 8 percentage points. Key win: LinkedIn campaign drove 40% more leads at 25% lower cost per lead. Area of concern: Email nurture engagement dropped significantly, with open rates down 12% from December.

**Key Metrics Dashboard:**

| Metric | January | December | Change | Target | Status |
|--------|---------|----------|--------|--------|--------|
| Total Leads | 423 | 367 | +15% | 400 | On track |
| MQLs | 178 | 164 | +9% | 170 | On track |
| SQLs | 52 | 67 | -22% | 70 | Off track |
| MQL→SQL Rate | 29% | 41% | -12pp | 40% | Off track |
| Cost per MQL | $142 | $178 | -20% | $150 | On track |
| Organic sessions | 8,340 | 7,920 | +5% | 8,000 | On track |

**Trend Analysis:**
- Lead volume grew steadily through the month, with a spike in week 3 (LinkedIn campaign launch)
- MQL to SQL conversion rate declined week-over-week starting mid-month
- Email engagement decline correlates with increased send frequency (4x/week in Jan vs. 2x/week in Dec)

**What Worked:**
1. **LinkedIn campaign**: 168 leads at $89 CPL (target was $120); video creative outperformed static images 2:1
2. **SEO momentum**: Organic traffic up 5%, driven by three blog posts published in December now ranking in top 3 for target keywords
3. **Webinar conversion**: January webinar had 62% attendance rate (vs. 45% average) and 18% converted to SQL

**What Needs Improvement:**
1. **Email nurture engagement**: Open rates down to 18% (from 25%), CTR down to 1.8% (from 3.2%); hypothesis: frequency fatigue
2. **MQL quality**: Conversion to SQL dropped; hypothesis: LinkedIn campaign drove volume but lower intent
3. **Paid search underperforming**: CPC up 30%, conversions flat; competitors increased bids

**Recommendations (Prioritized):**

High impact, low effort (do immediately):
- Reduce email frequency from 4x/week to 2x/week and monitor engagement recovery
- Pause underperforming paid search keywords (10 keywords driving 40% of spend, 5% of conversions)
- Add lead scoring criteria to better filter MQLs from LinkedIn campaigns before sales handoff

High impact, high effort (plan for next sprint):
- Refresh email nurture content (current sequence is 8 months old)
- Launch retargeting campaign for webinar attendees who didn't convert

**Next Period Focus:**
1. Recover MQL to SQL conversion rate to 35%+
2. Test new email nurture content and cadence
3. Scale LinkedIn campaign (proven winner)

**Step 5:** Elena reviews the report, adds a few context notes for her VP (explaining why email frequency increased), and presents it in their monthly review. The VP appreciates the clear insights and prioritized recommendations. Total time: 30 minutes instead of half a day building slides.

**Pro Tips:**

- **Connect your analytics tools** for automatic data pulling. Manual data entry works but takes longer.
- **Review weekly for paid campaigns** where you can adjust quickly, monthly for organic channels.
- **Ask for specific deep dives**: "Why did the MQL to SQL rate drop? Analyze by lead source" or "Compare email performance by segment."
- **Export to slides**: After generating the report, ask "Create a slide-ready version of the executive summary and key metrics."
- **Track recommendations over time**: At the end of each report, note which recommendations you implemented and check progress in the next report.

**Common Pitfalls:**

- **Reporting vanity metrics**: Impressions and clicks matter, but leads, pipeline, and revenue matter more. Ensure your report includes business outcome metrics.
- **No comparison period**: "We got 400 leads" means nothing without context. Always compare to prior period or target.
- **Analysis without action**: Every insight should lead to a recommendation. "Email open rates are down" needs "Reduce frequency and refresh subject lines."
- **Overcomplicating for the audience**: VPs need executive summaries; analysts need detailed breakdowns. Tailor the report depth to the audience.

---

### Command: `/seo-audit`

**Syntax:** `/seo-audit [url or topic] [audit type]`

**Description:** Run a comprehensive SEO audit including keyword research, on-page analysis, content gaps, technical checks, and competitor comparison. Produces a prioritized action plan for immediate and strategic SEO improvements.

**What It Produces:**
- Executive summary (overall SEO health, top 3 priorities)
- Keyword opportunity table (15-25 keywords with difficulty, opportunity score, current ranking, intent, recommended content type)
- On-page issues table (page, issue, severity, recommended fix)
- Content gap recommendations (topic, why it matters, format, priority, effort)
- Technical SEO checklist (status: pass/fail/warning for each check)
- Competitor comparison summary
- Prioritized action plan (quick wins and strategic investments)

**Required Inputs:**
1. **URL or domain**: The site to audit, or a topic/keyword for keyword research mode
2. **Audit type** (optional): Full site audit (default), keyword research, content gap analysis, technical SEO check, or competitor SEO comparison

**Optional Inputs:**
- Target keywords or topics
- Competitors to benchmark against

**Business Scenario Walkthrough:**

**Scenario:** Rachel is an SEO specialist at a SaaS company. Organic traffic has plateaued, and she needs to identify opportunities to regain growth. She has Ahrefs connected via MCP.

**Step 1:** Rachel runs:
```
/seo-audit https://www.example.com
```

**Step 2:** Claude defaults to a full site audit (since no audit type was specified) and starts the analysis. It:
- Pulls keyword ranking data from Ahrefs
- Analyzes on-page SEO across top landing pages
- Identifies content gaps by comparing to competitors
- Checks technical SEO factors
- Researches competitor SEO strategies

**Step 3:** Claude generates the audit report:

**Executive Summary:**
> Overall SEO health is solid with strong technical foundations and quality backlinks, but the site is missing significant content opportunities in the mid-funnel ("how to" guides and comparison content). Top 3 priorities: (1) Build out comparison and alternative pages for competitor keywords, (2) Refresh 12 high-traffic pages that haven't been updated in 18+ months, (3) Fix missing meta descriptions on 34 pages.

**Keyword Opportunity Table** (excerpt):

| Keyword | Est. Difficulty | Opportunity Score | Current Ranking | Intent | Recommended Content Type |
|---------|----------------|-------------------|-----------------|--------|--------------------------|
| "workflow automation tools" | Medium | High | Not ranking | Commercial | Comparison/listicle |
| "zapier alternative" | Low | High | Not ranking | Commercial | Alternative page |
| "how to automate workflows" | Medium | High | 18 | Informational | How-to guide |
| "workflow automation best practices" | Low | Medium | Not ranking | Informational | Pillar page |

(Full table includes 22 opportunities)

**On-Page Issues Table:**

| Page | Issue | Severity | Recommended Fix |
|------|-------|----------|-----------------|
| /product | Missing meta description | High | Add compelling 155-char meta description with primary keyword |
| /blog/automation-guide | Title tag too long (72 chars) | Medium | Shorten to under 60 characters |
| /features | No H1 tag | Critical | Add H1 matching page focus |
| /pricing | Keyword stuffing in opening paragraph | Medium | Rewrite naturally, reduce keyword density |

**Content Gap Recommendations:**

1. **Topic**: "Zapier alternatives" and competitor comparison pages
   - **Why it matters**: Competitors rank for these terms; high commercial intent; 2,400 monthly searches combined
   - **Format**: Individual alternative pages + master comparison page
   - **Priority**: High
   - **Effort**: Moderate (2-3 days for initial set)

2. **Topic**: "How to" guides for workflow automation by use case
   - **Why it matters**: Strong informational search volume (8,500/mo), mid-funnel content gap
   - **Format**: Step-by-step guides with examples
   - **Priority**: High
   - **Effort**: Substantial (ongoing series)

3. **Topic**: Industry-specific automation content (healthcare, legal, finance)
   - **Why it matters**: Competitors don't own these niches; lower competition
   - **Format**: Industry landing pages + case studies
   - **Priority**: Medium
   - **Effort**: Moderate

**Technical SEO Checklist:**

| Check | Status | Details |
|-------|--------|---------|
| Page speed | Warning | Homepage LCP: 3.2s (target: <2.5s); optimize images |
| Mobile-friendly | Pass | Responsive design, no issues |
| Structured data | Warning | Missing FAQ schema on 8 support pages; opportunity for rich snippets |
| Sitemap | Pass | XML sitemap present and submitted |
| Robots.txt | Pass | Properly configured |
| HTTPS | Pass | Secure site-wide |
| Broken links | Fail | 12 internal 404s, 6 external broken links |

**Competitor Comparison Summary:**

| Dimension | example.com | Competitor A | Competitor B | Winner |
|-----------|-------------|--------------|--------------|--------|
| Keyword count (ranking top 10) | 340 | 520 | 280 | Competitor A |
| Content depth (avg. blog word count) | 980 | 1,850 | 1,200 | Competitor A |
| Publishing frequency | 2x/month | 8x/month | 4x/month | Competitor A |
| Backlink signals | Strong | Strong | Moderate | Tie |
| Technical score | Excellent | Good | Good | example.com |

**Prioritized Action Plan:**

**Quick Wins (do this week):**
1. Fix 12 internal broken links
2. Add meta descriptions to 34 pages missing them
3. Add FAQ schema to 8 support pages

**Strategic Investments (plan for this quarter):**
1. Build competitor alternative pages (start with top 3 competitors by search volume)
2. Create "how to automate [use case]" content series (8 guides)
3. Refresh 12 high-traffic pages that are 18+ months old
4. Improve page speed (compress images, optimize LCP)

**Step 4:** Rachel reviews the audit. The keyword opportunities are compelling, and the quick wins are indeed quick. She schedules the broken link fixes for today, starts drafting the first competitor alternative page, and shares the strategic recommendations with her content lead. Total audit time: 45 minutes instead of a full day of manual analysis.

**Pro Tips:**

- **Connect Ahrefs or Similarweb** for precise keyword volume, difficulty, and ranking data. Without it, Claude uses web search and provides directional insights rather than exact numbers.
- **Run competitor-specific audits**: `/seo-audit https://competitor.com competitor SEO comparison` to benchmark against a specific competitor.
- **Focus audits by type**: If you know the problem area, specify it: `/seo-audit example.com technical SEO check` for a faster, focused audit.
- **Schedule quarterly full audits** and monthly keyword research checks to stay on top of opportunities.
- **Act on quick wins immediately**: Broken links and missing meta descriptions take minutes to fix and have immediate impact.

**Common Pitfalls:**

- **Ignoring content gaps**: Technical SEO and on-page fixes matter, but content gaps are often the biggest missed opportunity.
- **Keyword difficulty paralysis**: Don't only chase low-difficulty keywords. High-difficulty keywords with strong commercial intent can still be worth targeting with great content.
- **Not updating old content**: Refreshing high-traffic pages that are outdated is one of the highest-ROI SEO activities. Don't just create new content.
- **Treating the audit as a one-time exercise**: SEO is ongoing. The competitive landscape and search algorithms change constantly.

---

### Command: `/email-sequence`

**Syntax:** `/email-sequence [sequence type]`

**Description:** Design and draft complete email sequences with full copy, timing, branching logic, and performance benchmarks for any lifecycle or campaign use case.

**What It Produces:**
- Sequence overview table (all emails with subject lines, purpose, timing, CTA, conditions)
- Full email drafts (subject line options, preview text, body copy, CTA, timing, segment notes)
- Sequence flow diagram (visual representation of branching paths and exits)
- Branching logic notes (all conditions, exits, suppressions)
- A/B test suggestions
- Metrics to track (per-email and sequence-level)
- Performance benchmarks by sequence type

**Required Inputs:**
1. **Sequence type**: Onboarding, lead nurture, re-engagement, product launch, event follow-up, upgrade/upsell, win-back, or educational drip
2. **Goal**: What the sequence should achieve
3. **Audience**: Who receives it, lifecycle stage, segmentation details

**Optional Inputs:**
- Number of emails (if not specified, Claude recommends based on sequence type)
- Timing/cadence preferences
- Brand voice (applies automatically if configured)
- Specific offers, CTAs, or content assets to include

**Business Scenario Walkthrough:**

**Scenario:** Tom is a marketing operations manager building an onboarding sequence for new trial users. He needs the full sequence drafted and ready to implement in Klaviyo by end of week.

**Step 1:** Tom runs:
```
/email-sequence
```

**Step 2:** Claude prompts for details:
```
Sequence type: Onboarding
Goal: Activate new trial users by getting them to complete core setup and invite team members within 14 days
Audience: New trial signups for our project management tool. Mix of individual contributors and team leads. Most are evaluating 2-3 competitors simultaneously.
Number of emails: Recommend what makes sense
Cadence: Preference for tighter spacing early, then taper off
Additional context: We have a 5-minute quickstart video, a setup checklist template, and three customer case studies showcasing fast time-to-value.
```

**Step 3:** Claude recommends a 6-email sequence over 14 days and generates:

**Sequence Overview Table:**

| # | Subject Line | Purpose | Timing | Primary CTA | Condition |
|---|-------------|---------|--------|-------------|-----------|
| 1 | Welcome to [Product]! Here's your 5-minute start | Welcome and first quick win | Day 0 (immediate) | Watch quickstart video | All new trials |
| 2 | Your setup checklist (complete in 10 minutes) | Guide through core setup | Day 1 | Use setup checklist | Did not complete setup |
| 3 | See how [Company] set up in under an hour | Social proof and deeper feature education | Day 3 | Read case study | Completed setup OR opened email 2 |
| 4 | Invite your team and unlock collaboration features | Drive team adoption | Day 5 | Invite team members | Solo user (no invites sent) |
| 5 | You're halfway through your trial—what questions do you have? | Check-in and objection handling | Day 7 | Reply or book support call | All active users |
| 6 | 3 days left in your trial. Here's what to do next. | Conversion nudge | Day 11 | Upgrade to paid plan | Trial not converted |

**Full Email Drafts** (Email 1 example):

**Subject Line Options:**
1. "Welcome to [Product]! Here's your 5-minute start" (benefit-driven)
2. "You're in! Let's get you set up fast" (welcoming, direct)
3. "Your [Product] trial is ready. Start here." (clear, action-oriented)

**Preview Text:**
"Watch this quick video and start managing projects in minutes, not hours."

**Email Purpose:**
Set expectations, deliver immediate value, drive first action (watch video and create first project)

**Body Copy:**

```
Hi [First Name],

Welcome to [Product]! You just took the first step toward [benefit: streamlined project management / faster team collaboration / etc.].

We know you're evaluating options and time is limited, so we made setup fast. Most teams are up and running in under 10 minutes.

Here's how to start:

1. Watch this 5-minute quickstart video [LINK]
2. Create your first project using our template [LINK]
3. Invite a teammate to collaborate (optional but recommended)

That's it. You'll see the value immediately.

Need help? Just reply to this email—our team responds within an hour during business hours.

Looking forward to seeing what you build,
[Name]
[Product] Team

P.S. Check your inbox tomorrow for a setup checklist that'll walk you through key features.
```

**Primary CTA:**
"Watch the 5-minute quickstart" → links to video

**Timing:**
Sent immediately upon trial signup (triggered by account creation event)

**Segment/Condition Notes:**
All new trial signups receive this email. No exclusions.

**Sequence Flow Diagram:**

```
[Trial Signup] → Email 1 (Day 0)
                      |
                 Completed setup? ──Yes──> Email 3 (Day 3) → Email 4 (Day 5)
                      |                         |                  |
                      No                   Opened? ──No──> [Skip to Email 5]
                      |                        |
                      v                       Yes
                  Email 2 (Day 1)              |
                      |                        v
                 Completed setup? ──Yes──> Email 3 (Day 3) → Email 4 (Day 5)
                      |                                            |
                      No                                           |
                      |                                            v
                      +────────────────> Email 5 (Day 7) <─────────+
                                              |
                                         Converted? ──Yes──> [EXIT: Success]
                                              |
                                              No
                                              |
                                              v
                                          Email 6 (Day 11)
                                              |
                                         Converted? ──Yes──> [EXIT: Success]
                                              |
                                              No
                                              |
                                              v
                                    [EXIT: Trial ended, enter win-back sequence]
```

**Branching Logic Notes:**

Exit conditions:
- User upgrades to paid plan → remove from sequence immediately
- User churns before trial ends → remove from sequence
- User unsubscribes → suppress all emails

Branching conditions:
- Email 2 only sent if setup not completed after Email 1
- Email 3 sent to setup completers OR Email 2 openers (engagement signal)
- Email 4 only sent to solo users who haven't invited team members
- Email 6 only sent if trial not converted by Day 11

Re-entry rules:
- Users cannot re-enter this sequence
- If a user who completed trial but didn't convert signs up for a new trial 90+ days later, they enter a modified "returning user" onboarding sequence (separate)

**A/B Test Suggestions:**

1. **Email 1 subject line test**: "Welcome to [Product]! Here's your 5-minute start" vs. "You're in! Let's get you set up fast"
   - Split: 50/50
   - Measure: Open rate (primary), video view rate (secondary)

2. **Email 5 CTA test**: "Reply with your questions" vs. "Book a 15-minute call"
   - Split: 50/50
   - Measure: Response/booking rate

3. **Email 6 urgency framing**: "3 days left" vs. "Make the most of your final days"
   - Split: 50/50
   - Measure: Conversion rate

**Metrics to Track:**

Per-email metrics:
- Open rate, CTR, unsubscribe rate (track for each email individually)

Sequence-level metrics:
- Overall conversion rate (trial → paid)
- Time to conversion (how many days into the sequence)
- Drop-off points (where users disengage)
- Engagement score (opens + clicks across all emails)

Recommended review cadence: Weekly for the first month (to catch issues fast), then monthly

**Performance Benchmarks (Onboarding Sequences):**

| Metric | Target |
|--------|--------|
| Email 1 open rate | 60-70% |
| Email 1 CTR (video) | 15-25% |
| Overall sequence open rate | 40-50% average |
| Trial → Paid conversion rate | 20-30% |
| Unsubscribe rate | <0.5% across sequence |

**Step 4:** Tom reviews the sequence. The copy is solid and matches their tone. He tweaks Email 3 to reference a different case study that's more relevant to their core ICP. He exports the emails to Klaviyo, sets up the flow with branching logic, and launches the sequence. Total time: 2 hours instead of a full day (or more).

**Pro Tips:**

- **Connect Klaviyo or your email platform** for automatic flow setup guidance. Claude can map the branching logic to your platform's specific flow builder.
- **Specify behavioral triggers** in your inputs: "Email 2 should only send if they haven't created a project yet" gives Claude precise branching criteria.
- **Request platform-specific export**: "Export this sequence in a format I can import to Klaviyo" or "Give me HubSpot workflow setup instructions."
- **Test the full sequence on yourself** before launching to real users. Trigger the sequence manually and walk through every email and branch.
- **Ask for complementary sequences**: After building onboarding, ask "Create a re-engagement sequence for users who went inactive after Email 3."

**Common Pitfalls:**

- **Too many emails too fast**: Overwhelming users with daily emails in week 1 increases unsubscribes. Respect the user's inbox.
- **No branching logic**: Sending Email 4 "Invite your team" to users who already invited team members wastes an email opportunity.
- **Generic copy**: Use the user's name, reference their product usage, and personalize based on their segment.
- **Ignoring mobile**: 60%+ of emails are read on mobile. Keep paragraphs short (2-3 sentences), use clear CTAs, and front-load key information.
- **Not tracking drop-off**: If 70% of users disengage after Email 2, that email is the problem. Diagnose and fix it.

---

## Part III: Skills Deep Dive

Skills are background knowledge packages that Claude loads automatically when conversation context is relevant. Unlike commands (which you explicitly invoke), skills work silently to make Claude more knowledgeable about marketing domains.

### Overview of Skills

The marketing plugin includes five skills:

| Skill | Trigger Topics | Core Knowledge Areas |
|-------|---------------|---------------------|
| `brand-voice` | Brand voice, style guide, tone, messaging pillars, terminology | Voice documentation framework, tone adaptation, style enforcement, terminology management |
| `campaign-planning` | Campaign planning, channel strategy, content calendar, budget allocation, KPIs | Campaign frameworks (OAMCM), channel selection, calendar creation, budget approaches, success metrics |
| `competitive-analysis` | Competitive research, positioning, messaging comparison, battlecards | Research methodology, messaging frameworks, content gap analysis, positioning strategy, battlecard creation |
| `content-creation` | Writing content, content structure, headlines, CTAs, SEO | Content type templates, channel best practices, SEO fundamentals, headline formulas, CTA guidelines |
| `performance-analytics` | Marketing metrics, reporting, trend analysis, attribution, optimization | Metrics by channel, reporting templates, trend analysis, attribution models, optimization frameworks |

---

### Skill: `brand-voice`

**Name:** brand-voice

**Trigger Description (from SKILL.md frontmatter):**
> "Apply and enforce brand voice, style guide, and messaging pillars across content. Use when reviewing content for brand consistency, documenting a brand voice, adapting tone for different audiences, or checking terminology and style guide compliance."

**What It Provides:**

This skill gives Claude expertise in:
- How to document a brand voice from scratch
- How to apply voice attributes consistently
- How to adapt tone across channels and situations while maintaining voice
- How to enforce style guide rules (grammar, punctuation, formatting)
- How to manage terminology (preferred terms, avoided terms, inclusive language)

**Core Knowledge Areas:**

1. **Brand Voice Documentation Framework**: A complete structure for defining brand personality, voice attributes, audience awareness, core messaging pillars, tone spectrum, style rules, and terminology
2. **Voice Attributes**: Common attribute spectrums (formal/casual, authoritative/peer-level, warm/direct) with examples of how to define each attribute
3. **Tone Adaptation**: How voice stays consistent while tone adapts by channel (blog vs. social vs. email vs. support) and by situation (product launch vs. incident response)
4. **Style Guide Enforcement**: Decision tables for grammar rules (Oxford comma, contractions, number formatting), formatting conventions, and punctuation policies
5. **Terminology Management**: Frameworks for preferred terms, product names, inclusive language, jargon management, and competitor category terms

**Practical Example:**

**User:** "Help me document our brand voice. We're a B2B SaaS company, and we want to sound knowledgeable but not condescending, and approachable but still professional."

**Claude (drawing on the brand-voice skill):**

"Let me help you structure your brand voice documentation using a framework that makes it easy to apply consistently.

**Brand Voice Framework for [Your Company]**

**1. Brand Personality**
If your brand were a person: 'A knowledgeable colleague who explains complex things simply, celebrates your wins genuinely, and never talks down to you.'

**2. Voice Attributes**

Let's define 3-4 core attributes that capture 'knowledgeable but not condescending, approachable but professional':

**Attribute 1: Expert but Accessible**
- We are: Knowledgeable and authoritative without jargon or complexity for complexity's sake
- We are not: Dumbed-down or overly simplistic; we respect our audience's intelligence
- This sounds like: 'Here's what you need to know about attribution modeling, and why it matters for your team.'
- This does NOT sound like: 'Attribution modeling is a sophisticated analytical framework leveraging advanced statistical methodologies.'

**Attribute 2: Warm but Professional**
- We are: Friendly, empathetic, genuinely helpful
- We are not: Overly casual, using slang, or trying too hard to be cool
- This sounds like: 'We know this can be frustrating. Here's how to fix it in three steps.'
- This does NOT sound like: 'Hey there! This is totally annoying, right? Let's crush this bug! 💪'

**Attribute 3: Direct and Clear**
- We are: Concise, active voice, front-loaded key information
- We are not: Vague, passive, burying the lead
- This sounds like: 'Your campaign drove 340 leads this month—15% above target.'
- This does NOT sound like: 'It has been observed that lead generation activities in the reporting period exceeded performance expectations.'

[Claude continues with tone adaptation guidance, style rules, and terminology recommendations specific to B2B SaaS...]"

**When This Skill Activates:**

- User asks about brand voice, tone, or messaging
- User is drafting content and mentions "our brand voice" or "on-brand"
- User runs `/brand-review` (the command explicitly references this skill)
- User asks how to adapt messaging for different channels or audiences
- User discusses style guide decisions

---

### Skill: `campaign-planning`

**Name:** campaign-planning

**Trigger Description:**
> "Plan marketing campaigns with objectives, audience segmentation, channel strategy, content calendars, and success metrics. Use when launching a campaign, planning a product launch, building a content calendar, allocating budget across channels, or defining campaign KPIs."

**What It Provides:**

Claude gains expertise in:
- The OAMCM framework (Objective, Audience, Message, Channel, Measure) for structuring any campaign
- How to write SMART campaign objectives
- Audience profiling and segmentation
- Message hierarchy and proof point development
- Channel selection criteria and allocation frameworks
- Content calendar creation and production timeline estimation
- Budget allocation approaches and optimization principles
- Success metrics tailored to campaign type (awareness, lead gen, product launch, retention, event)

**Core Knowledge Areas:**

1. **Campaign Framework (OAMCM)**: Five-part structure ensuring every campaign has clear objective, defined audience, core message, appropriate channels, and success metrics
2. **Channel Selection Guide**: Detailed table of owned, earned, and paid channels with best-use cases, typical metrics, and effort estimates
3. **Content Calendar Creation**: Process for building calendars, cadence guidelines, production timeline benchmarks
4. **Budget Allocation**: Percentage-of-revenue method, channel allocation framework, optimization principles
5. **Success Metrics by Campaign Type**: KPI tables for awareness, lead generation, product launch, retention, and event campaigns

**Practical Example:**

**User:** "What channels should I use for a product launch campaign targeting mid-market finance teams?"

**Claude (drawing on campaign-planning skill):**

"For a product launch targeting mid-market finance teams, here's a channel strategy based on where this audience engages and what launch objectives typically require:

**Recommended Channel Mix:**

**Owned Channels (60% of effort):**
- **Email to existing customers/prospects** (high priority): Finance teams check email religiously. Segment by engagement level—power users get early access framing, inactive users get 'what's new' re-engagement.
- **Blog/website** (medium priority): Launch announcement post, feature deep-dives, FAQ page. Finance buyers research thoroughly before decisions.
- **Webinar** (high priority): Live product demo targeting CFOs and finance directors. This audience values seeing the product in action with Q&A.

**Earned Channels (20% of effort):**
- **Industry publication guest posts** (CFO.com, Accounting Today): Finance teams trust industry media. Pitch thought leadership on 'how [problem your product solves] impacts financial operations.'
- **Influencer/partner announcements** (if you have accounting firm or fintech partnerships): Endorsements carry weight in finance.

**Paid Channels (20% of effort):**
- **LinkedIn ads** (primary paid): Target by job title (CFO, Finance Director, Controller), company size, and industry. Finance professionals are active on LinkedIn for professional content.
- **Search ads** (secondary): Capture high-intent searches for the problem you solve. Finance teams search for solutions by problem, not by browsing.

**Why this mix for finance teams:**
- Finance buyers are risk-averse and research-heavy → need depth (webinar, blog content)
- They trust industry authority → earned media and thought leadership critical
- They are on LinkedIn but not other social → focus paid budget there
- Email is their primary communication channel → leverage your list

**Channel to avoid:**
- Consumer social (Instagram, Facebook): Finance professionals don't discover B2B tools here
- Broad display ads: Finance audience is narrow; targeted LinkedIn outperforms

**Would you like me to build a full launch campaign plan with timeline and content calendar for these channels?**"

**When This Skill Activates:**

- User runs `/campaign-plan` command
- User asks about campaign strategy, channel selection, or content calendar
- User discusses budget allocation or KPIs for marketing
- User mentions launching a product or planning a campaign

---

### Skill: `competitive-analysis`

**Name:** competitive-analysis

**Trigger Description:**
> "Research competitors and compare positioning, messaging, content strategy, and market presence. Use when analyzing a competitor, building battlecards, identifying content gaps, comparing feature messaging, or preparing competitive positioning recommendations."

**What It Provides:**

Claude gains frameworks for:
- Systematic competitive research across primary and secondary sources
- Messaging comparison and narrative analysis
- Content gap identification
- Positioning strategy and category selection
- Battlecard creation for sales enablement

**Core Knowledge Areas:**

1. **Competitive Research Methodology**: Comprehensive list of research sources (primary: website, blog, social, demos; secondary: review sites, analysts, news, SEO tools) and structured research process
2. **Messaging Comparison Frameworks**: Messaging matrix structure, value proposition comparison, narrative analysis (villain/hero/transformation/stakes)
3. **Content Gap Analysis**: How to audit competitor content by topic and format, identify coverage gaps and opportunities
4. **Positioning Strategy**: Positioning statement framework, positioning map (2x2 matrix), category strategy options, positioning pitfalls to avoid
5. **Battlecard Creation**: One-page structure for sales teams with competitor overview, their pitch, strengths/weaknesses, differentiators, objection handling, landmines

**Practical Example:**

**User:** "I need to create a battlecard for our sales team to use against Competitor X. What should I include?"

**Claude (drawing on competitive-analysis skill):**

"A battlecard is a one-page reference for your sales team to use in competitive deals. Here's the structure that works best:

**Battlecard for Competitor X**

**Header:**
- Competitor logo
- Last updated: [date]
- Win rate against this competitor: [if you track this]

**Quick Overview:**
- What they do (one sentence): [e.g., 'Enterprise workflow automation platform targeting IT and dev teams']
- Target customer: [e.g., 'Large enterprises with complex compliance requirements']
- Pricing model: [e.g., 'Enterprise-only, custom pricing starting ~$50K/year']
- Recent news: [e.g., 'Raised Series C in October; launched AI features in Q4']

**Their Pitch (What They Say):**
- Primary tagline: [their homepage headline]
- Top 3 claimed differentiators:
  1. [e.g., 'Enterprise-grade security and compliance']
  2. [e.g., 'Unlimited workflows and users']
  3. [e.g., 'Dedicated customer success manager']

**Strengths (Be Honest):**
- Where they genuinely excel: [e.g., 'Strong in regulated industries; excellent compliance documentation']
- What customers like (from reviews): [e.g., 'Robust audit trails; responsive support for enterprise accounts']
- Features where they lead: [e.g., 'SOC2 Type II, HIPAA, GDPR certified out of the box']

**Weaknesses:**
- Consistent customer complaints (from G2/Capterra): [e.g., 'Steep learning curve; requires developer for setup; slow to implement new features']
- Technical limitations: [e.g., 'No no-code builder—all workflows require scripting']
- Gaps in offering: [e.g., 'No mid-market or SMB tier; minimum commitment is $50K']

**Our Differentiators:**
1. **Ease of setup**: We have a no-code builder; customers are live in days vs. their months-long implementation.
   - Why it matters: Faster time to value, no dev resources needed
   - Proof: Average setup time 5 days vs. 60+ days for Competitor X
2. **Mid-market fit**: We have flexible pricing from $5K to $100K+; they start at $50K minimum.
   - Why it matters: Accessible for growing companies who will outgrow their current tool but aren't enterprise-scale yet
   - Proof: 60% of our customers are 50-500 employees
3. **Rapid iteration**: We ship weekly; they ship quarterly.
   - Why it matters: Customer feedback drives product faster
   - Proof: 42 feature releases last quarter vs. their 8

**Objection Handling:**

| If the prospect says... | Respond with... |
|------------------------|-----------------|
| 'Competitor X has better enterprise security' | 'We're SOC2 Type II certified as well, and we add HIPAA compliance in our Enterprise tier. Where we differ is ease of use—our platform is secure without requiring a dedicated admin to manage it. What specific compliance requirements are you evaluating?' |
| 'Competitor X offers unlimited users' | 'That's true for their enterprise tier. Let me ask: are you planning to have hundreds of users, or a core team managing workflows? Most of our customers find 10-50 seats is right-sized, and our per-seat pricing is more predictable than their enterprise-only model.' |
| 'We've heard Competitor X has better support' | 'Their enterprise customers do get dedicated CSMs. We offer that in our Enterprise tier too, plus our standard tier includes live chat support with sub-2-hour response time. Have you experienced issues with support on your current tool?' |

**Landmines to Set (Ask These Early):**
- 'How important is time to value? Are you looking to go live in weeks or months?' (highlights their slow implementation)
- 'Do you have developer resources available to build and maintain workflows?' (exposes their technical requirements)
- 'What's your timeline for seeing ROI?' (their long implementation delays ROI)

**Landmines to Defuse:**
They might encourage prospects to ask you:
- 'Can you support enterprises with 10,000+ employees?' → 'We have customers at that scale in [industry]. Our largest deployment is [number] users across [number] teams. What size deployment are you planning?'

**Win/Loss Themes:**
- We win when: Customer values speed to value, has limited technical resources, is mid-market
- We lose when: Highly regulated industry (healthcare, finance) where they've already invested in Competitor X's compliance infrastructure, or enterprise buyer who values brand name recognition

[End of battlecard]

Would you like me to research Competitor X and fill in these sections with real data?"

**When This Skill Activates:**

- User runs `/competitive-brief` command
- User asks about a specific competitor
- User mentions battlecards, positioning, or competitive messaging
- User discusses "what competitors are doing" or market landscape

---

### Skill: `content-creation`

**Name:** content-creation

**Trigger Description:**
> "Draft marketing content across channels — blog posts, social media, email newsletters, landing pages, press releases, and case studies. Use when writing any marketing content, when you need channel-specific formatting, SEO-optimized copy, headline options, or calls to action."

**What It Provides:**

Claude gains templates and best practices for:
- Seven content types (blog, social, email, landing page, press release, case study, each with detailed structure)
- Channel-specific writing guidelines (blog, social media by platform, email, web)
- SEO fundamentals for content (keyword strategy, on-page checklist, content-SEO integration)
- Headline and hook formulas
- CTA best practices and examples by context

**Core Knowledge Areas:**

1. **Content Type Templates**: Detailed structural templates for blog posts, social media, email newsletters, landing pages, press releases, case studies
2. **Writing Best Practices by Channel**: Channel-specific guidance (reading level, paragraph length, tone, formatting) for blog, LinkedIn, Twitter/X, Instagram, Facebook, email, web
3. **SEO Fundamentals**: Keyword strategy, on-page checklist (title tag, meta description, URL, headers, images, links), content-SEO integration tips
4. **Headline and Hook Formulas**: Six headline patterns and six hook patterns with examples
5. **CTA Best Practices**: Principles (action verbs, specificity, urgency, risk reduction), examples by context (blog, landing page, email, social, case study), placement guidance

**Practical Example:**

**User:** "What's a good structure for a case study about how a customer achieved results using our product?"

**Claude (drawing on content-creation skill):**

"Here's the proven case study structure that converts:

**Case Study Structure:**

**1. Title**: '[Customer] achieves [result] with [product]'
Example: 'Acme Corp reduces reporting time by 60% with BuildRight'

**2. Snapshot** (sidebar or callout box at the top):
- Customer name: Acme Corp
- Industry: B2B SaaS
- Company size: 150 employees
- Product used: BuildRight Pro
- Key result: 60% reduction in weekly reporting time

**3. Challenge Section:**
What problem the customer faced before using your product. Be specific and quantify the pain if possible.

Example:
> 'Acme Corp's operations team was spending 12 hours every week manually compiling reports from five different tools. The process was error-prone, and by the time reports were ready, the data was already outdated. This delayed decision-making and frustrated leadership.'

**4. Solution Section:**
What was implemented and how. Focus on the process and the customer's experience, not just your product features.

Example:
> 'Acme implemented BuildRight Pro in January 2024. Within two weeks, they had automated their entire reporting workflow by connecting their five tools to BuildRight's unified dashboard. The operations team worked with BuildRight's customer success team to customize report templates for each stakeholder group.'

**5. Results Section:**
Quantified outcomes with specific metrics. Use numbers, percentages, and timeframes.

Example:
> 'Within 30 days of going live:
> - Weekly reporting time dropped from 12 hours to 4.5 hours (62% reduction)
> - Report accuracy increased to 99.8% (previously 94% due to manual errors)
> - Leadership received reports 3 days faster, enabling quicker decision-making
> - The operations team redirected 7.5 hours/week to strategic projects instead of manual data entry'

**6. Customer Quote:**
A testimonial from a named individual with title and company. Make it authentic and specific.

Example:
> 'BuildRight transformed how we operate. What used to take our team half a day every week now happens automatically. More importantly, our leadership trusts the data because errors are virtually eliminated. This was the best operational investment we made last year.'
> — Sarah Johnson, Director of Operations, Acme Corp

**7. Call to Action:**
Clear next step for readers who want similar results.

Example:
> 'See how BuildRight can transform your operations. Book a demo to see the platform in action, or explore our ROI calculator to estimate your time savings.'

**Best Practices:**
- Get customer approval for all quotes and metrics before publishing
- Use the customer's name and logo (with permission)
- Include a visual: screenshot of the product in action or a simple metric chart
- Keep it scannable: use subheadings, bullets, and callout boxes
- Aim for 600-900 words (enough depth to be credible without losing readers)

Would you like me to draft a case study for a specific customer, or help you structure your results into this format?"

**When This Skill Activates:**

- User runs `/draft-content` command
- User asks how to structure a specific content type
- User mentions headlines, CTAs, or SEO
- User discusses writing for a specific channel (email, social, blog)

---

### Skill: `performance-analytics`

**Name:** performance-analytics

**Trigger Description:**
> "Analyze marketing performance with key metrics, trend analysis, and optimization recommendations. Use when building performance reports, reviewing campaign results, analyzing channel metrics (email, social, paid, SEO), or identifying what's working and what needs improvement."

**What It Provides:**

Claude becomes fluent in:
- Marketing metrics across all major channels (email, social, paid, SEO, content, pipeline)
- How to structure performance reports (weekly, monthly, quarterly)
- Trend analysis and forecasting techniques
- Attribution modeling basics
- Optimization frameworks (how to diagnose underperformance and prioritize fixes)

**Core Knowledge Areas:**

1. **Key Marketing Metrics by Channel**: Comprehensive tables defining metrics, benchmarks, and what each metric indicates for email marketing, social media, paid advertising, SEO, content marketing, and overall pipeline
2. **Reporting Templates and Dashboards**: Formats for weekly, monthly, and quarterly reports; dashboard design principles
3. **Trend Analysis and Forecasting**: How to identify trends, analyze patterns, and create simple forecasts
4. **Attribution Modeling Basics**: Explanation of last-touch, first-touch, linear, time decay, position-based, and data-driven attribution; when to use each; pitfalls to avoid
5. **Optimization Recommendations Framework**: Process for diagnosing issues (identify, diagnose, hypothesize, prioritize, test, measure, scale), optimization levers by funnel stage, prioritization matrix (impact vs. effort), testing best practices

**Practical Example:**

**User:** "My email open rates dropped from 28% to 19% over the last two months. What should I check?"

**Claude (drawing on performance-analytics skill):**

"A 9-percentage-point drop in email open rates is significant. Here's a diagnostic framework to identify the cause:

**Potential Causes to Investigate:**

**1. List Quality Issues:**
- Has your list grown significantly with new, less-engaged subscribers? New subscribers often have lower open rates initially.
- Check: Compare open rates for contacts added in the last 60 days vs. older contacts. If new subscribers are dragging down the average, segment them into a separate onboarding flow.

**2. Deliverability Problems:**
- Are more emails landing in spam or being blocked by ISPs?
- Check: Look at bounce rate and spam complaint rate. If bounce rate increased or you see spam complaints, your sender reputation may be declining.
- Fix: Clean your list (remove hard bounces, suppress unengaged contacts who haven't opened in 6+ months), ensure SPF/DKIM/DMARC are configured.

**3. Subject Line Fatigue:**
- Have you been using similar subject line patterns repeatedly?
- Check: Review your last 20 subject lines. If they're repetitive or formulaic, subscribers may be tuning out.
- Fix: Test new subject line approaches (question-based, curiosity-driven, benefit-focused, personalized).

**4. Send Frequency Change:**
- Did you increase email frequency? Sending too often causes subscribers to ignore your emails or mark them as spam.
- Check: Compare send frequency now vs. two months ago. If you went from 2x/week to 4x/week, that's likely the culprit.
- Fix: Reduce frequency, or let subscribers choose their cadence (daily digest, weekly, biweekly).

**5. Send Time Shift:**
- Did you change when you send emails (day of week or time of day)?
- Check: Compare send times. If you moved from Tuesday 10am to Friday 5pm, engagement will drop (people check email less on Friday evenings).
- Fix: Revert to your previous send time or A/B test optimal send times.

**6. Content Relevance:**
- Has your content shifted away from what your audience signed up for?
- Check: Review email topics from two months ago vs. now. If you've changed focus (e.g., from educational content to sales-heavy promotions), engagement suffers.
- Fix: Survey your list asking what content they want; return to proven content themes.

**7. Benchmark Context:**
- What's your industry and audience type? 19% may actually be acceptable depending on context.
- Reference: B2B email open rates average 15-30%, B2C average 15-25%. If you're B2B and at 19%, you're within range but below your own baseline.

**Immediate Action Plan:**

**This week:**
1. Pull a deliverability report (bounce rate, spam complaints, inbox placement if your ESP provides it)
2. Segment open rates by subscriber cohort (new vs. old, engaged vs. unengaged)
3. Review subject lines from the last 30 days for patterns

**Next week:**
Based on findings, test:
- Subject line variations (if repetitive subject lines are the issue)
- Send frequency reduction (if you increased frequency)
- List cleaning (if deliverability metrics show problems)

**Measure:**
Track open rate weekly. You should see improvement within 2-3 sends if you've addressed the root cause.

Would you like me to help you analyze specific data, or walk through any of these diagnostic steps in detail?"

**When This Skill Activates:**

- User runs `/performance-report` command
- User asks about marketing metrics, KPIs, or benchmarks
- User mentions analyzing performance, trends, or reporting
- User discusses attribution or optimization

---

## Part IV: Connectors & MCP Servers

### Understanding the Connector System

The marketing plugin connects to external tools and services via MCP (Model Context Protocol) servers. These connections allow Claude to read data from your marketing stack, post content to communication tools, and reference documents from your knowledge base.

**Two key concepts:**

1. **MCP Servers**: The actual technical connections defined in `.mcp.json`
2. **Placeholder System**: Tool-agnostic references in plugin files (like `~~chat` or `~~marketing automation`) that get mapped to your specific tools

### MCP Servers Included in the Plugin

The marketing plugin pre-configures connections to nine popular services:

| MCP Server Name | Service | Type | Purpose | Authentication |
|----------------|---------|------|---------|----------------|
| `slack` | Slack | HTTP | Post reports, briefs, and drafts to team channels; search message history | OAuth via Slack sign-in |
| `canva` | Canva | HTTP | Access and edit design assets | OAuth via Canva sign-in |
| `figma` | Figma | HTTP | Reference design files and brand assets | OAuth via Figma sign-in |
| `hubspot` | HubSpot | HTTP | Pull campaign data, manage contacts, track marketing automation performance | OAuth via HubSpot sign-in |
| `amplitude` | Amplitude | HTTP | Pull product analytics and user behavior data for performance reporting | OAuth via Amplitude sign-in |
| `notion` | Notion | HTTP | Access brand guidelines, campaign briefs, style guides, personas | OAuth via Notion sign-in |
| `ahrefs` | Ahrefs | HTTP | SEO keyword research, backlink analysis, site audits, competitor SEO data | OAuth via Ahrefs sign-in |
| `similarweb` | Similarweb | HTTP | Competitive traffic analysis and market benchmarking | OAuth via Similarweb sign-in |
| `klaviyo` | Klaviyo | HTTP | Draft and review email marketing sequences and campaigns | OAuth via Klaviyo sign-in |

**How MCP Servers Enhance Commands:**

| Command | Without MCP | With MCP Servers Connected |
|---------|------------|---------------------------|
| `/campaign-plan` | You manually provide audience and historical data | Claude pulls persona docs from Notion, references historical campaign performance from HubSpot |
| `/performance-report` | You paste metrics data | Claude automatically pulls email metrics from Klaviyo, user behavior from Amplitude, campaign data from HubSpot |
| `/seo-audit` | Claude uses web search for keyword research | Claude pulls precise keyword rankings, search volume, and backlink data from Ahrefs |
| `/competitive-brief` | Claude uses web search for competitor research | Claude supplements web search with competitive traffic data from Similarweb |
| `/draft-content` | Claude generates content based on your description | Claude references brand guidelines stored in Notion, checks Figma for brand asset specifications |
| `/brand-review` | You paste brand guidelines each time | Claude automatically loads brand voice documentation from Notion |

### The Placeholder System Explained

Plugin files use `~~category` syntax to refer to tools generically. This makes the plugin adaptable to different organizations' tool stacks.

**Example from `/campaign-plan` command:**
```markdown
If ~~product analytics is connected, reference any available historical 
performance benchmarks to inform targets.
```

When you have Amplitude connected, `~~product analytics` resolves to Amplitude. If you use Mixpanel instead, it resolves to Mixpanel.

**Placeholder Categories in the Marketing Plugin:**

| Category | Placeholder Syntax | Pre-Configured Tools | Common Alternatives |
|----------|-------------------|---------------------|---------------------|
| Chat/messaging | `~~chat` | Slack | Microsoft Teams, Discord |
| Design | `~~design` | Canva, Figma | Adobe Creative Cloud, Sketch |
| Marketing automation | `~~marketing automation` | HubSpot | Marketo, Pardot, Mailchimp, ActiveCampaign |
| Product analytics | `~~product analytics` | Amplitude | Mixpanel, Google Analytics, Heap |
| Knowledge base | `~~knowledge base` | Notion | Confluence, Guru, Google Docs |
| SEO tools | `~~SEO` | Ahrefs, Similarweb | Semrush, Moz |
| Email marketing | `~~email marketing` | Klaviyo | Mailchimp, Brevo, Customer.io, Sendgrid |

### Connecting an MCP Server

**Step 1: Trigger the Connection**

When you run a command that references an MCP server you haven't connected yet, Claude will prompt:

```
This command works best with HubSpot connected for campaign data. 
Would you like to connect HubSpot now?
```

**Step 2: Authenticate**

If you choose yes, Claude provides a link to the service's authentication page. You'll go through the standard OAuth flow (sign in, approve permissions).

**Step 3: Verify**

After authentication, Claude confirms:

```
HubSpot connected successfully. I can now pull campaign performance 
data, contact lists, and workflow metrics.
```

**Alternative: Connect Manually**

You can also connect MCP servers outside of command execution by asking:

```
Connect HubSpot
```

Claude will initiate the authentication flow.

### Which Connectors Are Essential?

**For Basic Functionality (Plugin Works Without These):**

The marketing plugin is designed to function without any MCP connections. Every command will prompt you for information instead of pulling it automatically. You can use the plugin effectively with zero connections.

**For Enhanced Functionality:**

| Use Case | Essential Connectors | Why |
|----------|---------------------|-----|
| Campaign planning and reporting | HubSpot or similar marketing automation | Automatic access to historical campaign data, contact segmentation, performance metrics |
| Performance analysis | Amplitude or Mixpanel + HubSpot or Klaviyo | Real performance data instead of manual input |
| SEO workflows | Ahrefs or Semrush | Precise keyword data, ranking tracking, backlink analysis |
| Brand consistency | Notion or Confluence | Centralized brand guidelines that load automatically |
| Team collaboration | Slack or Teams | Share briefs and reports directly without copy-paste |
| Content creation with brand assets | Figma or Canva | Reference design specs and brand assets |

**Recommended Connection Priority:**

1. **Marketing automation or CRM** (HubSpot, Marketo, Salesforce): This is the highest-impact connection for most commands.
2. **Knowledge base** (Notion, Confluence): Enables automatic brand guideline loading.
3. **Chat** (Slack, Teams): Makes sharing outputs frictionless.
4. **Product analytics** (Amplitude, Mixpanel): Critical for performance reporting if you track user behavior.
5. **SEO tools** (Ahrefs, Semrush): Essential if SEO is a significant focus.
6. **Email marketing** (Klaviyo, Mailchimp): Important if email is a primary channel.
7. **Design tools** (Figma, Canva): Nice-to-have for content creation referencing brand assets.

### Adding a Tool Not Pre-Configured

If you use a tool that's not in the plugin's `.mcp.json` but has an MCP server available, you can add it.

**Step 1: Find the MCP Server**

Search for "[tool name] MCP server" or check the tool's integration documentation.

**Step 2: Add to `.mcp.json`**

Edit the `.mcp.json` file in the plugin directory:

```json
{
  "mcpServers": {
    "slack": { "type": "http", "url": "https://mcp.slack.com/mcp" },
    ...existing servers...,
    "your-new-tool": {
      "type": "http",
      "url": "https://mcp.yourtool.com/endpoint"
    }
  }
}
```

**Step 3: Connect**

Ask Claude to connect to the new tool:

```
Connect to your-new-tool
```

### MCP Connection Troubleshooting

**Issue: "I authenticated but Claude says the tool isn't connected"**

**Fix:**
- Refresh your Claude session (close and reopen)
- Check that you approved all requested permissions during OAuth
- Try disconnecting and reconnecting: "Disconnect HubSpot" then "Connect HubSpot"

**Issue: "Claude can't find data in [tool]"**

**Fix:**
- Verify you have data in that tool (e.g., if HubSpot is empty, Claude can't pull data)
- Check that Claude is searching the right workspace/project (ask "Which HubSpot workspace are you connected to?")
- Be specific about what you're looking for: Instead of "pull campaign data," say "pull data for the Q4 LinkedIn campaign"

**Issue: "The connection keeps timing out"**

**Fix:**
- The tool's API may be slow or rate-limited
- Try a more specific request (narrow the date range, limit the number of records)
- Check the tool's status page for API outages

---

## Part V: Customization & Extension

The marketing plugin is a general-purpose foundation. Most organizations will want to customize it for their industry, company-specific processes, or unique marketing approaches. This section shows you how, with reference to the plugin development guide for detailed technical instructions.

For complete technical details on the extension framework, see [Plugin Development Guide](plugin-development-guide.md).

### Three Customization Approaches

| Approach | Best For | Effort Level | Maintainability |
|----------|---------|--------------|----------------|
| **A: Direct Modification** | Quick personal experiments, testing ideas | Low | Updates may overwrite changes |
| **B: Fork the Plugin** | Team-wide customizations, significant changes | Medium | Full control, manual update merging |
| **C: CLAUDE.md Rules** | Project-specific additions, lightest touch | Low | Coexists with plugin, no conflicts |

### Approach A: Direct Plugin Modification

Edit the plugin's files directly. This is the fastest way to experiment but has risks if the plugin updates.

**Example: Adding Pharmaceutical Compliance to Brand Review**

**Scenario:** Your company is a pharmaceutical marketer. You need `/brand-review` to check for regulatory compliance (fair balance, MLR requirements, off-label claim detection).

**Implementation:**

1. Open `/Users/tomi/Development/Zed/cowork_handbooks/cowork_plugins/marketing/1.0.0/commands/brand-review.md`

2. Add a new section after "Legal and Compliance Flags":

```markdown
### Pharmaceutical Compliance Checks (If Applicable)

If the content is for a pharmaceutical product, also evaluate:

**Fair Balance:**
- Do efficacy claims have corresponding risk information?
- Is risk information presented with equal prominence to efficacy?
- Is the indication statement accurate per approved labeling?

**Off-Label Risk:**
- Are there any claims or implications for uses not in the approved indication?
- Are patient population references consistent with approved labeling?

**Required Elements:**
- Is the product name accompanied by the generic (INN) name on first use?
- Are references cited for all efficacy or safety claims?
- Is the prescribing information reference included?

Flag any pharmaceutical compliance concerns as **Critical** severity.
```

3. Save the file. The change takes effect immediately.

**Pros:**
- Fast (5 minutes to implement)
- No installation or setup required

**Cons:**
- If the marketing plugin updates to version 1.0.1, your changes may be overwritten
- No separation between original and customized content

### Approach B: Fork the Plugin (Recommended for Teams)

Create a customized version of the plugin that incorporates your company or industry-specific needs. This is the right choice when multiple people on your team will use the customizations.

**Example: Creating a Pharma Marketing Plugin**

**Scenario:** You're a pharmaceutical marketing team. You need all the marketing plugin capabilities plus pharma-specific skills for regulatory compliance, medical affairs workflows, and HCP-focused campaigns.

**Implementation:**

**Step 1: Copy the Plugin**

```bash
cp -r /path/to/marketing/1.0.0 /path/to/marketing-pharma/1.0.0
```

**Step 2: Update plugin.json**

Edit `marketing-pharma/1.0.0/.claude-plugin/plugin.json`:

```json
{
  "name": "marketing-pharma",
  "version": "1.0.0",
  "description": "Marketing plugin extended for pharmaceutical and life sciences companies. Includes regulatory compliance, medical affairs, and HCP campaign workflows.",
  "author": {
    "name": "Your Company"
  }
}
```

**Step 3: Add Pharma-Specific Skills**

Create `marketing-pharma/1.0.0/skills/regulatory-compliance/SKILL.md`:

```markdown
---
name: regulatory-compliance
description: >
  Pharmaceutical marketing regulatory compliance rules and MLR review 
  requirements. Use when creating content for pharmaceutical products, 
  reviewing promotional materials for fair balance, preparing for MLR 
  review, checking off-label risks, or working with HCP-targeted marketing.
---

# Pharmaceutical Marketing Regulatory Compliance

## Fair Balance Requirements

All promotional materials for prescription products must present a 
fair balance between efficacy information and risk information...

[Full skill content with detailed compliance frameworks]
```

Create `marketing-pharma/1.0.0/skills/medical-affairs/SKILL.md`:

```markdown
---
name: medical-affairs
description: >
  Medical affairs and scientific communication strategies for 
  pharmaceutical marketing. Use when planning KOL engagement, 
  medical education programs, congress strategies, or MSL field activities.
---

# Medical Affairs for Pharma Marketing

## KOL Engagement Framework

[Detailed framework for identifying, tiering, and engaging key opinion leaders]
```

**Step 4: Add Pharma-Specific Command**

Create `marketing-pharma/1.0.0/commands/mlr-review.md`:

```markdown
---
description: Prepare promotional materials for medical-legal-regulatory review
argument-hint: "<content type>"
---

# MLR Review Preparation

Generate an MLR review package for pharmaceutical promotional materials...

[Full command workflow for preparing materials for MLR review]
```

**Step 5: Update MCP Connections**

Edit `marketing-pharma/1.0.0/.mcp.json` to add pharma-specific tools:

```json
{
  "mcpServers": {
    ...existing servers...,
    "pubmed": {
      "type": "http",
      "url": "https://mcp.pubmed.com/api"
    },
    "clinicaltrials": {
      "type": "http",
      "url": "https://mcp.clinicaltrials.gov/mcp"
    }
  }
}
```

**Step 6: Update CONNECTORS.md**

Add pharma-specific categories:

```markdown
| Category | Placeholder | Included servers | Other options |
|----------|-------------|-----------------|---------------|
| Medical literature | `~~medical literature` | PubMed | Embase, Cochrane |
| Clinical trials database | `~~clinical trials` | ClinicalTrials.gov | EU Clinical Trials Register |
```

**Step 7: Install the Forked Plugin**

```bash
claude plugins install /path/to/marketing-pharma.plugin
```

Or place the `marketing-pharma/1.0.0/` directory in your plugins folder.

**Result:**

Your team now has `marketing-pharma` plugin with:
- All original marketing plugin capabilities
- Pharma regulatory compliance skill that activates when discussing pharmaceutical content
- Medical affairs skill for KOL engagement and scientific communication
- `/mlr-review` command for preparing materials for regulatory review
- PubMed and ClinicalTrials.gov connections for evidence-based content

**Maintenance:**

When the original marketing plugin updates to 1.0.1, you can:
1. Review the changelog for new features
2. Manually merge relevant changes into your fork
3. Keep your pharma-specific additions unchanged

**Pros:**
- Clean separation between original and customized content
- Full control over the plugin
- Easy to share across your team
- Can receive updates by manually merging

**Cons:**
- More effort than direct modification
- Requires manual update merging when the original plugin changes

### Approach C: Complementary Skills via CLAUDE.md (Lightest Touch)

Keep the original plugin untouched. Add your customizations in your project's `CLAUDE.md` file and project-level skills directory.

**Example: Adding Company-Specific Brand Voice**

**Scenario:** You use the standard marketing plugin, but you want Claude to automatically apply your company's brand voice rules when drafting content, without modifying the plugin itself.

**Implementation:**

**Step 1: Create a Project-Level Skill**

Create `.claude/skills/acme-brand-voice/SKILL.md` in your project directory:

```markdown
---
name: acme-brand-voice
description: >
  Acme Corp brand voice guidelines, terminology, and style rules. 
  Use when drafting any marketing content for Acme Corp, reviewing 
  content against Acme brand standards, or adapting tone for 
  Acme's target audiences.
---

# Acme Corp Brand Voice

## Voice Attributes

**Confident but not arrogant**
- We are: Authoritative based on our expertise and results
- We are not: Boastful or putting down competitors
- This sounds like: "Our customers see results in the first week."
- This does NOT sound like: "We're the best platform on the market, and everyone else is trash."

**Warm but professional**
- We are: Friendly, empathetic, helpful
- We are not: Overly casual or using slang
- This sounds like: "We know this can be frustrating. Here's how to fix it."
- This does NOT sound like: "Ugh, that's the worst! Let's crush this bug together!"

**Clear and direct**
- We are: Concise, front-loaded, active voice
- We are not: Vague, jargon-heavy, burying the lead
- This sounds like: "Your campaign drove 340 leads this month—15% above target."
- This does NOT sound like: "Marketing activities in the reporting period demonstrated performance exceeding baseline expectations."

## Terminology

| Use This | Not This |
|----------|----------|
| Acme Platform | our platform, the tool |
| clients | customers, users |
| team members | employees, staff |
| workflow automation | automation, workflows (when used alone) |

## Style Rules

- Always use Oxford comma
- Write "email" not "e-mail"
- Use contractions (we're, you'll, it's) in conversational content
- No exclamation marks except in social media (max one per post)
- Numbers: Spell out one through nine, use numerals for 10+
```

**Step 2: Add Routing Rules in CLAUDE.md**

Edit or create `CLAUDE.md` in your project root:

```markdown
# Acme Corp Marketing Project

## Brand Voice Application

When using the marketing plugin's `/draft-content`, `/email-sequence`, 
or `/campaign-plan` commands, always apply the acme-brand-voice skill 
in addition to the plugin's standard brand-voice skill.

Acme-specific voice rules take precedence over generic guidance when 
there is a conflict.

## Content Review Standards

When using `/brand-review`, check content against:
1. Standard marketing best practices (from the plugin's brand-voice skill)
2. Acme Corp brand voice (from acme-brand-voice skill)
3. Acme terminology rules (must use "Acme Platform," "clients," "team members")

Flag any terminology violations as High severity.
```

**Result:**

When you run `/draft-content`, Claude automatically applies both:
- The marketing plugin's general content creation knowledge
- Your Acme-specific brand voice rules

The original marketing plugin is untouched. Your customizations live in your project directory.

**Pros:**
- Zero risk of plugin update conflicts
- Lightest-touch approach
- Easy to version control with your project
- Can be different per project (if you have multiple brands or business units)

**Cons:**
- Routing rules may not trigger as reliably as built-in plugin skills
- No structural enforcement (relies on Claude recognizing the context)
- If the plugin changes significantly, routing rules may need updates

### When to Use Each Approach

| Situation | Recommended Approach |
|-----------|---------------------|
| Testing an idea before committing | A: Direct Modification |
| Personal customizations just for you | A: Direct Modification |
| Team-wide customizations everyone will use | B: Fork the Plugin |
| Industry-specific additions (pharma, finance, legal) | B: Fork the Plugin |
| Multiple new skills and commands | B: Fork the Plugin |
| Company brand voice and terminology | C: CLAUDE.md (if light) or B: Fork (if extensive) |
| Project-specific additions | C: CLAUDE.md |
| Want to receive plugin updates without conflicts | C: CLAUDE.md |

### Industry-Specific Example: Financial Services Marketing

**Challenge:** The marketing plugin is designed for general B2B/B2C marketing. You're a financial services marketer and need compliance checks, regulatory terminology, and audience segments specific to finance.

**Solution: Fork the Plugin**

**Changes to make:**

1. **Add skills:**
   - `financial-compliance`: SEC regulations, FINRA advertising rules, required disclosures, risk disclaimer requirements
   - `financial-audiences`: Retail investors, HNW individuals, RIAs, institutional investors, family offices
   - `financial-content-types`: Thought leadership for wealth management, market commentary, educational content, product explanations

2. **Modify `/brand-review` command:**
   - Add financial services compliance checks (disclosure requirements, risk statements, performance disclaimers)
   - Check for required legal language

3. **Modify `/draft-content` command:**
   - Add template for market commentary
   - Add template for investment product description
   - Include prompts for required disclosures

4. **Add MCP servers:**
   - Bloomberg Terminal (if available via MCP)
   - Internal compliance database
   - Internal approved language library

**Result:** A `marketing-finance` plugin that understands financial services marketing while retaining all standard marketing capabilities.

### Company-Specific Example: Adding Internal Process Knowledge

**Challenge:** Your company has a specific campaign approval process, stakeholder matrix, and budget authorization workflow that the generic marketing plugin doesn't know about.

**Solution: CLAUDE.md Rules or New Skill**

**Option 1: Light Touch (CLAUDE.md)**

Add to your project's `CLAUDE.md`:

```markdown
## Acme Corp Campaign Approval Process

When using `/campaign-plan`, always include this approval workflow 
in the "Next Steps" section:

1. Marketing Manager review (required, 2 business days)
2. Budget approval (required if >$10K, 3 business days)
   - $10K-$50K: Director of Marketing
   - $50K-$150K: VP Marketing
   - >$150K: CMO + CFO
3. Legal review (required if campaign includes claims, comparisons, 
   or testimonials, 5 business days)
4. Executive approval (required if >$100K budget or press-facing, 
   5 business days)

Include stakeholder names:
- Marketing Manager: Sarah Johnson
- Director of Marketing: Michael Chen
- VP Marketing: Lisa Rodriguez
- CMO: David Park
- Legal: legal-review@acme.com
```

**Option 2: More Robust (Fork and Add Skill)**

Create `skills/acme-processes/SKILL.md` in a forked plugin with detailed workflow guidance, stakeholder matrices, budget tiers, and approval templates.

---

## Part VI: File Reference

### Complete File Tree

```
marketing/1.0.0/
├── .claude-plugin/
│   └── plugin.json                      # Plugin metadata (name, version, author)
├── commands/
│   ├── brand-review.md                  # Review content against brand guidelines
│   ├── campaign-plan.md                 # Generate campaign brief
│   ├── competitive-brief.md             # Research competitors
│   ├── draft-content.md                 # Draft marketing content
│   ├── email-sequence.md                # Design email sequences
│   ├── performance-report.md            # Build performance reports
│   └── seo-audit.md                     # Run SEO audits
├── skills/
│   ├── brand-voice/
│   │   └── SKILL.md                     # Brand voice documentation and enforcement
│   ├── campaign-planning/
│   │   └── SKILL.md                     # Campaign frameworks and strategy
│   ├── competitive-analysis/
│   │   └── SKILL.md                     # Competitive research methodology
│   ├── content-creation/
│   │   └── SKILL.md                     # Content templates and best practices
│   └── performance-analytics/
│       └── SKILL.md                     # Metrics, reporting, and optimization
├── .mcp.json                            # MCP server connections (Slack, HubSpot, etc.)
├── CONNECTORS.md                        # Placeholder system documentation
├── LICENSE                              # License information
└── README.md                            # Plugin overview and installation
```

**File Count:** 15 files total

### Cross-Reference Map: Commands and Skills

This table shows which skills are referenced or activated by each command:

| Command | Primary Skills Used | Why |
|---------|-------------------|-----|
| `/draft-content` | `content-creation`, `brand-voice` | Content templates, channel best practices, brand voice application |
| `/campaign-plan` | `campaign-planning`, `performance-analytics` | Campaign frameworks, channel strategy, success metrics |
| `/brand-review` | `brand-voice` | Voice attributes, style enforcement, terminology management |
| `/competitive-brief` | `competitive-analysis` | Research methodology, messaging comparison, positioning |
| `/performance-report` | `performance-analytics` | Metrics definitions, reporting templates, trend analysis, optimization |
| `/seo-audit` | `content-creation`, `competitive-analysis` | SEO best practices, content gap analysis, competitor SEO comparison |
| `/email-sequence` | `content-creation`, `campaign-planning`, `performance-analytics` | Email structure, sequence frameworks, metrics and benchmarks |

### Detailed File Descriptions

**`.claude-plugin/plugin.json`**
- Purpose: Plugin identity and metadata
- Critical fields: `name` (must be unique), `version` (1.0.0), `description`
- Used by: Claude plugin system to recognize and load the plugin

**`commands/*.md`**
- Purpose: Executable workflows triggered by slash commands
- Format: Markdown with YAML frontmatter
- Frontmatter fields: `description` (shows in /help), `argument-hint` (autocomplete guidance)
- Body: Instructions for Claude (imperative form: "Generate a report," "Analyze the data")

**`skills/*/SKILL.md`**
- Purpose: Domain knowledge that loads automatically based on conversation context
- Format: Markdown with YAML frontmatter
- Critical frontmatter: `name` (skill identifier), `description` (trigger phrases for activation)
- Body: Frameworks, best practices, templates, guidelines (imperative form)

**`.mcp.json`**
- Purpose: Configure connections to external tools and services
- Format: JSON
- Structure: `{ "mcpServers": { "server-name": { "type": "http", "url": "..." } } }`
- Supported types: `http`, `sse`, `stdio` (see Part IV for details)

**`CONNECTORS.md`**
- Purpose: Documentation of the placeholder system and tool categories
- Format: Markdown with tables
- Shows: What `~~` placeholders exist, what tools are pre-configured, what alternatives are available

**`README.md`**
- Purpose: Plugin overview, installation instructions, example workflows
- Audience: Users installing or evaluating the plugin

**`LICENSE`**
- Purpose: Legal license for the plugin
- Standard for open-source plugins

---

## Part VII: Troubleshooting & FAQ

### Common Issues and Solutions

**Issue: Command doesn't appear in `/help` after installing the plugin**

**Symptoms:**
- Plugin installed successfully but `/draft-content` (or other commands) not listed when typing `/help`

**Diagnosis:**
- Plugin not loaded into the current session
- Command file has invalid frontmatter or structure

**Solution:**
1. Restart Claude (close and reopen)
2. Verify installation: Ask "What plugins are installed?"
3. Check command file frontmatter:
   - Must have `---` delimiters at start and end
   - Fields must be valid YAML (`description: "text"`)
4. Check command file name: Must be `kebab-case.md` (lowercase, hyphens, no spaces)

**Issue: Skill doesn't seem to activate when expected**

**Symptoms:**
- You mention brand voice, but Claude doesn't reference brand-voice skill frameworks
- Responses feel generic despite skills being present

**Diagnosis:**
- Skill description in frontmatter doesn't include the trigger phrases you used
- Skill name in frontmatter doesn't match directory name

**Solution:**
1. Check skill frontmatter `description` field includes phrases you expect to trigger it
2. Verify skill `name` in frontmatter matches the directory name exactly
3. Try explicit phrases from the description: If description says "Use when reviewing content for brand consistency," say "Review this content for brand consistency"
4. Check that SKILL.md exists in the skill directory (not missing or misnamed)

**Issue: MCP server connection fails or times out**

**Symptoms:**
- Authentication completes but Claude says tool isn't connected
- Data requests fail with "Unable to connect to [tool]"

**Diagnosis:**
- OAuth permissions not fully granted
- Tool's API is down or rate-limited
- Network or firewall blocking the connection

**Solution:**
1. Disconnect and reconnect: "Disconnect HubSpot" then "Connect HubSpot"
2. Check permissions during OAuth: Ensure you approve all requested scopes
3. Verify tool status: Check the tool's status page for API issues
4. Try a simpler request: Instead of "pull all campaigns," try "pull data for one specific campaign"
5. Check Claude's connection status: Ask "What tools are connected?"

**Issue: `/performance-report` or data-pulling commands return no data**

**Symptoms:**
- Command runs but says "No data available" or asks you to provide data manually
- Expected MCP server connection doesn't seem to be used

**Diagnosis:**
- MCP server connected but no data exists in that tool for the time period or query
- Tool workspace/project not specified correctly
- Date range or filters exclude all data

**Solution:**
1. Verify data exists in the tool directly (log into HubSpot, check that campaigns ran in the time period)
2. Be specific about what data to pull: "Pull email campaign data for January 2025 from the 'Marketing' workspace in HubSpot"
3. Check which workspace Claude is connected to: Ask "Which HubSpot workspace are you using?"
4. Broaden the request: If "last week" returns nothing, try "last 30 days"

**Issue: Brand review doesn't apply my brand guidelines**

**Symptoms:**
- `/brand-review` provides generic review instead of checking against brand voice

**Diagnosis:**
- Brand guidelines not configured in local settings or Notion
- Notion connected but guidelines document not found

**Solution:**
1. Check if brand guidelines are configured: Ask "Do you have my brand guidelines loaded?"
2. If using Notion: Ensure the document is named something Claude can find ("Brand Voice," "Brand Guidelines," "Style Guide")
3. Provide guidelines explicitly: When running `/brand-review`, include "Review against these brand guidelines: [paste or share link]"
4. Configure once for automatic loading: Create a local settings file or dedicated Notion page

**Issue: Generated content doesn't match my brand voice**

**Symptoms:**
- `/draft-content` output is generic or uses wrong tone
- Terminology doesn't match your preferences

**Diagnosis:**
- Brand voice not configured
- Input didn't specify tone clearly
- Brand-voice skill not activated

**Solution:**
1. Configure brand voice in local settings or Notion (see Approach C in Part V)
2. Specify tone in every `/draft-content` request until brand voice is configured: "Tone: confident but approachable, warm but professional"
3. Create a project-level `acme-brand-voice` skill (see Part V, Approach C)
4. Provide examples: "Match the tone of this example: [paste example content]"

**Issue: SEO audit provides directional insights instead of precise data**

**Symptoms:**
- Keyword opportunities don't include search volume numbers
- Competitor comparison is qualitative instead of quantitative

**Diagnosis:**
- Ahrefs or Similarweb not connected
- Claude is using web search fallback

**Solution:**
1. Connect Ahrefs or Semrush: "Connect Ahrefs"
2. Accept that web search provides directional insights (still valuable, just less precise)
3. Manually supplement: Run `/seo-audit`, then add specific data from your SEO tool

**Issue: Command output is too generic or doesn't fit my situation**

**Symptoms:**
- Campaign plan feels template-like
- Recommendations don't account for your constraints

**Diagnosis:**
- Inputs were too vague
- Didn't provide enough context about your situation

**Solution:**
1. Be specific in inputs: Instead of "B2B audience," say "Demand gen managers at Series B SaaS companies with $5M-$20M ARR"
2. Include constraints: "We have no video production capability" or "Our content team can only produce one asset per week"
3. Provide context: "Our last campaign over-indexed on paid ads and underperformed; we want to focus more on organic this time"
4. Ask follow-up questions: After getting initial output, drill in: "Adjust this plan for a $15K budget instead of $30K"

### Frequently Asked Questions

**Q: Can I use this plugin in Claude.ai (the web app) or is it only for Cowork?**

**A:** The marketing plugin is primarily designed for Claude Cowork (the desktop application), where slash commands and MCP integrations work natively. Some capabilities may work in Claude Code, but web-based Claude.ai does not support plugins, slash commands, or MCP connections.

**Q: Do I need to connect all nine MCP servers to use the plugin?**

**A:** No. The plugin works without any MCP connections. Commands will prompt you for information instead of pulling it automatically. Connect only the tools you actually use and that add value to your workflow.

**Q: Can I add my own commands to the plugin?**

**A:** Yes. See Part V (Customization & Extension). You can add commands via direct modification, forking the plugin, or creating a complementary plugin. Commands are just Markdown files in the `commands/` directory.

**Q: How do I keep my customizations when the plugin updates?**

**A:** Use Approach C (CLAUDE.md and project-level skills) to avoid conflicts, or Approach B (fork the plugin) and manually merge updates. Approach A (direct modification) risks overwriting when the plugin updates.

**Q: Can I use this plugin for non-marketing content (like internal documentation)?**

**A:** The plugin is optimized for marketing content, but `/draft-content` and the content-creation skill can handle general business writing. For highly specialized non-marketing content, consider creating a dedicated plugin or using CLAUDE.md rules to extend this one.

**Q: What's the difference between a skill and a command?**

**A:** Commands are explicit actions you trigger (`/campaign-plan`). Skills are background knowledge that activates automatically when you discuss relevant topics. Commands produce deliverables. Skills make Claude smarter about a domain.

**Q: Can multiple people on my team use the same customized plugin?**

**A:** Yes. If you fork the plugin (Approach B), package it as a `.plugin` file and share it with your team. Everyone installs the same customized version.

**Q: How do I know which skill is active in a conversation?**

**A:** Ask Claude: "Which skills are currently loaded?" or "Are you using the brand-voice skill right now?"

**Q: Can I disable a skill or command I don't need?**

**A:** Yes. Delete the skill directory or command file from the plugin, or move it out of the plugin directory. Changes take effect after restarting Claude.

**Q: Does the plugin work for B2C, or is it only for B2B?**

**A:** The plugin works for both B2B and B2C marketing. Skills and commands include guidance for both contexts. You may want to customize for your specific industry (e-commerce, consumer apps, retail, etc.).

**Q: Can I use this plugin in languages other than English?**

**A:** The plugin is written in English, but Claude can generate content in other languages when you specify: "Draft a blog post in Spanish" or "Create this campaign plan in French." Skills and frameworks will reference English examples, but Claude adapts.

**Q: What if I use a marketing tool that isn't in the pre-configured MCP list?**

**A:** Check if the tool has an MCP server available. If yes, add it to `.mcp.json` (see Part IV). If the tool doesn't have an MCP server, you can still use the plugin—just provide data manually when prompted.

**Q: How often is the plugin updated?**

**A:** Check the plugin's repository or source for update frequency. Version 1.0.0 is the current version documented here.

**Q: Can I see examples of other teams' customizations?**

**A:** Anthropic does not publish customer-specific customizations, but the plugin development guide (Part V reference) includes example patterns for common industries (pharma, finance, etc.).

**Q: I found a bug or have a feature request. Where do I report it?**

**A:** Contact Anthropic support or file an issue in the plugin's repository if available.

**Q: Does this plugin track or store my data?**

**A:** The plugin itself does not track or store data. MCP connections operate according to each tool's privacy and data policies. Content you generate is subject to Claude's standard data handling.

**Q: Can I monetize or sell a customized version of this plugin?**

**A:** Check the LICENSE file for usage terms. Most Anthropic plugins use open-source licenses that allow modification and redistribution under certain conditions.

---

## Conclusion

The marketing plugin transforms Claude into a specialized marketing assistant with deep domain knowledge, structured workflows, and seamless tool integrations. Whether you're drafting a blog post, planning a multi-channel campaign, analyzing competitor positioning, or optimizing email performance, the plugin provides frameworks, best practices, and automation that compress hours of work into minutes.

**Next Steps:**

1. **Install and verify**: Run `/help` and confirm all seven commands are available
2. **Connect your top 1-2 tools**: Start with your marketing automation platform (HubSpot, Marketo) and knowledge base (Notion, Confluence)
3. **Run your first command**: Try `/draft-content` for a blog post or `/campaign-plan` for an upcoming initiative
4. **Customize for your organization**: Add your brand voice using Approach C (CLAUDE.md) or fork the plugin for team-wide customizations
5. **Explore skills**: Ask questions that trigger skills ("What metrics should I track for email?" or "How do I document our brand voice?") to see background knowledge in action

**For Advanced Users:**

- Review [Plugin Development Guide](plugin-development-guide.md) for detailed customization and extension techniques
- Build complementary skills for your industry or company
- Create additional commands for workflows unique to your marketing org
- Share your customizations with your team by packaging and distributing a forked plugin

The marketing plugin is a foundation. The more you customize it to your context, the more powerful it becomes.

---

**Document Version:** 1.0  
**Plugin Version Documented:** marketing 1.0.0  
**Last Updated:** 2025-02-14  
**Word Count:** ~16,800 words
