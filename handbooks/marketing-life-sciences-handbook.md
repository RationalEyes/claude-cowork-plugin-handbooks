# Marketing for Life Sciences — Plugin Handbook

## A Complete Guide to the Life Sciences Adaptation of the Claude Cowork Marketing Plugin

**Plugin**: `marketing-life-sciences` | **Version**: `1.0.0-ls` | **Base Version**: `1.0.0` | **Author**: Anthropic

> This handbook documents the Marketing for Life Sciences plugin, a comprehensive adaptation of the base Claude Cowork marketing plugin designed for pharmaceutical, biotechnology, and medical technology marketing teams. It covers all original marketing capabilities plus life-sciences-specific additions including regulatory compliance (FDA/EMA), MLR review workflows, HCP engagement, KOL strategy, congress marketing, and pharma-specific KPIs.

---

## Table of Contents

### Standard Handbook Sections
- **Part I: Overview & Quick Start** — What the plugin does, who it's for, how to get started
- **Part II: Commands Reference** — All 10 commands (7 inherited + 3 new) with pharma-specific walkthroughs
- **Part III: Skills Deep Dive** — All 7 skills (5 modified + 2 new) with detailed analysis
- **Part IV: Connectors & MCP Servers** — All integrations including life sciences additions (PubMed, ClinicalTrials.gov, OpenFDA)
- **Part V: Customization & Extension** — How to adapt the plugin for your therapeutic area and company
- **Part VI: File Reference** — Complete annotated file tree and cross-reference map
- **Part VII: Troubleshooting & FAQ** — Common issues and 15+ frequently asked questions

### Life Sciences Bonus Sections
- **Part VIII: Life Sciences Gap Analysis** — What the base marketing plugin was missing and why it matters
- **Part IX: Regulatory Landscape Overview** — FDA, EMA, and global compliance frameworks
- **Part X: Modified Components Inventory** — Detailed changelog of all additions and modifications
- **Part XI: Industry Workflow Integration** — How the plugin fits into real pharma marketing workflows
- **Part XII: Base vs. Life Sciences Comparison** — Side-by-side feature comparison and migration guide

---

# Part I: Overview & Quick Start

## What Is the Life Sciences Marketing Plugin?

The `marketing-life-sciences` plugin transforms Claude into a specialized marketing assistant built for the pharmaceutical, biotechnology, and medical technology industries. It provides everything the base marketing plugin offers -- content drafting, campaign planning, competitive analysis, brand voice enforcement, performance reporting, SEO auditing, and email sequence design -- and layers on top of it the regulatory knowledge, clinical vocabulary, and industry workflows that life sciences marketing teams need every day.

**Plugin metadata:**

| Field | Value |
|-------|-------|
| Name | `marketing-life-sciences` |
| Version | `1.0.0-ls` |
| Author | Anthropic |
| Description | "Life sciences adaptation of the marketing plugin for pharma, biotech, and medtech teams. Adds regulatory compliance (FDA/EMA), MLR review workflows, HCP engagement, KOL strategy, congress marketing, and pharma-specific KPIs on top of the full general marketing toolkit." |

The `-ls` version suffix signals that this plugin is a derivative of the base marketing plugin (v1.0.0), not a separate product. It preserves every capability of the original while extending it for the life sciences domain.

## Relationship to the Base Marketing Plugin

The life sciences plugin follows the "fork" extension pattern described in the plugin development guide (Approach B). This means:

- **All 7 original commands are preserved unchanged.** Commands like `/draft-content`, `/campaign-plan`, and `/brand-review` work exactly as they do in the base plugin. The same inputs, the same output structures, the same workflows.
- **All 5 original skills are preserved and extended.** Each base skill (`brand-voice`, `campaign-planning`, `competitive-analysis`, `content-creation`, `performance-analytics`) retains its full original content. Life sciences additions are appended at the end of each skill file, separated by a `<!-- Life Sciences Addition -->` marker.
- **All 9 original MCP server connections are preserved.** Slack, Canva, Figma, HubSpot, Amplitude, Notion, Ahrefs, Similarweb, and Klaviyo remain exactly as configured in the base plugin.

On top of this preserved foundation, the life sciences plugin adds:

- **3 new commands:** `/mlr-review`, `/congress-plan`, `/kol-strategy`
- **2 new skills:** `regulatory-compliance`, `medical-affairs-liaison`
- **4 reference documents:** FDA promotional rules, EMA requirements, KOL tier framework, congress planning guide
- **4 new MCP server connections:** PubMed, ClinicalTrials.gov, OpenFDA, Veeva CRM
- **9 new connector categories** for life sciences tools

The net result is a plugin with 10 commands, 7 skills, 4 reference documents, and 13 MCP servers -- a total of 26 files compared to the base plugin's 15.

## Business Problems Solved

**For Brand Managers at Pharma/Biotech Companies:**

- **MLR review bottlenecks.** The average branded sales aid takes 6-10 weeks to get through Medical-Legal-Regulatory review. The `/mlr-review` command lets you pre-screen content before formal submission, catching common rejection reasons -- unsupported claims, insufficient fair balance, off-label implications, outdated references -- and reducing revision cycles from 3 rounds to 1.
- **Content that fails compliance.** Every efficacy claim needs a reference. Every branded piece needs fair balance. Every patient material needs a readable ISI. The `regulatory-compliance` skill encodes these rules so that content produced through `/draft-content` automatically follows pharma-compliant structures.
- **Disconnected congress planning.** Planning an ASCO or ESMO presence involves medical affairs, commercial, legal, events, and communications teams coordinating across a 36-week timeline. The `/congress-plan` command produces a comprehensive plan covering booth strategy, satellite symposia, KOL engagement, competitive intelligence, social media, content repurposing, budget, and success metrics in a single structured output.

**For Medical Affairs Leads:**

- **KOL identification and tiering.** Finding the right opinion leaders for an advisory board, speaker program, or publication collaboration requires cross-referencing publications, clinical trial registrations, congress presentations, and guideline committee memberships. The `/kol-strategy` command and `medical-affairs-liaison` skill provide a structured framework for identification, scoring, tiering, and engagement planning.
- **MSL deployment alignment.** Territory planning for Medical Science Liaisons should be driven by KOL density and scientific engagement needs, not commercial opportunity. The plugin provides territory sizing factors, interaction frequency targets by KOL tier, and activity metrics for measuring MSL effectiveness.
- **Advisory board compliance.** Advisory boards are high-value but high-risk activities. The plugin encodes the 8-step planning checklist, compliance requirements (expertise-based selection, FMV compensation, documented utilization), and format options that keep these engagements defensible.

**For Marketing Directors at Medtech/Biotech:**

- **Pharma-specific campaign planning.** Life sciences campaigns are not general marketing campaigns. Disease awareness campaigns cannot mention a product name. Product launch campaigns span 18+ months across pre-launch, launch, and post-launch phases. Congress marketing campaigns require 6-9 months of lead time. The `campaign-planning` skill now includes frameworks for all six life sciences campaign types.
- **Regulatory-aware competitive analysis.** Pharma competitive intelligence goes beyond messaging and positioning to include label comparison, formulary positioning analysis, clinical trial data benchmarking, and pipeline tracking. The `competitive-analysis` skill adds these dimensions with structured comparison matrices.
- **Life sciences KPI tracking.** NRx, TRx, market share, prescriber adoption curves, formulary win rates, congress engagement scores, and MSL interaction quality are not in any general marketing playbook. The `performance-analytics` skill adds five category tables covering 36 pharma-specific KPIs with definitions, data sources, and benchmarks.

**For Regulatory Affairs Teams Supporting Marketing:**

- **Pre-submission screening.** The `/mlr-review` command simulates all three review functions -- medical, legal, and regulatory -- with detailed checklists covering 30 individual review items. It classifies content, scores fair balance on a 5-point scale across 5 dimensions, and produces an assessment of APPROVE, APPROVE WITH REVISIONS, REVISE AND RESUBMIT, or REJECT.
- **Regulatory reference access.** The `regulatory-compliance` skill's reference documents provide detailed guidance on FDA promotional rules (OPDP requirements, Form FDA 2253, digital/social media guidance) and EMA requirements (Directive 2001/83/EC, member state variations for Germany, France, UK, Italy, and Spain, EFPIA Code).

## Target Users

This plugin is designed for:

- **Brand managers** at pharmaceutical and biotech companies who plan campaigns, manage agencies, and shepherd content through MLR review
- **Medical affairs leads** who coordinate MSL field activities, KOL engagement, advisory boards, and congress strategies
- **Marketing directors** at pharma, biotech, and medtech companies who oversee multi-channel campaigns across HCP, patient, and payer audiences
- **Regulatory affairs professionals** who review promotional materials for FDA/EMA compliance
- **Commercial operations teams** who track prescriber adoption, market share, and field force effectiveness
- **Content managers** who produce detail aids, clinical data visualizations, patient education materials, and congress content
- **Market access teams** who develop formulary dossiers and competitive payer positioning
- **Agency account teams** working on pharmaceutical brands who need regulatory guardrails built into their creative workflows

## Quick Start Walkthrough

### Step 1: Install the Plugin

This is a **custom plugin** — unlike the standard Cowork plugins (Marketing, Sales, Finance, etc.) that are available with a single click from Plugin Settings, the Marketing Life Sciences plugin must be installed from a `.plugin` file.

**Cowork (recommended):** Open the `marketing-life-sciences.plugin` file in the Cowork desktop app. Cowork will display a rich preview showing all plugin files — commands, skills, references, and MCP configurations. Browse the contents and click **Accept** to install. The plugin activates immediately.

**Claude Code CLI (alternative):** If you are using Claude Code in the terminal, copy the plugin folder to your plugins directory:

```bash
claude plugins add /path/to/marketing-life-sciences
```

> **Tip:** If your organization's IT team or plugin administrator distributes this as a `.plugin` file, simply open it in Cowork — no command-line steps needed. For organizations building this plugin themselves, see the `marketing-life-sciences/` directory in this project for the complete, ready-to-package plugin source.

### Step 2: Verify Installation

Type `/help` in Claude. You should see all 10 commands:

- `/brand-review` -- Review content against brand voice and style
- `/campaign-plan` -- Generate a campaign brief with objectives, channels, and metrics
- `/competitive-brief` -- Research competitors and compare positioning
- `/congress-plan` -- Plan congress marketing activities **(new)**
- `/draft-content` -- Draft blog posts, emails, landing pages, and more
- `/email-sequence` -- Design multi-email sequences
- `/kol-strategy` -- Develop a KOL engagement strategy **(new)**
- `/mlr-review` -- Simulate medical-legal-regulatory review **(new)**
- `/performance-report` -- Build a performance report with trends and recommendations
- `/seo-audit` -- Run a comprehensive SEO audit

### Step 3: Run Your First Life Sciences Command

For a quick demonstration of the plugin's life sciences capabilities, run the MLR review simulation:

```
/mlr-review
```

Claude will prompt you for inputs. Provide:

```
Content: [paste a promotional email draft for an oncology product]
Classification: Branded promotional
Target market: US (FDA)
Product context: KEYTRUDA (pembrolizumab), approved for adjuvant treatment 
of renal cell carcinoma, has black box warning: No
```

Claude will run through all five review steps -- content classification, medical review, legal review, regulatory review, and fair balance assessment -- and produce a structured MLR Review Summary with severity-ranked findings, annotated content revisions, a reference verification table, and a compliance checklist. This pre-screening can save weeks of revision cycles before formal MLR submission.

### Step 4: Connect Life Sciences Data Sources

The plugin pre-configures connections to four life sciences data sources in addition to the nine base marketing tools. Connect the ones relevant to your workflow:

- **PubMed (NCBI):** For literature search, KOL publication analysis, and reference verification. Requires an NCBI API key.
- **ClinicalTrials.gov:** For competitive pipeline intelligence and KOL identification via principal investigator searches. No authentication required.
- **OpenFDA:** For drug labeling data, adverse event databases, and regulatory action history. No authentication required.
- **Veeva CRM:** For HCP engagement tracking, approved email, and content management. Requires a Veeva CRM license.

### Step 5: Explore Life Sciences Skills

Skills activate automatically when conversation context is relevant. Try asking:

```
What are the fair balance requirements for a branded digital banner ad?
```

Claude will draw on the `regulatory-compliance` skill to explain that digital banner ads require a brief summary or link to the full PI, that major risks must be visible without scrolling, and that the fair balance scoring framework expects equal visual weight between benefit and risk information.

Or ask:

```
How do I tier KOLs for an advisory board in non-small cell lung cancer?
```

Claude will reference the `medical-affairs-liaison` skill and the KOL tier framework to walk you through the 7 scoring dimensions (Publication Impact, Clinical Trial Leadership, Congress Presence, Guideline Involvement, Institutional Influence, Digital Influence, and Engagement Potential), the composite scoring methodology, and the tier thresholds (Tier 1: 4.0-5.0, Tier 2: 3.0-3.9, Tier 3: 2.0-2.9).

## Component Architecture

The life sciences marketing plugin combines three types of components that work together, with clear separation of concerns between general marketing knowledge and life sciences specialization.

### Commands (10 Total: 7 Inherited + 3 New)

Commands are user-triggered workflows invoked with a slash. Each command follows a structured input-output pattern. The 7 inherited commands (`/brand-review`, `/campaign-plan`, `/competitive-brief`, `/draft-content`, `/email-sequence`, `/performance-report`, `/seo-audit`) are unchanged from the base plugin. Life sciences specialization for these commands comes from the skills layer -- when you run `/draft-content`, the `content-creation` skill now includes life sciences content types (detail aids, MOA content, formulary dossiers), so the command automatically produces pharma-appropriate output without any command-level modification.

The 3 new commands (`/mlr-review`, `/congress-plan`, `/kol-strategy`) are life-sciences-only workflows that rely on the 2 new skills for their domain knowledge.

### Skills (7 Total: 5 Modified + 2 New)

Skills are background knowledge packages that Claude loads automatically based on conversation context. The 5 modified skills (`brand-voice`, `campaign-planning`, `competitive-analysis`, `content-creation`, `performance-analytics`) retain all their original marketing knowledge and gain appended sections covering pharma-specific frameworks, terminology, and workflows. Their trigger descriptions are expanded with additional life sciences phrases so they activate on pharma-specific queries.

The 2 new skills (`regulatory-compliance`, `medical-affairs-liaison`) provide deep domain expertise in pharmaceutical regulatory compliance and medical affairs operations. Each includes reference documents for detailed guidance loaded on demand.

### MCP Servers (13 Total: 9 Inherited + 4 New)

MCP servers connect Claude to external tools. The 9 inherited servers (Slack, Canva, Figma, HubSpot, Amplitude, Notion, Ahrefs, Similarweb, Klaviyo) are preserved identically. The 4 new servers (PubMed, ClinicalTrials.gov, OpenFDA, Veeva CRM) connect Claude to life sciences data sources for literature search, clinical trial data, drug labeling, and HCP engagement tracking.

### How They Work Together

Here is what happens when you run `/mlr-review` with connected tools:

1. You invoke the command: `/mlr-review`
2. Claude loads the `regulatory-compliance` skill for compliance frameworks and checklists
3. Claude also loads the `brand-voice` skill for pharma-specific claim substantiation rules
4. Claude prompts you for inputs (content, classification, target market, product context)
5. If PubMed is connected, Claude can verify cited references against the biomedical literature
6. If OpenFDA is connected, Claude can cross-check indication statements against current drug labeling
7. Claude runs the 5-step review process (classification, medical, legal, regulatory, fair balance)
8. Claude produces the structured output: MLR Review Summary, Detailed Findings, Annotated Content, Reference Verification, and Compliance Checklist
9. Claude asks if you want to revise the content, fix critical issues only, or generate a compliant alternative

Without MCP connections, the process still works -- Claude applies its knowledge from the skill files and asks you for any information it would have pulled from tools automatically.

---

# Part II: Commands Reference

## Overview of All 10 Commands

| Command | Source | Primary Use Case | Output |
|---------|--------|-----------------|--------|
| `/brand-review` | Base | Review content against brand voice and compliance | Severity-ranked findings with revision suggestions |
| `/campaign-plan` | Base | Plan a multi-channel marketing campaign | Comprehensive campaign brief with timeline and metrics |
| `/competitive-brief` | Base | Research and compare competitors | Structured competitive analysis with positioning gaps |
| `/congress-plan` | **New (LS)** | Plan medical congress marketing activities | 11-section congress plan with timeline and budget |
| `/draft-content` | Base | Draft marketing content across channels | Publication-ready draft with formatting and SEO |
| `/email-sequence` | Base | Design multi-email automation flows | Complete sequence with copy, timing, and branching logic |
| `/kol-strategy` | **New (LS)** | Develop KOL engagement strategy | 11-section strategy with tiering and measurement |
| `/mlr-review` | **New (LS)** | Simulate MLR review of promotional content | Compliance assessment with findings and revisions |
| `/performance-report` | Base | Analyze marketing performance | Report with metrics, trends, and recommendations |
| `/seo-audit` | Base | Evaluate SEO health and opportunities | Audit with keyword opportunities and action plan |

---

## Inherited Commands in a Life Sciences Context

The 7 inherited commands are documented in full in the base marketing handbook. Here we focus on how each command gains life sciences capabilities through the modified skills layer, with pharma-specific scenarios demonstrating their use.

### `/brand-review` in Life Sciences

**Syntax:** `/brand-review <content to review>`

**Description (from frontmatter):** "Review content against your brand voice, style guide, and messaging pillars"

When used in a life sciences context, this command draws on the expanded `brand-voice` skill, which now includes pharma fair balance requirements, ISI placement rules, claim substantiation standards, prohibited language checks, and pharma-specific tone adaptation guidance.

**Life Sciences Scenario:**

A brand manager at a mid-size biotech has received a draft detail aid for their newly approved JAK inhibitor from their agency. Before submitting it to MLR, she runs:

```
/brand-review
[pastes the detail aid copy]
```

Claude detects the pharmaceutical context from the content and loads the life sciences additions from the `brand-voice` skill. In addition to standard brand consistency checks, the review now includes:

- **Claim substantiation audit:** Every efficacy claim is checked for a corresponding reference. "Superior response rates" flagged as High severity because it lacks a head-to-head study citation.
- **Fair balance assessment:** The draft has 3 pages of efficacy data and half a page of safety information -- flagged as Major because risk information lacks comparable prominence.
- **Prohibited language detection:** The word "safe" appears without qualification ("DRUG X has a safe and well-tolerated profile") -- flagged as Critical.
- **ISI completeness check:** The ISI section is missing the updated contraindications from the most recent label revision -- flagged as Critical.
- **Drug naming convention check:** The first mention uses brand name only without the INN -- flagged as Medium for scientific-audience materials.

**Pro Tips for Life Sciences:**
- Run `/brand-review` before `/mlr-review` for a two-stage quality gate. Brand review catches voice and style issues; MLR review catches regulatory compliance issues.
- Configure your brand guidelines in Notion (or your `~~knowledge base`) to include your ISI template and approved claims library. Claude will automatically reference them.
- For patient-facing materials, ask Claude to check reading level (target 6th-8th grade) in addition to brand voice.

### `/campaign-plan` in Life Sciences

**Syntax:** `/campaign-plan <campaign objective or product>`

**Description (from frontmatter):** "Generate a full campaign brief with objectives, channels, content calendar, and success metrics"

The `campaign-planning` skill now includes 6 life sciences campaign types (disease awareness, product launch, congress marketing, peer-to-peer, patient support program, and medical education), HCP/patient/payer segmentation frameworks, MLR review timeline benchmarks, and a pharma-specific channel guide.

**Life Sciences Scenario:**

A marketing director at a rare disease biotech is planning a pre-launch disease awareness campaign for a condition with less than 50% diagnosis rates:

```
/campaign-plan
Goal: Increase diagnosis rates for hereditary angioedema (HAE) by driving 
patients with unexplained recurrent swelling to seek specialist referral
Audience: Primary care physicians and patients experiencing unexplained 
episodic swelling
Timeline: 12 months pre-launch, beginning March 2026
Budget: $2M
Additional context: Our product is in Phase 3 for HAE; this is an 
unbranded campaign -- no product may be mentioned
```

Claude generates a campaign brief that automatically applies the disease awareness campaign rules: no product naming, no branded elements, CTA limited to "talk to your doctor" rather than requesting a specific product. The content calendar builds in MLR review lead times (3-6 weeks for unbranded materials), and the channel strategy focuses on patient-facing websites, social media disease awareness pages, patient advocacy partnerships, and PCP-directed medical education.

**Regulatory Pitfall to Avoid:** Never let an unbranded disease awareness campaign and a branded product campaign overlap in ways that make the connection between them obvious to regulators. Maintain clear organizational and temporal separation.

### `/competitive-brief` in Life Sciences

**Syntax:** `/competitive-brief <competitor or market segment>`

**Description (from frontmatter):** "Research competitors and generate a positioning and messaging comparison"

The `competitive-analysis` skill now includes formulary positioning analysis, clinical trial comparison matrices, label comparison templates, pipeline intelligence tracking, and pharma-specific battlecard sections.

**Life Sciences Scenario:**

A commercial strategy lead at an oncology-focused biotech needs a competitive landscape assessment for their PD-L1 inhibitor entering the adjuvant NSCLC market:

```
/competitive-brief
Competitors: KEYTRUDA (pembrolizumab, Merck), OPDIVO (nivolumab, BMS), 
IMFINZI (durvalumab, AstraZeneca)
Our product: TECENTRIQ (atezolizumab), adjuvant NSCLC Stage IB-IIIA
Focus areas: Label comparison, clinical data, formulary positioning, 
pipeline threats
```

Claude produces a competitive brief that goes beyond messaging comparison to include:
- **Label Comparison Matrix** covering approved indications, line of therapy, biomarker requirements, dosing schedule, and black box warnings across all four products
- **Pivotal Trial Comparison** with primary endpoints, OS/PFS/ORR data, Grade 3-4 AE rates, and discontinuation rates -- with the explicit caveat that cross-trial comparisons are not equivalent to head-to-head data
- **Formulary Positioning Analysis** across commercial and Medicare Part D, including PA requirements and step therapy positioning
- **Pipeline Intelligence** tracking upcoming data readouts and potential label expansions from competitors

**Regulatory Pitfall to Avoid:** Never present cross-trial comparisons as if they were head-to-head evidence. Differences in patient populations, endpoints, and study design make indirect comparisons unreliable. Always flag this limitation prominently.

### `/draft-content` in Life Sciences

**Syntax:** `/draft-content <content type and topic>`

**Description (from frontmatter):** "Draft blog posts, social media, email newsletters, landing pages, press releases, and case studies"

The `content-creation` skill now includes 5 life sciences content types (branded sales aids, clinical data visualizations, MOA content, formulary dossiers, patient education materials) and MLR review requirements for reference annotation, PI/SmPC integration, and content classification.

**Life Sciences Scenario:**

A medical communications manager needs a mechanism of action (MOA) section for a new branded website for their bispecific antibody:

```
/draft-content
Type: Mechanism of action content
Topic: How our bispecific T-cell engager works in relapsed/refractory 
B-cell ALL by simultaneously binding CD19 on malignant B cells and CD3 
on T cells
Audience: Oncologists and hematologists
Key messages: Dual-targeting mechanism, endogenous T-cell activation, 
no need for ex-vivo T-cell modification
```

Claude produces MOA content that follows the life sciences content rules: descriptions based on approved labeling and published literature, no implied benefits beyond what the mechanism supports, scientific accuracy suitable for medical affairs verification, and reference annotations for every factual claim using superscript notation (^[1], ^[2]).

**Pro Tips for Life Sciences:**
- Always specify whether the content is for HCPs or patients. The content structure, vocabulary, reading level, and regulatory requirements differ significantly.
- For branded materials, include the product's approved indication and key safety information as context so Claude can build in appropriate fair balance.
- Request reference annotations explicitly if you need MLR-ready output: "Annotate all efficacy claims with reference numbers."

### `/email-sequence` in Life Sciences

**Syntax:** `/email-sequence [sequence type]`

**Description (from frontmatter):** "Design and draft multi-email sequences for nurture flows, onboarding, drip campaigns, and more"

**Life Sciences Scenario:**

A digital marketing manager at a specialty pharma company needs an HCP email sequence promoting a new once-monthly formulation of an existing diabetes drug:

```
/email-sequence
Type: Product launch
Goal: Drive prescriber adoption of GLUZARO XR (exenatide monthly) among 
endocrinologists and PCPs currently prescribing weekly exenatide
Audience: Endocrinologists and high-volume diabetes PCPs who have written 
at least 5 exenatide scripts in the past 6 months
Additional context: Monthly formulation approved 4 weeks ago. Key 
advantage: monthly vs. weekly injection. Same efficacy profile. All emails 
must be Veeva Approved Email templates.
```

Claude designs the sequence with pharma compliance built in: every email includes fair balance, links to the full PI, ISI in the email footer, and approved claims only. The branching logic accounts for HCP engagement patterns (opened, clicked through to clinical data, requested samples) rather than consumer purchase behaviors.

**Regulatory Pitfall to Avoid:** HCP email marketing in pharma must use approved email templates (typically through Veeva Approved Email). Every email is a promotional piece requiring MLR review. Build the full MLR review timeline (3-4 weeks for social/email content) into your sequence launch plan.

### `/performance-report` in Life Sciences

**Syntax:** `/performance-report <time period or campaign>`

**Description (from frontmatter):** "Build a marketing performance report with key metrics, trends, and optimization recommendations"

The `performance-analytics` skill now includes 36 pharma-specific KPIs across commercial (NRx, TRx, market share, SOV), HCP engagement (reach, frequency, detail effectiveness), payer/access (formulary coverage, PA override rates), congress engagement (booth traffic, symposium attendance), and patient engagement (PSP enrollment, adherence) categories. It also includes the Brand Performance Report template and Launch Tracker Dashboard structure.

**Life Sciences Scenario:**

A brand director needs a monthly brand performance report for a specialty oncology product in its second year on market:

```
/performance-report
Type: Brand performance report
Time period: January 2026
Comparison: December 2025 and January 2025 (YoY)
Stakeholder audience: VP Commercial and brand team
Additional context: Product is 18 months post-launch. Focus areas: 
NRx/TRx trends, prescriber adoption, formulary wins, competitive share
```

Claude generates a report structured around the Brand Performance Report template: executive summary with NRx/TRx trend and market share change, commercial metrics table with MoM and YoY comparisons, HCP engagement analysis, payer/access updates, patient metrics, competitive intelligence, campaign performance, and prioritized recommendations.

### `/seo-audit` in Life Sciences

**Syntax:** `/seo-audit <url or topic> [audit type]`

**Description (from frontmatter):** "Run a comprehensive SEO audit -- keyword research, on-page analysis, content gaps, technical checks, and competitor comparison"

**Life Sciences Scenario:**

A digital marketing lead at a biotech wants to improve their branded patient website's organic visibility:

```
/seo-audit https://www.drugbrand.com content gap analysis
```

Claude conducts the content gap analysis with awareness that pharmaceutical branded websites have unique SEO constraints: all branded pages require fair balance and ISI, limiting the flexibility of title tags and meta descriptions; competitor comparison content must be factual and reference-backed; and patient-facing content must balance SEO optimization with health literacy requirements (6th-8th grade reading level).

---

## New Life Sciences Commands (Detailed Walkthroughs)

### Command: `/mlr-review`

**Syntax:** `/mlr-review <content to review>`

**Description (from frontmatter):** "Simulate medical-legal-regulatory review of promotional content"

**What It Does:**

This command simulates the three-function Medical-Legal-Regulatory review process that all pharmaceutical promotional content must pass through before distribution. It identifies compliance issues, flags unsubstantiated claims, checks fair balance, and produces a reviewable assessment. The purpose is pre-screening: catching common rejection reasons before formal MLR submission to reduce revision cycles and accelerate time-to-approval.

**Inputs:**

1. **Content to review** -- pasted directly, via file path, `~~knowledge base` reference, URL, or batch of multiple pieces
2. **Content classification** -- one of 7 types: branded promotional, unbranded disease awareness, reminder advertising, scientific exchange, patient-facing material, congress material, or social media content
3. **Target market** (optional) -- US (FDA), EU (EMA), or specific country. Defaults to US FDA.
4. **Product context** (optional but recommended) -- product name (brand and INN), approved indications, key safety information, black box warning or REMS status

**5-Step Review Process:**

1. **Content Classification.** Claude uses the regulatory-compliance skill's classification matrix to determine the review pathway. A 4-step decision tree determines whether the material is branded promotional, unbranded, reminder advertising, help-seeking, scientific exchange, institutional, or patient labeling. The classification determines which review checks apply and the required review level (Full MLR, Medical + Legal, Abbreviated MLR, Medical only, or Regulatory only).

2. **Medical Review.** Claude evaluates the content from the perspective of a medical reviewer, checking 10 items: efficacy claims match labeling, clinical data accuracy, statistical context included (CI, p-value, HR), study limitations acknowledged, patient population described, no extrapolation beyond approved indication, MOA accuracy, AE profile completeness, no off-label implications, and references complete and from approved sources.

3. **Legal Review.** Claude evaluates from the legal perspective, checking 10 items: no unsubstantiated comparatives, no superlatives without substantiation, trademark/registration symbol compliance, copyright compliance for images and content, no misleading data presentations, fair competitor references, testimonial disclosures, no outcome guarantees, Sunshine Act/EFPIA compliance, and HIPAA/GDPR privacy compliance.

4. **Regulatory Review.** Claude evaluates from the regulatory perspective, checking 10 items: indication statement matches labeling, fair balance maintained, ISI complete and current, black box warning displayed if applicable, PI/SmPC attached or linked, material coded with unique job number, expiration/review date assigned, distribution channel appropriate, OPDP/EMA filing requirements identified, and local country-specific requirements met.

5. **Fair Balance Assessment.** Claude applies the fair balance scoring framework across 5 dimensions, each rated 1-5:
   - **Prominence** -- 5 = equal visual weight between efficacy and risk; 1 = risk buried or minimized
   - **Completeness** -- 5 = all material risks included; 1 = significant risks omitted
   - **Readability** -- 5 = risk info equally readable; 1 = smaller font, lighter color, dense text
   - **Placement** -- 5 = risk near associated benefit claims; 1 = risk segregated at end only
   - **Language** -- 5 = clear, direct risk language; 1 = euphemistic or minimizing language

   Scoring thresholds: 4-5 average = fair balance likely adequate; 3 = at risk, revise before submission; below 3 = inadequate, major revision required.

**Output Structure:**

The command produces 5 output sections:

**MLR Review Summary:**
```
Content type: Branded promotional
Target market: US (FDA)
Overall assessment: APPROVE WITH REVISIONS
Fair balance score: 3.4 / 5.0
Critical issues: 1
Major issues: 3
Minor issues: 5
```

**Detailed Findings Table:**

| # | Issue | Review Function | Severity | Location | Recommendation |
|---|-------|----------------|----------|----------|---------------|
| 1 | Efficacy claim "superior response rates" lacks head-to-head data | Medical | Critical | Page 2, paragraph 1 | Remove "superior" or cite specific comparative study |
| 2 | ISI missing updated contraindication from Jan 2026 label revision | Regulatory | Major | ISI section | Update ISI to match current PI version |
| 3 | Risk information in 8pt font while efficacy in 11pt | Regulatory | Major | Pages 2-3 vs. Page 5 | Match font sizes for risk and benefit content |

**Annotated Content:** Before/after revisions for top issues showing original text and a compliant alternative.

**Reference Verification Table:** Each claim mapped to its cited reference, with validity assessment (Yes/No/Missing).

**Compliance Checklist Summary:** 8-item pass/fail checklist (indication matches labeling, fair balance maintained, ISI complete, PI attached, all claims referenced, no off-label implications, black box warning displayed if applicable, material properly classified).

**Full Walkthrough -- Simulating MLR Review for an Oncology Product Email:**

A brand manager at a pharma company has drafted a promotional email to oncologists about new overall survival data for their PD-1 inhibitor in first-line metastatic melanoma. Before sending it to the MLR committee, she runs:

```
/mlr-review
```

She provides the email draft and context:

```
Content: [pastes promotional email text]
Classification: Branded promotional
Target market: US (FDA)
Product: ONCORIS (nivolizumab), approved for unresectable or metastatic 
melanoma. No black box warning. No REMS.
```

Claude classifies the content as branded promotional (Full MLR review required) and runs all 5 steps. Key findings:

- **Critical:** The phrase "ONCORIS delivers unprecedented survival benefit" uses the word "unprecedented" as an unsubstantiated superlative. Recommendation: Replace with "ONCORIS demonstrated a statistically significant improvement in overall survival (HR=0.72; 95% CI: 0.60-0.87; p=0.0006) in the ONCO-301 trial."
- **Major:** The email presents a Kaplan-Meier curve but truncates the Y-axis at 40%, visually exaggerating the separation between curves. Recommendation: Show the full 0-100% Y-axis.
- **Major:** Risk information is presented in a single paragraph at the bottom of the email in smaller text. Fair balance score: Prominence = 2, Completeness = 4, Readability = 2, Placement = 2, Language = 4. Average = 2.8 (inadequate). Recommendation: Present key safety information with equal formatting and integrate risk mentions near corresponding efficacy claims.
- **Minor:** The email does not include a link to the full Prescribing Information. Recommendation: Add "Please see full Prescribing Information at [URL]" with a prominent hyperlink.

Overall assessment: REVISE AND RESUBMIT. The brand manager addresses the critical and major issues before submitting to the actual MLR committee, potentially saving 2-3 weeks of revision cycles.

**Pro Tips:**
- Run `/mlr-review` on every piece of content before formal MLR submission. Catching issues early saves weeks.
- For batch reviews, submit multiple pieces at once: "Review these 5 social media posts for our upcoming diabetes campaign."
- Use the reference verification table to build your submission package -- it maps every claim to its source, which is exactly what MLR reviewers need.
- After review, ask Claude to "Generate a compliant alternative version from scratch" for content with many critical issues -- sometimes it is faster to rewrite than to revise.

**Pitfalls to Avoid:**
- This is a simulation, not a replacement for your actual MLR committee. Use it as a pre-screening tool.
- Always verify the current PI/SmPC version. Labels get updated, and content reviewed against an outdated label will fail formal MLR.
- Do not assume a "clean" simulation means guaranteed MLR approval. Human reviewers may catch context-dependent issues that a simulation cannot.

---

### Command: `/congress-plan`

**Syntax:** `/congress-plan <congress name or therapeutic area>`

**Description (from frontmatter):** "Plan conference and congress marketing activities for life sciences"

**What It Does:**

This command generates a comprehensive congress marketing and medical affairs plan covering all aspects of a pharmaceutical company's presence at a medical conference: data dissemination, exhibition booth, satellite symposia, KOL engagement, competitive intelligence, social media, content repurposing, timeline, budget, and success metrics.

**Inputs:**

1. **Congress name** -- specific congress (e.g., ASCO 2026, ESMO 2026, ADA 2026) or therapeutic area if congress not yet selected
2. **Product(s)** -- brand name, INN, approved indications, data to be presented, abstract acceptance status
3. **Objectives** -- data dissemination, KOL engagement, competitive intelligence, brand awareness, pre-launch preparation
4. **Budget range** (optional)
5. **Team size** (optional) -- breakdown by role (MSLs, commercial, medical, leadership)
6. **Historical context** (optional) -- previous year's activities and learnings

**11-Section Output:**

1. **Congress Overview** -- dates, location, attendance, therapeutic relevance, competitor presence
2. **Data Dissemination Plan** -- per abstract: title, format, session, presenting author, key data points, pre/post communication plans
3. **Exhibition Booth Plan** -- size, location, design themes, interactive elements, staffing plan by role and shift, training requirements, materials checklist (all requiring MLR approval)
4. **Satellite Symposium Plan** -- topic, scientific justification, speakers with rationale, format, audience, compliance requirements
5. **KOL Engagement Plan** -- priority KOLs (Tier 1 and Tier 2), meeting objectives, MSL assignments, follow-up plan
6. **Competitive Intelligence Plan** -- competitor presentations to attend, booth reconnaissance, intelligence template, real-time communication plan
7. **Social Media and Communications Plan** -- pre/during/post content calendars, compliance review process, hashtag strategy, media engagement
8. **Content Repurposing Plan** -- post-congress outputs (highlights email, infographics, webinars, blog posts, competitive briefings)
9. **Timeline** -- week-by-week countdown from 36 weeks out to +2 weeks post-congress
10. **Budget Breakdown** -- by category (booth, symposium, travel, materials, KOL engagement, social/digital, contingency)
11. **Success Metrics** -- booth traffic, KOL meetings vs. planned, symposium attendance, social impressions, competitive intel items, content engagement, media coverage

**Full Walkthrough -- Planning ASCO 2026 for an Oncology Product:**

A commercial strategy lead at a biotech company with a newly approved KRAS G12C inhibitor runs:

```
/congress-plan
```

She provides:

```
Congress: ASCO 2026 (American Society of Clinical Oncology, May 29 - 
June 2, 2026, Chicago)
Product: KRASYNTA (adagrasib), approved for locally advanced or metastatic 
NSCLC with KRAS G12C mutation. Phase 3 data (KRYSTAL-12) will be 
presented as a late-breaking oral.
Objectives: 
- Data dissemination (pivotal Phase 3 OS data, first presentation)
- KOL engagement (20 Tier 1/2 oncology KOLs)
- Competitive intelligence (monitor sotorasib updates from Amgen)
- Pre-launch market shaping for CRC indication (Phase 2 data accepted 
  as poster)
Budget: $1.5M
Team: 6 MSLs, 4 commercial, 3 medical affairs, 2 leadership
```

Claude generates a comprehensive plan:

**Data Dissemination Plan:** For the late-breaking oral, Claude outlines a pre-congress embargo strategy, media briefing materials, a social media countdown, coordinated simultaneous journal publication, and post-presentation rapid-response content (press release within 1 hour, infographic within 24 hours, HCP email within 48 hours). For the CRC poster, a separate dissemination plan with QR code linking to supplementary digital content and MSL follow-up assignments for GI oncology KOLs.

**Exhibition Booth Plan:** Claude recommends a 30x40 booth with a dedicated data theater for the KRYSTAL-12 results, an interactive molecular pathway display, a biomarker testing education station, and a patient support program information area. The staffing plan assigns MSLs to the data theater and scientific exchange areas, commercial team to the main engagement area, and specifies shift rotations to ensure coverage during keynote sessions.

**KOL Engagement Plan:** Claude identifies Tier 1 KOLs to target for 1:1 scientific exchange meetings based on their involvement in KRAS research, suggests scheduling meetings around the late-breaking session to maximize discussion of the new data, and assigns specific MSLs to each KOL based on existing relationships.

**Timeline:** The plan includes a 36-week countdown starting from abstract submission (September 2025) through the 2-week post-congress wrap-up, with specific milestones for booth reservation, material development, MLR review submissions, speaker training, logistics finalization, and content shipping.

**Pro Tips:**
- Start planning 9-12 months before the congress. Premium booth space and satellite symposium slots sell out early, especially at ASCO, ESMO, and ASH.
- After generating the plan, ask Claude to "Develop the competitive intelligence gathering template" or "Draft the pre-congress communication to the field force" for detailed sub-deliverables.
- Use the plan as a coordination document across medical affairs, commercial, events, and communications teams. Share it via `~~chat` (Slack/Teams) for team alignment.

**Pitfalls to Avoid:**
- Do not neglect MLR review timelines. All booth materials, leave-behinds, digital displays, and social media content need MLR approval. Build 6-8 weeks of review time into the timeline.
- Satellite symposia must be clearly labeled as industry-sponsored and separated from official congress scientific sessions. Overtly promotional content damages credibility and may violate congress rules.
- Competitive intelligence gathering must be ethical. Attend public sessions and observe public booth content. Do not misrepresent your identity or attempt to access restricted information.

---

### Command: `/kol-strategy`

**Syntax:** `/kol-strategy <therapeutic area or product>`

**Description (from frontmatter):** "Develop a KOL engagement strategy for a therapeutic area or product"

**What It Does:**

This command develops a comprehensive Key Opinion Leader engagement strategy including identification, tiering, engagement planning, advisory board design, speaker program structure, MSL deployment alignment, and measurement. It draws on the `medical-affairs-liaison` skill and its KOL tier framework reference document.

**Inputs:**

1. **Therapeutic area or product** -- disease area or specific product (e.g., "non-small cell lung cancer", "KEYTRUDA", "type 2 diabetes")
2. **Strategic objective** -- pre-launch market shaping, launch support, post-launch lifecycle, competitive defense, or pipeline development
3. **Geography** -- US national, US regional, EU (specify countries), or global
4. **Current state** (optional) -- existing relationships, MSL team size, known KOLs, budget
5. **Timeline** -- planning horizon (e.g., "next 12 months", "pre-launch 18-month plan")

**11-Section Output:**

1. **Strategic Context** -- why KOL engagement matters for this product/area, treatment landscape, competitive KOL landscape, strategic gaps
2. **KOL Identification** -- initial long list from publication search, clinical trial PI search (via `~~clinical trials data`), and congress presenter search
3. **KOL Tiering** -- application of the 7-dimension scoring framework (Publication Impact, Clinical Trial Leadership, Congress Presence, Guideline/Society Involvement, Institutional Influence, Digital/Media Influence, Engagement Potential), each weighted and scored 1-5, with tier thresholds (Tier 1: 4.0-5.0, Tier 2: 3.0-3.9, Tier 3: 2.0-2.9)
4. **Engagement Plan by Tier** -- activity matrix mapping advisory boards, speaker programs, MSL meetings, congress engagement, publication collaboration, clinical trial roles, and consulting against each tier
5. **Advisory Board Plan** -- number, type, topics, composition, timeline, format, budget, compliance
6. **Speaker Program Plan** -- national vs. regional structure, speaker identification and training, approved topics, compliance
7. **MSL Deployment Alignment** -- KOL density by geography, MSL-to-KOL ratios, territory adjustments, interaction frequency targets, insight capture processes
8. **KOL Engagement Calendar** -- quarterly activity plan aligned to congresses, product milestones, and publication timelines
9. **Measurement Framework** -- 7 metrics (KOL coverage, interaction quality, advisory board utilization, speaker program reach, publication output, sentiment tracking, competitive share of KOL voice)
10. **Budget Framework** -- annual cost by activity (advisory boards, speaker programs, MSL team, congress engagement, publication support, consulting)
11. **Compliance and Risk Mitigation** -- FMV documentation, Sunshine Act/EFPIA transparency, promotional/scientific separation, documentation requirements, conflict of interest management, anti-kickback considerations

**Full Walkthrough -- KOL Strategy for a New Indication in Cardiology:**

The head of medical affairs at a cardiovascular-focused pharma company is developing a KOL engagement plan for their PCSK9 inhibitor ahead of a label expansion into familial hypercholesterolemia in adolescents:

```
/kol-strategy
Therapeutic area: Familial hypercholesterolemia (FH) in adolescents, 
PCSK9 inhibitor class
Strategic objective: Pre-launch market shaping (18 months to expected 
approval of pediatric indication)
Geography: US national
Current state: We have 12 MSLs covering cardiovascular and lipid 
specialists nationally. We have existing Tier 1 relationships with 
15 adult FH KOLs. No current relationships with pediatric lipidologists.
Timeline: 18-month plan through expected PDUFA date
```

Claude generates the full strategy:

**KOL Identification:** Claude distinguishes between two KOL populations needed: (1) pediatric lipidologists who treat adolescent FH patients, and (2) adult FH KOLs who need to be educated about the new pediatric indication. For the pediatric population, identification sources include authors of pediatric lipid guideline publications, PIs on pediatric statin trials found via ClinicalTrials.gov, presenters at the National Lipid Association (NLA) pediatric sessions, and members of the American Academy of Pediatrics lipid screening committee.

**KOL Tiering:** Claude applies the 7-dimension framework with weights adjusted for this specific context: Publication Impact (25%) weighted higher because the pediatric FH literature is small and concentrated among a few researchers; Guideline Involvement (20%) weighted higher because AAP and NLA guideline authors will shape prescribing in this new population; Engagement Potential (15%) weighted higher because this is a new therapeutic area for the company and willingness to engage is critical.

**Engagement Plan:** For Tier 1 pediatric FH KOLs, Claude recommends early scientific exchange meetings (MSL-led, non-promotional) to discuss the Phase 3 pediatric data, followed by an advisory board 12 months pre-launch to gather input on the disease management landscape in adolescents, and speaker program recruitment 6 months pre-launch to build advocacy ahead of approval.

**Compliance Section:** Claude flags that pediatric KOL engagement carries additional scrutiny because it involves a vulnerable population. All activities must be clearly non-promotional until approval, MSL interactions must be documented as scientific exchange, and advisory board compensation must reflect documented FMV for pediatric specialists (who may have different rate benchmarks than adult cardiologists).

**Pro Tips:**
- If `~~clinical trials data` (ClinicalTrials.gov) is connected, Claude can search for principal investigators on relevant trials and include them in the initial KOL long list with specific trial references.
- After generating the strategy, ask Claude to "Research and identify specific KOLs for pediatric familial hypercholesterolemia" for a data-driven long list, or "Develop detailed advisory board agendas" for the next level of planning.
- Use the measurement framework to report KOL engagement ROI to leadership. Track KOL coverage (% of tiered KOLs with at least one interaction) and sentiment trending over time.

**Pitfalls to Avoid:**
- Never select KOLs based on prescribing volume for advisory boards or speaker programs. Selection must be based on scientific expertise relevant to the advisory objective. Prescribing-based selection creates anti-kickback risk.
- Pre-launch KOL engagement must remain strictly scientific and non-promotional. MSLs can discuss published data and clinical trial results, but commercial teams cannot promote the product before approval.
- Document every KOL interaction. Undocumented interactions create compliance gaps that are difficult to defend during audits.
- Fair market value compensation must be established before engagement begins, based on documented rate surveys for the specialty and time commitment. Overpaying creates Sunshine Act visibility and potential anti-kickback exposure.

---

# Part III: Skills Deep Dive

Skills are background knowledge packages that Claude loads automatically when conversation context is relevant. Unlike commands, which you explicitly invoke with a slash, skills work silently to make Claude more knowledgeable about marketing and life sciences domains.

The life sciences plugin includes 7 skills: 5 modified from the base marketing plugin and 2 entirely new.

## Overview of All 7 Skills

| Skill | Source | Trigger Topics | Life Sciences Additions |
|-------|--------|---------------|------------------------|
| `brand-voice` | Modified | Brand voice, style, tone, terminology, **pharma fair balance, ISI, claim substantiation** | Pharma brand voice rules, ISI placement, claim substantiation, pharma tone by audience, drug naming conventions, prohibited language |
| `campaign-planning` | Modified | Campaigns, launches, calendars, KPIs, **disease awareness, congress marketing, HCP engagement, regulatory review workflows** | 6 LS campaign types, HCP/patient/payer segmentation, MLR review timelines, pharma channel guide |
| `competitive-analysis` | Modified | Competitors, positioning, battlecards, **drug labels, formulary positioning, clinical trial benchmarking, pipeline intelligence** | Formulary analysis, clinical trial comparison, label comparison, pipeline tracking, LS battlecard sections |
| `content-creation` | Modified | Content drafting, SEO copy, headlines, CTAs, **MLR-ready materials, PI/SmPC content, clinical data visualizations, MOA descriptions** | 5 LS content types, reference annotation, PI/SmPC integration, content classification for MLR |
| `performance-analytics` | Modified | Metrics, reporting, trends, attribution, **pharma KPIs (NRx, TRx, SOV), prescriber adoption, congress engagement** | 36 pharma KPIs across 5 categories, brand performance report template, launch tracker dashboard, prescriber tracking |
| `regulatory-compliance` | **New** | FDA/EMA compliance, MLR review, fair balance, off-label restrictions, promotional classification | Full skill: classification matrix, MLR simulation checklists, fair balance scorer, off-label guardrails, 2 reference docs |
| `medical-affairs-liaison` | **New** | KOL engagement, MSL planning, advisory boards, congress strategy, medical affairs | Full skill: MSL planning, KOL mapping/tiering, advisory board planning, congress strategy, 2 reference docs |

---

## Modified Skills: What Was Added for Life Sciences

### Skill: `brand-voice` (Modified)

**Name:** brand-voice

**Trigger Description (from SKILL.md frontmatter):**
> "Apply and enforce brand voice, style guide, and messaging pillars across content. Use when reviewing content for brand consistency, documenting a brand voice, adapting tone for different audiences, checking terminology and style guide compliance, enforcing pharma fair balance requirements, managing ISI placement, or ensuring claim substantiation in life sciences promotional materials."

**Base Knowledge (Preserved):** Brand voice documentation framework (personality, attributes, audience awareness, messaging pillars, tone spectrum, style rules, terminology), voice attribute spectrums, tone adaptation by channel and situation, style guide enforcement (grammar, formatting, punctuation), and terminology management (preferred terms, product names, inclusive language, jargon, competitor terms).

**Life Sciences Additions (4 New Sections):**

**1. Pharma Brand Voice Rules.** Establishes the principle that every word in a pharmaceutical promotional piece carries legal and clinical weight. Three subsections:

- **Fair Balance in Brand Voice:** Rules for ensuring risk information has comparable prominence to efficacy information. Specific prohibitions include burying risk in smaller fonts or lighter colors, using minimizing language like "merely," "only," or "just a minor" when describing side effects, and presenting efficacy claims without corresponding safety context.

- **ISI Placement:** Requirements for Important Safety Information across formats. ISI must use clear, direct language with no euphemisms for adverse events, follow the approved PI/SmPC verbatim for required statements, appear in normal reading flow rather than requiring a separate click or scroll past the fold, and be accessible without extra interaction in digital materials.

- **Claim Substantiation Requirements:** A detailed table mapping 5 claim types to their required substantiation sources:

| Claim Type | Substantiation Required |
|------------|------------------------|
| Efficacy claim | Cited clinical trial data from approved labeling |
| Superiority claim | Head-to-head comparative trial data |
| Safety claim | Approved labeling language |
| MOA claim | Approved labeling or published literature |
| Patient outcome claim | Real-world evidence or clinical trial with specified study design |

Rules include: never extrapolate across indications, always include study name/design/population, present absolute numbers alongside relative risk reductions, and never use superlatives without head-to-head data.

**2. Pharma Tone Adaptation by Audience.** A table mapping 6 audiences to appropriate tone and constraints:

- **HCPs:** Scientific, evidence-based, peer-level. Use clinical terminology and cite trial data.
- **Patients:** Empathetic, clear, empowering. 6th-8th grade reading level, no medical jargon, ISI in accessible format.
- **Caregivers:** Supportive, practical, informative. Acknowledge their role and address emotional burden.
- **Payers:** Economic, outcomes-focused, data-driven. Lead with HEOR data (NNT, ICER, budget impact).
- **KOLs:** Collegial, data-rich, discussion-oriented. No promotional framing; invite scientific dialogue.
- **MSLs (internal):** Precise, balanced, non-promotional. Strictly scientific exchange.

**3. Pharma Terminology Management.** Drug naming conventions table (4 contexts: scientific audience, patient-facing, regulatory submissions, reminder advertising, each with correct format), and clinical terminology standards (9 abbreviations with when to spell out, e.g., OS, PFS, ORR, HR, NNT, AE, MOA, PI, SmPC).

**4. Prohibited Language.** Table of 6 prohibited terms with explanations and alternatives: "Cure" (use "treatment"), "Safe" unqualified (use "well-tolerated in clinical trials"), "Proven" unqualified (use "demonstrated efficacy in [Study Name]"), "Breakthrough" in claims (use only if FDA Breakthrough Therapy designated), "First-line"/"Standard of care" unsupported (cite specific guideline), and any off-label use suggestion.

**Practical Pharma Scenario:**

A medical communications agency submits a branded leave-behind piece for a GLP-1 receptor agonist. The brand manager asks Claude: "Review the language in this detail aid for compliance with our brand voice and pharma terminology rules."

Claude loads the `brand-voice` skill (including life sciences additions) and checks: drug naming convention (brand name should appear with INN on first mention for HCP audiences), claim substantiation (every efficacy statement has a reference annotation), prohibited language (flags "proven weight loss" as needing qualification), ISI placement (verifies ISI appears within normal reading flow), and fair balance (assesses whether the 4-page efficacy section is balanced by the 1-page safety section -- it is not, and Claude flags this as a major concern).

---

### Skill: `campaign-planning` (Modified)

**Name:** campaign-planning

**Trigger Description (from SKILL.md frontmatter):**
> "Plan marketing campaigns with objectives, audience segmentation, channel strategy, content calendars, and success metrics. Use when launching a campaign, planning a product launch, building a content calendar, allocating budget across channels, defining campaign KPIs, planning life sciences campaigns (disease awareness, congress marketing, HCP engagement, patient support programs), segmenting HCP audiences, or building regulatory review workflows into campaign timelines."

**Base Knowledge (Preserved):** OAMCM campaign framework, channel selection guide (owned/earned/paid), content calendar creation, production timeline benchmarks, budget allocation approaches, and success metrics by campaign type.

**Life Sciences Additions (4 New Sections):**

**1. Life Sciences Campaign Types.** Detailed frameworks for 6 pharma-specific campaign types: disease awareness (unbranded, no product naming, "talk to your doctor" CTA only), product launch (3 phases spanning 18+ months with regulatory constraints at each phase), congress marketing (6-9 month planning lead time, booth/symposia/KOL components), peer-to-peer (speaker programs, advisory boards, compliance requirements), patient support programs (co-pay assistance, nurse educators, adherence monitoring), and medical education (CME vs. non-CME governance distinctions).

**2. Life Sciences Audience Segmentation.** Three detailed segmentation frameworks: HCP segmentation across 7 dimensions (specialty, prescribing behavior, influence tier, practice setting, digital engagement, formulary access, patient volume), patient segmentation across 6 dimensions (disease stage, treatment status, health literacy, caregiver involvement, insurance coverage, geography), and payer segmentation across 4 dimensions (payer type, formulary status, decision-maker role, lives covered).

**3. Regulatory Review Workflow.** MLR review timeline benchmarks for 7 material types (ranging from 3-4 weeks for social media content to 8-12 weeks for video content), and the critical Campaign Timeline Adjustment Rule: add MLR lead time on top of standard production timelines. What takes 3-5 days in general marketing takes 5-8 weeks in pharma.

**4. Life Sciences Channel Guide.** Table of 8 pharma-specific channels (medical journals, medical portals, conference booths, MSL field visits, patient advocacy partnerships, rep-triggered email, DTC television/digital, formulary dossiers) with audience, use case, and regulatory considerations for each.

---

### Skill: `competitive-analysis` (Modified)

**Name:** competitive-analysis

**Trigger Description (from SKILL.md frontmatter):**
> "Research competitors and compare positioning, messaging, content strategy, and market presence. Use when analyzing a competitor, building battlecards, identifying content gaps, comparing feature messaging, preparing competitive positioning recommendations, comparing drug labels and indications, analyzing formulary positioning, benchmarking clinical trial data across competitors, or evaluating competitive pipeline and lifecycle management strategies in life sciences."

**Base Knowledge (Preserved):** Competitive research methodology (primary and secondary sources), messaging comparison frameworks, content gap analysis, positioning strategy, and battlecard creation.

**Life Sciences Additions (5 New Sections):**

**1. Formulary Positioning Analysis.** Comparison template with 9 dimensions (commercial formulary tier, Medicare Part D, prior authorization, step therapy, quantity limits, specialty pharmacy, patient OOP cost, co-pay assistance, lives covered). Data sources: MMIT, Fingertip Formulary, Elsevier Gold Standard, payer policy documents, CMS formulary files.

**2. Clinical Trial Comparison.** Pivotal trial comparison matrix with 14 parameters (trial name, design, N, primary endpoint, primary result, key secondary endpoints, median follow-up, OS, PFS, ORR, DoR, Grade 3-4 AEs, discontinuation rate, QoL data). Critical caveat prominently stated: "Never make cross-trial comparisons as if they were head-to-head data."

**3. Label Comparison.** Template covering 10 label elements (indications, line of therapy, combo vs. mono, biomarker requirements, black box warning, REMS, dosing, route, contraindications, pregnancy category).

**4. Pipeline Intelligence.** Tracking table (pipeline product, sponsor, phase, indication, expected readout, potential impact) with data sources: ClinicalTrials.gov, investor presentations, SEC filings, conference abstracts, FDA/EMA actions.

**5. Life Sciences Battlecard Additions.** Four pharma-specific battlecard sections: clinical differentiation (head-to-head data, efficacy by endpoint, safety advantages, convenience), access and affordability (formulary positioning, OOP cost, support programs, reimbursement), regulatory and label advantages (broader indication, fewer restrictions, companion diagnostic requirements), and objection handling for life sciences with 4 pre-built objection/response pairs addressing common HCP pushback like "Competitor X has longer survival data."

Additionally, a competitive monitoring section lists 6 pharma-specific intelligence channels: FDA/EMA regulatory actions, ClinicalTrials.gov, congress abstracts, analyst reports (EvaluatePharma, GlobalData, Citeline), patent filings/expirations, and payer policy updates.

---

### Skill: `content-creation` (Modified)

**Name:** content-creation

**Trigger Description (from SKILL.md frontmatter):**
> "Draft marketing content across channels -- blog posts, social media, email newsletters, landing pages, press releases, and case studies. Use when writing any marketing content, when you need channel-specific formatting, SEO-optimized copy, headline options, calls to action, MLR-ready promotional materials, PI/SmPC-referenced content, clinical data visualizations, MOA descriptions, formulary dossier content, or life sciences content requiring reference annotation and regulatory compliance."

**Base Knowledge (Preserved):** Templates for 6 content types (blog, social, email newsletter, landing page, press release, case study), writing best practices by channel, SEO fundamentals, headline and hook formulas, and CTA best practices.

**Life Sciences Additions (2 New Sections):**

**1. Life Sciences Content Types.** Five specialized content formats:

- **Branded Sales Aid (Detail Aid):** 8-part structure (cover with brand/generic/indication, efficacy pages with charts and citations, safety pages with AEs and contraindications, dosing/administration, access/support, ISI pages, references, PI/SmPC). Every claim must be annotated with its source reference. Full MLR review required.

- **Clinical Data Visualization:** 5 common types (Kaplan-Meier curves, forest plots, waterfall plots, spider plots, bar charts). Rules: never modify axes/scales to exaggerate, include complete statistical context, cite sources, present competitor data only from published sources.

- **Mechanism of Action (MOA) Content:** Rules: base on approved labeling or published literature, ensure scientific accuracy verified by medical affairs, do not imply benefits beyond what the MOA supports.

- **Formulary Dossier:** AMCP Format standard with 7 sections (product info, disease description, clinical evidence, health economics, comparative effectiveness, real-world evidence, appendices).

- **Patient Education Materials:** Requirements: 6th-8th grade reading level, multiple languages, ISI in patient-friendly language, health literacy expert review, ADA accessibility for digital.

**2. MLR Review Requirements for Content.** Three subsections:

- **Reference Annotation:** Format specification using superscript notation (^[1], ^[2]). Every efficacy claim needs a reference. Safety claims reference PI/SmPC. Sequential numbering required.

- **PI/SmPC Integration by Format:** Print materials attach full PI. Digital materials provide a prominent link. Video/audio directs audience to where to find PI. Social media includes a link in every branded post or bio.

- **Content Classification for MLR:** Table mapping 8 content types to their review level: branded promotional (Full MLR), unbranded (Medical + Legal), reminder (Abbreviated MLR), scientific exchange (Medical only), internal training (Full MLR -- same rigor as external), congress materials (Full MLR), social media branded (Full MLR), and press releases with product claims (Full MLR + Corporate Communications).

---

### Skill: `performance-analytics` (Modified)

**Name:** performance-analytics

**Trigger Description (from SKILL.md frontmatter):**
> "Analyze marketing performance with key metrics, trend analysis, and optimization recommendations. Use when building performance reports, reviewing campaign results, analyzing channel metrics (email, social, paid, SEO), identifying what's working and what needs improvement, tracking pharma KPIs (NRx, TRx, market share, share of voice), measuring prescriber adoption, analyzing congress engagement scores, or reporting on HCP and patient engagement in life sciences marketing."

**Base Knowledge (Preserved):** Marketing metrics by channel (email, social, paid, SEO, content, pipeline), reporting templates (weekly, monthly, QBR), trend analysis and forecasting, attribution modeling, and optimization recommendations framework.

**Life Sciences Additions (3 New Sections):**

**1. Life Sciences Performance Metrics.** Five KPI category tables covering 36 pharma-specific metrics:

- **Commercial KPIs (10 metrics):** NRx (new prescriptions), TRx (total prescriptions), market share, share of voice, prescriber adoption rate, prescriber loyalty/persistence, patient starts, patient persistence, days on therapy (DOT), and revenue per prescription.

- **HCP Engagement KPIs (7 metrics):** HCP reach, frequency (contact rate), detail effectiveness, rep-triggered email open rate, digital engagement score, sample-to-Rx conversion, and MSL interaction quality.

- **Payer and Market Access KPIs (6 metrics):** Formulary coverage (lives), formulary wins, average time to formulary listing, PA override rate, patient OOP cost, and co-pay assistance utilization.

- **Congress Engagement KPIs (7 metrics):** Booth traffic, symposium attendance, poster visits, KOL meetings completed, social media impressions (congress), post-congress content engagement, and media coverage.

- **Patient Engagement KPIs (6 metrics):** PSP enrollment rate, patient website visits, patient education downloads, adherence program engagement, patient NPS/CSAT, and caregiver engagement.

Each metric includes a definition, data source, and benchmark/target guidance.

**2. Life Sciences Reporting Templates.** Two specialized templates:

- **Brand Performance Report (Monthly):** 8 sections -- executive summary (NRx/TRx trend, market share), commercial metrics, HCP engagement, payer/access, patient metrics, competitive intelligence, campaign performance, and recommendations.

- **Launch Tracker Dashboard:** 6 components for the first 12-18 months -- launch curve (weekly NRx vs. plan and analogues), prescriber adoption curve, formulary wins tracker, patient funnel, SOV, and field force effectiveness.

**3. Prescriber Tracking and Share of Voice.** Prescriber segmentation by adoption status (Champions, Trialists, Prospects, Lapsed). SOV measurement guidance: track across channels, compare SOV to market share (SOV > share = growth signal), measure by therapeutic area.

---

## New Skills (Detailed Descriptions)

### Skill: `regulatory-compliance` (New)

**Name:** regulatory-compliance

**Trigger Description (from SKILL.md frontmatter):**
> "Pharmaceutical and medical device regulatory compliance for marketing materials. Use when reviewing promotional content for FDA or EMA compliance, preparing materials for MLR review, checking fair balance requirements, classifying promotional materials by type, simulating medical-legal-regulatory review, ensuring off-label restrictions are met, or navigating life sciences advertising regulations."

**Core Knowledge (5 Major Sections):**

**1. Promotional Material Classification.**

The classification matrix defines 7 material types:

| Type | Product Named | Claims Made | Review Required |
|------|---------------|-------------|-----------------|
| Branded promotional | Yes | Yes | Full MLR |
| Unbranded disease awareness | No | Disease-level only | Medical + Legal |
| Reminder advertising | Yes | No | Abbreviated MLR |
| Help-seeking advertisement | No | No | Medical + Legal |
| Scientific exchange | Varies | Scientific data | Medical review |
| Institutional advertising | No (company only) | No product claims | Legal + Corporate |
| Patient labeling | Yes | Approved labeling only | Regulatory |

A 4-step decision tree walks through classification: (1) Does the material name a product? (2) Does it make efficacy/safety/superiority claims? (3) Is it intended for scientific exchange? (4) Default to branded promotional.

**2. MLR Review Simulation.**

Three detailed checklists with 10 items each:

- **Medical Review Checklist:** Efficacy claims match labeling, clinical data accuracy, statistical context, study limitations, patient population described, no extrapolation, MOA accuracy, AE profile complete, no off-label implications, references complete.

- **Legal Review Checklist:** No unsubstantiated comparatives, no superlatives, trademark compliance, copyright compliance, no misleading data, fair competitor references, testimonial disclosures, no outcome guarantees, Sunshine Act/EFPIA compliance, HIPAA/GDPR privacy.

- **Regulatory Review Checklist:** Indication matches labeling, fair balance, ISI complete, black box warning if applicable, PI/SmPC attached, material coded, expiration date, distribution channel appropriate, OPDP/EMA filing, local requirements.

Plus a table of 8 common MLR rejection reasons with prevention advice: claim not supported by reference, misleading data presentation, insufficient fair balance, off-label implication, missing ISI, outdated references, unapproved comparative claim, and inconsistency with current labeling.

**3. Fair Balance Checker.**

The 5-dimension scoring framework (Prominence, Completeness, Readability, Placement, Language), each 1-5 with detailed criteria per score level. Scoring thresholds: 4-5 average = adequate, 3 = at risk, below 3 = inadequate. Plus a fair balance requirements table by content format (print detail aid, digital banner, email, video/audio, social media, website, conference poster) specifying what fair balance looks like in each medium.

**4. Off-Label Restriction Compliance.**

Seven red flags to watch for (unapproved populations, different dosing, trials in unapproved indications, off-label testimonials, cross-indication comparisons, broader population language, links to off-label publications). A comparison table distinguishing 5 permissible scientific exchanges from 5 prohibited promotional activities. For example: responding to unsolicited HCP requests is permissible; proactively sharing off-label data in a promotional context is not.

**5. Regulatory Framework References.**

Points to the two reference documents for detailed guidance.

**Reference Document: `fda-promotional-rules.md`**

This reference provides comprehensive US FDA regulatory guidance:

- **Governing Authority:** OPDP (CDER), CBER (biologics), CDRH (devices)
- **Legal Framework:** FD&C Act Section 502, 502(n); 21 CFR 202, 201.100, 99
- **Material Categories:** Product claim ads (generic name prominence, brief summary, fair balance), reminder ads (name only, no claims, prohibited for black box products), help-seeking ads (disease only, FTC-regulated)
- **Enforcement Actions:** Untitled letters (voluntary correction), warning letters (demand immediate action), seizure, injunctions, criminal prosecution
- **OPDP Requirements:** Brief summary for print, major statement for broadcast (toll-free number, website, print reference, ask doctor/pharmacist), fair balance standard, substantiation requirements
- **Digital/Social Media Guidance:** Three FDA guidance documents cited (2014 character-limited platforms, 2014 correcting misinformation, 2009 risk information). Key rules for sponsored links, social posts, user-generated content, paid search, and influencer/KOL posts
- **Pre-Submission:** Form FDA 2253, pre-launch restrictions, REMS communication plans

**Reference Document: `ema-requirements.md`**

This reference provides comprehensive EU regulatory guidance:

- **Legal Framework:** Directive 2001/83/EC (Title VIII, Articles 86-100), Regulation (EC) No 726/2004
- **HCP Advertising (Article 91):** Required content (SmPC-compatible, supply classification, revision date), content standards (accurate, verifiable, sufficiently complete), prohibited practices (Article 94: no gifts except inexpensive practice-relevant items, modest hospitality, limited free samples)
- **Public Advertising:** Article 88 prohibition on DTC for prescription medicines, disease awareness permitted if no product reference, OTC advertising requirements
- **Member State Variations:** 5 countries detailed: Germany (HWG, FSA self-regulation), France (ANSM visa pre-approval, Bertrand Law transparency), UK post-Brexit (MHRA, PMCPA/ABPI Code, certified signatory pre-approval), Italy (AIFA, prior authorization for HCP materials, Farmindustria Code), Spain (AEMPS, Royal Decree 1416/1994, Farmaindustria Code)
- **SmPC Compliance:** Mapping of 6 SmPC sections (4.1 indications, 4.2 posology, 4.3 contraindications, 4.4 warnings, 4.8 undesirable effects, 5.1 pharmacodynamic properties) to promotional relevance
- **EFPIA Code:** Accuracy, balance, fairness requirements; "safe" not without qualification; "new" limited to 12 months; transparency disclosure code for transfers of value to HCPs/HCOs
- **Digital Advertising:** Same rules as traditional media, HCP-gated access for promotional content, GDPR compliance

**Practical Pharma Scenario:**

A regulatory affairs specialist receives a set of branded social media posts from the marketing team for compliance review. She asks Claude: "What are the MLR review requirements for branded social media content, and what fair balance looks like on social platforms?"

Claude loads the `regulatory-compliance` skill and explains: branded social media posts require Full MLR review (from the content classification table). Fair balance on social media requires an ISI link in every branded post and a risk summary in post text for platforms that allow sufficient character space (from the fair balance by format table). Additionally, Claude references the FDA's 2014 guidance on character-limited platforms, explaining the one-click rule for risk information, and notes that influencer/KOL posts about products must comply with the same standards as company-generated content (from the `fda-promotional-rules.md` reference).

---

### Skill: `medical-affairs-liaison` (New)

**Name:** medical-affairs-liaison

**Trigger Description (from SKILL.md frontmatter):**
> "Plan and manage medical affairs activities including MSL engagement, KOL mapping and tiering, advisory board planning, and medical congress strategy. Use when developing KOL engagement plans, mapping opinion leaders in a therapeutic area, planning advisory boards, creating congress strategies, coordinating MSL field activities, or bridging medical affairs and commercial marketing in life sciences."

**Core Knowledge (4 Major Sections):**

**1. MSL Engagement Planning.**

Establishes the critical distinction between MSLs and sales representatives through a 6-dimension comparison (function, reporting line, content, initiation, compensation, regulatory). MSLs are medical affairs professionals focused on scientific exchange, reporting to medical affairs (not commercial), using published data (not promotional materials), with compensation not tied to prescribing behavior.

Territory planning based on scientific engagement needs: KOL density, academic medical centers, clinical trial sites, congress density, travel logistics. Interaction frequency targets: Tier 1 KOLs quarterly (4-6/year), Tier 2 semi-annually (2-3/year), Tier 3 annually. MSL Activity Metrics table with 6 metrics: KOL interactions per quarter (target 40-60 per MSL), Tier 1 coverage (>90%), interaction quality score (trend tracking), insights captured (5-10 per quarter), medical information requests handled, and congress attendance.

**2. KOL Mapping and Tiering.**

Seven identification sources: publications (PubMed, Scopus), clinical trials (ClinicalTrials.gov PIs), congress presentations, guideline committees (NCCN, ACC/AHA, ESMO, ADA), editorial boards, peer nomination, and social media/digital influence.

Tier summary: Tier 1 (National/Global) = guideline authors, major congress speakers, high-impact publications, highest engagement priority; Tier 2 (Regional) = regional speakers, department heads, active researchers, high priority; Tier 3 (Local/Community) = high-prescribing community physicians, local leaders, standard priority.

KOL Profiling template with 10 data points: professional background, research focus, publication record, congress activity, guideline involvement, industry relationships (check Sunshine Act/EFPIA disclosures), digital presence, sentiment, engagement history.

**3. Advisory Board Planning.**

8-step planning checklist: define objective, justify need, select participants by expertise (not prescribing volume), set FMV compensation, prepare agenda, compliance review, document outcomes, demonstrate utilization.

4 format options: in-person (8-15 advisors, half/full day), virtual (6-12, 2-4 hours), ad hoc consulting (1-3, 1-2 hours), standing committee (8-12, 2-4 meetings/year).

8 compliance requirements: expertise-based selection, FMV compensation, justified numbers, appropriate venue, modest hospitality, pre-meeting contracts, documented outcomes, transparency reporting.

**4. Congress Strategy.**

Congress engagement model mapping 7 activities to leaders and objectives: scientific presentations (medical affairs/R&D, data dissemination), satellite symposia (medical + commercial, education), exhibition booth (commercial + medical, HCP engagement), KOL meetings (MSL team, relationship building), competitive intelligence (medical + commercial, competitor assessment), media engagement (corporate communications, press coverage), social media (commercial compliant, amplification).

Prioritization criteria: therapeutic relevance, KOL attendance density, abstract opportunities, competitive intel value, investment required.

Post-congress activities checklist: distribute highlights, update competitive files, follow up KOL meetings, repurpose content, analyze metrics.

**Reference Document: `kol-tier-framework.md`**

Detailed scoring methodology with 7 dimensions:

1. **Publication Impact (Weight 20-25%):** Scored 1-5 from minimal activity to 10+ first/last-author top-tier publications with top-decile H-index
2. **Clinical Trial Leadership (Weight 15-20%):** From no involvement to PI or steering committee on multiple Phase 3 trials
3. **Congress Presence (Weight 15-20%):** From minimal to invited plenary/keynote at major international congresses (ASCO, ESMO, AHA)
4. **Guideline and Society Involvement (Weight 15-20%):** From basic membership to chair or lead author of major treatment guidelines (NCCN, ACC/AHA)
5. **Institutional Influence (Weight 10-15%):** From individual practitioner to department chair at top academic medical center
6. **Digital and Media Influence (Weight 5-10%):** From no digital presence to 10K+ HCP followers, active educator, media spokesperson
7. **Engagement Potential (Weight 10-15%):** From anti-industry stance to known willingness with prior positive experience

Composite Score = SUM(score x weight). Tier thresholds: Tier 1 (4.0-5.0, top 5-10%), Tier 2 (3.0-3.9, next 15-20%), Tier 3 (2.0-2.9, next 25-30%). Four qualitative validation checks: Does the tier match MSL field experience? Would other KOLs agree? Are there emerging stars scored lower? Are there high-scorers who are disengaged?

Also includes: KOL landscape mapping (network visualization through co-authorship, institutional affiliations, congress co-presentations, guideline committee co-membership), geographic distribution for MSL alignment, emerging KOL identification criteria (junior faculty, early-career researchers, social media educators, clinical fellows at top institutions), and KOL engagement tracker template with 8 columns (Name, Tier, Last Interaction, Next Planned, Engagement Type, Key Insights, Sentiment, MSL Owner).

**Reference Document: `congress-planning-guide.md`**

Detailed congress planning reference:

- **Major Congress Calendar:** Congresses listed across 7 therapeutic areas: Oncology (ASCO, ESMO, ASH, AACR), Cardiology (ACC, AHA, ESC), Endocrinology/Diabetes (ADA, EASD), Neurology (AAN, ECTRIMS), Hepatology/GI (AASLD, EASL, DDW), Immunology/Rheumatology (ACR, EULAR), Respiratory (ATS, ERS).

- **7-Phase Planning Timeline:** 12 months before (participation decision, booth reservation, data identification, budget planning), 9 months (abstracts, symposium planning, KOL identification, hotels, booth design), 6 months (abstract confirmations, symposium finalization, materials development, MLR submission, social media plan), 3 months (booth design finalized, MLR complete, speaker training, field force briefing, CI strategy, media materials), 1 month (materials shipped, congress guide distributed, logistics confirmed, social media pre-scheduled, CI templates prepared, staff briefed), during congress (setup, KOL meetings, CI coverage, symposium execution, social media, lead capture, daily briefings), post-congress within 2 weeks (congress report, highlights distribution, KOL follow-up, archiving, content repurposing, metrics analysis, competitive file updates, next year planning).

- **Booth Strategy:** Staffing plan (5 roles: booth lead, medical affairs/MSLs, commercial, compliance, technical support), content rules (MLR-approved only, staff trained on approved messages, GDPR for EU congresses), and traffic optimization tips (schedule KOL visits during low-traffic periods, use interactive digital tools, position high-interest content prominently, staff during peak hours).

- **Satellite Symposium Planning:** Program design (60-90 minutes, 2-3 presentations, Tier 1 KOL speakers), speaker management (expertise-based selection, approved slides, training call 2-4 weeks before, disclosure requirements, FMV compensation), and compliance (clearly labeled as sponsored, separate from official sessions, no promotion in CME, modest hospitality, documented attendance).

- **Competitive Intelligence:** Gathering framework (new data, label expansion signals, pipeline updates, messaging changes, KOL relationships), template table (Competitor, Presentation, Key Data Point, Implication, Action Required), and post-congress debrief structure (review intel, assess positioning impact, adjust strategy, update battlecards, communicate to leadership and field).

**Practical Pharma Scenario:**

A medical affairs director is planning advisory boards for the upcoming year. She asks Claude: "Help me plan an advisory board program for our SGLT2 inhibitor in heart failure. We need input on real-world treatment patterns and barriers to earlier initiation."

Claude loads the `medical-affairs-liaison` skill and walks her through the 8-step planning checklist: define the objective (gather expert input on barriers to early SGLT2i initiation in HFrEF), justify the format (advisory board chosen because interactive multi-expert discussion is needed to understand regional variation in treatment patterns -- a survey alone would not capture the nuance), select participants by expertise in heart failure management (cardiologists, heart failure specialists, clinical pharmacists -- not by prescribing volume), establish FMV compensation based on documented specialty rates for a 4-hour virtual engagement, design a structured agenda with 2/3 of time allocated to advisor input and 1/3 to context-setting presentations, submit the plan and participant list for compliance review, plan outcome documentation, and establish a utilization plan showing how advisory board insights will inform the patient support program redesign and MSL talking points.

---

# Part IV: Connectors & MCP Servers

## Understanding the Connector System

The life sciences marketing plugin connects to external tools and services via MCP (Model Context Protocol) servers. These connections allow Claude to read data from your marketing and life sciences tools, search biomedical literature, access drug labeling data, and post content to communication channels.

Two key concepts:

1. **MCP Servers** are the actual technical connections defined in `.mcp.json`. They specify the server type (HTTP or stdio), the URL or command to connect, and any required environment variables.
2. **Placeholders** are tool-agnostic references in plugin files using `~~category` syntax (like `~~biomedical literature` or `~~clinical trials data`). These get resolved to whatever specific tool you have connected in that category.

## Complete MCP Server Inventory

### Base Marketing Servers (9 -- Inherited from Base Plugin)

| Server | Service | Type | URL | Purpose |
|--------|---------|------|-----|---------|
| `slack` | Slack | HTTP | `https://mcp.slack.com/mcp` | Post reports, briefs, drafts to team channels |
| `canva` | Canva | HTTP | `https://mcp.canva.com/mcp` | Access and edit design assets |
| `figma` | Figma | HTTP | `https://mcp.figma.com/mcp` | Reference design files and brand assets |
| `hubspot` | HubSpot | HTTP | `https://mcp.hubspot.com/anthropic` | Campaign data, contacts, marketing automation |
| `amplitude` | Amplitude | HTTP | `https://mcp.amplitude.com/mcp` | Product analytics and user behavior data |
| `notion` | Notion | HTTP | `https://mcp.notion.com/mcp` | Brand guidelines, campaign briefs, knowledge base |
| `ahrefs` | Ahrefs | HTTP | `https://api.ahrefs.com/mcp/mcp` | SEO keyword research, backlinks, site audits |
| `similarweb` | Similarweb | HTTP | `https://mcp.similarweb.com` | Competitive traffic analysis and market benchmarking |
| `klaviyo` | Klaviyo | HTTP | `https://mcp.klaviyo.com/mcp` | Email marketing sequences and campaign analytics |

All 9 are preserved with identical configuration from the base plugin.

### New Life Sciences Servers (4)

| Server | Service | Type | Configuration | Purpose |
|--------|---------|------|---------------|---------|
| `pubmed` | PubMed (NCBI) | stdio | `node ${CLAUDE_PLUGIN_ROOT}/servers/pubmed-server.js` | Biomedical literature search, reference verification, KOL publication analysis |
| `clinicaltrials` | ClinicalTrials.gov | HTTP | `https://clinicaltrials.gov/api/v2` | Clinical trial search, PI identification, competitive pipeline intel |
| `openfda` | OpenFDA | HTTP | `https://api.fda.gov` | Drug labeling data, adverse event databases, regulatory actions |
| `veeva` | Veeva CRM | HTTP | `https://mcp.veeva.com/mcp` | HCP engagement tracking, approved email, content management |

**PubMed (NCBI)** is the only stdio-type server in the plugin (all others use HTTP). It runs as a local process using a Node.js script at `${CLAUDE_PLUGIN_ROOT}/servers/pubmed-server.js` and requires an NCBI API key set via the `NCBI_API_KEY` environment variable. PubMed powers three critical life sciences workflows: verifying cited references during `/mlr-review`, searching for KOL publications during `/kol-strategy`, and finding relevant clinical evidence for competitive analysis.

**ClinicalTrials.gov** is a public REST API requiring no authentication. It enables Claude to search for clinical trials by condition, intervention, or investigator name -- supporting KOL identification (finding principal investigators), competitive pipeline intelligence (tracking competitor trial registrations and status changes), and trial data comparison for competitive analysis.

**OpenFDA** is a public REST API requiring no authentication. It provides access to drug labeling data (current and historical prescribing information), adverse event reports (FAERS database), enforcement actions, and drug recall information. This supports `/mlr-review` (cross-checking claims against current labeling) and competitive analysis (comparing approved indications and safety profiles).

**Veeva CRM** requires an active Veeva CRM license and authentication. Veeva is the dominant CRM platform in life sciences, used by the majority of pharma companies for field force management, HCP engagement tracking, approved email distribution, and content management (via Veeva Vault PromoMats). When connected, Claude can access HCP interaction history, pull engagement metrics for performance reporting, and reference approved email templates for `/email-sequence`.

## The Placeholder System with Life Sciences Examples

Plugin files use `~~category` placeholders to reference tools generically, making the plugin adaptable to different organizations' tool stacks.

### Base Connector Categories (7 -- from Base Plugin)

| Category | Placeholder | Included Server | Other Options |
|----------|-------------|----------------|---------------|
| Chat | `~~chat` | Slack | Microsoft Teams |
| Design | `~~design` | Canva, Figma | Adobe Creative Cloud |
| Marketing automation | `~~marketing automation` | HubSpot | Marketo, Pardot, Mailchimp |
| Product analytics | `~~product analytics` | Amplitude | Mixpanel, Google Analytics |
| Knowledge base | `~~knowledge base` | Notion | Confluence, Guru |
| SEO | `~~SEO` | Ahrefs, Similarweb | Semrush, Moz |
| Email marketing | `~~email marketing` | Klaviyo | Mailchimp, Brevo, Customer.io |

### New Life Sciences Connector Categories (9)

| Category | Placeholder | Included Server | Other Options |
|----------|-------------|----------------|---------------|
| Biomedical literature | `~~biomedical literature` | PubMed (NCBI) | Embase, Cochrane Library, Google Scholar |
| Clinical trials data | `~~clinical trials data` | ClinicalTrials.gov | EU Clinical Trials Register, WHO ICTRP |
| Drug safety and labeling | `~~drug safety and labeling` | OpenFDA | DailyMed, EMA medicines database |
| CRM (life sciences) | `~~life sciences CRM` | Veeva CRM | IQVIA OCE, Salesforce Health Cloud |
| MLR review platform | `~~MLR review` | -- (none pre-configured) | Veeva Vault PromoMats, Zinc Ahead |
| Prescribing data | `~~prescribing data` | -- (none pre-configured) | IQVIA, Symphony Health, Komodo Health |
| Formulary data | `~~formulary data` | -- (none pre-configured) | MMIT, Fingertip Formulary, Elsevier Gold Standard |
| Medical education | `~~medical education` | -- (none pre-configured) | Medscape, DocCheck, Coliquio, Doximity |
| Competitive intelligence | `~~competitive intelligence` | -- (none pre-configured) | EvaluatePharma, GlobalData, Citeline |

Five of the 9 new categories have no pre-configured server -- they are placeholder categories documenting the ecosystem of tools that could be connected as MCP servers become available. Only 4 categories (biomedical literature, clinical trials data, drug safety and labeling, and life sciences CRM) have actual MCP server entries in `.mcp.json`.

**How Placeholders Appear in Commands:**

From the `/kol-strategy` command:
```
If ~~clinical trials data is connected, search for:
- Principal investigators on relevant clinical trials
- Authors of recent high-impact publications in the therapeutic area
- Presenters at major congresses in the last 2-3 years
```

When ClinicalTrials.gov is connected, `~~clinical trials data` resolves to it. If you connect the EU Clinical Trials Register instead, the same placeholder resolves to that tool.

## Connecting Each Server

### PubMed (NCBI)

PubMed requires an NCBI API key. To obtain one:

1. Create an NCBI account at https://www.ncbi.nlm.nih.gov/account/
2. Go to the API Key Management page in your account settings
3. Generate a new API key
4. Set the environment variable: `export NCBI_API_KEY=your_key_here`

Once the API key is set, the PubMed server starts automatically when the plugin loads. You can verify the connection by asking Claude to search for publications.

### ClinicalTrials.gov

No setup required. ClinicalTrials.gov is a public API with no authentication. The server is available immediately after plugin installation.

### OpenFDA

No setup required. OpenFDA is a public API with no authentication. For heavy usage, you may want to register for an API key at https://open.fda.gov/apis/authentication/ to get higher rate limits, but it is not required.

### Veeva CRM

Veeva requires an active CRM license. When you first use a command that references `~~life sciences CRM`, Claude will prompt you to authenticate via the Veeva MCP server's OAuth flow. You will need your Veeva instance URL and admin credentials.

### Base Marketing Servers (Slack, HubSpot, etc.)

These connect via standard OAuth flows when first referenced. Claude prompts you with an authentication link. See the base marketing handbook for detailed connection instructions for each.

## Essential vs. Nice-to-Have for Pharma Marketing

| Priority | Connector Category | Why |
|----------|-------------------|-----|
| **Essential** | Knowledge base (Notion/Confluence) | Stores brand guidelines, ISI templates, approved claims libraries, and campaign briefs. Enables automatic guideline loading for `/brand-review` and `/mlr-review`. |
| **Essential** | Life sciences CRM (Veeva) | Core platform for HCP engagement data, approved email, and field force management. Powers HCP engagement KPIs in performance reports. |
| **Essential** | Chat (Slack/Teams) | Enables sharing of MLR review results, congress plans, and competitive briefs with cross-functional teams. |
| **High value** | Clinical trials data (ClinicalTrials.gov) | Powers KOL identification via PI search, competitive pipeline tracking, and trial comparison matrices. Free and no setup required. |
| **High value** | Drug safety and labeling (OpenFDA) | Enables cross-checking claims against current labeling during MLR review. Free and no setup required. |
| **High value** | Marketing automation (HubSpot/Marketo) | Enables data-driven campaign planning and performance reporting with actual campaign metrics. |
| **High value** | Biomedical literature (PubMed) | Powers reference verification in MLR review, KOL publication analysis, and evidence-based content development. |
| **Useful** | SEO tools (Ahrefs) | For branded website optimization, content gap analysis, and organic traffic measurement. |
| **Useful** | Email marketing (Klaviyo) | For sequence design and email performance analytics. Many pharma teams use Veeva Approved Email instead. |
| **Useful** | Design tools (Canva/Figma) | For referencing design assets and brand specifications during content creation. |

## Adding Additional Life Sciences Connectors

The placeholder system makes it straightforward to add tools not pre-configured in the plugin.

### Adding a Medical Education Portal (e.g., Medscape, DocCheck, Coliquio)

Medical education portals are listed as alternatives under the `~~medical education` category but have no pre-configured server. To add one:

**Step 1:** Check if the platform offers an MCP server. Search for "[platform name] MCP server" or check their developer/integration documentation.

**Step 2:** Add the server to `.mcp.json`:

```json
{
  "mcpServers": {
    ...existing servers...,
    "medscape": {
      "type": "http",
      "url": "https://mcp.medscape.com/endpoint"
    }
  }
}
```

**Step 3:** The `~~medical education` placeholder will now resolve to Medscape when referenced in commands or skills.

### Adding Prescribing Data (e.g., IQVIA)

IQVIA is the gold standard for prescription data (NRx, TRx, market share). If IQVIA offers an MCP server:

```json
"iqvia": {
  "type": "http",
  "url": "https://mcp.iqvia.com/mcp"
}
```

This would dramatically enhance `/performance-report` by enabling Claude to pull actual NRx/TRx data, prescriber adoption curves, and market share trends directly, rather than requiring manual data input.

### Adding an MLR Review Platform (e.g., Veeva Vault PromoMats)

If Veeva Vault PromoMats or Zinc Ahead offers an MCP server, connecting it would enable Claude to submit content directly into the MLR workflow after pre-screening with `/mlr-review`, pull the status of materials in review, and access the approved claims library for reference during content creation.

```json
"veeva-vault": {
  "type": "http",
  "url": "https://mcp.veeva.com/vault/mcp"
}
```

### Adding Formulary Data (e.g., MMIT)

Formulary data connectors would enhance `/competitive-brief` by enabling Claude to pull real-time formulary coverage data for competitive positioning analysis rather than relying on manual input.

### Adding Competitive Intelligence (e.g., EvaluatePharma, GlobalData)

These platforms provide pipeline databases, analyst reports, and market forecasts. Connecting them would enable Claude to pull competitor pipeline data during `/competitive-brief` and track pipeline milestones during `/kol-strategy` planning.

### General Process for Any New Connector

1. Verify the tool offers an MCP server (HTTP or stdio type)
2. Add the server configuration to `.mcp.json` with appropriate type, URL, and any required environment variables or authentication
3. Map the tool to the appropriate `~~category` placeholder in `CONNECTORS.md`
4. Restart Claude to pick up the new configuration
5. Test the connection by asking Claude to interact with the new tool

The plugin is designed to be extensible. As the life sciences MCP ecosystem grows -- with more tools like IQVIA, MMIT, Medscape, and Veeva Vault offering MCP servers -- the plugin's capabilities will expand proportionally without requiring changes to commands or skills.
# Part V: Customization & Extension

The `marketing-life-sciences` plugin is itself a customization of the base marketing plugin, built using Approach B (Fork the Plugin) from the plugin development guide. It serves as both a ready-to-use pharma marketing toolkit and a foundation for further specialization. Most life sciences organizations will want to extend it further -- adding therapeutic area depth, company-specific MLR workflows, regional regulatory rules, or proprietary KOL frameworks.

This section covers three approaches to customization, each illustrated with life-sciences-specific examples. For general plugin architecture concepts, refer to the [Plugin Development Guide](plugin-development-guide.md). Here we focus on what pharma, biotech, and medtech teams specifically need to customize and how to do it.

---

## Three Customization Approaches for Life Sciences

| Approach | Best For | Effort | Maintainability | Risk |
|----------|---------|--------|----------------|------|
| **A: Direct Modification** | Adding a therapeutic area, adding regulatory rules for a new market | Low | Plugin updates may overwrite changes | Medium |
| **B: Fork the Plugin** | Creating a therapeutic-area-focused variant, creating a region-specific variant | Medium-High | Full control, manual merge on updates | Low |
| **C: Complementary Skills via CLAUDE.md** | Company brand guidelines, internal MLR processes, formulary strategy, congress calendars | Low | Survives plugin updates with zero conflicts | Low |

---

## Approach A: Direct Plugin Modification

Edit the plugin files directly to add capabilities. This is the fastest path for targeted additions that do not warrant a full fork.

### Example A1: Adding a Therapeutic Area (Oncology)

**Scenario:** Your company focuses on oncology. The plugin's life sciences additions are therapeutic-area-agnostic. You want Claude to understand oncology-specific campaign types, HCP segments, and KPIs when planning oncology campaigns.

**Implementation:**

**Step 1:** Open `skills/campaign-planning/SKILL.md` and append after the existing Life Sciences Addition section:

```markdown
<!-- Oncology Specialization -->

## Oncology Campaign Considerations

### Oncology-Specific Campaign Types

**Biomarker-Driven Disease Awareness**
Campaigns centered on biomarker testing (e.g., PD-L1 expression, MSI-H/dMMR,
BRCA mutations, HER2 status). These are typically unbranded and encourage
testing before treatment selection. Key channel: oncology medical portals
(OncLive, Cancer Network), tumor boards, pathology partnerships.

**Line-of-Therapy Sequencing Campaigns**
Positioning a product within the treatment algorithm (1L, 2L, 3L+). Requires
precise alignment with NCCN Guidelines and approved labeling. All claims must
reference the specific line of therapy in the approved indication.

**Combination Therapy Campaigns**
When the product is approved in combination with another agent, campaigns must
present the combination's efficacy and safety profile, not the monotherapy data.
Fair balance must cover the safety profile of the combination regimen.

**Tumor Board Education Programs**
Non-promotional educational programs targeting multidisciplinary tumor boards
(medical oncologists, surgical oncologists, radiation oncologists, pathologists,
radiologists). Format: case-based discussions with KOL faculty. Compliance:
must be balanced, not product-promotional.

### Oncology HCP Segmentation

| Segment | Description | Engagement Approach |
|---------|-------------|-------------------|
| Medical oncologists | Primary prescribers for systemic therapy | Sales rep + MSL; detail aids, P2P programs |
| Surgical oncologists | Influence neoadjuvant/adjuvant decisions | MSL-led scientific exchange |
| Radiation oncologists | Relevant for combination regimens involving radiation | Congress engagement, tumor board education |
| Hematologist-oncologists | For hematologic malignancies (lymphoma, leukemia, myeloma) | Dedicated field teams, ASH/EHA congress focus |
| Pathologists | Drive biomarker testing that determines treatment eligibility | Unbranded biomarker campaigns, lab partnerships |
| Oncology nurses/APPs | Administer treatments, manage side effects, influence adherence | Patient support program promotion, nurse educator programs |
| Oncology pharmacists | Manage formulary, prior authorizations, specialty pharmacy | Formulary dossiers, HEOR presentations |

### Oncology-Specific KPIs

| KPI | Definition | Oncology Nuance |
|-----|-----------|-----------------|
| Biomarker testing rate | % of eligible patients tested for relevant biomarker before treatment | Critical for biomarker-driven therapies; low testing = missed patients |
| Time to treatment (TTT) | Days from diagnosis to first treatment dose | Influenced by prior authorization delays and specialty pharmacy logistics |
| Line-of-therapy market share | Share within a specific line (1L, 2L, etc.) | More meaningful than overall market share in oncology |
| Duration of therapy (DOT) | Median months on treatment | Key for chronic/maintenance therapies; correlates with revenue |
| Regimen share | Share of a specific combination regimen vs. alternatives | Important when multiple combination partners compete |

### Key Oncology Congresses

| Congress | Timing | Focus | Relevance |
|----------|--------|-------|-----------|
| ASCO Annual Meeting | Late May/early June | Solid tumors, cross-cutting | Largest oncology congress globally |
| ESMO Annual Congress | September/October | Solid tumors, European focus | Primary EU oncology venue |
| ASH Annual Meeting | December | Hematologic malignancies | Must-attend for hematology-oncology |
| AACR Annual Meeting | April | Translational/early science | Pre-clinical and early clinical data |
| SABCS | December | Breast cancer | Specialty congress for breast oncology |
| ASCO GU | January/February | Genitourinary cancers | Specialty congress for prostate, bladder, kidney |
| ASCO GI | January | Gastrointestinal cancers | Specialty congress for CRC, HCC, pancreatic |
```

**Step 2:** Similarly extend `skills/competitive-analysis/SKILL.md` to add oncology-specific competitive intelligence dimensions:

```markdown
<!-- Oncology Competitive Intelligence -->

## Oncology Competitive Analysis Additions

### Clinical Trial Landscape Monitoring
For oncology, track:
- Phase 3 registrational trials by tumor type and line of therapy
- Breakthrough Therapy Designations (BTD) and Accelerated Approval signals
- PDUFA dates for competing products
- Companion diagnostic development timelines

### NCCN Guidelines Monitoring
NCCN Guideline updates are among the most significant competitive events in
oncology. A competitor receiving a Category 1 or "Preferred" designation can
shift market share within weeks. Monitor:
- NCCN Compendium changes quarterly
- Voting member composition and potential KOL influence
- Category of Evidence changes (1, 2A, 2B, 3)
```

**Step 3:** Save both files. Changes take effect immediately.

**Time to implement:** 30-60 minutes.

### Example A2: Adding Regulatory Rules for a New Market (Japan JPMA Code)

**Scenario:** Your company is launching in Japan. The plugin covers FDA and EMA but not Japan's JPMA Code or PMD Act requirements.

**Implementation:**

Create a new reference file at `skills/regulatory-compliance/references/jpma-requirements.md`:

```markdown
# Japan Pharmaceutical Promotion Regulations

## Governing Framework

- **Pharmaceuticals and Medical Devices Act (PMD Act)**
- **JPMA Code of Practice** (Japan Pharmaceutical Manufacturers Association)
- **Fair Competition Code** for ethical pharmaceutical marketing

## Key JPMA Requirements

### Organizational Requirements
- A "Promotion Oversight Department" must exist, separate from sales/marketing
- A designated "Promotional Materials Officer" must review all materials
- Standard operating procedures for drug information promotion are required

### Content Requirements
- All promotional materials must be consistent with the approved Japanese
  package insert (Tenpu Bunsho)
- Comparative claims require head-to-head clinical data conducted in
  compliance with GCP
- Remuneration to HCPs must be appropriate relative to services rendered
- Hospitality at sponsored events must be modest and secondary to the
  educational purpose

### Disclosure Requirements (2024 Update)
- Companies must disclose expenses related to information provision
  activities to HCPs
- Entertainment expenses must be publicly disclosed
- Research funding and grants to medical institutions require transparency

### Enforcement
- JPMA Code Compliance Committee can issue warnings, suspend membership,
  or expel companies
- PMD Act violations can result in business suspension orders from MHLW

## MLR Review Adaptation for Japan
When reviewing materials for the Japanese market:
- Verify all claims against the Japanese package insert (not US PI or EU SmPC)
- Check compliance with JPMA promotional material standards
- Ensure the Promotional Materials Officer review step is included in workflow
- Confirm FMV documentation follows Japanese industry standards
```

Then add a pointer in `skills/regulatory-compliance/SKILL.md` under the Regulatory Framework References section:

```markdown
- `references/jpma-requirements.md` — Japan JPMA Code and PMD Act requirements
```

**Time to implement:** 45 minutes.

---

## Approach B: Fork the Plugin

Copy the entire `marketing-life-sciences` directory, rename it, and modify the copy. Install it as a separate plugin. This is recommended when changes are substantial enough that they define a meaningfully different variant.

### Example B1: Creating "marketing-life-sciences-oncology"

**Scenario:** Your oncology business unit wants a dedicated plugin variant that is deeply specialized for oncology marketing. It should include tumor-type-specific content rules, oncology-only HCP segmentation, NCCN guideline integration, and oncology-focused KPIs as defaults rather than additions.

**Implementation:**

**Step 1:** Copy the plugin.

```bash
cp -r marketing-life-sciences/ marketing-life-sciences-oncology/
```

**Step 2:** Update `plugin.json`:

```json
{
  "name": "marketing-life-sciences-oncology",
  "version": "1.0.0-onc",
  "description": "Oncology-specialized marketing plugin for pharma and biotech oncology teams. Includes tumor-type-specific content workflows, NCCN guideline alignment, biomarker campaign planning, and oncology congress strategy on top of the full life sciences marketing toolkit.",
  "author": { "name": "Your Company" }
}
```

**Step 3:** Restructure skills for oncology defaults.

Instead of appending oncology content at the end of general skills, make oncology the primary lens. For example, in `skills/campaign-planning/SKILL.md`, restructure the Life Sciences Campaign Types section so oncology types (biomarker awareness, line-of-therapy sequencing, tumor board education, combination therapy campaigns) appear as the primary campaign types, with a note that general pharma types also apply.

**Step 4:** Add an oncology-specific skill.

Create `skills/oncology-landscape/SKILL.md`:

```markdown
---
name: oncology-landscape
description: >
  Oncology treatment landscape, tumor types, and competitive dynamics.
  Use when planning oncology marketing campaigns, analyzing the
  competitive pipeline in oncology, understanding tumor-type-specific
  treatment algorithms, referencing NCCN guidelines, or segmenting
  oncology HCPs by subspecialty.
---

# Oncology Treatment Landscape

## Tumor Type Quick Reference

### Non-Small Cell Lung Cancer (NSCLC)
- **Biomarkers**: EGFR, ALK, ROS1, BRAF V600E, KRAS G12C, MET, RET,
  NTRK, PD-L1 expression
- **Treatment paradigm**: Biomarker testing drives 1L selection;
  IO + chemo backbone for PD-L1 low/negative; targeted therapy for
  driver mutations
- **Key competitors**: Pembrolizumab, nivolumab + ipilimumab,
  atezolizumab, osimertinib, sotorasib, adagrasib
- **Key congresses**: ASCO, ESMO, WCLC (IASLC)

### Breast Cancer
- **Subtypes**: HR+/HER2-, HER2+, Triple-Negative (TNBC)
- **Biomarkers**: ER, PR, HER2, PD-L1, BRCA1/2, PIK3CA
- **Treatment paradigm**: Subtype-driven; CDK4/6 inhibitors dominant
  in HR+/HER2-; ADCs transforming HER2+ and TNBC
- **Key congresses**: SABCS, ASCO, ESMO Breast

[Additional tumor types: CRC, RCC, melanoma, prostate, bladder,
hematologic malignancies...]

## NCCN Guidelines Integration

When creating promotional content for oncology products:
1. Verify the product's NCCN category and designation
2. Never claim guideline endorsement beyond the actual designation
3. Monitor guideline update cycles (panels meet 2-4 times annually)
4. Track competitor guideline positioning changes
```

**Step 5:** Update `.mcp.json` to add oncology-specific data sources if available (for example, adding an NCCN data connector placeholder in `CONNECTORS.md`).

**Result:** A self-contained oncology marketing plugin that any oncology brand team can install and use immediately, with oncology as the default lens rather than an appendix.

### Example B2: Creating "marketing-life-sciences-eu"

**Scenario:** Your EU affiliate team operates under different regulatory constraints than the US headquarters. You need a variant where EMA/EU regulations are the default framework, country-specific rules (Germany HWG, France ANSM visa, UK PMCPA) are first-class citizens, and US FDA rules are secondary reference material.

**Implementation:**

**Step 1:** Copy and rename.

```bash
cp -r marketing-life-sciences/ marketing-life-sciences-eu/
```

**Step 2:** Update `plugin.json`:

```json
{
  "name": "marketing-life-sciences-eu",
  "version": "1.0.0-eu",
  "description": "EU-focused life sciences marketing plugin for pharmaceutical teams operating in European markets. EMA regulations, EFPIA Code, and country-specific rules (Germany HWG, France ANSM, UK PMCPA) as default frameworks.",
  "author": { "name": "Your Company" }
}
```

**Step 3:** Restructure the regulatory-compliance skill.

In `skills/regulatory-compliance/SKILL.md`, reorder the content so the EU framework (Directive 2001/83/EC, EFPIA Code) appears first and FDA rules are referenced as "US-specific additions." Update the MLR Review Simulation section to default to SmPC (not PI) for label verification, and default fair balance checks to EU standards.

**Step 4:** Expand country-specific reference files.

Create individual reference files for each priority market:

- `references/germany-hwg-requirements.md` -- Heilmittelwerbegesetz details, FSA Code, required risk statements ("Zu Risiken und Nebenwirkungen...")
- `references/france-ansm-requirements.md` -- ANSM visa pre-approval process, Bertrand Law transparency, CEPS pricing considerations
- `references/uk-pmcpa-requirements.md` -- ABPI Code, certified signatory requirements, MHRA post-Brexit specifics
- `references/italy-aifa-requirements.md` -- AIFA prior authorization, Farmindustria Code
- `references/spain-aemps-requirements.md` -- AEMPS rules, Farmaindustria Code

**Step 5:** Update the `/mlr-review` command default market to "EU (EMA)" instead of "US (FDA)."

**Step 6:** Update `.mcp.json` to replace or supplement US-focused servers. Add the EU Clinical Trials Register as an alternative or complement to ClinicalTrials.gov. Add EMA medicines database connector placeholder.

**Result:** A plugin where EU teams do not need to mentally translate from a US-default framework. Country-specific compliance is immediately accessible, and the MLR simulation defaults to EU regulatory expectations.

---

## Approach C: Complementary Skills via CLAUDE.md

Keep the `marketing-life-sciences` plugin completely untouched. Add company-specific or project-specific knowledge in your project's `CLAUDE.md` file and `.claude/skills/` directory. This is the recommended approach for company-specific customizations because it survives plugin updates with zero merge conflicts.

### Example C1: Company-Specific Brand Guidelines

**Scenario:** AcmePharma's oncology franchise has a distinct brand voice that differs from both generic marketing and the plugin's general pharma guidelines. Their flagship product "ONCORIX" (vemutatinib) has specific naming conventions, approved claims, and visual identity standards.

**Implementation:**

Create `.claude/skills/acmepharma-brand/SKILL.md` in your project:

```markdown
---
name: acmepharma-brand
description: >
  AcmePharma brand voice and oncology franchise brand guidelines.
  Use when creating content for AcmePharma products, reviewing materials
  against AcmePharma brand standards, drafting content for ONCORIX
  (vemutatinib), or applying AcmePharma's oncology franchise visual
  and verbal identity.
---

# AcmePharma Oncology Franchise Brand Guidelines

## Brand Voice: Oncology Franchise

**Voice Attributes:**
- **Scientifically Grounded**: Every statement is backed by data. We lead
  with evidence, not emotion. We respect the intelligence of oncologists.
- **Empathetically Direct**: We acknowledge the gravity of cancer treatment
  decisions. We are clear, not clinical. We are hopeful without overpromising.
- **Confidently Measured**: We are confident in our data but never dismissive
  of competing approaches. We never use superlatives.

**Tone by Audience:**

| Audience | Tone | Example |
|----------|------|---------|
| Medical oncologists | Peer-scientific, data-led | "In the ONCORIX-301 trial, median PFS was 14.2 months (95% CI: 11.8-16.9) vs. 9.4 months with standard of care (HR 0.62; P<0.001).^[1]" |
| Oncology nurses | Clinical-practical, supportive | "ONCORIX is administered as a 200 mg IV infusion every 3 weeks. The most common adverse reactions (>=20%) were fatigue, nausea, and rash." |
| Patients with cancer | Empathetic, clear, hopeful | "ONCORIX is a treatment option for adults with [approved indication]. Talk to your doctor about whether ONCORIX may be right for you." |
| Payers | Evidence-based, value-oriented | "ONCORIX demonstrated a statistically significant improvement in progression-free survival, with a cost-effectiveness profile favorable vs. current standard of care." |

## ONCORIX (vemutatinib) Naming Conventions

| Context | Format | Example |
|---------|--------|---------|
| First mention in any document | Brand (INN) | ONCORIX (vemutatinib) |
| Subsequent mentions | Brand only | ONCORIX |
| Scientific publications | INN (Brand) | vemutatinib (ONCORIX) |
| Reminder advertising | Brand only, no claims | ONCORIX |
| Regulatory submissions | INN only | vemutatinib |

- ONCORIX is always written in ALL CAPS
- vemutatinib is always lowercase except at sentence start
- The registered trademark symbol (R) appears on the first mention in
  any printed material: ONCORIX(R)

## Prohibited Language (AcmePharma-Specific)

| Term | Status | Use Instead |
|------|--------|-------------|
| "Breakthrough" | Prohibited in all materials | "Demonstrated significant improvement" |
| "Game-changer" | Prohibited | "Represents an advance in treatment" |
| "Cure" | Prohibited in all contexts | Never imply cure for oncology products |
| "Safe" (unqualified) | Prohibited | "Demonstrated a manageable safety profile" |
| "Best-in-class" | Prohibited without head-to-head data | "Demonstrated [specific metric] in [trial name]" |
```

Add routing rules in `CLAUDE.md`:

```markdown
## AcmePharma Brand Standards

When using any marketing-life-sciences command for AcmePharma products,
always apply the acmepharma-brand skill in addition to the plugin's
standard brand-voice skill.

AcmePharma brand rules take precedence over generic pharma brand
guidance when there is a conflict.

All ONCORIX content must use the naming conventions defined in
the acmepharma-brand skill. Flag any deviation as Critical severity.
```

### Example C2: Internal MLR Submission Process and Templates

**Scenario:** AcmePharma uses Veeva Vault PromoMats with a specific MLR workflow that includes a pre-review quality check, defined reviewer roles, and SLA timelines. You want Claude to understand this process when running `/mlr-review`.

Create `.claude/skills/acmepharma-mlr-process/SKILL.md`:

```markdown
---
name: acmepharma-mlr-process
description: >
  AcmePharma internal MLR review process, submission requirements,
  and workflow timelines. Use when preparing content for MLR review,
  running the mlr-review command, estimating review timelines, or
  understanding AcmePharma's promotional review committee structure.
---

# AcmePharma MLR Review Process

## Submission Requirements

All materials submitted to MLR must include:

1. **Submission Form (PromoMats Job Bag)**
   - Material title and job number (format: AP-[BRAND]-[YEAR]-[SEQ])
   - Material type classification (per plugin regulatory-compliance skill)
   - Target audience
   - Distribution channel(s)
   - Intended use date
   - Originating department and submitter name

2. **Annotated Draft**
   - Every efficacy claim annotated with superscript reference number
   - Every safety statement annotated with PI/SmPC section reference
   - Fair balance highlighted in yellow
   - ISI highlighted in blue

3. **Reference Package**
   - All cited references as PDFs in PromoMats
   - Approved Claims Library reference codes for each claim
   - PI/SmPC version number and date

## Reviewer Roles and SLA

| Role | Responsibility | SLA |
|------|---------------|-----|
| Medical Reviewer (MD/PharmD) | Clinical accuracy, off-label check, reference verification | 5 business days |
| Legal Reviewer | IP, comparative claims, testimonials, Sunshine Act | 5 business days |
| Regulatory Reviewer | FDA/EMA compliance, fair balance, ISI, classification | 5 business days |
| Brand Manager (submitter) | Incorporate feedback, resubmit | 3 business days |
| Final Approver (Sr. Director Medical) | Final sign-off after all reviewers approve | 2 business days |

## Total Timeline by Material Type

| Material Type | Standard Review | Expedited Review |
|--------------|----------------|-----------------|
| Detail aid (print) | 8-10 weeks | 5-6 weeks |
| Digital banner ad | 4-5 weeks | 2-3 weeks |
| Email (rep-triggered) | 4-5 weeks | 2-3 weeks |
| Congress booth panels | 8-10 weeks | 6-7 weeks |
| Social media post | 3-4 weeks | 1-2 weeks |
| Video (HCP-facing) | 10-12 weeks | 7-8 weeks |
| Patient brochure | 8-10 weeks | 5-6 weeks |
| Press release (product) | 6-8 weeks | 4-5 weeks |

## Expedited Review Criteria

Expedited review is available only for:
- Competitive response materials (competitor label change or new data)
- Congress materials with immovable deadlines
- Regulatory-required communications (Dear HCP letters, REMS updates)

Requires VP Medical Affairs approval to initiate expedited track.

## Common Rejection Reasons (AcmePharma-Specific)

1. Claim not in Approved Claims Library -- use only pre-approved claims
2. Reference older than 3 years without justification memo
3. Missing ISI version number in footer
4. Fair balance font size smaller than body copy
5. Comparative language without head-to-head data from AcmePharma trial
```

### Example C3: Company Formulary Strategy and Payer Landscape

Create `.claude/skills/acmepharma-market-access/SKILL.md`:

```markdown
---
name: acmepharma-market-access
description: >
  AcmePharma formulary strategy and payer landscape for ONCORIX.
  Use when developing payer-facing materials, discussing formulary
  positioning, planning market access campaigns, or creating
  reimbursement support content.
---

# AcmePharma ONCORIX Market Access

## Current Formulary Status (as of Q1 2026)

| Payer Segment | Coverage Status | Tier | PA Required | Lives Covered |
|--------------|----------------|------|-------------|---------------|
| Commercial (top 10 PBMs) | 8 of 10 covered | Specialty | Yes (7 of 8) | ~180M lives |
| Medicare Part B | Covered (buy-and-bill) | N/A | No | ~65M lives |
| Medicare Part D | 4 of 5 major plans | Specialty | Yes | ~48M lives |
| Medicaid | Mandatory coverage | N/A | Varies by state | ~90M lives |
| VA/DoD | National Formulary | Specialty | No | ~9M lives |

## Key Payer Objections and Responses

| Objection | Response Framework |
|-----------|-------------------|
| "Price is higher than competitor X" | Lead with total cost of care: fewer hospitalizations, shorter infusion time, less supportive care needed. Reference BIA showing budget-neutral within 12 months. |
| "No head-to-head data vs. standard of care" | Reference ONCORIX-301 trial design (active comparator arm), indirect treatment comparison published in [journal], and real-world evidence from [registry]. |
| "Limited long-term safety data" | Reference 3-year follow-up data from ONCORIX-301 extension, post-marketing safety database of 15,000+ patients, and FDA post-marketing commitment status. |

## ONCORIX Patient Support Program

- Co-pay assistance: $0 co-pay for commercially insured patients
  (income limit: 500% FPL)
- Free drug program: For uninsured patients meeting income criteria
- Nurse navigator: Dedicated support for treatment initiation,
  adherence monitoring, and side effect management
- Specialty pharmacy network: 3 contracted specialty pharmacies
  with 48-hour delivery guarantee
```

### Example C4: Company-Specific Congress Calendar

Create `.claude/skills/acmepharma-congress-calendar/SKILL.md`:

```markdown
---
name: acmepharma-congress-calendar
description: >
  AcmePharma 2026 congress calendar, booth standards, and event
  planning requirements. Use when planning congress activities,
  developing congress marketing plans, or coordinating AcmePharma's
  presence at medical conferences.
---

# AcmePharma 2026 Congress Calendar

## Priority Congresses (Tier 1 -- Full Presence)

| Congress | Dates | Location | Booth Size | Satellite Symposium | Budget |
|----------|-------|----------|-----------|---------------------|--------|
| ASCO Annual | May 29 - Jun 2 | Chicago, IL | 40x40 ft | Yes (Saturday evening) | $1.2M |
| ESMO Annual | Sep 12-16 | Barcelona, Spain | 12x8 m | Yes (Sunday lunch) | EUR 850K |
| ASH Annual | Dec 5-8 | San Diego, CA | 30x30 ft | No (poster only) | $600K |

## Priority Congresses (Tier 2 -- Targeted Presence)

| Congress | Dates | Presence Type | Budget |
|----------|-------|-------------|--------|
| AACR Annual | Apr 11-16 | Poster + KOL meetings only | $150K |
| ASCO GU | Jan 22-24 | Booth (20x20) + poster | $350K |
| SABCS | Dec 9-13 | Poster + KOL dinner | $200K |
| ESMO GI | Jun 25-28 | Poster only | $80K |

## AcmePharma Booth Standards

- All booth content must receive MLR approval minimum 8 weeks
  before congress
- Booth staff must complete Product Training Module (PTM-2026)
  and Congress Compliance Training (CCT-2026) before attending
- Maximum 3 interactive digital stations per booth
- Patient case simulations require Medical Affairs sign-off
- All booth visitors scanned via lead capture system (consent required
  for EU congresses per GDPR)
- Competitive intelligence forms must be submitted within 24 hours
  of congress close
```

Add to `CLAUDE.md`:

```markdown
## AcmePharma Congress Planning

When using /congress-plan for AcmePharma events, always reference the
acmepharma-congress-calendar skill for dates, budgets, and booth standards.
All congress plans must include the MLR timeline requirement (8 weeks minimum
for booth content approval).
```

---

## Which Approach When: Decision Matrix for Pharma Marketing Teams

| Customization Scenario | Recommended Approach | Rationale |
|----------------------|---------------------|-----------|
| Adding one therapeutic area's clinical landscape | A (Direct Modification) | Contained addition to 2-3 skill files |
| Adding regulatory rules for one new market | A (Direct Modification) | Single new reference file plus a pointer |
| Creating a TA-focused variant (oncology, cardiology, CNS) | B (Fork the Plugin) | Substantial restructuring; skills reordered for TA defaults |
| Creating a region-specific variant (EU, Japan, LATAM) | B (Fork the Plugin) | Regulatory framework restructuring; different defaults |
| Adding your company's brand voice and product guidelines | C (CLAUDE.md) | Company-specific, changes frequently, survives updates |
| Adding your internal MLR workflow and SLA timelines | C (CLAUDE.md) | Operational process, not domain knowledge |
| Adding your approved claims library | C (CLAUDE.md) | Proprietary content, updated frequently |
| Adding your formulary strategy and payer landscape | C (CLAUDE.md) | Competitive data, updated quarterly |
| Adding your congress calendar and booth standards | C (CLAUDE.md) | Updated annually, company-specific |
| Combining multiple of the above for a full company deployment | B (Fork) + C (CLAUDE.md) | Fork for structural changes, CLAUDE.md for operational details |

**The most common pattern for enterprise pharma deployments:**

1. **Fork the plugin** (Approach B) to add your therapeutic area depth and regional regulatory framework
2. **Add company-specific knowledge via CLAUDE.md** (Approach C) for brand guidelines, MLR processes, claims libraries, congress calendars, and payer strategies
3. **Keep direct modifications** (Approach A) for quick experiments and testing before committing to a fork

---

## Detailed Use Case 1: Adding a Therapeutic Area (Cardiology)

This walkthrough shows how to add cardiology specialization to the `marketing-life-sciences` plugin using Approach A (direct modification). A similar pattern applies for any therapeutic area -- neurology, immunology, endocrinology, rare diseases, etc.

### Files to Modify

| File | What to Add |
|------|-------------|
| `skills/campaign-planning/SKILL.md` | Cardiology campaign types, HCP segments, channel strategy |
| `skills/competitive-analysis/SKILL.md` | Cardiovascular competitive landscape dimensions, trial endpoints |
| `skills/performance-analytics/SKILL.md` | Cardiology-specific KPIs (lipid lowering rates, CV event reduction) |
| `skills/content-creation/SKILL.md` | Cardiology content types (CVOT summary, lipid management guide) |
| `skills/medical-affairs-liaison/references/congress-planning-guide.md` | ACC, AHA, ESC congress details |

### Step-by-Step Implementation

**1. Add cardiology campaign types to `skills/campaign-planning/SKILL.md`:**

```markdown
<!-- Cardiology Specialization -->

## Cardiology Campaign Considerations

### Cardiology-Specific Campaign Types

**CV Risk Reduction Awareness (Unbranded)**
Focus on cardiovascular risk factors (LDL-C, hypertension, residual
inflammatory risk). Drive risk assessment and testing. CTA: "Know your
numbers" or "Talk to your cardiologist about your residual CV risk."

**Guideline-Aligned Treatment Campaigns**
Position product within ACC/AHA or ESC treatment guidelines. Reference
specific guideline recommendations with Class of Recommendation and
Level of Evidence designations.

**Outcomes Data Dissemination**
For products with cardiovascular outcomes trial (CVOT) data, campaigns
center on MACE reduction, hospitalization reduction, or mortality benefit.
All claims must precisely match the CVOT primary endpoint result.

### Cardiology HCP Segmentation

| Segment | Description | Primary Channel |
|---------|-------------|----------------|
| Interventional cardiologists | Cath lab procedures, stents, structural heart | Congress engagement, peer-to-peer |
| Heart failure specialists | Advanced HF, LVAD, transplant | MSL engagement, advisory boards |
| Electrophysiologists | Arrhythmia management, devices | Specialized congress (HRS) |
| General cardiologists | Broad CV management, risk reduction | Rep visits, digital, medical portals |
| Primary care physicians | CV risk screening, lipid management, hypertension | High-volume digital campaigns, P2P education |
| Cardiac surgeons | Surgical intervention decisions | MSL-only, congress engagement |

### Cardiology KPIs

| KPI | Definition | Cardiology Nuance |
|-----|-----------|-------------------|
| LDL-C goal attainment rate | % of patients reaching target LDL-C | Key outcome for lipid-lowering therapies |
| Guideline-recommended therapy rate | % of eligible patients on guideline therapy | Measures treatment gap; opportunity for market growth |
| MACE rate reduction | Major adverse cardiovascular events prevented | Primary outcome in CVOTs; drives formulary positioning |
| Specialist referral rate | % of high-risk patients referred to cardiology | Important for therapies requiring specialist initiation |
```

**2. Add cardiology competitive dimensions to `skills/competitive-analysis/SKILL.md`:**

```markdown
<!-- Cardiology Competitive Analysis -->

## Cardiovascular Competitive Intelligence

### CVOT Comparison Framework
| Parameter | Your Product | Competitor A | Competitor B |
|-----------|-------------|--------------|--------------|
| Trial name | | | |
| N enrolled | | | |
| Primary endpoint (MACE) | | | |
| HR (95% CI) | | | |
| NNT (over trial duration) | | | |
| CV death component | | | |
| HF hospitalization | | | |
| All-cause mortality | | | |
| Key safety signals | | | |

### Guideline Positioning Tracker
Monitor ACC/AHA, ESC, and NLA guideline updates for:
- Class of recommendation changes
- New treatment algorithm placements
- Head-to-head data incorporation
- Cost-effectiveness evidence requirements
```

**3. Update the congress planning guide** to include detailed ACC, AHA, and ESC congress profiles with typical booth sizes, symposium formats, and planning timelines.

**Total time to implement:** 2-4 hours for a complete cardiology addition across all relevant files.

---

## Detailed Use Case 2: Adding Company-Specific Processes (AcmePharma)

This walkthrough shows a full Approach C implementation for a fictional pharmaceutical company "AcmePharma" with its flagship oncology product ONCORIX (vemutatinib).

### Files to Create

All files live in the project's `.claude/` directory, not inside the plugin.

```
your-project/
├── .claude/
│   └── skills/
│       ├── acmepharma-brand/
│       │   └── SKILL.md              # Brand voice, product naming, prohibited terms
│       ├── acmepharma-mlr-process/
│       │   └── SKILL.md              # Internal MLR workflow, reviewer roles, SLAs
│       ├── acmepharma-claims-library/
│       │   └── SKILL.md              # Approved claims with reference codes
│       ├── acmepharma-market-access/
│       │   └── SKILL.md              # Formulary status, payer objections, PSP details
│       └── acmepharma-congress-calendar/
│           └── SKILL.md              # 2026 congress calendar, booth standards
└── CLAUDE.md                          # Routing rules connecting all skills
```

### The CLAUDE.md Routing File

```markdown
# AcmePharma Oncology Marketing Project

## Plugin Integration Rules

This project uses the marketing-life-sciences plugin with the following
AcmePharma-specific skills layered on top.

### Brand Standards
When using /draft-content, /brand-review, or /email-sequence for any
AcmePharma product, always apply the acmepharma-brand skill. AcmePharma
rules override generic pharma brand voice guidance on conflicts.

### MLR Review
When using /mlr-review, always incorporate AcmePharma's internal MLR
process from the acmepharma-mlr-process skill. Include:
- The AcmePharma job number format (AP-[BRAND]-[YEAR]-[SEQ])
- Review timeline estimates based on AcmePharma SLAs
- The Approved Claims Library reference for every claim

### Claims Substantiation
All efficacy and safety claims for ONCORIX must reference the
acmepharma-claims-library skill. Only claims with an active ACL
reference code may be used. Flag any claim without an ACL code
as Critical severity in MLR review.

### Market Access
When using /campaign-plan or /competitive-brief for ONCORIX,
reference the acmepharma-market-access skill for current formulary
status, payer objection frameworks, and PSP details.

### Congress Planning
When using /congress-plan, reference the acmepharma-congress-calendar
skill for AcmePharma-specific dates, budgets, booth standards, and
compliance requirements.

### Content Classification
All ONCORIX content must follow AcmePharma's classification system:
- Type A: Branded promotional (Full MLR, 8-10 weeks)
- Type B: Unbranded disease awareness (Medical + Legal, 5-6 weeks)
- Type C: Scientific exchange (Medical review only, 3-4 weeks)
- Type D: Internal training (Full MLR, same as external, 6-8 weeks)
```

### The Approved Claims Library Skill

```markdown
---
name: acmepharma-claims-library
description: >
  AcmePharma Approved Claims Library for ONCORIX (vemutatinib).
  Use when drafting promotional content, annotating claims for
  MLR review, verifying claim substantiation, or checking whether
  a specific efficacy or safety statement has been pre-approved.
---

# ONCORIX Approved Claims Library

## How to Use This Library

Every efficacy, safety, or comparative claim in promotional materials
must reference an Approved Claim Code (ACC). Format: ONX-[CATEGORY]-[SEQ]

When drafting content, annotate each claim as: "Claim text"^[ACC: ONX-EFF-001]

## Efficacy Claims

| ACC Code | Approved Claim | Reference | Expiry |
|----------|---------------|-----------|--------|
| ONX-EFF-001 | "ONCORIX demonstrated a statistically significant improvement in progression-free survival vs. standard of care (median PFS 14.2 months vs. 9.4 months; HR 0.62; 95% CI: 0.49-0.78; P<0.001)." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |
| ONX-EFF-002 | "42% of patients treated with ONCORIX achieved an objective response (ORR 42%; 95% CI: 35-49%)." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |
| ONX-EFF-003 | "Median duration of response was 11.3 months (95% CI: 8.7-14.1)." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |
| ONX-EFF-004 | "ONCORIX demonstrated a trend toward improved overall survival (HR 0.78; 95% CI: 0.59-1.03; P=0.08). OS data were immature at the time of analysis." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |

## Safety Claims

| ACC Code | Approved Claim | Reference | Expiry |
|----------|---------------|-----------|--------|
| ONX-SAF-001 | "The most common adverse reactions (>=20%) were fatigue (45%), nausea (38%), rash (32%), diarrhea (28%), and decreased appetite (22%)." | ONCORIX PI Section 6.1 | Tied to PI version |
| ONX-SAF-002 | "Grade 3-4 treatment-related adverse events occurred in 34% of patients treated with ONCORIX vs. 28% with standard of care." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |
| ONX-SAF-003 | "Treatment discontinuation due to adverse events occurred in 12% of patients in the ONCORIX arm." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |

## Comparative Claims

| ACC Code | Approved Claim | Reference | Expiry |
|----------|---------------|-----------|--------|
| ONX-CMP-001 | "ONCORIX demonstrated superior PFS compared to standard of care in the ONCORIX-301 trial." | ONCORIX-301 (Suzuki et al., NEJM 2025) | Dec 2026 |

**Note:** Cross-trial comparisons are NOT approved. Any statement comparing
ONCORIX to a competitor's product from a different trial is prohibited.

## Claims Under Review (Do Not Use)

| Pending Code | Claim | Status | Expected Approval |
|-------------|-------|--------|------------------|
| ONX-EFF-P01 | QoL improvement claim based on ONCORIX-301 PRO data | Under Medical Review | Q2 2026 |
| ONX-EFF-P02 | Subgroup efficacy claim for patients with high PD-L1 | Under Regulatory Review | Q2 2026 |
```

**Result:** A complete company-specific layer that turns the generic life sciences plugin into an AcmePharma-branded marketing engine. Claude will automatically apply AcmePharma's brand voice when drafting ONCORIX content, reference the approved claims library during MLR review, cite correct formulary status in campaign plans, and use the company's congress calendar for event planning -- all without modifying a single file in the plugin itself.

---

# Part VI: File Reference

## Complete Annotated File Tree

The `marketing-life-sciences` plugin contains 26 files. Each file is annotated with its origin (unchanged from base, modified, or new), size, and purpose.

```
marketing-life-sciences/
│
├── .claude-plugin/
│   └── plugin.json                         NEW        398 B     Plugin identity and metadata
│
├── commands/
│   ├── brand-review.md                     UNCHANGED  4,850 B   Review content against brand voice
│   ├── campaign-plan.md                    UNCHANGED  4,461 B   Generate campaign brief
│   ├── competitive-brief.md                UNCHANGED  4,546 B   Research competitors
│   ├── congress-plan.md                    NEW        6,351 B   Plan congress/conference marketing
│   ├── draft-content.md                    UNCHANGED  4,364 B   Draft marketing content
│   ├── email-sequence.md                   UNCHANGED  10,354 B  Design email sequences
│   ├── kol-strategy.md                     NEW        7,329 B   Develop KOL engagement strategy
│   ├── mlr-review.md                       NEW        6,011 B   Simulate MLR review
│   ├── performance-report.md               UNCHANGED  5,151 B   Build performance reports
│   └── seo-audit.md                        UNCHANGED  9,305 B   Run SEO audits
│
├── skills/
│   ├── brand-voice/
│   │   └── SKILL.md                        MODIFIED   14,881 B  Brand voice + pharma fair balance, ISI, claim rules
│   ├── campaign-planning/
│   │   └── SKILL.md                        MODIFIED   18,862 B  Campaign planning + LS campaign types, HCP segmentation
│   ├── competitive-analysis/
│   │   └── SKILL.md                        MODIFIED   15,294 B  Competitive analysis + formulary, label, pipeline comparison
│   ├── content-creation/
│   │   └── SKILL.md                        MODIFIED   15,089 B  Content creation + detail aids, MOA, formulary dossier
│   ├── medical-affairs-liaison/
│   │   ├── SKILL.md                        NEW        10,156 B  MSL engagement, KOL mapping, advisory boards, congress
│   │   └── references/
│   │       ├── congress-planning-guide.md   NEW        8,083 B   Congress calendar, booth strategy, satellite symposia
│   │       └── kol-tier-framework.md        NEW        5,997 B   7-dimension KOL scoring methodology
│   ├── performance-analytics/
│   │   └── SKILL.md                        MODIFIED   22,699 B  Performance analytics + NRx/TRx, SOV, congress KPIs
│   └── regulatory-compliance/
│       ├── SKILL.md                        NEW        9,044 B   MLR simulation, fair balance, off-label rules
│       └── references/
│           ├── ema-requirements.md          NEW        7,621 B   EU Directive 2001/83/EC, EFPIA Code, country rules
│           └── fda-promotional-rules.md     NEW        6,639 B   OPDP rules, CCN rule, digital guidance
│
├── .mcp.json                               MODIFIED   1,296 B   13 MCP servers (9 base + 4 new)
├── CONNECTORS.md                           MODIFIED   2,240 B   16 connector categories (7 base + 9 new)
├── LICENSE                                 UNCHANGED  11,358 B  License information
└── README.md                               MODIFIED   8,593 B   Plugin documentation with LS overview
```

### File Count Summary

| Category | Unchanged | Modified | New | Total |
|----------|-----------|----------|-----|-------|
| Plugin metadata | 0 | 0 | 1 | 1 |
| Commands | 7 | 0 | 3 | 10 |
| Skills (SKILL.md) | 0 | 5 | 2 | 7 |
| Reference documents | 0 | 0 | 4 | 4 |
| Configuration (.mcp.json) | 0 | 1 | 0 | 1 |
| Documentation (CONNECTORS, README) | 0 | 2 | 0 | 2 |
| License | 1 | 0 | 0 | 1 |
| **Total** | **8** | **8** | **10** | **26** |

### Cross-Reference Map: Commands to Skills

This table shows which skills each command draws upon, and which reference documents may be loaded on demand during execution.

| Command | Primary Skills | Reference Documents Loaded On Demand | Life Sciences MCP Servers Used |
|---------|---------------|--------------------------------------|-------------------------------|
| `/mlr-review` | `regulatory-compliance`, `brand-voice`, `content-creation` | `fda-promotional-rules.md`, `ema-requirements.md` | OpenFDA (label verification) |
| `/congress-plan` | `medical-affairs-liaison`, `campaign-planning`, `competitive-analysis` | `congress-planning-guide.md`, `kol-tier-framework.md` | ClinicalTrials.gov (PI identification) |
| `/kol-strategy` | `medical-affairs-liaison`, `competitive-analysis` | `kol-tier-framework.md`, `congress-planning-guide.md` | ClinicalTrials.gov (PI search), PubMed (publication analysis) |
| `/draft-content` | `content-creation`, `brand-voice`, `regulatory-compliance` | `fda-promotional-rules.md` (if pharma content) | PubMed (reference verification) |
| `/campaign-plan` | `campaign-planning`, `performance-analytics` | None typically | None typically |
| `/brand-review` | `brand-voice`, `regulatory-compliance` | `fda-promotional-rules.md`, `ema-requirements.md` | None typically |
| `/competitive-brief` | `competitive-analysis`, `performance-analytics` | None typically | ClinicalTrials.gov (pipeline search), OpenFDA (label comparison) |
| `/performance-report` | `performance-analytics` | None typically | Veeva (HCP engagement data) |
| `/email-sequence` | `content-creation`, `campaign-planning`, `performance-analytics`, `brand-voice` | `fda-promotional-rules.md` (if pharma email) | None typically |
| `/seo-audit` | `content-creation`, `competitive-analysis` | None typically | None typically |

### Cross-Reference Map: Skills to Reference Documents

| Skill | Reference Documents | Purpose of References |
|-------|-------------------|----------------------|
| `regulatory-compliance` | `fda-promotional-rules.md`, `ema-requirements.md` | Detailed regulatory framework loaded when Claude needs specific rule citations |
| `medical-affairs-liaison` | `kol-tier-framework.md`, `congress-planning-guide.md` | KOL scoring methodology and congress planning checklists loaded for detailed planning |
| `brand-voice` | None (self-contained) | Pharma brand voice rules are in the SKILL.md body |
| `campaign-planning` | None (self-contained) | LS campaign types and HCP segmentation are in the SKILL.md body |
| `competitive-analysis` | None (self-contained) | Formulary and pipeline frameworks are in the SKILL.md body |
| `content-creation` | None (self-contained) | LS content types and MLR requirements are in the SKILL.md body |
| `performance-analytics` | None (self-contained) | Pharma KPIs and reporting templates are in the SKILL.md body |

### MCP Server Reference

The plugin configures 13 MCP servers -- 9 inherited from the base marketing plugin and 4 new life-sciences-specific servers.

**Inherited Servers (9 -- identical to base marketing plugin):**

| Server Name | Service | Type | Purpose in Life Sciences Context |
|-------------|---------|------|----------------------------------|
| `slack` | Slack | HTTP | Share MLR review summaries, congress briefings, competitive updates with team channels |
| `canva` | Canva | HTTP | Access and edit design assets for detail aids, booth graphics, patient materials |
| `figma` | Figma | HTTP | Reference brand asset specifications, booth layout designs |
| `hubspot` | HubSpot | HTTP | HCP email campaign data, marketing automation for disease awareness campaigns |
| `amplitude` | Amplitude | HTTP | Digital engagement analytics, HCP portal behavior tracking |
| `notion` | Notion | HTTP | Brand guidelines, approved claims documents, congress planning notes |
| `ahrefs` | Ahrefs | HTTP | SEO research for disease education content, medical portal competitor analysis |
| `similarweb` | Similarweb | HTTP | Competitive web traffic analysis for pharma brand websites |
| `klaviyo` | Klaviyo | HTTP | HCP email sequence management, patient newsletter campaigns |

**New Life Sciences Servers (4):**

| Server Name | Service | Type | Auth Required | Purpose |
|-------------|---------|------|---------------|---------|
| `pubmed` | PubMed (NCBI) | stdio | NCBI API Key (`NCBI_API_KEY` env var) | Search biomedical literature for reference verification, KOL publication analysis, competitive scientific intelligence |
| `clinicaltrials` | ClinicalTrials.gov | HTTP | None (public API) | Search clinical trial registrations for pipeline intelligence, principal investigator identification, trial comparison |
| `openfda` | OpenFDA | HTTP | None (public API) | Access drug labeling data, adverse event reports, regulatory action history for label comparison |
| `veeva` | Veeva CRM | HTTP | Veeva CRM license | HCP engagement tracking, approved email management, content management integration |

**Note on PubMed:** This is the only `stdio` server in the plugin. Unlike HTTP servers that connect to cloud-hosted endpoints, the PubMed server runs a local Node.js process. It references a server script at `${CLAUDE_PLUGIN_ROOT}/servers/pubmed-server.js`. This script file is referenced in the configuration but is not included in the plugin distribution -- it must be installed separately per the README instructions.

### Detailed File Descriptions

**`.claude-plugin/plugin.json`** -- The plugin identity file. Contains the plugin name (`marketing-life-sciences`), version (`1.0.0-ls`), description, and author. The `-ls` version suffix distinguishes this fork from the base marketing plugin. This file is new (not modified from base) because the plugin has a different name and identity.

**`.mcp.json`** -- MCP server configuration. A JSON file defining all 13 server connections. Modified from the base to add the 4 life sciences servers (PubMed, ClinicalTrials.gov, OpenFDA, Veeva). The 9 base servers are preserved with identical configuration.

**`CONNECTORS.md`** -- Documents 16 placeholder categories (7 base + 9 new). The 9 new life sciences categories cover biomedical literature, clinical trials data, drug safety and labeling, life sciences CRM, MLR review platforms, prescribing data, formulary data, medical education portals, and competitive intelligence platforms. Of these 9, only 4 have pre-configured servers in `.mcp.json`; the remaining 5 are documented as ecosystem categories with alternative tool suggestions.

**`README.md`** -- Plugin overview and installation instructions. Modified from the base to describe life sciences capabilities, list the 4 new MCP servers and their setup requirements (particularly the NCBI API key for PubMed and Veeva license requirement), and provide example use cases for pharma marketing teams.

**Commands (unchanged from base):** The 7 inherited commands (`brand-review.md`, `campaign-plan.md`, `competitive-brief.md`, `draft-content.md`, `email-sequence.md`, `performance-report.md`, `seo-audit.md`) are byte-for-byte identical to the base marketing plugin. Life sciences specialization for these commands comes entirely from the skills layer -- when `/draft-content` runs, it automatically picks up pharma content types from the modified `content-creation` skill. This architectural decision keeps commands generic and pushes domain knowledge into skills.

**Commands (new):** The 3 new commands (`mlr-review.md`, `congress-plan.md`, `kol-strategy.md`) have no base plugin equivalent. They represent workflows unique to life sciences marketing: regulatory compliance review, medical congress planning, and KOL engagement strategy.

**Skills (modified):** Each of the 5 modified skills (`brand-voice`, `campaign-planning`, `competitive-analysis`, `content-creation`, `performance-analytics`) preserves the complete base skill content verbatim. Life sciences additions appear after a `<!-- Life Sciences Addition -->` HTML comment marker. The frontmatter `description` field in each is expanded with additional trigger phrases to ensure activation on pharma-specific queries. This pattern makes upstream merges straightforward: everything above the comment is base content, everything below is the LS addition.

**Skills (new):** The 2 new skills (`regulatory-compliance`, `medical-affairs-liaison`) have no base plugin equivalent. Each follows the progressive disclosure pattern: a concise SKILL.md body with frameworks and checklists, plus detailed reference documents in `references/` subdirectories that load only on demand.

**Reference documents:** All 4 reference files are new additions. They contain deep regulatory and procedural knowledge that would be too large for the SKILL.md body. The `fda-promotional-rules.md` (6,639 B) covers OPDP rules, enforcement actions, and digital guidance. The `ema-requirements.md` (7,621 B) covers EU Directive 2001/83/EC, 5 country variations, and the EFPIA Code. The `kol-tier-framework.md` (5,997 B) provides a 7-dimension scoring methodology for KOL tiering. The `congress-planning-guide.md` (8,083 B) contains a major congress calendar across 7 therapeutic areas, a multi-phase planning timeline, and booth/symposium strategy guides.

### Size and Complexity Indicators

| File | Lines | Bytes | Complexity |
|------|-------|-------|------------|
| `performance-analytics/SKILL.md` | 361 | 22,699 | High -- largest skill; 5 KPI category tables, 2 reporting templates, prescriber tracking |
| `campaign-planning/SKILL.md` | 359 | 18,862 | High -- 6 LS campaign types, 3 segmentation frameworks, regulatory timeline, channel guide |
| `competitive-analysis/SKILL.md` | 346 | 15,294 | High -- 5 new analysis sections (formulary, trials, labels, pipeline, battlecards) |
| `content-creation/SKILL.md` | 279 | 15,089 | Medium-High -- 5 LS content types, MLR reference annotation, PI integration |
| `brand-voice/SKILL.md` | 275 | 14,881 | Medium-High -- pharma voice rules, audience tone table, terminology, prohibited language |
| `email-sequence.md` (command) | 219 | 10,354 | High -- most complex command, 8 sequence types, branching logic |
| `medical-affairs-liaison/SKILL.md` | 169 | 10,156 | Medium -- MSL engagement, KOL mapping, advisory boards, congress strategy |
| `seo-audit.md` (command) | 189 | 9,305 | Medium-High -- 5 audit types, multi-step process |
| `regulatory-compliance/SKILL.md` | 162 | 9,044 | Medium -- classification matrix, 3 review checklists, fair balance scorer |
| `congress-planning-guide.md` (reference) | 186 | 8,083 | Medium -- congress calendar, planning timeline, booth strategy |
| `ema-requirements.md` (reference) | 142 | 7,621 | Medium -- EU framework, 5 country variations, EFPIA Code |
| `kol-strategy.md` (command) | 186 | 7,329 | Medium -- 11-section output, tiering framework |
| `fda-promotional-rules.md` (reference) | 143 | 6,639 | Medium -- OPDP rules, enforcement actions, digital guidance |
| `congress-plan.md` (command) | 156 | 6,351 | Medium -- 11-section output, congress planning workflow |
| `kol-tier-framework.md` (reference) | 144 | 5,997 | Medium -- 7-dimension scoring, tier thresholds, engagement tracker |
| `mlr-review.md` (command) | 150 | 6,011 | Medium -- 5-step review process, fair balance scoring |

---

# Part VII: Troubleshooting & FAQ

## Life-Sciences-Specific Troubleshooting

### Issue: `/mlr-review` Producing Generic (Non-Pharma) Output

**Symptoms:**
- Running `/mlr-review` returns a generic content review instead of a pharma-specific MLR simulation
- No fair balance scoring, no reference verification, no material classification
- Output looks like a standard `/brand-review` result

**Causes and Fixes:**

1. **Regulatory-compliance skill not triggering.**
   - Check that `skills/regulatory-compliance/SKILL.md` exists and its frontmatter `description` field contains pharma-specific trigger phrases.
   - Verify the frontmatter `name` field reads `regulatory-compliance` and matches the directory name exactly.
   - Try rephrasing your request to include explicit trigger language: "Simulate an MLR review of this promotional material for FDA compliance" rather than just "Review this content."

2. **Content not identified as pharmaceutical.**
   - The command asks you to classify the content type. If you skip this step or provide ambiguous input, Claude may not activate pharma-specific review logic.
   - Fix: When prompted, explicitly classify as "branded promotional," "unbranded disease awareness," or another pharma-specific type.

3. **Product context missing.**
   - Without product context (brand name, INN, approved indication), Claude cannot verify claims against labeling or check off-label implications.
   - Fix: Provide product context when prompted: product name, approved indications, key safety information, and whether the product carries a boxed warning.

4. **Reference documents not loading.**
   - If `references/fda-promotional-rules.md` or `references/ema-requirements.md` are missing or renamed, Claude lacks detailed regulatory frameworks.
   - Fix: Verify both files exist in `skills/regulatory-compliance/references/` with exact filenames.

### Issue: Regulatory Compliance Skill Not Triggering

**Symptoms:**
- Discussing FDA compliance, fair balance, or MLR review but Claude responds with general marketing knowledge
- Pharma-specific terms (ISI, PI, SmPC, OPDP) not recognized in context

**Causes and Fixes:**

1. **Skill description too narrow or missing trigger phrases.**
   - Open `skills/regulatory-compliance/SKILL.md` and check the `description` field.
   - It should include phrases like: "reviewing promotional content for FDA or EMA compliance," "preparing materials for MLR review," "checking fair balance requirements," "simulating medical-legal-regulatory review."
   - If these phrases are missing, add them.

2. **Conversation context does not clearly indicate pharma.**
   - Claude uses conversation context to decide which skills to activate. If your discussion has been about general marketing and you suddenly ask about fair balance, the skill may not trigger immediately.
   - Fix: Be explicit. Say "I'm working on pharmaceutical promotional content and need to check FDA fair balance compliance" rather than "Check the balance of this content."

3. **Plugin not loaded.**
   - Confirm the `marketing-life-sciences` plugin is installed and active. Ask Claude: "What plugins are installed?" or "Do you have the regulatory-compliance skill available?"

### Issue: New MCP Servers (PubMed, ClinicalTrials.gov, OpenFDA) Not Connecting

**Symptoms:**
- `/kol-strategy` cannot search publications or find principal investigators
- `/competitive-brief` cannot pull clinical trial data
- `/mlr-review` cannot verify drug labeling against OpenFDA

**Causes and Fixes:**

1. **PubMed server requires NCBI API key.**
   - PubMed is the only `stdio` (local process) server in the plugin. It requires the `NCBI_API_KEY` environment variable to be set.
   - Fix: Obtain a free API key from [NCBI](https://www.ncbi.nlm.nih.gov/account/) and set it: `export NCBI_API_KEY=your_key_here`
   - Note: The PubMed server also requires the server script at `${CLAUDE_PLUGIN_ROOT}/servers/pubmed-server.js`. If this script is not present, the server will not start. Check the plugin's README for installation instructions for the PubMed server component.

2. **ClinicalTrials.gov and OpenFDA are public APIs -- no authentication needed.**
   - If these connections fail, the issue is likely network-related (firewall, proxy, or API downtime).
   - Fix: Test the APIs directly in a browser: `https://clinicaltrials.gov/api/v2` and `https://api.fda.gov`. If these load, the issue is with `.mcp.json` configuration.
   - Verify the URLs in `.mcp.json` match exactly: `"url": "https://clinicaltrials.gov/api/v2"` and `"url": "https://api.fda.gov"`.

3. **Veeva requires CRM license.**
   - The Veeva MCP server (`https://mcp.veeva.com/mcp`) requires a valid Veeva CRM license and authentication.
   - Fix: Coordinate with your IT team to obtain Veeva MCP access. Not all Veeva license tiers include MCP connectivity.

4. **General MCP debugging.**
   - Verify `.mcp.json` is valid JSON (no trailing commas, no syntax errors).
   - Ask Claude: "What MCP servers are connected?" to see which connections are active.
   - Restart your Claude session after making changes to `.mcp.json`.

### Issue: Fair Balance Checker Giving False Positives or Negatives

**Symptoms:**
- Content that clearly has adequate fair balance is flagged as "inadequate"
- Content with obvious fair balance issues receives a passing score

**Causes and Fixes:**

1. **False positives (flagging adequate content).**
   - The fair balance checker uses a 5-dimension scoring framework (Prominence, Completeness, Readability, Placement, Language). If any single dimension scores below 3, it triggers a warning even if overall balance is acceptable.
   - Fix: Review each dimension's score individually. If one dimension is scored low due to format limitations (e.g., social media has inherent placement constraints), provide that context: "This is a social media post -- evaluate fair balance using the social media format standards from the regulatory-compliance skill."

2. **False negatives (missing real issues).**
   - The checker relies on the product context you provide. If you do not specify the product's safety profile, boxed warning status, or REMS requirements, the checker cannot evaluate ISI completeness.
   - Fix: Always provide complete product context when running `/mlr-review`, including: approved indication, boxed warning (yes/no), REMS (yes/no), key contraindications, and most common adverse reactions.

3. **Format-specific standards not applied.**
   - Fair balance requirements differ by format (print detail aid vs. digital banner vs. social media post). If the content format is not specified, Claude may apply default (print) standards.
   - Fix: Specify the exact content format when submitting for review.

### Issue: Congress Planning Not Using the Right Conference Data

**Symptoms:**
- `/congress-plan` suggests generic conference planning instead of specific congress details
- Wrong congress dates, locations, or therapeutic area alignment

**Causes and Fixes:**

1. **Congress name not recognized.**
   - If you enter a congress abbreviation Claude does not recognize, it falls back to generic planning.
   - Fix: Use full names or common abbreviations: "ASCO Annual Meeting 2026," "ESMO 2026," "ADA Scientific Sessions 2026," "ACC 2026."

2. **Congress planning guide not loading.**
   - The detailed congress data lives in `skills/medical-affairs-liaison/references/congress-planning-guide.md`. If this file is missing or renamed, Claude lacks the congress calendar.
   - Fix: Verify the file exists at the expected path.

3. **Outdated congress dates.**
   - The congress planning guide contains dates for specific years. If it has not been updated for the current year, dates will be incorrect.
   - Fix: Update the congress calendar in `congress-planning-guide.md` annually. Alternatively, Claude can search the web for current congress dates if you ask: "Look up the exact dates for ASCO 2026."

---

## General Plugin Troubleshooting

### Issue: Plugin Not Loading / Skills Not Activating

**Checklist:**

1. **Verify `.claude-plugin/plugin.json` exists and is valid JSON.** The file must be at `.claude-plugin/plugin.json` (note the dot prefix). Must contain at least a `name` field. Common error: trailing commas in JSON.

2. **Verify the plugin is installed.** Ask Claude: "What plugins are installed?" If `marketing-life-sciences` is not listed, reinstall.

3. **Check directory structure.** The `.claude-plugin/` folder must be at the plugin root, not nested inside another directory.

4. **Skills must have `SKILL.md` (all caps).** Files named `skill.md` or `Skill.md` will not be recognized. Verify: `skills/regulatory-compliance/SKILL.md`, not `skills/regulatory-compliance/skill.md`.

5. **YAML frontmatter format.** Both `---` delimiters must be present. `name` and `description` fields are required in skill frontmatter. Use spaces not tabs for indentation.

### Issue: MCP Server Authentication Failures

**Checklist:**

1. **HTTP servers (Slack, HubSpot, Veeva, etc.):** Disconnect and reconnect. Ensure you approved all requested OAuth permissions. Check that your account has the necessary access level (admin vs. viewer).

2. **stdio servers (PubMed):** Verify the environment variable is set (`echo $NCBI_API_KEY`). Check that `node` is installed and accessible. Verify the server script path resolves correctly.

3. **Public API servers (ClinicalTrials.gov, OpenFDA):** These need no authentication. If failing, check network connectivity, firewall rules, or proxy configuration.

### Issue: Command Not Found Errors

**Checklist:**

1. Command files must be in the `commands/` directory (not in subdirectories).
2. File extension must be `.md`.
3. Filename becomes the command name: `mlr-review.md` becomes `/mlr-review`.
4. Filenames must use kebab-case: `mlr-review.md`, not `MLRReview.md` or `mlr_review.md`.
5. No two plugins can define the same command name. If you have both `marketing` and `marketing-life-sciences` installed simultaneously, 7 commands will conflict. Use one or the other.

### Issue: Connector Placeholder Confusion

**Symptoms:** Claude mentions `~~biomedical literature` or `~~life sciences CRM` in output, which looks like a placeholder rather than a tool reference.

**Explanation:** Placeholder syntax (`~~category`) is intentional. It means the referenced tool category is documented in `CONNECTORS.md` but the specific tool either is not configured in `.mcp.json` or is not connected. Five of the nine life sciences connector categories have no pre-configured server: `~~MLR review`, `~~prescribing data`, `~~formulary data`, `~~medical education`, and `~~competitive intelligence`.

**Fix:** Either connect a tool for that category (add it to `.mcp.json`), or acknowledge that Claude will ask you to provide that data manually when needed. For example, if `~~prescribing data` has no configured server, Claude will ask you to paste NRx/TRx data instead of pulling it automatically.

---

## Frequently Asked Questions

**Q1: Can I use this plugin for medical devices (not just drugs)?**

**A:** Yes, with some adaptation. The regulatory-compliance skill covers both pharmaceutical and medical device promotional materials. However, the plugin's depth is stronger on pharmaceutical marketing (FDA OPDP rules, PI/SmPC references, prescribing data KPIs). For medical devices, you may want to add device-specific regulatory knowledge (510(k) vs. PMA pathway, CE marking, MDR 2017/745 in the EU, CDRH advertising rules) using Approach A or C. The core campaign planning, competitive analysis, and content creation skills apply equally to devices and drugs.

**Q2: Does this plugin replace our MLR review process?**

**A:** No. The `/mlr-review` command simulates an MLR review to help you prepare content before formal submission. It identifies likely compliance issues, checks fair balance, and flags unsubstantiated claims -- but it is a preparatory tool, not a substitute for review by qualified medical, legal, and regulatory professionals. Think of it as a quality check that reduces rejection rates and review cycles by catching common issues before your MLR team sees the material.

**Q3: How do I add support for our specific regulatory market?**

**A:** Create a new reference file in `skills/regulatory-compliance/references/` following the pattern of `fda-promotional-rules.md` and `ema-requirements.md`. Name it for the market (e.g., `jpma-requirements.md` for Japan, `anvisa-requirements.md` for Brazil). Include the governing framework, key content requirements, review process specifics, and enforcement mechanisms. Then add a pointer to the new file in `skills/regulatory-compliance/SKILL.md` under the Regulatory Framework References section. See the Approach A example earlier in this part for a full Japan JPMA walkthrough.

**Q4: Can I customize the HCP segmentation tiers?**

**A:** Yes. The HCP segmentation framework in the `campaign-planning` skill uses generic dimensions (specialty, prescribing behavior, influence tier, practice setting, digital engagement, access/formulary, patient volume). You can customize this by editing the skill directly (Approach A) to match your company's segmentation model, or by creating a company-specific segmentation skill via CLAUDE.md (Approach C). Most pharma companies have proprietary segmentation models that should be added via Approach C to protect competitive information.

**Q5: How does the plugin handle off-label content requests?**

**A:** The regulatory-compliance skill includes explicit off-label restriction compliance rules. If you ask Claude to create content that implies off-label use, the skill flags 7 specific red flags (unapproved populations, different dosing, trials in unapproved indications, testimonials for off-label use, comparisons across indications, broader population language, and links to off-label publications). Claude will not generate promotional content for off-label uses. For legitimate scientific exchange about unapproved uses (which is permissible under specific conditions), the skill distinguishes between permissible and non-permissible scientific communication.

**Q6: What happens if I do not connect PubMed or ClinicalTrials.gov?**

**A:** The plugin works without these connections. Commands that would use them (like `/kol-strategy` for publication analysis or `/competitive-brief` for pipeline search) will either use web search as a fallback or ask you to provide the data manually. The output quality is still high, but the depth of evidence-based features (KOL publication scoring, principal investigator identification, clinical trial landscape mapping) will be reduced. PubMed and ClinicalTrials.gov are free public APIs, so there is little reason not to connect them if your IT environment permits.

**Q7: Can I use this alongside the base marketing plugin?**

**A:** It is not recommended. The `marketing-life-sciences` plugin contains all 7 original commands with identical names. Installing both plugins simultaneously will create command name conflicts (both define `/draft-content`, `/campaign-plan`, etc.). Use one or the other. The life sciences plugin includes all base marketing capabilities, so there is no functionality loss from using it exclusively.

**Q8: How do I update when a new base marketing plugin version comes out?**

**A:** Because the life sciences plugin is a fork (Approach B) of the base marketing plugin, updates require a manual merge. The process:
1. Review the base plugin changelog to identify what changed.
2. For unchanged command files (7 of 10), simply copy the updated versions over.
3. For modified skill files (5 of 7), merge the upstream changes into the section above the `<!-- Life Sciences Addition -->` comment. The LS additions below that comment should remain untouched unless the base changes conflict.
4. For new LS-only files (commands, skills, references), no merge is needed.
5. Test all commands and skills after merging.

The `<!-- Life Sciences Addition -->` comment marker in modified skills makes this merge process straightforward.

**Q9: Can non-pharma biotech companies use this? (Lab equipment, diagnostics, reagents)**

**A:** The plugin is optimized for pharmaceutical and biotech marketing where regulatory compliance (FDA/EMA promotional rules), MLR review, and HCP engagement are central concerns. For diagnostics companies, the KOL strategy, congress planning, and HCP engagement skills are directly applicable. For lab equipment and reagent companies, the regulatory compliance features may be less relevant (these products are not typically subject to OPDP oversight), but the campaign planning, competitive analysis, and content creation skills with their life sciences adaptations (scientific audiences, congress marketing, medical portal channels) are still valuable. Consider using Approach A to remove or de-emphasize the pharmaceutical regulatory content if it is not relevant.

**Q10: How do I add our company's claim library?**

**A:** Use Approach C (CLAUDE.md with a complementary skill). Create a skill file at `.claude/skills/your-claims-library/SKILL.md` containing your approved claims, reference codes, substantiating references, and expiration dates. Add a routing rule in `CLAUDE.md` instructing Claude to reference this library when running `/mlr-review` or `/draft-content`. See the detailed AcmePharma claims library example in the Approach C section above. Update the claims library skill file whenever your MLR team approves new claims or retires old ones.

**Q11: Can the plugin generate content in languages other than English?**

**A:** The plugin's skills and commands are written in English, and all regulatory references are for English-language markets (US FDA, EU EMA). However, Claude can generate content in other languages when you specify: "Draft this detail aid in German" or "Create a disease awareness campaign in Japanese." The pharma-specific frameworks (fair balance, claim substantiation, ISI placement) apply regardless of language, but you should verify the output against local-language regulatory requirements, which the plugin may not cover in depth for non-English markets. For extensive non-English operations, consider creating a region-specific fork (see Approach B, marketing-life-sciences-eu example).

**Q12: How do I handle materials that need review in multiple markets simultaneously (global campaigns)?**

**A:** The `/mlr-review` command accepts a target market parameter. For global campaigns, run the review multiple times -- once for each target market. For example, run it with "US (FDA)" for the US version and "EU (EMA)" for the EU version. Each run will apply the relevant regulatory framework. For a streamlined approach, create a CLAUDE.md rule: "When reviewing global campaign materials, automatically evaluate against both FDA and EMA requirements and produce a combined findings table noting which issues are US-specific, EU-specific, or apply to both markets."

**Q13: What is the difference between the `/mlr-review` command and the `/brand-review` command for pharma content?**

**A:** Both review content, but they serve different purposes. `/brand-review` evaluates content against brand voice, style guidelines, and messaging consistency -- it is the same as the base marketing plugin and checks tone, terminology, and general legal/compliance flags. `/mlr-review` specifically simulates a pharmaceutical MLR review: it classifies the material type, runs medical/legal/regulatory checklists, scores fair balance across 5 dimensions, verifies references against approved labeling, and checks for off-label implications. For pharma content, use `/mlr-review` for regulatory compliance and `/brand-review` for brand voice consistency. In practice, many teams run both.

**Q14: Can I use this plugin for veterinary pharmaceutical marketing?**

**A:** The plugin is designed for human pharmaceutical marketing. Veterinary pharmaceutical marketing operates under different regulatory frameworks (FDA Center for Veterinary Medicine in the US, rather than CDER/OPDP). The campaign planning, content creation, competitive analysis, and KOL strategy skills are conceptually transferable, but the regulatory compliance skill and MLR review command would need significant modification. Consider forking the plugin (Approach B) and replacing the regulatory framework references with veterinary-specific regulations.

**Q15: How do I track which version of the plugin my team is using?**

**A:** The version is recorded in `.claude-plugin/plugin.json`. The current version is `1.0.0-ls`. When you make modifications (especially via Approach A or B), update the version field to reflect your changes -- for example, `1.0.0-ls-acmepharma-v2`. This makes it clear which variant is installed on each team member's system.

**Q16: Our company has a modular content strategy. Does the plugin support that?**

**A:** The plugin's content-creation skill includes MLR review requirements that reference annotation and claim substantiation -- both foundational to modular content. However, the plugin does not manage a modular content repository directly (that is typically handled by Veeva Vault PromoMats or similar platforms). To integrate your modular content strategy, use Approach C to create a skill that documents your content module taxonomy, approved module combinations, and module-level metadata requirements. Connect Veeva via the pre-configured MCP server to give Claude access to your approved modules when drafting new content.

**Q17: How does the plugin handle combination therapy content where two products from different companies are used together?**

**A:** The content-creation skill's life sciences addition covers combination therapy content types. When creating content for a combination regimen, the plugin's regulatory compliance rules apply: fair balance must cover the safety profile of the entire combination (not just your product), the indication statement must match the combination approval, and references must come from the combination trial data. For co-promotion scenarios (where both companies are involved in marketing), create a CLAUDE.md rule specifying which company's brand guidelines, claims library, and MLR process apply.

**Q18: Where can I find the most current regulatory guidance referenced by the plugin?**

**A:** The reference documents (`fda-promotional-rules.md`, `ema-requirements.md`) are static files that reflect regulatory guidance as of the plugin's release date. Regulatory requirements change. The FDA issues new guidance documents regularly, and the EMA updates its framework through new directives and implementing regulations. Keep these reference files current by checking: FDA OPDP website (fda.gov/about-fda/cder/opdp) for new guidance documents, EMA website (ema.europa.eu) for updated advertising requirements, and EFPIA website for Code of Practice updates. Update the reference files when significant regulatory changes occur.
# Part VIII: Life Sciences Gap Analysis

The base marketing plugin (v1.0.0) is an excellent general-purpose marketing toolkit. It handles content creation, campaign planning, brand voice management, competitive analysis, and performance analytics with genuine sophistication. For a SaaS company, a consumer brand, or a retail marketing team, it covers the territory well.

But pharmaceutical, biotech, and medtech marketing is not general-purpose marketing. It operates under a regulatory regime that has no parallel in other industries. A promotional email that would be perfectly fine for a software product could, if sent by a pharma company about a prescription drug, trigger an FDA warning letter, a multimillion-dollar fine, or a consent decree that places a company's entire promotional apparatus under government supervision for years.

The life sciences marketing plugin (v1.0.0-ls) exists because the distance between general marketing and life sciences marketing is not a matter of degree -- it is a matter of kind. This chapter documents that distance in detail, organized across seven gap categories. For each gap, we describe what the base plugin lacked, why the absence matters in real-world pharma operations, and what the life sciences plugin now provides.

## 1. Regulatory Compliance Gap

**What was missing.** The base marketing plugin has no awareness of pharmaceutical advertising regulations. It does not know that the FDA's Office of Prescription Drug Promotion (OPDP) oversees all promotional materials for prescription drugs. It has no concept of fair balance -- the legal requirement that risk information must be presented with comparable prominence to benefit claims. It cannot distinguish between branded promotional materials (which require full Medical-Legal-Regulatory review and a brief summary of risk information), reminder ads (which can mention only the drug name with no claims), and help-seeking ads (which describe a disease without naming a product). It has no guardrails against off-label promotion -- the prohibition on suggesting that a drug be used for any indication, patient population, dose, or route of administration not in the FDA-approved labeling.

**Why it matters.** Pharmaceutical advertising regulation is not optional guidance. It is federal law, enforced with severe consequences. The historical record speaks clearly:

- **Pfizer ($2.3 billion, 2009)**: The largest healthcare fraud settlement in history at the time, resolving allegations of off-label promotion of Bextra (valdecoxib) and illegal marketing of three other drugs. The settlement included a $1.195 billion criminal fine.
- **GlaxoSmithKline ($3 billion, 2012)**: Settled charges of off-label promotion of Paxil for pediatric use and Wellbutrin for weight loss and sexual dysfunction -- uses never approved by the FDA.
- **Johnson & Johnson ($2.2 billion, 2013)**: Resolved allegations of off-label promotion of Risperdal for elderly dementia patients and children, uses for which the drug was not approved.
- **Novartis ($390 million, 2015)**: Settled charges related to kickbacks to physicians through speaker programs that functioned as inducements rather than genuine educational events.
- **Teva Pharmaceuticals ($425 million, 2024)**: Resolved allegations of Anti-Kickback Statute violations related to using a charity to funnel copay subsidies to Medicare patients.

These are not edge cases. They represent a systematic pattern of enforcement that makes regulatory compliance the single most consequential concern in pharmaceutical marketing. In September 2025, the FDA issued over 100 enforcement letters in a single action -- the highest annual total in nearly 25 years -- with 42 targeting DTC television advertisements for failing the Clear, Conspicuous, and Neutral (CCN) standard for risk disclosure.

A marketing tool that generates pharmaceutical promotional content without regulatory awareness is not merely incomplete. It is actively dangerous.

**What the plugin now provides.** The life sciences plugin adds a dedicated `regulatory-compliance` skill with a promotional material classification matrix, a full MLR review simulation framework (30 checklist items across medical, legal, and regulatory review functions), a five-dimension fair balance scoring system, off-label red flag detection, and two detailed reference documents covering FDA promotional rules and EMA advertising requirements. The `/mlr-review` command operationalizes this knowledge into a structured pre-submission review workflow that classifies content, evaluates it against all three MLR review functions, scores fair balance, verifies references, and produces findings rated by severity (Critical, Major, Minor) with specific remediation guidance.

## 2. Audience Segmentation Gap

**What was missing.** The base marketing plugin understands marketing personas -- fictional representations of target customers defined by demographics, goals, and pain points. This works well for consumer and B2B marketing, where personas like "Marketing Manager Maria" or "Developer Dave" capture meaningful audience differences.

But pharmaceutical marketing does not target personas. It targets healthcare professionals (HCPs) segmented by medical specialty, prescribing behavior, institutional affiliation, influence tier, practice setting, patient volume, formulary access, and digital engagement patterns. An oncologist at Memorial Sloan Kettering who chairs NCCN guideline committees and presents at ASCO plenary sessions requires fundamentally different engagement than a community oncologist in a suburban group practice, even though both treat the same disease. The base plugin has no framework for this kind of segmentation.

**Why it matters.** One-size-fits-all messaging fails in pharmaceutical marketing for structural reasons. An oncologist evaluating a new immunotherapy wants to see hazard ratios, Kaplan-Meier curves, and subgroup analyses from Phase 3 trials. A primary care physician considering a diabetes drug wants simplified efficacy data and practical dosing guidance. A payer evaluating formulary inclusion wants cost-effectiveness analyses and budget impact models. Sending the wrong content to the wrong audience does not merely reduce engagement -- it damages credibility with HCPs who expect scientifically precise, specialty-appropriate communication.

Furthermore, HCP influence is not uniform. A Tier 1 Key Opinion Leader who authors treatment guidelines shapes prescribing behavior for thousands of physicians. A Tier 3 community physician influences prescribing within a single practice. The engagement model, content depth, and resource allocation must differ dramatically across these tiers.

**What the plugin now provides.** The modified `campaign-planning` skill adds three detailed segmentation frameworks: HCP segmentation across seven dimensions (specialty, prescribing behavior, influence tier, practice setting, digital engagement, formulary access, patient volume), patient segmentation across six dimensions, and payer segmentation across four dimensions. The `medical-affairs-liaison` skill adds a full KOL tiering framework with seven scoring dimensions (publication impact, clinical trial leadership, congress presence, guideline involvement, institutional influence, digital influence, engagement potential) and composite scoring thresholds for Tier 1 through Tier 3 classification.

## 3. Campaign Type Gap

**What was missing.** The base marketing plugin handles generic campaign planning -- defining objectives, audiences, channels, content calendars, and success metrics. This framework serves well for product launches, awareness campaigns, and lead generation in most industries.

Pharmaceutical marketing, however, runs campaign types that have no equivalent in general marketing. Disease awareness campaigns (both branded and unbranded) operate under distinct regulatory rules: an unbranded campaign cannot mention the product name, logo, or branding, and its call to action must be "talk to your doctor" rather than "ask about [product]." Congress marketing campaigns require 6-12 months of planning across booth strategy, satellite symposia, data dissemination, KOL engagement, and competitive intelligence -- a complexity that dwarfs a typical trade show plan. Peer-to-peer (P2P) campaigns involve training physician speakers to deliver approved presentations to their peers, with strict compliance requirements around approved slides, fair market value compensation, venue restrictions, and Sunshine Act reporting. Medical Science Liaison (MSL) engagement is an entirely non-promotional scientific exchange channel that must be structurally separated from commercial activity.

**Why it matters.** A pharma brand team's annual plan typically includes all of these campaign types running simultaneously. If the planning tool cannot distinguish between them -- cannot enforce the rule that unbranded campaigns must not reference the product, cannot plan a congress with a 36-week countdown timeline, cannot structure a P2P program with compliance guardrails -- then the tool forces teams back to manual processes for their most critical work.

**What the plugin now provides.** The modified `campaign-planning` skill adds six pharma-specific campaign types with detailed descriptions, objectives, regulatory constraints, and channel guidance: disease awareness (unbranded), product launch (branded), congress marketing, peer-to-peer, patient support program, and medical education campaigns. The `/congress-plan` command provides an 11-section congress planning framework with week-by-week timelines. The `/kol-strategy` command structures KOL engagement planning across identification, tiering, advisory boards, speaker programs, MSL deployment, and measurement.

## 4. Content Compliance Gap

**What was missing.** The base marketing plugin creates content without any concept of claim substantiation, reference annotation, Important Safety Information (ISI) requirements, or Prescribing Information (PI) / Summary of Product Characteristics (SmPC) integration. It drafts blog posts, social media copy, and email newsletters -- content types that in pharma require rigorous compliance treatment before they can be distributed.

Every efficacy claim in a pharmaceutical promotional piece must be annotated with a specific reference to a published clinical trial or the approved labeling. Every branded material must include the ISI -- a comprehensive summary of contraindications, warnings, precautions, and adverse reactions drawn verbatim from the approved PI or SmPC. Every piece of branded content must either attach or link to the full PI/SmPC. These are not best practices; they are legal requirements.

**Why it matters.** Content that fails Medical-Legal-Regulatory (MLR) review cannot be distributed. Industry benchmarks show that standard MLR review cycles run 20-45 days from submission to final approval, and the most common reasons for rejection are unsupported claims, insufficient fair balance, off-label implications, and incomplete ISI. Every rejection cycle adds weeks to the content timeline.

The real cost, however, is not just delay. Content that bypasses compliance and reaches the market with unsubstantiated claims, missing safety information, or off-label implications exposes the company to FDA enforcement action, competitor complaints, and litigation. The base plugin generates content that would fail MLR review on first submission, every time, for any branded pharmaceutical material.

**What the plugin now provides.** The modified `content-creation` skill adds five life sciences content types (branded sales aid, clinical data visualization, mechanism of action content, formulary dossier, patient education materials), each with structural templates and compliance requirements. It adds a reference annotation format specification (superscript notation with sequential numbering), PI/SmPC integration requirements by format (print, digital, video, social media), and a content classification matrix mapping eight content types to their required MLR review level. The `/mlr-review` command provides a structured pre-submission check that catches the most common rejection reasons before content reaches the formal review committee.

## 5. KPI Gap

**What was missing.** The base marketing plugin tracks standard marketing KPIs: email open rates, click-through rates, social media engagement, website traffic, conversion rates, and campaign ROI. These metrics are valuable for general marketing but miss entirely what pharmaceutical companies need to measure.

Pharma commercial success is measured in prescriptions -- new prescriptions (NRx), total prescriptions (TRx), and market share. Brand performance is tracked through Share of Voice (SOV), which measures promotional prominence relative to competitors across advertising, sales force activity, and digital channels. Scientific positioning is measured through Scientific Share of Voice (SSoV), which tracks publications, congress presentations, and KOL advocacy. Market access is measured in formulary wins, formulary tier status, and the percentage of target patients with insurance coverage.

**Why it matters.** A pharmaceutical marketing team that reports on email open rates and social media impressions without connecting those metrics to prescriber behavior and market share is presenting vanity metrics. The industry's fundamental measurement challenge -- cited by 69% of pharma companies as their top difficulty -- is connecting promotional activity to prescribing behavior. Only 24% of pharmaceutical companies comprehensively collect and analyze HCP engagement data, and merely 22% act on those insights. A marketing tool that reinforces generic KPI frameworks perpetuates this measurement gap rather than closing it.

**What the plugin now provides.** The modified `performance-analytics` skill adds five pharma-specific KPI category tables: commercial KPIs (10 metrics including NRx, TRx, market share, SOV, prescriber adoption), HCP engagement KPIs (7 metrics including detail effectiveness and MSL interaction quality), payer and market access KPIs (6 metrics including formulary coverage and PA override rate), congress engagement KPIs (7 metrics), and patient engagement KPIs (6 metrics). It adds two specialized reporting templates: a monthly brand performance report and a launch tracker dashboard. It introduces prescriber segmentation by adoption status (Champions, Trialists, Prospects, Lapsed) and SOV measurement guidance.

## 6. Channel Gap

**What was missing.** The base marketing plugin knows the channels that general marketers use: social media platforms, email marketing, content marketing (blogs, landing pages), paid search, paid social, and SEO. These channels exist in pharma marketing, but they are neither the primary nor the most impactful channels for reaching healthcare professionals.

HCPs engage with pharmaceutical information through medical portals (Medscape reaches 94% of U.S. physicians monthly), peer-to-peer speaker programs, medical congresses, MSL field visits, rep-triggered approved email (through platforms like Veeva Approved Email), formulary dossier submissions, and medical journal advertising. These channels operate under compliance constraints that have no parallel in consumer marketing: medical portal content must be HCP-gated, speaker programs must use approved slides with documented fair market value compensation, congress materials require months of MLR review lead time, and MSL interactions must be strictly non-promotional.

**Why it matters.** If a marketing planning tool cannot account for these channels -- cannot plan an MSL field engagement strategy, cannot build a congress content plan, cannot structure a medical portal advertising campaign -- then it covers perhaps 30% of the channels through which pharmaceutical companies actually reach their audiences. The remaining 70% must be planned manually or in separate systems, fragmenting the marketing planning process.

**What the plugin now provides.** The modified `campaign-planning` skill adds a pharma-specific channel guide covering eight life sciences channels (medical journals, medical portals, conference booths, MSL field visits, patient advocacy partnerships, rep-triggered email, DTC television/digital, formulary dossiers) with audience, use case, and regulatory considerations for each. The CONNECTORS.md file adds nine new connector categories for life sciences systems: biomedical literature (PubMed), clinical trials data (ClinicalTrials.gov), drug safety and labeling (OpenFDA), life sciences CRM (Veeva), MLR review platforms, prescribing data sources, formulary data sources, medical education platforms, and competitive intelligence platforms. The `.mcp.json` configuration adds four new MCP server integrations (PubMed, ClinicalTrials.gov, OpenFDA, Veeva).

## 7. Terminology Gap

**What was missing.** The base marketing plugin speaks the language of general marketing: personas, funnels, CTAs, A/B testing, engagement rates. It does not know the terminology that pharmaceutical marketers use daily. It does not distinguish between a drug's International Nonproprietary Name (INN, the generic name like "pembrolizumab") and its brand name ("KEYTRUDA"), nor does it know the conventions for when to use which format in which context. It does not understand clinical endpoints (Overall Survival, Progression-Free Survival, Overall Response Rate), statistical measures (Hazard Ratio, Confidence Interval, Number Needed to Treat), or safety terminology (adverse events, contraindications, black box warnings).

**Why it matters.** Pharmaceutical content that uses consumer marketing language rather than scientific communication conventions immediately signals to HCPs that the author does not understand their world. Worse, incorrect terminology can create compliance problems. Calling a drug "safe" without qualification is prohibited in promotional materials. Using the word "cure" for a treatment that achieves remission is a regulatory violation. Referring to a clinical trial's "success" without specifying which endpoint was met and with what statistical significance is misleading. The terminology gap is not cosmetic -- it is substantive, affecting both credibility and compliance.

**What the plugin now provides.** The modified `brand-voice` skill adds pharma terminology management including drug naming conventions (a table mapping four contexts to the correct name format), clinical terminology standards (a table of ten common clinical abbreviations with guidance on when to spell them out), a pharma tone adaptation matrix mapping six audiences (HCPs, patients, caregivers, payers, KOLs, MSLs) to appropriate tone and constraints, and a prohibited language table listing six terms that must not appear in promotional materials (Cure, Safe unqualified, Proven unqualified, Breakthrough in claims, unsupported First-line/Standard of care claims, and off-label use suggestions) with compliant alternatives.

## The Cumulative Effect

Each of these seven gaps, taken individually, would justify modifications to the base plugin. Taken together, they demonstrate that pharmaceutical marketing operates in a fundamentally different domain from general marketing -- one where regulatory law, clinical science, and commercial strategy intersect at every decision point.

The life sciences plugin does not replace the base marketing toolkit. It preserves every base command, every base skill, and every base integration. What it adds is the regulatory awareness, audience sophistication, campaign specificity, content compliance, measurement precision, channel coverage, and terminological accuracy that life sciences marketing demands. The result is a tool that speaks the language of pharma marketing directors and medical affairs leads, not because it discards general marketing principles, but because it layers industry-specific knowledge on top of them.

---

# Part IX: Regulatory Landscape Overview

Pharmaceutical marketing is the most heavily regulated form of commercial communication in the world. Every claim, every image, every piece of safety information in a promotional material exists within a legal framework that has been shaped by decades of legislation, enforcement actions, and industry self-regulation. This chapter provides a business-user-friendly guide to the regulatory landscape that the life sciences plugin is designed to navigate.

## Major Regulatory Frameworks

### FDA (United States)

The United States Food and Drug Administration, through its Office of Prescription Drug Promotion (OPDP), is the primary authority overseeing pharmaceutical advertising and promotional labeling in the U.S. market. OPDP sits within the Center for Drug Evaluation and Research (CDER) and reviews promotional materials to ensure they are truthful, balanced, and not misleading.

**Legal foundation.** The core regulations are found in the Federal Food, Drug, and Cosmetic Act (FD&C Act), particularly Sections 502 (misbranding) and 201(n) (which establishes that labeling is misleading if it fails to reveal material facts). Title 21 of the Code of Federal Regulations Part 202 (21 CFR 202) provides the specific rules governing prescription drug advertising.

**What OPDP regulates.** Every promotional communication from a pharmaceutical manufacturer falls under OPDP's jurisdiction: print ads in medical journals, broadcast TV and radio ads, digital content on websites and social media, sales aids and detail pieces used by field representatives, exhibit materials at medical congresses, and email campaigns to healthcare professionals.

**Three categories of prescription drug advertising.** OPDP classifies all promotional materials into three categories, each with different requirements:

1. **Product-claim ads** present the drug's name, at least one approved indication, and efficacy or safety claims. These require fair balance and must include a brief summary (in print) or major statement (in broadcast) covering the drug's most significant risks from the approved labeling.

2. **Reminder ads** mention only the drug's name, dosage form, and cost -- they make no claims about efficacy or safety. Because no claims are made, they are exempt from including risk information. However, reminder ads cannot be used for drugs with boxed warnings or Risk Evaluation and Mitigation Strategies (REMS).

3. **Help-seeking ads** describe a disease or condition and encourage patients to consult their doctor. They do not name a specific product and are therefore regulated by the Federal Trade Commission (FTC) rather than the FDA.

**DTC advertising.** The United States and New Zealand are the only two countries that permit direct-to-consumer advertising of prescription drugs. U.S. DTC ad spending exceeds $6 billion annually. Product-claim DTC ads must include the major statement and provide "adequate provision" for consumers to access the full prescribing information (via a toll-free number, website, or reference to a concurrent print ad).

**The CCN Final Rule.** Effective May 20, 2024 (compliance date November 20, 2024), the Clear, Conspicuous, and Neutral (CCN) rule codifies five standards for how the major statement in DTC TV and radio ads must be presented: language must be readily understandable to consumers; audio risk information must match the pace, volume, and articulation of the rest of the ad; text must be of sufficient size, contrast, and duration; no audio or visual elements may distract from risk comprehension; and the major statement must be delivered in a neutral manner.

**Enforcement.** OPDP enforces compliance through untitled letters (requesting voluntary correction of less serious violations) and warning letters (demanding immediate corrective action for serious violations, such as making false or misleading claims or omitting material risk information). In severe cases, the FDA can pursue seizure, injunctions, or criminal prosecution. The September 2025 enforcement wave -- over 100 letters in a single action, with 42 targeting DTC TV ads -- signaled a dramatic escalation from the near-zero enforcement letters issued in 2023 and 2024.

**Digital and social media guidance.** The FDA has issued guidance documents addressing character-limited platforms (2014), correcting third-party misinformation (2014), and presenting risk information in digital formats (2009). Key principles: sponsored search results must include risk information alongside benefit claims; social media posts must maintain fair balance; user-generated content must be monitored and misinformation corrected; paid influencer and KOL posts are held to the same standards as company-generated content.

### EMA (European Union)

The European Medicines Agency (EMA) provides centralized regulatory oversight, but pharmaceutical advertising rules in the EU are primarily governed by EU Directive 2001/83/EC, Title VIII (Articles 86-100). Unlike the U.S. system with its single federal regulator, EU advertising regulation involves both the harmonized directive and member state implementing legislation, creating a layered compliance landscape.

**The fundamental difference from the U.S.** Article 88 of Directive 2001/83/EC explicitly prohibits advertising prescription medicines to the general public throughout the EU. There is no DTC advertising of prescription drugs in Europe. This single rule eliminates an entire category of promotional activity that consumes billions of dollars in the U.S. market.

**Advertising to healthcare professionals.** EU rules require that advertising to HCPs include essential information compatible with the Summary of Product Characteristics (SmPC), including the medicinal product's supply classification. Companies must maintain a scientific service responsible for product information, and pharmaceutical sales representatives must be adequately trained with sufficient scientific knowledge.

**Prohibited practices.** Article 94 prohibits gifts, pecuniary advantages, or benefits in kind to HCPs, except for items of inexpensive value relevant to medical practice and reasonable hospitality at promotional or scientific events. Free samples are restricted (limited quantities, upon written request, and for a limited period after launch).

**Member state variations.** Despite the common EU framework, each member state has distinct implementing rules that create significant compliance complexity:

- **Germany**: The Heilmittelwerbegesetz (HWG, Health Advertising Act) and Arzneimittelgesetz (AMG, Medicinal Products Act) govern pharmaceutical advertising. Germany uses a self-assessment model rather than pre-clearance. The FSA (Freiwillige Selbstkontrolle fur die Arzneimittelindustrie) provides industry self-regulation. All advertisements must include a mandatory risk statement directing patients to read the package leaflet.

- **France**: The ANSM (Agence Nationale de Securite du Medicament) requires prior approval -- a "visa" -- for certain promotional materials before distribution. This is one of the strictest pre-clearance regimes in Europe. The Bertrand Law requires public disclosure of all transfers of value between pharmaceutical companies and healthcare professionals.

- **United Kingdom**: Post-Brexit, the UK follows the Medicines and Healthcare products Regulatory Agency (MHRA) under the Human Medicines Regulations 2012. Industry self-regulation operates through the ABPI (Association of the British Pharmaceutical Industry) Code of Practice, enforced by the PMCPA (Prescription Medicines Code of Practice Authority). The ABPI Code requires that a "certified signatory" -- a person certified to have knowledge of the Code, MHRA requirements, and relevant legislation -- approves all promotional materials before use.

- **Italy**: AIFA (Agenzia Italiana del Farmaco) oversees pharmaceutical advertising, requiring prior authorization for HCP-directed materials. The Farmindustria Code provides self-regulatory requirements.

- **Spain**: AEMPS (Agencia Espanola de Medicamentos y Productos Sanitarios) operates under Royal Decree 1416/1994. The Farmaindustria Code supplements regulatory requirements. Prior notification is required for certain advertising activities.

**The EFPIA Code.** The European Federation of Pharmaceutical Industries and Associations (EFPIA) Code of Practice provides an overarching self-regulatory framework for member companies across Europe. Key requirements include that promotional claims must be accurate, balanced, and fair; the word "safe" must not be used without qualification; the term "new" must not be used for products marketed for more than 12 months; and companies must disclose all transfers of value to HCPs and healthcare organizations annually.

**SmPC compliance.** All promotional claims in the EU must be compatible with the approved SmPC. The SmPC is the definitive reference for what can and cannot be said in promotional materials, analogous to the U.S. Prescribing Information but with its own structure and requirements.

### Japan (JPMA Code and PMDA)

Japan's pharmaceutical promotion is governed by the Pharmaceuticals and Medical Devices Act (PMD Act), supplemented by the Japan Pharmaceutical Manufacturers Association (JPMA) self-regulatory codes. The JPMA Code requires companies to establish standard operating procedures for drug information promotion, maintain a promotion oversight department separate from sales and marketing, and appoint a designated "Promotional Materials Officer." The JPMA Code Compliance Committee can issue serious warnings, suspend membership, or expel companies. As of April 2024, amended regulations require pharmaceutical companies to disclose expenses related to information provision and entertainment, increasing transparency.

### Other Key Markets

- **UK (Post-Brexit)**: MHRA oversight under the Human Medicines Regulations 2012, with ABPI/PMCPA self-regulation providing the primary enforcement mechanism through the Code of Practice.
- **Canada**: Health Canada regulates pharmaceutical advertising under the Food and Drugs Act. The Pharmaceutical Advertising Advisory Board (PAAB) reviews promotional materials. DTC advertising of prescription drugs is prohibited except for name, price, and quantity ads.
- **Australia**: The Therapeutic Goods Administration (TGA) regulates under the Therapeutic Goods Act 1989. Medicines Australia provides industry self-regulation through its Code of Conduct.

## Key Compliance Concepts

### Fair Balance

Fair balance is the foundational principle requiring that promotional materials present risk information with comparable prominence, depth, and detail to benefit claims. An advertisement fails fair balance if effectiveness information is presented in greater scope, detail, or emphasis than the summary of side effects, contraindications, and warnings.

In practice, fair balance means:
- Risk information must appear in the same font size, color contrast, and visual treatment as efficacy claims in print materials.
- Audio risk disclosures in broadcast ads must be delivered at the same pace, volume, and clarity as benefit statements.
- Visual elements -- imagery, color, animation, graphics -- must not distract from or minimize risk disclosures.
- In digital formats, safety information must be accessible without requiring the user to scroll past multiple screens of benefit content.

The life sciences plugin addresses fair balance through the regulatory-compliance skill's five-dimension scoring framework (Prominence, Completeness, Readability, Placement, Language), each scored on a 1-5 scale. The `/mlr-review` command applies this framework as Step 5 of every review simulation, producing a quantified fair balance assessment with specific dimension-level feedback.

### Off-Label Promotion

Off-label promotion is any communication from a pharmaceutical manufacturer that suggests, implies, or encourages use of a drug for indications, patient populations, doses, or routes of administration not approved in the FDA labeling (or SmPC in the EU). Off-label promotion constitutes misbranding under the FD&C Act.

**What is permitted.** The FDA's January 2025 guidance on "Communications From Firms to Health Care Providers Regarding Scientific Information on Unapproved Uses" describes the enforcement policy for firm-initiated scientific communications about unapproved uses to HCPs. Such communications must be truthful, non-misleading, and based on adequate and well-controlled clinical investigations; clearly identified as relating to an unapproved use; shared by medical or scientific personnel (not sales representatives); and non-promotional in character. Responding to genuinely unsolicited requests from HCPs for off-label information is also permissible, provided the response is balanced, includes the approved labeling, and is delivered through medical affairs (not commercial) channels.

**What is not permitted.** Proactively sharing off-label data in promotional contexts, cherry-picking off-label data to support commercial messaging, using sales representatives to discuss unapproved uses, and structuring speaker programs or advisory boards to disseminate off-label information are all prohibited.

The plugin addresses off-label restrictions through the regulatory-compliance skill's seven red flags for off-label content and a comparison table distinguishing permissible scientific exchange from prohibited off-label promotion. The `/mlr-review` command includes an explicit off-label check in its medical review step.

### Pre-Approval Information Exchange

Before a drug receives FDA approval, any public communication implying that the product is safe, effective, or likely to receive approval could be viewed as unlawful promotion. However, limited pre-approval communications are permitted: institutional advertising (announcing research in a therapeutic area without naming the product), limited "coming soon" announcements, clinical trial recruitment communications, and -- critically -- Pre-approval Information Exchange (PIE) with formulary decision-makers for budgeting and planning purposes, provided no promotional claims are made.

### Substantiation Requirements

The FDA requires that promotional claims be supported by "substantial evidence," which typically means adequate and well-controlled clinical investigations. In practice, this means every efficacy claim in a promotional piece must be traceable to specific data from pivotal clinical trials, the approved labeling, or peer-reviewed publications of adequate and well-controlled studies. Claims cannot be extrapolated across indications, patient populations, or endpoints without supporting data. Post-hoc analyses and subgroup data can be referenced but must be identified as such.

The plugin addresses substantiation through the content-creation skill's reference annotation format (superscript notation with sequential numbering), the brand-voice skill's claim substantiation requirements table mapping five claim types to their required evidence sources, and the `/mlr-review` command's reference verification table.

### Adverse Event Reporting in Promotional Context

Pharmaceutical companies have an obligation to report adverse events (AEs) that come to their attention through any channel, including promotional activities. If an HCP mentions an adverse event during a sales call, at a congress booth, or in response to a promotional email, the company must capture and report that AE through its pharmacovigilance system. This obligation extends to social media: if a patient or HCP reports an adverse event in a comment on a company's social media post, the company must capture it.

### Sunshine Act and Transparency Reporting

The Physician Payments Sunshine Act (Section 6002 of the Affordable Care Act) requires pharmaceutical and medical device companies to report all payments and transfers of value to physicians and teaching hospitals to the Centers for Medicare and Medicaid Services (CMS). Data is published through the Open Payments system. Reporting categories include consulting fees, speaker honoraria, meals, travel, research grants, royalties, and ownership interests. The reporting threshold is extremely low -- virtually all transfers of value must be reported. Civil fines for non-compliance range from $1,000 to $100,000 per violation, with a cap of approximately $1.4 million.

In Europe, the EFPIA Disclosure Code requires similar transparency reporting, with annual public disclosure of all transfers of value to HCPs and healthcare organizations. Member state implementations vary, with France's Bertrand Law being among the most stringent.

The plugin addresses transparency through compliance requirements sections in the `/kol-strategy` command, the medical-affairs-liaison skill's advisory board compliance checklist, and the `/mlr-review` command's legal review step (which checks Sunshine Act/EFPIA obligations).

## How the Plugin Maps Regulations to Features

The following table maps each major regulatory requirement to the specific plugin feature that addresses it:

| Regulatory Requirement | Plugin Feature | Location |
|----------------------|---------------|----------|
| Promotional material classification | Classification matrix and decision tree | regulatory-compliance skill |
| Fair balance | Five-dimension scoring framework | regulatory-compliance skill; `/mlr-review` Step 5 |
| Off-label restriction | Seven red flags + permissible vs. prohibited table | regulatory-compliance skill; `/mlr-review` Step 2 |
| Claim substantiation | Reference annotation format + claim type/evidence table | content-creation skill; brand-voice skill |
| ISI requirements | Format-specific ISI placement rules | brand-voice skill; content-creation skill |
| PI/SmPC integration | Format-specific attachment/linking requirements | content-creation skill |
| MLR review preparation | 30-item checklist across three review functions | regulatory-compliance skill; `/mlr-review` command |
| Drug naming conventions | Four-context naming format table | brand-voice skill |
| Prohibited language | Six-term prohibition table with compliant alternatives | brand-voice skill |
| Content classification for review | Eight content types mapped to review level | content-creation skill |
| Black box warning display | Checklist item in regulatory review | regulatory-compliance skill |
| Sunshine Act compliance | Legal review checklist; advisory board compliance | `/mlr-review`; `/kol-strategy`; medical-affairs-liaison skill |
| EFPIA requirements | EMA reference document; advisory board compliance | regulatory-compliance references; medical-affairs-liaison skill |
| FDA digital/social guidance | Format-specific fair balance requirements | regulatory-compliance skill |
| Speaker program compliance | FMV, venue, content controls | medical-affairs-liaison skill; `/kol-strategy` |
| Congress material compliance | MLR timeline; material requirements | campaign-planning skill; `/congress-plan` |

This is not a compliance system -- it is a marketing tool with compliance awareness. It does not replace the judgment of medical, legal, and regulatory reviewers. What it does is ensure that content generated through the plugin is structured, annotated, and balanced in a way that anticipates MLR requirements rather than ignoring them. The goal is to reduce the number of revision cycles by catching the most common compliance issues before formal review begins.

---

# Part X: Modified Components Inventory

This chapter provides a detailed inventory of every component that was added or modified in the life sciences plugin compared to the base marketing plugin. For each component, we document what changed, why it changed, and -- for modified skills -- a before/after comparison highlighting the key additions.

## Modified Skills (5)

All five base marketing skills are preserved in full. The modification pattern is consistent: the entire base skill body is kept verbatim, and new life sciences content is appended at the end of the file after a `<!-- Life Sciences Addition -->` comment marker. The skill's frontmatter `description` field is expanded with additional trigger phrases so that the skill activates on pharma-specific queries while continuing to activate on general marketing queries.

### 1. brand-voice

**What was added.** Four new sections appended: Pharma Brand Voice Rules (covering fair balance in brand voice, ISI placement requirements, and claim substantiation); Pharma Tone Adaptation by Audience (a matrix mapping six audiences to appropriate tone and constraints); Pharma Terminology Management (drug naming conventions across four contexts, clinical terminology standards for ten common abbreviations); and Prohibited Language in Pharma Promotional Materials (six prohibited terms with explanations and compliant alternatives).

**Why.** Every word in a pharmaceutical promotional piece carries clinical and legal weight. A general brand voice framework that focuses on tone, personality, and messaging pillars is necessary but insufficient. Pharma brand voice must also enforce regulatory constraints: never bury risk information, never use minimizing language for adverse events, always substantiate claims with referenced evidence, always follow drug naming conventions appropriate to the audience.

**Before/after comparison (description field).**

| Version | Description trigger phrases |
|---------|---------------------------|
| Base (v1.0.0) | "...reviewing content for brand consistency, documenting a brand voice, adapting tone for different audiences, or checking terminology and style guide compliance." |
| Life Sciences (v1.0.0-ls) | Adds: "...enforcing pharma fair balance requirements, managing ISI placement, or ensuring claim substantiation in life sciences promotional materials." |

**Key additions at a glance:**
- Claim substantiation table: maps 5 claim types (efficacy, superiority, safety, MOA, patient outcome) to required substantiation sources
- Drug naming conventions: 4 contexts (scientific, patient-facing, regulatory, reminder advertising) with correct format for each
- Prohibited language table: 6 terms (Cure, Safe unqualified, Proven unqualified, Breakthrough in claims, unsupported First-line/SOC, off-label suggestions) with compliant alternatives
- Audience tone matrix: 6 audiences (HCPs, Patients, Caregivers, Payers, KOLs, MSLs) with tone, language level, and key constraints

### 2. campaign-planning

**What was added.** Four new sections: Life Sciences Campaign Types (six pharma-specific campaign types with detailed objectives, rules, channels, and compliance constraints); Life Sciences Audience Segmentation (three segmentation frameworks across HCP, patient, and payer dimensions); Regulatory Review Workflow in Campaign Planning (MLR review timeline benchmarks for seven material types, plus the "Campaign Timeline Adjustment Rule"); and Life Sciences Channel Guide (eight pharma-specific channels with audience, use case, and regulatory considerations).

**Why.** Campaign planning in pharma differs structurally from general marketing. Timelines must account for MLR review cycles (a branded sales aid requires 6-10 weeks total, compared to days for a general marketing asset). Audience segmentation operates on clinical and prescribing dimensions unknown in consumer marketing. Campaign types like disease awareness (unbranded), congress marketing, and P2P programs have regulatory constraints that general campaign frameworks cannot capture.

**Before/after comparison (description field).**

| Version | Description trigger phrases |
|---------|---------------------------|
| Base (v1.0.0) | "...launching a campaign, planning a product launch, building a content calendar, allocating budget across channels, or defining campaign KPIs." |
| Life Sciences (v1.0.0-ls) | Adds: "...planning life sciences campaigns (disease awareness, congress marketing, HCP engagement, patient support programs), segmenting HCP audiences, or building regulatory review workflows into campaign timelines." |

**Key additions at a glance:**
- 6 pharma campaign types: disease awareness (unbranded), product launch (branded with 3 phases), congress marketing, P2P, patient support, medical education
- HCP segmentation: 7 dimensions (specialty, prescribing behavior, influence tier, practice setting, digital engagement, access/formulary, patient volume)
- MLR timeline benchmarks: 7 material types with initial review, revision cycles, and total lead time (e.g., branded detail aid = 6-10 weeks total)
- Campaign Timeline Adjustment Rule: add MLR lead time on top of standard production timeline

### 3. competitive-analysis

**What was added.** Five new sections: Formulary Positioning Analysis (comparison template with nine dimensions and data sources); Clinical Trial Comparison (a 14-parameter pivotal trial comparison matrix with the critical caveat against inappropriate cross-trial comparisons); Label Comparison (a 10-element comparison template); Pipeline Intelligence (a tracking table template with data sources); and Life Sciences Battlecard Additions (four new battlecard sections plus pharma-specific objection handling and competitive monitoring sources).

**Why.** Competitive analysis in pharma operates on dimensions that do not exist in general marketing: formulary tier positioning, label breadth (approved indications, lines of therapy, biomarker requirements), clinical trial data (hazard ratios, survival curves, response rates), and pipeline intelligence (what competitors have in Phase 2 and Phase 3). Battlecards must address clinical differentiation and access/affordability, not just messaging and positioning.

**Before/after comparison (description field).**

| Version | Description trigger phrases |
|---------|---------------------------|
| Base (v1.0.0) | "...analyzing a competitor, building battlecards, identifying content gaps, comparing feature messaging, or preparing competitive positioning recommendations." |
| Life Sciences (v1.0.0-ls) | Adds: "...comparing drug labels and indications, analyzing formulary positioning, benchmarking clinical trial data across competitors, or evaluating competitive pipeline and lifecycle management strategies in life sciences." |

### 4. content-creation

**What was added.** Two new sections: Life Sciences Content Types (five specialized formats -- branded sales aid with 8-part structure, clinical data visualization with rules for five chart types, MOA content, AMCP-format formulary dossier, and patient education materials with health literacy requirements); and MLR Review Requirements for Content (reference annotation format specification, PI/SmPC integration requirements by format, and content classification for MLR with a table mapping eight content types to review levels).

**Why.** Pharmaceutical content creation is inseparable from compliance. Every branded sales aid has a prescribed structure (cover, efficacy pages with citations, safety pages, dosing, access, ISI, references, PI/SmPC). Every clinical data visualization must follow rules about axis scales, statistical context, and source citation. Every piece of content must be classified and routed through the appropriate MLR review pathway.

**Before/after comparison (description field).**

| Version | Description trigger phrases |
|---------|---------------------------|
| Base (v1.0.0) | "...writing any marketing content, when you need channel-specific formatting, SEO-optimized copy, headline options, or calls to action." |
| Life Sciences (v1.0.0-ls) | Adds: "...MLR-ready promotional materials, PI/SmPC-referenced content, clinical data visualizations, MOA descriptions, formulary dossier content, or life sciences content requiring reference annotation and regulatory compliance." |

### 5. performance-analytics

**What was added.** Three new sections: Life Sciences Performance Metrics (five KPI category tables covering 36 pharma-specific metrics across commercial, HCP engagement, payer/market access, congress engagement, and patient engagement dimensions); Life Sciences Reporting Templates (monthly brand performance report and launch tracker dashboard structures); and Prescriber Tracking and Share of Voice (prescriber segmentation by adoption status, SOV measurement guidance, and SOV-to-market-share correlation analysis).

**Why.** Pharmaceutical performance measurement centers on prescription behavior (NRx, TRx, market share), market access (formulary wins, coverage rates), and scientific positioning (SOV, SSoV) -- none of which appear in general marketing analytics frameworks. A pharma performance report that does not track prescriber adoption curves, formulary wins, and share of voice is missing the metrics that drive commercial decisions.

**Before/after comparison (description field).**

| Version | Description trigger phrases |
|---------|---------------------------|
| Base (v1.0.0) | "...building performance reports, reviewing campaign results, analyzing channel metrics (email, social, paid, SEO), or identifying what's working and what needs improvement." |
| Life Sciences (v1.0.0-ls) | Adds: "...tracking pharma KPIs (NRx, TRx, market share, share of voice), measuring prescriber adoption, analyzing congress engagement scores, or reporting on HCP and patient engagement in life sciences marketing." |

## New Skills (2)

### regulatory-compliance

**Location:** `skills/regulatory-compliance/SKILL.md` + 2 reference documents

**Purpose.** Provides the regulatory knowledge foundation for the entire life sciences plugin. Contains frameworks for classifying promotional materials, simulating MLR review, checking fair balance, and enforcing off-label restrictions.

**Content structure:**
- Promotional Material Classification -- a matrix of 7 material types with their naming, claims, and review requirements, plus a 4-step classification decision tree
- MLR Review Simulation -- 30 checklist items across medical review (10), legal review (10), and regulatory review (10), plus 8 common MLR rejection reasons with prevention guidance
- Fair Balance Checker -- 5-dimension scoring framework (Prominence, Completeness, Readability, Placement, Language) on a 1-5 scale, plus fair balance requirements by 7 content formats
- Off-Label Restriction Compliance -- 7 red flags for off-label content, plus a permissible vs. prohibited scientific exchange comparison table (5 pairs)

**Reference documents:**
- `references/fda-promotional-rules.md` -- Comprehensive FDA regulatory reference covering OPDP authority, key regulations (FD&C Act, 21 CFR 202), promotional material categories, enforcement actions, brief summary and major statement requirements, fair balance standards, digital and social media guidance, and pre-submission requirements (Form FDA 2253)
- `references/ema-requirements.md` -- EU regulatory reference covering Directive 2001/83/EC, HCP advertising requirements (Article 91), public advertising prohibition (Article 88), member state variations (Germany, France, UK, Italy, Spain), SmPC compliance mapping (6 sections), EFPIA Code requirements, and digital advertising rules in the EU

### medical-affairs-liaison

**Location:** `skills/medical-affairs-liaison/SKILL.md` + 2 reference documents

**Purpose.** Provides the medical affairs and KOL management knowledge that bridges scientific and commercial strategy. Covers MSL engagement, KOL identification and tiering, advisory board planning, and congress strategy.

**Content structure:**
- MSL Engagement Planning -- MSL vs. sales rep distinction table (6 dimensions), territory planning framework, interaction planning template, 6 activity metrics with targets
- KOL Mapping and Tiering -- 7 identification sources, 3-tier summary with profiles and typical activities, 10-point KOL profiling template
- Advisory Board Planning -- 8-step planning checklist, 4 format options (in-person, virtual, ad hoc, standing), 8 compliance requirements
- Congress Strategy -- 7-activity engagement model, prioritization criteria, post-congress activity checklist

**Reference documents:**
- `references/kol-tier-framework.md` -- Detailed scoring methodology with 7 dimensions (Publication Impact, Clinical Trial Leadership, Congress Presence, Guideline/Society Involvement, Institutional Influence, Digital/Media Influence, Engagement Potential), each rated 1-5 with suggested weights. Composite scoring thresholds for tier assignment (Tier 1: 4.0-5.0, Tier 2: 3.0-3.9, Tier 3: 2.0-2.9). KOL landscape mapping guidance and engagement tracker template.
- `references/congress-planning-guide.md` -- Major congress calendar across 7 therapeutic areas (listing congresses like ASCO, ESMO, ASH, AHA, ESC, ADA, AAN, AASLD). 7-phase planning timeline from 12 months to post-congress. Booth strategy with staffing plan. Satellite symposium planning framework. Competitive intelligence gathering methodology.

## New Commands (3)

### /mlr-review

**Purpose.** Simulate a Medical-Legal-Regulatory review of pharmaceutical or medical device promotional content before formal MLR submission.

**Inputs:** Content to review (pasted, file, URL, or batch); content classification (7 types); target market (US/EU/country, default US); product context (brand name, INN, indications, safety info, black box/REMS status).

**Process:** 5-step review -- (1) content classification using the regulatory-compliance skill matrix, (2) medical review evaluating clinical accuracy, reference verification, data presentation, statistical context, off-label implications, and study context, (3) legal review evaluating unsubstantiated claims, comparatives, trademarks, copyright, testimonials, and transparency reporting, (4) regulatory review evaluating indication statement, fair balance, ISI, PI/SmPC, black box warning, classification, and expiration date, (5) fair balance assessment using the 5-dimension scoring framework.

**Outputs:** MLR Review Summary (classification, market, overall assessment from APPROVE to REJECT, fair balance score, issue counts by severity); Detailed Findings Table (issue, review function, severity, location, recommendation); Annotated Content (before/after for top issues); Reference Verification Table; Compliance Checklist Summary (8 items).

### /congress-plan

**Purpose.** Generate a comprehensive congress marketing and medical affairs plan for a medical conference.

**Inputs:** Congress name or therapeutic area; product(s) with brand/INN, indications, and data presentation status; objectives; budget range; team size; historical context.

**Outputs:** 11 sections -- Congress Overview; Data Dissemination Plan; Exhibition Booth Plan (design, interactive elements, staffing by role/shift, materials checklist); Satellite Symposium Plan; KOL Engagement Plan (priority KOLs, MSL assignments, meeting objectives); Competitive Intelligence Plan; Social Media and Communications Plan; Content Repurposing Plan; Timeline (week-by-week from 36 weeks out to +2 weeks post-congress); Budget Breakdown (7 categories); Success Metrics (7 quantitative measures).

### /kol-strategy

**Purpose.** Develop a comprehensive KOL engagement strategy including identification, tiering, engagement planning, and measurement.

**Inputs:** Therapeutic area or product; strategic objective (pre-launch, launch, post-launch, competitive defense, pipeline); geography; current state; timeline.

**Outputs:** 11 sections -- Strategic Context; KOL Identification (using clinical trials data and publications); KOL Tiering (applying the scoring framework); Engagement Plan by Tier (7-activity matrix across 4 tiers); Advisory Board Plan; Speaker Program Plan; MSL Deployment Alignment; KOL Engagement Calendar (quarterly); Measurement Framework (7 metrics); Budget Framework (6 activity categories); Compliance and Risk Mitigation (FMV, Sunshine Act, AKS considerations).

## Updated Configuration

### .mcp.json Additions

Four new MCP server integrations:

| Server | Type | URL/Config | Purpose |
|--------|------|-----------|---------|
| PubMed (NCBI) | stdio | Local server script; requires `NCBI_API_KEY` | Biomedical literature search for reference verification, KOL publication analysis, competitive intelligence |
| ClinicalTrials.gov | HTTP | `https://clinicaltrials.gov/api/v2` | Clinical trial registrations for competitive pipeline intelligence, KOL identification (principal investigators), trial comparison |
| OpenFDA | HTTP | `https://api.fda.gov` | Drug labeling, adverse event data, regulatory action history |
| Veeva | HTTP | `https://mcp.veeva.com/mcp` | CRM integration for HCP engagement tracking, approved email, content management |

All 9 base MCP servers (Slack, Canva, Figma, HubSpot, Amplitude, Notion, Ahrefs, Similarweb, Klaviyo) are preserved unchanged.

### CONNECTORS.md New Categories

Nine new connector categories added under a "Life sciences connectors" section:

| Category | Placeholder | Pre-configured Server | Other Options |
|----------|------------|----------------------|---------------|
| Biomedical literature | `~~biomedical literature` | PubMed (NCBI) | Embase, Cochrane Library, Google Scholar |
| Clinical trials data | `~~clinical trials data` | ClinicalTrials.gov | EU Clinical Trials Register, WHO ICTRP |
| Drug safety and labeling | `~~drug safety and labeling` | OpenFDA | DailyMed, EMA medicines database |
| CRM (life sciences) | `~~life sciences CRM` | Veeva CRM | IQVIA OCE, Salesforce Health Cloud |
| MLR review platform | `~~MLR review` | None | Veeva Vault PromoMats, Zinc Ahead |
| Prescribing data | `~~prescribing data` | None | IQVIA, Symphony Health, Komodo Health |
| Formulary data | `~~formulary data` | None | MMIT, Fingertip Formulary, Elsevier Gold Standard |
| Medical education | `~~medical education` | None | Medscape, DocCheck, Coliquio, Doximity |
| Competitive intelligence | `~~competitive intelligence` | None | EvaluatePharma, GlobalData, Citeline |

### README.md Updates

The README was rewritten to document the full life sciences plugin, including separate tables for base and life sciences commands, expanded skill descriptions reflecting the appended content, a new reference documents table, life sciences example workflows (MLR review simulation, congress planning, KOL strategy development, compliant content drafting), life sciences configuration guidance (approved indications, ISI text, claims library, KOL lists, congress calendar), and a separate Life Sciences Integrations section documenting the four new MCP servers.

## Summary: Total Component Inventory

| Component Type | Base (v1.0.0) | Life Sciences (v1.0.0-ls) | Delta |
|---------------|---------------|--------------------------|-------|
| Files | 15 | 26 | +11 |
| Commands | 7 | 10 | +3 new |
| Skills | 5 | 7 | +2 new, 5 modified |
| Reference documents | 0 | 4 | +4 new |
| MCP servers | 9 | 13 | +4 new |
| Connector categories | 7 | 16 | +9 new |

---

# Part XI: Industry Workflow Integration

The life sciences plugin is not an isolated tool. It is designed to integrate into the workflows that pharmaceutical, biotech, and medtech marketing teams execute daily. This chapter maps the plugin's commands and skills to real-world pharma marketing workflows, demonstrates integration with existing industry systems, and walks through three concrete workflow scenarios.

## End-to-End Brand Planning Workflow

A pharmaceutical brand plan follows a structured annual cycle that moves from market understanding through strategy development, execution, and measurement. The life sciences plugin provides support at every stage of this cycle.

### Stage 1: Market Research and Competitive Intelligence

**Business activity.** The brand team analyzes the competitive landscape, assessing competitor labels, formulary positioning, clinical trial pipelines, and share of voice. This analysis informs positioning strategy and identifies opportunities and threats.

**Plugin support.** The `/competitive-brief` command drives the initial competitive analysis. The modified `competitive-analysis` skill contributes formulary positioning analysis (comparing tier status, prior authorization requirements, and patient out-of-pocket costs), clinical trial comparison matrices (14-parameter head-to-head comparisons of pivotal trials), label comparison templates (10 elements from indications to pregnancy category), and pipeline intelligence tracking. ClinicalTrials.gov integration enables real-time pipeline monitoring. OpenFDA integration provides access to drug labeling and regulatory action history.

### Stage 2: Brand Strategy and Positioning

**Business activity.** The team develops the brand's voice, messaging pillars, and positioning relative to competitors. In pharma, this must account for regulatory constraints on language, claim substantiation requirements, and audience-specific tone adaptation.

**Plugin support.** The `brand-voice` skill provides the framework, now extended with pharma brand voice rules (fair balance requirements, ISI placement, claim substantiation), drug naming conventions, prohibited language guidance, and audience tone adaptation across HCPs, patients, caregivers, payers, KOLs, and MSLs.

### Stage 3: Campaign Planning

**Business activity.** The team plans the year's campaigns: product launch activities, disease awareness programs, congress marketing, peer-to-peer education, patient support outreach, and digital HCP engagement. Each campaign type has distinct objectives, regulatory constraints, and timelines.

**Plugin support.** The `/campaign-plan` command generates comprehensive campaign briefs. The modified `campaign-planning` skill adds six pharma campaign types, HCP/patient/payer segmentation frameworks, MLR review timeline benchmarks, and the pharma-specific channel guide. The "Campaign Timeline Adjustment Rule" -- add MLR lead time on top of standard production timelines -- ensures realistic scheduling.

### Stage 4: KOL Engagement Planning

**Business activity.** The medical affairs and commercial teams collaborate (within compliance boundaries) to develop KOL engagement strategies. This includes identifying and tiering KOLs, planning advisory boards, structuring speaker programs, and aligning MSL deployment.

**Plugin support.** The `/kol-strategy` command delivers an 11-section KOL strategy. The `medical-affairs-liaison` skill provides KOL identification sources (using PubMed for publication analysis and ClinicalTrials.gov for principal investigator identification), the tiering framework with seven scoring dimensions, advisory board planning checklists, and MSL deployment guidance.

### Stage 5: Content Development

**Business activity.** The marketing team creates the promotional toolkit: detail aids, digital content, email campaigns, patient materials, congress collateral, and formulary dossiers. Every piece requires reference annotation, ISI integration, and appropriate content classification for MLR routing.

**Plugin support.** The `/draft-content` command generates content. The modified `content-creation` skill adds five life sciences content types (branded sales aid with 8-part structure, clinical data visualization, MOA content, formulary dossier in AMCP format, patient education materials), reference annotation format specification, PI/SmPC integration requirements, and content classification for MLR routing.

### Stage 6: MLR Review

**Business activity.** All promotional materials undergo Medical-Legal-Regulatory review before distribution. This is typically the most time-consuming step in the pharma content lifecycle, with standard review cycles running 20-45 days.

**Plugin support.** The `/mlr-review` command simulates the three-function review before formal submission. The `regulatory-compliance` skill provides the classification matrix, 30-item checklist, fair balance scoring, and off-label detection. By catching common rejection reasons (unsupported claims, insufficient fair balance, off-label implications, missing ISI) before formal submission, the plugin aims to reduce revision cycles.

### Stage 7: Congress and Conference Planning

**Business activity.** The team plans presence at major medical congresses: booth design, satellite symposia, data dissemination, KOL meetings, competitive intelligence gathering, and post-congress content development. Planning begins 6-12 months before the event.

**Plugin support.** The `/congress-plan` command delivers an 11-section congress plan. The `medical-affairs-liaison` skill provides the congress engagement model, prioritization criteria, and post-congress activity checklists. The congress planning guide reference document provides the major congress calendar across seven therapeutic areas and a seven-phase planning timeline.

### Stage 8: Performance Tracking

**Business activity.** The team monitors commercial performance (NRx, TRx, market share), HCP engagement metrics, formulary wins, congress impact, and overall share of voice. Reports are delivered monthly to brand leadership and quarterly to senior management.

**Plugin support.** The `/performance-report` command generates performance reports. The modified `performance-analytics` skill adds 36 pharma-specific KPIs across five categories, two specialized reporting templates (monthly brand performance report and launch tracker dashboard), prescriber adoption segmentation, and SOV measurement guidance.

## Visual Workflow Map

The following text-based diagram maps the end-to-end brand planning workflow to specific plugin commands and skills:

```
BRAND PLANNING WORKFLOW                    PLUGIN COMMANDS & SKILLS
========================                   ========================

[1] Market Research &          -------->   /competitive-brief
    Competitive Intelligence               competitive-analysis skill
                                           ~~clinical trials data (ClinicalTrials.gov)
                                           ~~drug safety and labeling (OpenFDA)
          |
          v
[2] Brand Strategy &           -------->   brand-voice skill
    Positioning                            (pharma voice rules, naming, prohibited terms)
          |
          v
[3] Campaign Planning          -------->   /campaign-plan
                                           campaign-planning skill
                                           (LS campaign types, HCP segmentation, MLR timelines)
          |
          v
[4] KOL Engagement             -------->   /kol-strategy
    Planning                               medical-affairs-liaison skill
                                           ~~biomedical literature (PubMed)
                                           ~~clinical trials data (ClinicalTrials.gov)
          |
          v
[5] Content Development        -------->   /draft-content
                                           content-creation skill
                                           (LS content types, reference annotation, PI/SmPC)
          |
          v
[6] MLR Review                 -------->   /mlr-review
                                           regulatory-compliance skill
                                           (classification, checklists, fair balance, off-label)
          |
          v
[7] Congress Planning          -------->   /congress-plan
                                           medical-affairs-liaison skill
                                           (congress model, timeline, competitive intel)
          |
          v
[8] Performance Tracking       -------->   /performance-report
                                           performance-analytics skill
                                           (pharma KPIs, prescriber tracking, SOV)
```

## Integration with Existing Pharma Systems

The life sciences plugin connects to the technology ecosystem that pharmaceutical companies already use. These integrations extend the plugin's capabilities beyond standalone content generation into the operational systems where pharma marketing actually happens.

### Veeva Vault PromoMats

Veeva Vault PromoMats is the industry-dominant platform for managing promotional content lifecycle, with an estimated 80%+ market share in pharma. The Veeva MCP server integration enables the plugin to interact with the content management system where promotional materials are stored, reviewed, and distributed. This means content drafted through the plugin can be submitted into the PromoMats workflow for formal MLR review, and approved content can be retrieved for reference when creating derivative materials. The plugin's modular content approach -- creating reusable, pre-reviewed content components -- aligns with the modular content architectures that leading PromoMats implementations support.

### Veeva CRM

Veeva CRM (now transitioning to Vault CRM) is the dominant platform for pharmaceutical field force management, with deployments at nine of the top 20 global pharma companies. Integration enables the plugin to access HCP profiles, engagement history, and interaction data that inform KOL strategy development and campaign targeting. When the plugin identifies priority KOLs through the `/kol-strategy` command, those profiles can be cross-referenced against CRM data on existing relationships and engagement history.

### PubMed (NCBI)

PubMed provides access to over 36 million citations from biomedical and life sciences journals. The PubMed MCP server integration enables the plugin to search the literature for reference verification (confirming that cited publications support promotional claims), KOL publication analysis (quantifying an expert's publication output, citation impact, and co-author network), and competitive intelligence (tracking competitor publications and clinical data dissemination). This integration is particularly valuable for the `/kol-strategy` command's identification step and the `/mlr-review` command's reference verification step.

### ClinicalTrials.gov

ClinicalTrials.gov is the world's largest clinical trial registry. Integration enables the plugin to search for active and completed trials by condition, intervention, sponsor, and investigator. This powers competitive pipeline intelligence (what competitors are studying, in what phases, with what endpoints), KOL identification (finding principal investigators on relevant trials), and clinical trial comparison (the competitive-analysis skill's 14-parameter pivotal trial matrix). The `/kol-strategy` command uses this integration to identify researchers leading trials in a therapeutic area.

### Medical Portals and HCP Engagement Platforms

While not pre-configured as MCP servers, the CONNECTORS.md file documents the medical education connector category with placeholders for Medscape (reaching 94% of U.S. physicians monthly), DocCheck (leading European HCP platform), Coliquio (DACH physician community), and Doximity (80%+ of U.S. physicians). As MCP servers become available for these platforms, the plugin's channel coverage will extend into the primary digital environments where HCPs consume pharmaceutical information.

## Sample Workflow Scenarios

### Scenario 1: Launch Week for a New Oncology Drug

**Context.** Your company has received FDA approval for a new PD-L1 inhibitor indicated for first-line non-small cell lung cancer (NSCLC) in combination with chemotherapy. Promotional activities can begin immediately.

**Day 1-2: Competitive positioning.**
Run `/competitive-brief` targeting the NSCLC immunotherapy landscape. The competitive-analysis skill generates formulary positioning comparisons against KEYTRUDA (pembrolizumab), OPDIVO (nivolumab), and IMFINZI (durvalumab), including label comparison (approved indications, biomarker requirements, dosing), clinical trial comparison (primary endpoints, hazard ratios, response rates), and pipeline intelligence for upcoming competitor data. Cross-reference against ClinicalTrials.gov for active competitor studies.

**Day 3-5: Content development.**
Run `/draft-content` for the launch toolkit. Generate the primary detail aid (branded sales aid format with 8-part structure), an HCP email series introducing the new indication data, and a patient education brochure. Each piece is drafted with reference annotations, ISI integration, and content classification. Run `/mlr-review` on each piece to simulate pre-submission review and identify issues before formal MLR.

**Day 5-7: KOL activation.**
Run `/kol-strategy` for NSCLC immunotherapy, with "launch support" as the strategic objective. Identify priority KOLs from trial investigators and congress presenters, apply the tiering framework, and develop an engagement plan covering launch advisory boards, speaker program initiation, and MSL deployment. Cross-reference KOL candidates against PubMed publication records and ClinicalTrials.gov investigator roles.

**Day 7-10: Performance baseline.**
Run `/performance-report` to establish baseline metrics using the launch tracker dashboard template. Define targets for NRx growth, prescriber adoption milestones, formulary submission timeline, and HCP engagement reach. Set up SOV tracking against established competitors.

### Scenario 2: Preparing for ASCO Annual Meeting

**Context.** Your company has two accepted abstracts at the American Society of Clinical Oncology (ASCO) Annual Meeting: one oral presentation of pivotal Phase 3 data and one poster of real-world evidence. ASCO is 16 weeks away.

**Week 1: Congress strategy.**
Run `/congress-plan` with ASCO 2026 as the congress, specifying both data presentations, objectives (data dissemination, KOL engagement, competitive intelligence), team size, and budget. The command generates the full 11-section plan: booth design around the pivotal data theme, satellite symposium plan, KOL meeting schedule prioritizing investigators and guideline committee members, competitive intelligence assignments for key competitor presentations, social media content calendar, and the 36-week-to-+2-week timeline (starting at week 16 in this case).

**Week 2-4: KOL engagement.**
Run `/kol-strategy` focused on ASCO-attending KOLs. Identify which Tier 1 and Tier 2 KOLs will attend, schedule 1:1 MSL meetings, plan a post-data advisory board to gather expert feedback on the Phase 3 results, and prepare scientific exchange materials for MSL use during the congress.

**Week 4-8: Content development and MLR review.**
Run `/draft-content` for all congress materials: booth panels, leave-behind materials, digital content for interactive displays, post-congress highlight email, data summary infographics. Run `/mlr-review` on each piece. Submit to formal MLR with sufficient lead time (the campaign-planning skill's MLR timeline benchmarks indicate 4-6 weeks for congress materials).

**Week 8-12: Competitive preparation.**
Run `/competitive-brief` focused on the competitors expected to present at ASCO. Generate competitive intelligence templates for the team to use during the congress. Prepare pre-read materials summarizing the competitive landscape for all attendees.

**Post-congress: Content repurposing and performance.**
Run `/draft-content` to create derivative content from congress presentations: blog posts, webinar scripts, updated competitive briefings. Run `/performance-report` to capture congress engagement metrics (booth traffic, KOL meetings completed, social media impressions, post-congress content engagement).

### Scenario 3: Quarterly MLR Review of Existing Materials

**Context.** Your regulatory affairs team has flagged that the product's label was updated last month with new safety data. All existing promotional materials must be reviewed for continued accuracy and compliance.

**Step 1: Inventory and triage.**
Gather all active promotional materials from Veeva PromoMats (via the Veeva integration). Categorize by content type using the content-creation skill's classification matrix (branded promotional, unbranded, reminder, congress material, social media, patient-facing).

**Step 2: Systematic review.**
Run `/mlr-review` on each material in batch mode. For each piece, the command evaluates whether the ISI is current (it will not be, given the label update), whether safety claims reflect the updated labeling, and whether any existing efficacy claims are affected by the new safety data. Flag materials where the label change creates a fair balance issue (new safety information may require additional prominence).

**Step 3: Revision prioritization.**
Based on the MLR review findings, prioritize revisions by severity (Critical issues first, then Major, then Minor) and by distribution volume (high-reach materials first). Use the content-creation skill to draft updated versions with corrected ISI, revised safety sections, and updated references.

**Step 4: Reporting.**
Run `/performance-report` using a custom report type to document the quarterly review: number of materials reviewed, issues found by severity, materials requiring revision, materials requiring withdrawal, and timeline for corrective actions.

## Workflow Principles

Three principles underpin the plugin's integration into pharma workflows:

**Compliance by design, not by afterthought.** Rather than generating content first and checking compliance later, the plugin embeds regulatory awareness into every step. Content drafted through the content-creation skill arrives with reference annotations, ISI placement, and appropriate classification. Campaign timelines include MLR review cycles from the start. KOL engagement plans include compliance guardrails as a structural element.

**Progressive depth.** The plugin follows a progressive disclosure pattern. Commands provide structured workflows. Skills provide domain knowledge that commands draw upon. Reference documents provide detailed regulatory and procedural guidance that skills access on demand. This means a quick content draft pulls from the skill layer, while a complex MLR review simulation can reach into the full regulatory reference documents for detailed FDA or EMA guidance.

**System integration, not system replacement.** The plugin does not attempt to replace Veeva PromoMats, Veeva CRM, or the formal MLR review process. It augments these systems by providing intelligent assistance at the content creation, planning, and pre-review stages -- the work that happens before materials enter enterprise systems for formal processing.

---

# Part XII: Base vs. Life Sciences Comparison

This chapter provides a comprehensive side-by-side comparison of the base marketing plugin (v1.0.0) and the life sciences marketing plugin (v1.0.0-ls), covering every dimension of difference. Use this chapter to determine which version fits your organization and to understand what changes when migrating from base to life sciences.

## Feature Comparison Table

### Commands

| Command | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|---------|---------------|--------------------------|
| `/draft-content` | Blog posts, social media, email, landing pages, press releases, case studies | Same + detail aids, MOA content, formulary dossiers, patient education (via modified skill) |
| `/campaign-plan` | Generic campaign briefs with objectives, channels, calendar, metrics | Same + pharma campaign types, HCP segmentation, MLR timeline integration (via modified skill) |
| `/brand-review` | Brand voice, style guide, messaging consistency review | Same + fair balance, ISI, claim substantiation, prohibited language checks (via modified skill) |
| `/competitive-brief` | Website, messaging, content strategy, positioning analysis | Same + formulary positioning, label comparison, clinical trial comparison, pipeline intel (via modified skill) |
| `/performance-report` | Email, social, paid, SEO metrics with trend analysis | Same + NRx/TRx, market share, SOV, prescriber adoption, congress and patient metrics (via modified skill) |
| `/seo-audit` | Full site, keyword, content gap, technical, competitor SEO | Identical (unchanged) |
| `/email-sequence` | Onboarding, nurture, re-engagement, launch, and 4 more sequence types | Identical (unchanged) |
| `/mlr-review` | Not available | Simulate medical-legal-regulatory review with 5-step process |
| `/congress-plan` | Not available | 11-section medical congress plan |
| `/kol-strategy` | Not available | 11-section KOL engagement strategy |

### Skills

| Skill | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|-------|---------------|--------------------------|
| brand-voice | Voice documentation, tone adaptation, style enforcement, terminology | + Pharma brand voice rules, ISI placement, claim substantiation, drug naming, prohibited language, audience tone matrix |
| campaign-planning | Campaign frameworks, channel selection, calendars, budgets, KPIs | + 6 pharma campaign types, HCP/patient/payer segmentation, MLR timeline benchmarks, pharma channel guide |
| competitive-analysis | Research methodology, messaging comparison, battlecards, positioning | + Formulary positioning, clinical trial comparison, label comparison, pipeline intelligence, pharma battlecard sections |
| content-creation | 6 content types, writing best practices, SEO, headlines, CTAs | + 5 LS content types, reference annotation format, PI/SmPC integration, content classification for MLR |
| performance-analytics | KPIs by channel, reporting templates, trend analysis, attribution | + 36 pharma KPIs (5 categories), brand performance report, launch tracker, prescriber tracking, SOV |
| regulatory-compliance | Not available | Promotional classification, MLR simulation (30 items), fair balance scoring, off-label compliance |
| medical-affairs-liaison | Not available | MSL engagement, KOL mapping/tiering, advisory boards, congress strategy |

### MCP Servers

| Server | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|--------|---------------|--------------------------|
| Slack | Yes | Yes |
| Canva | Yes | Yes |
| Figma | Yes | Yes |
| HubSpot | Yes | Yes |
| Amplitude | Yes | Yes |
| Notion | Yes | Yes |
| Ahrefs | Yes | Yes |
| Similarweb | Yes | Yes |
| Klaviyo | Yes | Yes |
| PubMed (NCBI) | No | Yes |
| ClinicalTrials.gov | No | Yes |
| OpenFDA | No | Yes |
| Veeva | No | Yes |
| **Total** | **9** | **13** |

### Connector Categories

| Category | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|----------|---------------|--------------------------|
| Chat | Yes | Yes |
| Design | Yes | Yes |
| Marketing automation | Yes | Yes |
| Product analytics | Yes | Yes |
| Knowledge base | Yes | Yes |
| SEO | Yes | Yes |
| Email marketing | Yes | Yes |
| Biomedical literature | No | Yes |
| Clinical trials data | No | Yes |
| Drug safety and labeling | No | Yes |
| CRM (life sciences) | No | Yes |
| MLR review platform | No | Yes (placeholder) |
| Prescribing data | No | Yes (placeholder) |
| Formulary data | No | Yes (placeholder) |
| Medical education | No | Yes (placeholder) |
| Competitive intelligence | No | Yes (placeholder) |
| **Total** | **7** | **16** |

### Reference Documents

| Document | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|----------|---------------|--------------------------|
| FDA Promotional Rules | No | Yes |
| EMA Requirements | No | Yes |
| KOL Tier Framework | No | Yes |
| Congress Planning Guide | No | Yes |
| **Total** | **0** | **4** |

### Compliance Features

| Feature | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|---------|---------------|--------------------------|
| Generic legal/compliance flags in brand review | Yes | Yes |
| Promotional material classification matrix | No | Yes (7 types) |
| MLR review simulation | No | Yes (30 checklist items) |
| Fair balance scoring | No | Yes (5 dimensions, 1-5 scale) |
| Off-label detection | No | Yes (7 red flags) |
| Claim substantiation framework | No | Yes (5 claim types) |
| ISI placement requirements | No | Yes (7 content formats) |
| Drug naming conventions | No | Yes (4 contexts) |
| Prohibited language enforcement | No | Yes (6 terms) |
| Reference annotation format | No | Yes (superscript notation) |
| Content classification for MLR routing | No | Yes (8 types) |

### Audience Handling

| Capability | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|-----------|---------------|--------------------------|
| Marketing personas | Yes | Yes |
| HCP segmentation (7 dimensions) | No | Yes |
| Patient segmentation (6 dimensions) | No | Yes |
| Payer segmentation (4 dimensions) | No | Yes |
| KOL tiering (7 scoring dimensions) | No | Yes |
| Audience tone adaptation (6 LS audiences) | No | Yes |

### KPIs and Measurement

| KPI Category | Base (v1.0.0) | Life Sciences (v1.0.0-ls) |
|-------------|---------------|--------------------------|
| Email/social/paid/SEO metrics | Yes | Yes |
| Commercial pharma KPIs (NRx, TRx, market share, SOV) | No | Yes (10 metrics) |
| HCP engagement KPIs | No | Yes (7 metrics) |
| Payer/market access KPIs | No | Yes (6 metrics) |
| Congress engagement KPIs | No | Yes (7 metrics) |
| Patient engagement KPIs | No | Yes (6 metrics) |
| Prescriber adoption tracking | No | Yes |
| Share of voice analysis | No | Yes |
| Launch tracker dashboard | No | Yes |

## When to Use Each Version

### Use the base marketing plugin (v1.0.0) if:

- **You are a general marketing team** at a technology, consumer products, retail, media, or professional services company.
- **Your industry is not regulated** by FDA, EMA, or equivalent pharmaceutical regulatory authorities.
- **Your content does not require MLR review** or formal regulatory compliance sign-off before publication.
- **Your audience is consumers or business buyers**, not healthcare professionals segmented by specialty and prescribing behavior.
- **Your KPIs are standard marketing metrics**: conversion rates, engagement rates, traffic, leads, revenue attribution.
- **You do not need** clinical trial data, biomedical literature search, drug labeling databases, or pharmaceutical CRM integration.

The base plugin is a complete, sophisticated marketing toolkit. It covers content creation, campaign planning, brand management, competitive analysis, performance reporting, SEO auditing, and email sequence design. For non-regulated industries, it provides everything needed without the additional complexity of pharmaceutical compliance.

### Use the life sciences plugin (v1.0.0-ls) if:

- **You are a pharmaceutical company** -- whether Big Pharma, specialty pharma, or generic manufacturer -- marketing prescription drugs or biologics.
- **You are a biotechnology company** developing therapies that will require (or already have) FDA/EMA approval and promotional marketing.
- **You are a medical device or diagnostics company** whose promotional materials require regulatory compliance review.
- **You are a contract research organization (CRO)** or medical communications agency serving pharma/biotech clients.
- **Your content undergoes MLR review** before distribution to healthcare professionals or patients.
- **Your marketing targets HCPs** segmented by specialty, prescribing behavior, and influence tier.
- **Your KPIs include** prescriptions (NRx/TRx), market share, formulary wins, share of voice, and prescriber adoption.
- **You plan and execute** medical congress strategies, KOL engagement programs, and disease awareness campaigns.

### Use both versions if:

- **You are a large diversified organization** with both consumer health and prescription pharmaceutical divisions. The consumer health division uses the base plugin for OTC product marketing; the prescription pharmaceutical division uses the life sciences plugin. Each team gets the appropriate level of regulatory awareness without unnecessary complexity.
- **You are a pharma company with a consumer-facing digital team** that manages corporate communications, recruitment marketing, or non-product websites alongside the promotional marketing team. The corporate team uses the base plugin; the promotional team uses the life sciences version.

## Migration Guide: Base to Life Sciences

### What changes

Moving from the base marketing plugin to the life sciences version involves the following changes:

1. **Plugin identity.** The plugin name changes from `marketing` to `marketing-life-sciences`, and the version changes from `1.0.0` to `1.0.0-ls`.

2. **Three new commands become available.** `/mlr-review`, `/congress-plan`, and `/kol-strategy` are added to the command palette. No existing commands are removed or modified.

3. **Five existing skills gain life sciences content.** The brand-voice, campaign-planning, competitive-analysis, content-creation, and performance-analytics skills each receive appended sections with pharma-specific frameworks, templates, and guidance. The base content of each skill remains unchanged -- the life sciences additions are purely additive.

4. **Two new skills are added.** The regulatory-compliance and medical-affairs-liaison skills, along with their four reference documents, provide entirely new capabilities.

5. **Four new MCP servers are configured.** PubMed, ClinicalTrials.gov, OpenFDA, and Veeva are added to the `.mcp.json` file. PubMed requires an NCBI API key. Veeva requires a Veeva CRM license. ClinicalTrials.gov and OpenFDA are public APIs requiring no authentication.

6. **Nine new connector categories are documented.** The CONNECTORS.md file adds life sciences connector categories, four with pre-configured servers and five as placeholder categories.

### What stays the same

- **All 7 base commands** are preserved byte-for-byte. `/draft-content`, `/campaign-plan`, `/brand-review`, `/competitive-brief`, `/performance-report`, `/seo-audit`, and `/email-sequence` work exactly as they do in the base plugin.
- **All 9 base MCP servers** are preserved with identical configuration. Slack, Canva, Figma, HubSpot, Amplitude, Notion, Ahrefs, Similarweb, and Klaviyo continue to work as before.
- **All 7 base connector categories** are preserved unchanged.
- **The base content of all 5 existing skills** is preserved verbatim. Everything above the `<!-- Life Sciences Addition -->` marker in each skill file is identical to the base version.

### Configuration that carries over

- **Brand voice settings** (brand personality, tone, messaging pillars) -- these continue to function and should be supplemented with pharma-specific settings (approved indications, ISI text, claims library).
- **MCP server authentication** -- all existing server connections (Slack, HubSpot, Amplitude, etc.) carry over without reconfiguration.
- **Knowledge base content** (Notion documents, brand guidelines, competitive files) -- all existing references remain valid and accessible.

### Additional configuration for life sciences

After migration, configure these life sciences-specific settings:

- **Approved indication statements** for each product (must match FDA-approved labeling exactly).
- **ISI text** (Important Safety Information) for each product, maintained current with the latest PI/SmPC.
- **Approved claims library** with reference annotations linking each claim to its substantiating evidence.
- **KOL target lists and tier assignments** for each therapeutic area.
- **Congress calendar and priorities** for the planning year.
- **NCBI API key** for PubMed integration (free registration at NCBI).
- **Veeva CRM credentials** for CRM integration (requires existing Veeva license).

### Migration steps

1. Install the life sciences plugin: `claude plugins add knowledge-work-plugins/marketing-life-sciences`
2. Remove the base plugin if both are installed (the life sciences version is a superset): `claude plugins remove knowledge-work-plugins/marketing`
3. Configure the NCBI API key environment variable for PubMed access.
4. Configure Veeva CRM credentials if you have a Veeva license.
5. Add product-specific settings (approved indications, ISI, claims library) to your local configuration.
6. Test by running `/mlr-review` on an existing promotional piece to verify the regulatory-compliance skill is active.
7. Test by running `/kol-strategy` for your primary therapeutic area to verify the medical-affairs-liaison skill and ClinicalTrials.gov integration are working.

The migration is additive -- it extends capabilities without disrupting existing workflows. Teams that have been using the base plugin for general marketing tasks will find that all existing commands and skills continue to function identically, with the life sciences additions activating only when pharma-specific queries or content types are involved.

## Architectural Philosophy

The relationship between the base and life sciences plugins reflects a deliberate architectural choice. The base plugin was not modified -- it was extended. Commands remain generic; domain specialization lives in the skills layer. This means that when a user runs `/draft-content` and specifies "branded sales aid" as the content type, the content-creation skill's life sciences additions activate automatically, producing a compliant pharmaceutical detail aid with reference annotations and ISI. But when the same user runs `/draft-content` and specifies "blog post," the base content-creation skill handles it exactly as it would in the base plugin.

This design ensures that the life sciences plugin is not a walled garden of pharmaceutical-only functionality. It is a superset that serves the full spectrum of marketing needs -- from a social media post to a congress plan, from an email sequence to an MLR review simulation -- with the regulatory and scientific precision that life sciences marketing demands.
