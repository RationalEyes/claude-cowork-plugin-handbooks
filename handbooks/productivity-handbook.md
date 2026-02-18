# The Productivity Plugin Handbook

## Your Workplace Memory and Task Command Center

**Plugin Version:** 1.0.0  
**Author:** Anthropic  
**For:** Knowledge workers, team leads, operations managers, and anyone drowning in shorthand

---

## Part I: What This Plugin Does and Why You Need It

### The Problem This Solves

You say "ask todd to do the PSR for oracle" and Claude responds with "Who's Todd? What's PSR? Which Oracle?"

Your workplace runs on shorthand. Nicknames. Acronyms. Project codenames. Internal terminology that makes perfect sense to you but is meaningless to an AI that doesn't know your world.

The productivity plugin fixes this. It teaches Claude to speak your language.

### What You Get

This plugin gives Claude three capabilities that transform it from a helpful chatbot into a true workplace collaborator:

**1. Workplace Memory**

A two-tier memory system that decodes your internal language:

```
You: "ask todd to do the PSR for oracle"

Claude (with memory):
"Ask Todd Martinez (Finance lead) to prepare the Pipeline Status Report 
for the Oracle Systems deal ($2.3M, closing Q2)"
```

No clarifying questions. No round trips. Claude just knows.

**2. Task Management**

A simple, powerful task system that lives in plain Markdown:

- Add tasks naturally in conversation
- Claude tracks, triages, and syncs with external tools
- Visual dashboard with drag-and-drop task boards
- Everything stays in sync: edit from chat, dashboard, or file

**3. Unified Dashboard**

A local HTML file that shows you everything:

- Kanban-style task board with live updates
- Complete memory browser (people, projects, terminology)
- Edit directly in the UI or via the file - they sync automatically
- No servers, no cloud storage, no privacy concerns

### Who This Is For

**Knowledge workers** who juggle multiple projects, communicate with dozens of people, and need to stay on top of commitments without drowning in tools.

**Team leads** who coordinate across teams, translate between stakeholders, and maintain context for their team's work.

**Operations managers** who keep many plates spinning, need to remember who owns what, and want a system that works the way their brain does.

If you use nicknames, acronyms, or project codenames in your daily work, this plugin is for you.

---

## Part II: Installation and First-Time Setup

### Installing the Plugin

**Cowork (recommended):** Open **Plugin Settings** in the Cowork desktop app, find **Productivity**, and click **Install**. The plugin activates immediately — no CLI required.

**Claude Code CLI (alternative):** If you are using Claude Code in the terminal rather than Cowork, install via:

```bash
claude plugins add knowledge-work-plugins/productivity
```

> **Note:** All standard Cowork plugins, including Productivity, are available from Plugin Settings with a single click. The CLI command above is only needed for Claude Code terminal users.

### First Run: The Bootstrap Process

The first time you use the plugin, run the start command:

```bash
/productivity:start
```

This initializes three things:

1. **TASKS.md** - Your task list (if it doesn't already exist)
2. **CLAUDE.md** - Working memory (hot cache for frequent lookups)
3. **memory/** - Deep storage directory (complete knowledge base)

If these already exist, the start command simply opens your dashboard and you're ready to go.

### The Memory Bootstrap Interview

If this is truly your first run, Claude needs to learn your workplace language. The most efficient way is to scan your existing task list.

**Claude will ask:**

```
Where do you keep your todos or task list? This could be:
- A local file (e.g., TASKS.md, todo.txt)
- An app (e.g., Asana, Linear, Jira, Notion, Todoist)
- A notes file

I'll use your tasks to learn your workplace shorthand.
```

Point Claude to your task source. It will analyze each task item, identify potential shorthand, and ask you about it:

```
Task: "Send PSR to Todd re: Phoenix blockers"

I see some terms I want to make sure I understand:

1. PSR - What does this stand for?
2. Todd - Who is Todd? (full name, role)
3. Phoenix - Is this a project codename? What's it about?
```

You answer each question once. Claude remembers forever.

### Optional: Comprehensive Scan

After the task list decoding, Claude offers to do a deeper scan:

```
Do you want me to do a comprehensive scan of your messages, emails, 
and documents? This takes longer but builds much richer context about 
the people, projects, and terms in your work.

Or we can stick with what we have and add context later.
```

**If you choose comprehensive scan**, Claude pulls from:

- Chat (Slack) - recent messages, channels, DMs
- Email (Microsoft 365) - sent messages, recipients
- Documents (Notion) - recent docs, collaborators
- Calendar (Microsoft 365) - meetings, attendees

It builds a braindump of people, projects, and terms, then presents findings grouped by confidence level:

- Ready to add (high confidence) - offers to add directly
- Needs clarification - asks you
- Low frequency / unclear - notes for later

### What Gets Created

After bootstrap, you have:

**TASKS.md** (in your working directory):
```markdown
# Tasks

## Active
- [ ] **Send PSR to Todd** - re: Phoenix blockers, due Friday

## Waiting On

## Someday

## Done
```

**CLAUDE.md** (working memory, ~50-80 lines):
```markdown
# Memory

## Me
Alex Chen, Product Manager on Platform team.

## People
| Who | Role |
|-----|------|
| **Todd** | Todd Martinez, Finance lead |
| **Sarah** | Sarah Wilson, Engineering (Platform) |

## Terms
| Term | Meaning |
|------|---------|
| PSR | Pipeline Status Report |
| standup | Daily 9am sync |

## Projects
| Name | What |
|------|------|
| **Phoenix** | DB migration, Q2 launch |
```

**memory/** directory:
```
memory/
  glossary.md          # Complete decoder ring
  people/
    todd-martinez.md   # Full profile
    sarah-wilson.md
  projects/
    phoenix.md         # Project details
  context/
    company.md         # Teams, tools, processes
```

**dashboard.html** (in your working directory) - Ready to open in your browser.

---

## Part III: Core Workflows

### Daily Use Pattern

The plugin is designed for three daily touchpoints:

**Morning:** Check what's on your plate
```
You: what's on my plate today?

Claude: [Reads TASKS.md, summarizes Active + Waiting On sections]

Active (5 tasks):
- Send PSR to Todd (due today)
- Review API spec from Sarah
- Sync with Greg on Phoenix timeline
- Draft Q2 roadmap
- Follow up with Platform team on blockers

Waiting On (2 tasks):
- Budget approval from Finance (since Jan 12)
- Design mockups from Brand team (since Jan 15)
```

**Throughout the day:** Add tasks naturally
```
You: I need to follow up on the Phoenix blockers with Sarah
     and send the updated timeline to Greg by Friday

Claude: [Adds both tasks to TASKS.md Active section]
        Added:
        - Follow up on Phoenix blockers with Sarah
        - Send updated timeline to Greg - due Friday
```

**End of day / weekly:** Update and triage
```
You: /productivity:update

Claude: [Syncs from external tools, triages stale items, fills memory gaps]

Update complete:
- Tasks: +2 from Linear, 1 completed, 2 triaged
- Memory: 1 gap filled (learned about Jamie Park, Design Lead)
- All tasks decoded ✓
```

### Task Management Workflows

#### Adding Tasks

Tasks can be added three ways:

**1. Natural conversation:**
```
You: remind me to send the report to todd by friday

Claude: [Adds to Active section in TASKS.md]
```

**2. From meeting summaries:**
```
You: [shares meeting notes]

Claude: "I noticed 3 action items:
        - You committed to send mockups to Sarah
        - Follow up with Greg on budget
        - Review the API spec by EOW
        
        Should I add these to your task list?"
```

**3. Via the dashboard:** Click "+ Add task" in any column

#### Completing Tasks

**In conversation:**
```
You: done with the PSR

Claude: [Finds "Send PSR to Todd", marks complete, moves to Done section]
```

**In the dashboard:** Click the checkbox

**Directly in TASKS.md:** Change `[ ]` to `[x]`, add strikethrough, add date

All three methods stay in sync automatically.

#### Organizing Tasks

**Four default sections:**

- **Active** - Working on now
- **Waiting On** - Blocked on others
- **Someday** - Backlog / future
- **Done** - Completed (keep ~1 week)

**Add custom sections** by editing TASKS.md or via the dashboard. Everything just works.

**Move tasks between sections** by dragging in board view or by editing the file.

#### Task Sync from External Tools

The `/productivity:update` command syncs from connected project trackers:

- Asana
- Linear  
- Atlassian (Jira)
- monday.com
- ClickUp
- GitHub Issues (if in a repo)

**Sync behavior:**

| External task | TASKS.md match? | Action |
|---------------|-----------------|--------|
| Found, not in TASKS.md | No match | Offer to add |
| Found, already in TASKS.md | Match by title (fuzzy) | Skip |
| In TASKS.md, not external | No match | Flag as potentially stale |
| Completed externally | In Active section | Offer to mark done |

Claude presents the diff and lets you decide what to sync.

#### Stale Task Triage

`/productivity:update` flags items that might need attention:

- Tasks with due dates in the past
- Tasks in Active for 30+ days
- Tasks with no context (no person, no project)

Claude presents each for triage: Mark done? Reschedule? Move to Someday?

### Memory Management Workflows

#### How Memory Works: The Two-Tier System

**Tier 1: CLAUDE.md (Hot Cache)**

- Top ~30 people you interact with most
- ~30 most common acronyms/terms
- Active projects (5-15)
- Your preferences
- Goal: Cover 90% of daily decoding needs
- Size: ~50-80 lines, always loaded

**Tier 2: memory/ (Deep Storage)**

- Complete decoder ring - everyone, every term
- Rich detail files for people, projects, context
- Searched when something isn't in CLAUDE.md
- Can grow indefinitely

**Lookup flow:**

```
User: "ask todd about the PSR for phoenix"

1. Check CLAUDE.md (hot cache)
   → Todd? ✓ Todd Martinez, Finance
   → PSR? ✓ Pipeline Status Report
   → Phoenix? ✓ DB migration project

2. If not found → search memory/glossary.md
   → Full glossary has everyone/everything

3. If still not found → ask user
   → "What does X mean? I'll remember it."
```

This design keeps CLAUDE.md lean while supporting unlimited scale.

#### Adding Memory

**Explicitly:**
```
You: remember that PSR stands for Pipeline Status Report

Claude: [Adds to memory/glossary.md]
        [Adds to CLAUDE.md Terms if frequently used]
```

**From context:**
```
You: I'm meeting with Sarah Wilson tomorrow, she's the new 
     Engineering lead for Platform

Claude: [Creates memory/people/sarah-wilson.md]
        [Adds to CLAUDE.md Key People]
        
        Got it - Sarah Wilson, Engineering lead (Platform).
        I'll remember that.
```

**During comprehensive update:**
```
You: /productivity:update --comprehensive

Claude: [Scans chat, email, calendar, docs]
        
        New people mentioned frequently:
        - Jamie Park (12 mentions) - appears to be Design Lead
        - Alex K (8 mentions) - DMs about API work
        
        Should I add these to memory?
```

#### Memory Structure

**memory/glossary.md** - The complete decoder ring:

```markdown
# Glossary

## Acronyms
| Term | Meaning | Context |
|------|---------|---------|
| PSR | Pipeline Status Report | Weekly sales doc |
| OKR | Objectives & Key Results | Quarterly planning |
| P0/P1/P2 | Priority levels | P0 = drop everything |

## Nicknames → Full Names
| Nickname | Person |
|----------|--------|
| Todd | Todd Martinez (Finance) |
| T | Also Todd Martinez |

## Project Codenames
| Codename | Project |
|----------|---------|
| Phoenix | Database migration |
| Horizon | New mobile app |
```

**memory/people/{name}.md** - Individual profiles:

```markdown
# Todd Martinez

**Also known as:** Todd, T
**Role:** Finance Lead
**Team:** Finance
**Reports to:** CFO (Michael Chen)

## Communication
- Prefers Slack DM
- Quick responses, very direct
- Best time: mornings

## Context
- Handles all PSRs and financial reporting
- Key contact for deal approvals over $500k
- Works closely with Sales on forecasting
```

**memory/projects/{name}.md** - Project details:

```markdown
# Project Phoenix

**Codename:** Phoenix
**Also called:** "the migration"
**Status:** Active, launching Q2

## What It Is
Database migration from legacy Oracle to PostgreSQL.

## Key People
- Sarah - tech lead
- Todd - budget owner
- Greg - stakeholder (sales impact)

## Context
$1.2M budget, 6-month timeline. Critical path for Horizon project.
```

#### Promotion and Demotion

**Promote to CLAUDE.md when:**
- You use a term/person frequently
- It's part of active work
- It comes up in daily conversation

**Demote to memory/ only when:**
- Project completed
- Person no longer frequent contact
- Term rarely used

This keeps CLAUDE.md fresh and relevant - your working memory, not an archive.

#### Memory Enrichment

Claude continuously enriches memory from your tasks:

- Links from tasks → add to project/people files
- Status changes ("launch done") → update project status
- Relationships ("Todd's sign-off on Maya's proposal") → cross-reference people
- Deadlines → add to project files

This happens automatically during `/productivity:update`.

### Dashboard Workflows

The dashboard is a local HTML file that provides visual task management and memory browsing.

**Opening the dashboard:**

1. Run `/productivity:start` (opens automatically)
2. Or manually open `dashboard.html` from your working directory

**Features:**

**Task Board View:**
- Kanban-style columns for each section
- Drag and drop to reorder or move between sections
- Click to edit task title, notes, subtasks
- Add tasks via "+ Add task" buttons
- Toggle checkboxes inline

**Task List View:**
- Compact linear view of all tasks
- Quick add at top
- Edit inline
- Drag to reorder

**Memory Browser:**
- Tabs for different memory categories (People, Projects, Terms, Files)
- Search across all memory
- Click to expand and view full details
- Edit memory files directly

**Live Sync:**
- Changes in dashboard → immediately saved to files
- Changes in files → dashboard detects and reloads
- Changes via Claude → reflected everywhere

**No Network Required:**
- Runs entirely locally
- No cloud storage
- No privacy concerns
- Works offline

---

## Part IV: Commands Reference

### /productivity:start

**What it does:** Initialize the productivity system and open the dashboard.

**When to use:** First time setup, or anytime to open the dashboard.

**What it creates:**
- TASKS.md (if doesn't exist)
- CLAUDE.md and memory/ (if first run)
- dashboard.html (if doesn't exist)

**First run behavior:** Triggers memory bootstrap interview (see Part II).

**Subsequent runs:** Simply opens the dashboard and reports status.

**Example:**
```
You: /productivity:start

Claude: Dashboard ready. Your tasks and memory are both loaded.
        - 5 active tasks, 2 waiting on others
        - Memory: 12 people, 15 terms, 3 projects
        
        Use /productivity:update to sync and triage.
```

### /productivity:update

**What it does:** Sync tasks and refresh memory from current activity.

**Default mode:**
1. Load current TASKS.md and memory
2. Sync tasks from external sources (Linear, Asana, GitHub, etc.)
3. Triage stale items (overdue, 30+ days active, missing context)
4. Decode all tasks for memory gaps
5. Fill gaps by asking user
6. Capture enrichment from task context

**When to use:** 
- Daily or weekly maintenance
- After completing several tasks
- When you notice tasks getting stale

**Example:**
```
You: /productivity:update

Claude: Checking external sources...
        
        Found 2 new tasks in Linear:
        - "Implement auth flow" (assigned yesterday)
        - "Fix mobile layout bug" (assigned today)
        
        Add to TASKS.md? [both added]
        
        Stale items:
        - "Review budget proposal" - due 3 days ago
          → Mark done? Reschedule?
        
        Memory gaps:
        - "Starlight" mentioned in tasks but not in memory
          → What's Starlight? [user explains, adds to projects]
        
        Update complete:
        - Tasks: +2 from Linear, 1 completed, 1 triaged
        - Memory: 1 project added
        - All tasks decoded ✓
```

### /productivity:update --comprehensive

**What it does:** Everything in default mode, PLUS deep scan of communication and documents.

**Additional steps:**
1. Scan chat (Slack) - recent messages, active channels
2. Scan email (Microsoft 365) - sent messages, recipients
3. Scan documents (Notion) - recent docs, collaborators
4. Scan calendar (Microsoft 365) - recent and upcoming events
5. Flag potential missing tasks
6. Suggest new memories (people, projects, terms)

**When to use:**
- Weekly deep sync
- After returning from vacation
- When starting a new project
- When you feel like Claude is missing context

**Example:**
```
You: /productivity:update --comprehensive

Claude: Running comprehensive scan...
        
        Possible Missing Tasks:
        
        From chat (Jan 18):
        "I'll send the updated mockups by Friday"
        → Add to TASKS.md?
        
        From meeting "Phoenix Standup" (Jan 17):
        Recurring meeting but no Phoenix tasks active
        → Anything needed here?
        
        New People (not in memory):
        - Jamie Park (12 mentions) - appears in design discussions
        - Alex K (8 mentions) - DMs about API work
        
        New Projects:
        - "Starlight" (15 mentions) - planning docs, product discussions
        
        Suggested Cleanup:
        - "Horizon project" - No mentions in 30 days. Mark completed?
        
        Update complete:
        - Tasks: 2 added, 1 archived
        - Memory: 2 people added, 1 project added, 1 archived
```

---

## Part V: Skills Reference

### task-management

**Triggers:** User asks about tasks, wants to add/complete tasks, needs help tracking commitments.

**What it provides:**

- Task file format specifications
- Interaction patterns for reading/adding/completing tasks
- Conventions for task metadata (who it's for, due dates, waiting since)
- Task extraction logic from conversations

**Key capabilities:**

**Reading tasks:**
- Summarizes Active and Waiting On sections
- Highlights overdue or urgent items
- Reports on context (who, what, when)

**Adding tasks:**
- Extracts tasks from natural language
- Formats with proper syntax
- Includes context (person, due date)
- Asks before adding (no auto-add)

**Completing tasks:**
- Finds tasks by fuzzy matching
- Marks complete with date
- Moves to Done section

**Task extraction:**
- Identifies commitments from meeting notes
- Flags "I'll..." statements as potential tasks
- Offers to add without auto-adding

**Dashboard integration:**
- Checks for dashboard.html existence
- Copies from plugin if missing
- Keeps file and dashboard in sync

### memory-management

**Triggers:** Shorthand, nicknames, acronyms, or internal terminology in user requests. Also when user says "remember this" or asks "who is X" / "what does X mean".

**What it provides:**

- Two-tier memory architecture (CLAUDE.md + memory/)
- Lookup flow and decoding logic
- Memory file formats and structures
- Promotion/demotion rules
- Memory enrichment patterns

**Key capabilities:**

**Decoding shorthand:**
1. Check CLAUDE.md (hot cache)
2. Search memory/glossary.md (full glossary)
3. Search memory/people/, projects/ (rich detail)
4. Ask user if unknown

**Adding memory:**
- Glossary items → memory/glossary.md (+ CLAUDE.md if frequent)
- People → memory/people/{name}.md (+ CLAUDE.md if important)
- Projects → memory/projects/{name}.md (+ CLAUDE.md if active)
- Preferences → CLAUDE.md Preferences section

**Capturing nicknames:**
- Always asks for "also known as"
- Critical for decoding casual references
- Stored in glossary and individual files

**Memory maintenance:**
- Promotes frequently-used items to CLAUDE.md
- Demotes stale items to memory/ only
- Keeps CLAUDE.md under ~100 lines (the "hot 30" rule)

**Progressive disclosure:**
- Loads CLAUDE.md for quick parsing
- Dives into memory/ for execution details
- Example: CLAUDE.md says "Todd = Todd Martinez, Finance"
- memory/people/todd-martinez.md says "prefers Slack, direct, mornings"

---

## Part VI: Tool Connections and Data Sources

### Connected Services

The plugin connects to eight categories of tools via MCP (Model Context Protocol):

| Category | Included Servers | Purpose |
|----------|-----------------|---------|
| Chat | Slack | Message scanning, team context |
| Email | Microsoft 365 | Action item discovery, recipient tracking |
| Calendar | Microsoft 365 | Meeting extraction, attendee context |
| Knowledge base | Notion | Reference documents, wiki content |
| Project tracker | Asana, Linear, Atlassian (Jira), monday.com, ClickUp | Task syncing, assignment tracking |
| Office suite | Microsoft 365 | Document collaboration |

### How Tool Connections Work

**Pre-configured in .mcp.json:**

The plugin includes MCP server definitions for all services. When Claude needs to access a service, it prompts you to authenticate through the standard OAuth flow (the "Sign in with..." experience).

**After first authentication:** The connection persists. No need to re-authenticate each session.

**What each connection provides:**

**Chat (Slack):**
- Search recent messages
- Read channel history
- Extract mentions of people, projects, terms
- Identify commitments ("I'll send that over")

**Email (Microsoft 365):**
- Search sent messages
- Extract recipients (builds people context)
- Find action items ("I'll review by Friday")
- Track communication patterns

**Calendar (Microsoft 365):**
- List recent and upcoming events
- Extract attendees (builds people context)
- Identify recurring meetings (ongoing projects)
- Find gaps in memory (meeting about Phoenix but no Phoenix tasks)

**Knowledge base (Notion):**
- Search documents
- Find collaborators
- Extract project context
- Reference documentation

**Project tracker (Asana, Linear, Jira, monday, ClickUp):**
- Fetch assigned tasks
- Sync task status
- Import new assignments
- Mark tasks complete

**Office suite (Microsoft 365):**
- Access documents
- Track collaborators
- Find project references

### Using the Plugin Without Connections

The plugin works perfectly well without any external connections. You manage tasks and memory manually:

**Task management:**
- Add tasks via conversation or dashboard
- No automatic sync from external tools
- Manual triage and completion

**Memory management:**
- Bootstrap from your local task file
- Add memories as you encounter them
- No automatic scanning of messages/email/docs

**This is totally valid.** Many users prefer the simplicity and privacy of a local-only system.

### Adding Alternative Tools

The plugin uses tool-agnostic placeholders in its instructions:

- `~~chat` = any chat tool (Slack, Teams, Discord)
- `~~project tracker` = any project tool (Asana, Linear, Jira, etc.)
- `~~knowledge base` = any wiki/docs tool (Notion, Confluence, Guru)

If you use a different tool in a category, you can configure it by adding the MCP server to your Cowork settings. The plugin adapts automatically.

See CONNECTORS.md in the plugin directory for the complete list of categories and alternatives.

---

## Part VII: Advanced Techniques and Customization

### Memory Best Practices

#### The "Hot 30" Rule

CLAUDE.md should contain approximately:
- 30 people (most frequent contacts)
- 30 terms (most common acronyms/terminology)
- 5-15 projects (currently active)

This covers ~90% of daily decoding needs while keeping the file scannable.

#### Nickname Discipline

Always capture how people are actually referred to:

```markdown
## People
| Who | Role |
|-----|------|
| **Todd** | Todd Martinez, Finance lead |
| **T** | Todd Martinez (alternate) |
| **Sarah** | Sarah Wilson, Engineering (Platform) |
| **SW** | Sarah Wilson (in emails) |
```

In memory/glossary.md:
```markdown
## Nicknames → Full Names
| Nickname | Person |
|----------|--------|
| Todd | Todd Martinez (Finance) |
| T | Todd Martinez |
| Sarah | Sarah Wilson (Engineering) |
| SW | Sarah Wilson |
```

This is critical. If someone says "T needs the PSR," Claude must decode it.

#### Contextual Disambiguation

Some terms mean different things in different contexts. Capture that:

```markdown
## Terms
| Term | Meaning | Context |
|------|---------|---------|
| Oracle | Oracle Systems (client) | When discussing deals/sales |
| Oracle | Oracle Database | When discussing tech stack |
```

#### Project Evolution Tracking

When projects change status, update memory but don't delete history:

**memory/projects/phoenix.md:**
```markdown
# Project Phoenix

**Status:** COMPLETED (launched Q2 2025)
**Also called:** "the migration"

## What It Was
Database migration from legacy Oracle to PostgreSQL.
Launched April 2025, transitioned to maintenance mode.

## Key People
- Sarah Wilson - tech lead
- Todd Martinez - budget owner

## Outcomes
- Completed on time, under budget
- 40% performance improvement
- Now in maintenance (Platform team owns)
```

Demote from CLAUDE.md but keep the full history in memory/projects/.

### Task Management Patterns

#### Task Templates

For recurring task types, create templates:

**Weekly review task:**
```markdown
- [ ] **Weekly review** - triage active tasks, check waiting ons, plan next week
```

**Project standup prep:**
```markdown
- [ ] **Phoenix standup prep** - review blockers, update status doc, prep questions
  - Check Linear for new issues
  - Review recent Slack discussions
  - Update status in Notion doc
```

#### Waiting On Tracking

When tasks are blocked, move to Waiting On with context:

```markdown
## Waiting On
- [ ] **Budget approval for Phoenix** - from Todd, requested Jan 12
- [ ] **Design mockups for landing page** - from Brand team, needed by Jan 20
```

During `/productivity:update`, Claude flags items that have been waiting too long.

#### Someday Section Strategy

Use Someday for:
- Ideas you might pursue later
- Tasks dependent on completed work
- Low-priority backlog

Review monthly and either:
- Promote to Active (if priority increased)
- Delete (if no longer relevant)
- Keep in Someday (still valid, still low priority)

### Dashboard Customization

The dashboard is a single HTML file. You can customize it:

**Color scheme:** Edit CSS variables at the top:
```css
:root {
  --accent: #D97757;           /* Change to your brand color */
  --bg-primary: #faf9f5;       /* Background color */
  --text-primary: #141413;     /* Text color */
}
```

**Section order:** Drag column headers in board view to reorder

**Custom sections:** Add new sections by editing TASKS.md or creating them in the dashboard

**Font:** Change the font-family in CSS

The dashboard auto-saves all changes back to TASKS.md. No need to manually sync.

### Memory Migration Strategy

If you're joining an existing team or project with established terminology:

**1. Gather existing glossaries:**
- Company wiki pages about acronyms
- Team onboarding docs
- Existing terminology guides

**2. Import in bulk:**

Create memory/glossary.md with all terms upfront:

```markdown
# Glossary

## Acronyms
[paste entire company acronym list]

## Project Codenames
[paste all active project codes]
```

**3. Refine through use:**

As you use Claude, promote frequently-used items to CLAUDE.md. Demote rarely-used ones.

**4. Enrich organically:**

As you encounter people and projects, add context files in memory/people/ and memory/projects/.

### Comprehensive Update Strategies

**Daily light updates:**
```bash
/productivity:update
```
Fast, syncs tasks, triages obvious staleness.

**Weekly deep scans:**
```bash
/productivity:update --comprehensive
```
Scans all communication, finds gaps, suggests additions.

**Monthly memory audits:**

Manually review:
- CLAUDE.md - demote stale items
- memory/projects/ - archive completed projects
- memory/people/ - remove people who left the company
- memory/glossary.md - remove deprecated terms

### Privacy and Data Management

**Everything is local:**
- Tasks stored in TASKS.md in your working directory
- Memory stored in CLAUDE.md and memory/ in your working directory
- Dashboard is a local HTML file
- No cloud storage, no external servers (except MCP connections you choose)

**What gets sent to external services:**
- Only during `/productivity:update --comprehensive`
- Only search queries to connected services (Slack, email, etc.)
- You see exactly what gets scanned and approve what gets added

**Disconnecting services:**

Remove MCP connections from Cowork settings anytime. The plugin continues to work with manual task/memory management.

**Moving your workspace:**

Your entire productivity system is contained in:
- TASKS.md
- CLAUDE.md
- memory/ directory
- dashboard.html

Copy these four items to a new location and everything works identically.

---

## Appendix A: File Format Specifications

### TASKS.md Format

```markdown
# Tasks

## Active
- [ ] **Task title** - context, for whom, due date
  - [ ] Optional subtask
  - [ ] Another subtask

## Waiting On
- [ ] **Task waiting on someone else** - from [person], since [date]

## Someday
- [ ] **Future task** - not urgent

## Done
- [x] ~~Completed task~~ - (Jan 15, 2025)
```

**Rules:**
- Sections are H2 headers (`## Section Name`)
- Tasks are unordered list items with checkboxes (`- [ ]` or `- [x]`)
- **Bold** task titles for scannability
- Context after title, separated by ` - `
- Subtasks indented with 2 spaces
- Completed tasks: `[x]`, strikethrough title, completion date in parens

### CLAUDE.md Format

```markdown
# Memory

## Me
[Name], [Role] on [Team]. [One sentence about what I do.]

## People
| Who | Role |
|-----|------|
| **[Nickname]** | [Full Name], [role/team] |

→ Full list: memory/glossary.md, profiles: memory/people/

## Terms
| Term | Meaning |
|------|---------|
| [ACRONYM] | [Expansion/definition] |

→ Full glossary: memory/glossary.md

## Projects
| Name | What |
|------|------|
| **[Codename]** | [Brief description] |

→ Details: memory/projects/

## Preferences
- [Preference 1]
- [Preference 2]
```

**Rules:**
- Keep under ~100 lines total
- Tables for compactness
- **Bold** for nicknames/codenames (scanning)
- Footer references to deep storage
- Only frequently-used items

### memory/glossary.md Format

```markdown
# Glossary

Workplace shorthand, acronyms, and internal language.

## Acronyms
| Term | Meaning | Context |
|------|---------|---------|
| [ACRONYM] | [Expansion] | [When/where used] |

## Internal Terms
| Term | Meaning |
|------|---------|
| [term] | [Definition] |

## Nicknames → Full Names
| Nickname | Person |
|----------|--------|
| [nickname] | [Full Name (Role)] |

## Project Codenames
| Codename | Project |
|----------|---------|
| [code] | [Project name/description] |
```

### memory/people/{name}.md Format

```markdown
# [Full Name]

**Also known as:** [nickname], [alternate name]
**Role:** [Job title]
**Team:** [Team/department]
**Reports to:** [Manager name]

## Communication
- Preferred channel: [Slack/email/etc.]
- Communication style: [direct, formal, casual, etc.]
- Best time: [mornings, afternoons, etc.]

## Context
- [Key responsibility or expertise]
- [Important relationship or role]
- [Anything else to remember]

## Notes
- [Personal notes, preferences, quirks]
```

### memory/projects/{name}.md Format

```markdown
# [Project Name]

**Codename:** [Codename if different]
**Also called:** [Alternate references]
**Status:** [Active, Completed, On Hold, Cancelled]

## What It Is
[2-3 sentence description]

## Key People
- [Name] - [role on project]
- [Name] - [role on project]

## Context
[Budget, timeline, dependencies, importance, etc.]

## Links
- [Project tracker URL]
- [Documentation URL]
- [Slack channel]

## Timeline
- Started: [date]
- Target completion: [date]
- Status: [current state]
```

### memory/context/company.md Format

```markdown
# Company Context

## Tools & Systems
| Tool | Used for | Internal name |
|------|----------|---------------|
| [Tool] | [Purpose] | [Nickname if any] |

## Teams
| Team | What they do | Key people |
|------|--------------|------------|
| [Team] | [Responsibility] | [Lead name] |

## Processes
| Process | What it means |
|---------|---------------|
| [Process name] | [Description] |

## Terminology
| Term | Meaning |
|------|---------|
| [Company-specific term] | [Definition] |
```

---

## Appendix B: Troubleshooting

### Dashboard Not Updating

**Symptom:** Changes in TASKS.md don't appear in dashboard

**Solution:** Refresh the browser. The dashboard watches for file changes but may need a manual refresh.

**Alternative:** Close and reopen dashboard.html

### Memory Not Decoding

**Symptom:** Claude asks "Who's Todd?" when Todd is in memory

**Check:**
1. Is Todd in CLAUDE.md or memory/glossary.md?
2. Is the spelling/capitalization exact?
3. Try asking "what do you know about todd?"

**Solution:** If missing, add explicitly:
```
You: remember that Todd is Todd Martinez, Finance lead

Claude: Got it - I'll remember Todd Martinez.
```

### Task Sync Not Working

**Symptom:** `/productivity:update` doesn't find tasks from Linear/Asana/etc.

**Check:**
1. Is the MCP server connected? (Check Cowork settings)
2. Have you authenticated? (First use prompts for sign-in)
3. Are there actually tasks assigned to you in the external tool?

**Solution:** Re-authenticate the MCP connection or manually add tasks from the external tool.

### Comprehensive Scan Taking Too Long

**Symptom:** `/productivity:update --comprehensive` runs for minutes

**Expected:** This is normal. Scanning months of messages/email/docs takes time.

**Optimization:** Run comprehensive scan less frequently (weekly instead of daily).

**Alternative:** Use default `/productivity:update` for quick daily syncs.

### Memory Growing Too Large

**Symptom:** CLAUDE.md is 200+ lines, feeling unwieldy

**Solution:** Demote less-frequently-used items:

1. Review CLAUDE.md People table
2. Move people you haven't interacted with in 30+ days to memory/glossary.md only
3. Do the same for Terms and Projects
4. Keep CLAUDE.md focused on current, active context

**Target:** ~50-80 lines in CLAUDE.md

### Tasks Appearing Multiple Times

**Symptom:** Same task shows up in multiple sections or duplicated

**Cause:** Manual editing of TASKS.md introduced duplicates

**Solution:** 
1. Open TASKS.md directly
2. Remove duplicate entries
3. Dashboard will sync on next refresh

**Prevention:** Use either dashboard OR file editing, not both simultaneously

---

## Appendix C: Integration Examples

### Morning Routine Automation

Create a morning startup workflow:

```
You: morning routine

Claude: [Reads TASKS.md, checks calendar, scans recent Slack]

Good morning! Here's your day:

Calendar:
- 9:00 AM - Phoenix standup (Sarah, Greg)
- 2:00 PM - Budget review with Todd
- 4:00 PM - Platform sync

Active Tasks (5):
- Send PSR to Todd (DUE TODAY)
- Review API spec from Sarah
- Sync with Greg on Phoenix timeline
- Draft Q2 roadmap
- Platform blocker follow-up

Waiting On:
- Budget approval (6 days waiting)

Recent activity:
- Sarah shared updated mockups in #phoenix yesterday
- Greg asked about timeline in DMs

Suggested tasks:
- Prep for budget review with Todd (meeting at 2pm)
- Follow up on budget approval (been 6 days)

Ready to tackle the day?
```

### End-of-Day Wrap-Up

```
You: what did I get done today?

Claude: [Reviews Done section, recent updates]

Completed today:
- ✓ Sent PSR to Todd
- ✓ Reviewed API spec from Sarah
- ✓ Phoenix standup prep

Still open:
- Draft Q2 roadmap (in progress)
- Platform blocker follow-up

New tasks added:
- Follow up on budget approval
- Prep for next week's Phoenix demo

Moved to Someday:
- Mobile app redesign research

Good day! 3 tasks completed, 2 in progress.
```

### Project Handoff

When handing off a project, export all context:

```
You: give me everything about the Phoenix project - tasks, 
     people, timeline, status

Claude: [Reads memory/projects/phoenix.md, finds related tasks, 
         pulls people profiles]

# Project Phoenix - Complete Handoff

## Overview
Database migration from legacy Oracle to PostgreSQL
Status: Active, launching Q2 2025
Budget: $1.2M, 6-month timeline

## Key People
- Sarah Wilson (sarah@company.com) - Tech lead
  - Engineering, Platform team
  - Prefers Slack, very responsive
  - Owns technical architecture
  
- Todd Martinez (todd@company.com) - Budget owner
  - Finance lead
  - Handles PSRs and approvals
  - Direct communication style

- Greg (sales) - Stakeholder
  - Concerned about sales impact
  - Needs timeline updates

## Active Tasks
- Sync with Greg on Phoenix timeline
- Platform blocker follow-up

## Recent Activity
- Standup meetings every Monday 9am
- Sarah shared updated mockups yesterday
- Budget review scheduled this week

## Links
- Slack channel: #phoenix
- Project tracker: [Linear workspace]
- Documentation: [Notion page]

[Full export ready for new owner]
```

### Weekly Planning Session

```
You: help me plan next week

Claude: [Reviews TASKS.md, checks calendar, considers projects]

Let's plan your week:

## Priorities (from active tasks)
1. Draft Q2 roadmap (no deadline set - should we add one?)
2. Phoenix timeline sync with Greg
3. Platform blocker follow-up

## Upcoming Commitments
- Phoenix demo prep (meeting scheduled for Thu)
- Budget follow-up (been waiting 6 days)

## Calendar Blocks
- Phoenix standup (Mon 9am, recurring)
- Budget review with Todd (Wed 2pm)
- Platform sync (Fri 4pm)

## Suggested Structure
Monday: 
- Phoenix standup
- Draft Q2 roadmap (block 2-3 hours)

Wednesday:
- Finish Q2 roadmap
- Budget review with Todd at 2pm

Thursday:
- Phoenix demo prep
- Timeline sync with Greg

Friday:
- Platform blocker follow-up
- Platform sync at 4pm
- Weekly review and triage

Should I add these time blocks to your calendar?
```

---

## Final Thoughts

The productivity plugin transforms Claude from a helpful assistant into a true workplace collaborator. It learns your language, tracks your commitments, and maintains context so you can focus on getting work done instead of explaining yourself.

Start simple. Run `/productivity:start`, let Claude learn your shorthand, and add tasks as they come up. The system grows with you organically.

The magic happens when you stop thinking about "managing the system" and just work naturally. Say "ask todd about the PSR for phoenix" and Claude knows exactly what you mean. That's the goal.

Your workplace runs on shorthand. Now Claude speaks it too.

---

**Quick Start Checklist:**

- [ ] Install plugin: `claude plugins add productivity`
- [ ] Run `/productivity:start`
- [ ] Complete memory bootstrap (point Claude to your task list)
- [ ] Open dashboard.html in browser
- [ ] Add first task naturally in conversation
- [ ] Run `/productivity:update` to see sync in action
- [ ] Set weekly reminder for `/productivity:update --comprehensive`

That's it. You're ready to work.