## Hi, I'm Sebastian 👋

Project manager and product owner. I take products from idea to working version: understanding the problem, writing the concept, slicing requirements, prioritizing and accepting the results.

For delivery, I work with AI agents (Claude Code) the way I would with a development team. I provide the concept, specification, backlog and acceptance criteria; the agents write the code; I review every result against the requirements. So the projects here mainly show how I run projects: concepts, decision logs, stage plans, reviews and open issues all live in each repository.

**Case study:** [Seven products delivered with AI agents: what works and what doesn't](case-study.md) · [Deutsche Fassung](fallstudie.md)

### [DerKurator AI](https://github.com/seb-nsu/DerKuratorAI) · PMO digital twin

Steering committees ask in plain language, "What happens if we put project X on hold for three months?", and get a decision paper with a GO / CONDITIONAL GO / NO-GO verdict, quantified impact and the chain of dependencies. Core principle: the AI neither decides nor calculates. Numbers come from deterministic tools, verdicts from a rule engine configured by the PMO. Focus: portfolio steering, decision papers, traceability

### [Ideenportal](https://github.com/seb-nsu/Ideaportal) · Idea and innovation management

Every idea gets an answer within a fixed deadline. AI agents prepare market and competitor analysis and the business case; people decide at three gates. Concept in three versions after a 360-degree review, a backlog of 146 stories across four releases, multi-tenant, with GDPR and works council requirements built in from the start. Focus: product concept, release planning, stakeholder requirements

### [Bitschmiede](https://github.com/seb-nsu/Bitschmiede) · Business simulation game, free to play ([play in the browser](https://seb-nsu.github.io/Bitschmiede/))

Run a game and engine studio from 1980 to 2040. Built in stages against a binding specification with rule IDs; a reconciliation table resolves contradictions, and open questions are documented instead of decided silently. Balancing through automated simulation runs.

Focus: specification, stage planning, acceptance

### [TimeLog](https://github.com/seb-nsu/Timelog) · Automatic working time tracking

Laptop and phone record working time via the office network and device start-up/shut-down; a shared rule set checks breaks and maximum working hours under German working time law. Privacy as a hard requirement: no location data, network identifiers stored only as hashes. Focus: business rules, data protection, multiple platforms

### [Digital-Helfer](https://github.com/seb-nsu/Digital-Helfer) · Guides for older people ([live site](https://seb-nsu.github.io/Digital-Helfer/))

A calm website in plain German: PC, smartphone, video calls, online safety, with a practice area. Built for my parents and refined based on their feedback. Focus: user-centred design, accessibility

### More
- [*Backlog-Check*](https://github.com/seb-nsu/Backlog-Check): checks a backlog against fixed rules before stories go into delivery: missing or untestable acceptance criteria, stories that are too large, hidden dependencies, cycles, duplicates and contradictions. Every finding names the rule and the text it refers to. No AI, Python standard library only
- [*Accessibility*](https://github.com/seb-nsu/Accessibility): accessibility test for websites against WCAG 2.2 AA, every finding mapped to EN 301 549. A rule scan (axe-core) plus scripts that take over much of the manual testing: keyboard, focus, reflow, text spacing, forms, contrast and dark mode
- [*Cloud Price Information*](https://github.com/seb-nsu/Cloud-Price-Information): fetch, compare and archive public list prices from nine cloud providers
- [*Couch Quest*](https://github.com/seb-nsu/Max-against-the-world): concept and production of a 2D adventure game, with a decision log for every choice

### Private projects
Not public, so no links. Happy to show them on request.

- *Dirigent*: a thin orchestrator that runs work from idea to review across several AI models and tools. Workflow, state, quality gates and budget live in fixed code; the actual work is done by existing programs, and any model or tool can stand behind each step. A local overview page shows every project's status with buttons for pre-checks, plans, runs and budgets.
- *Workflow Plugin*: a Claude Code plugin that organises AI work in teams of roles, from idea through backlog, development and acceptance to review. Each role runs as its own sub-agent with its own view, its own notes and defined write access. An entry check tells each phase what the project is still missing.
- *Spürnase*: read and search access to the whole public web for AI agents, as a command-line tool and an MCP server. No API keys and no browser cookies; the generic path works for any page, and site adapters only add extra data. Results come back as uniform JSON with fallback chains.
- *Project Map*: a knowledge graph across all my repositories. It shows purpose, stack and status of each project, how repositories depend on each other, which building blocks are built more than once, and where decisions (ADRs) and open questions sit. Updated automatically and viewable as an interactive map.
- *CuraPlan*: project management for classic, agile and hybrid projects in one tool, derived from DerKurator AI. Rule-based decisions instead of AI gut feeling, time booking from the Outlook calendar, sprints with a definition of ready, and team capacity planning confirmed by line managers. Delivered in six releases.
- *FOCUS Cockpit*: an enterprise FinOps platform that normalises cloud, SaaS, AI and data-centre costs to the FOCUS 1.4 standard. Cost allocation that always adds up, budgets with alerts, anomaly detection, forecasting and month-end close with four-eyes approval. Row-level permissions per company, division and cost centre.
- *Bikerepair*: a mobile bike repair service with a customer app, a technician app and workshop software on one backend.
- *Tagwerk*: tasks, habits and your day on one screen, local-first in the browser or as a phone app ([open it](https://tagwerk.expo.app)).
- *StilRat*: an AI hairstyle consultant for salons that shows customers three realistic, feasible styles on a tablet.

## How I work
- **Problem first, then solution.** Every project starts with a concept: target group, value, scope.
- **Decisions are written down.** With date and rationale, so it stays clear later why things are the way they are.
- **Slice small, check early.** Stages with acceptance criteria, external reviews, open issues kept visible.
- **AI with guardrails.** AI does the groundwork, people decide; every number has a source.
