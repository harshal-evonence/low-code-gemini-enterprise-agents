# Low Code Agents

A collection of **14 Gemini Enterprise low-code agents** built with Agent Designer, covering
engineering, HR, finance, sales, marketing, legal, IT, supply chain, sustainability and
executive operations.

Every agent is grounded in connected enterprise data — Google Drive, Gmail, Calendar, Chat,
Search and Jira — and is configured never to fabricate information. Each folder is
self-contained: the `Readme.md` carries the full agent configuration (name, description,
connectors, instructions, sub-agents) needed to recreate it in Gemini Enterprise.

---

## Agents

| # | Agent | What it does | Connectors | Sub-agents |
| --- | --- | --- | --- | --- |
| 1 | [Technical PRD & Sprint Agent](1_Technical%20PRD%20&%20Sprint%20Agent/Readme.md) | Turns feature requests into Technical PRDs, user stories, sprint plans and release summaries | Drive, Chat, Jira | 3 |
| 2 | [Talent & Onboarding Orchestrator](2_Talent%20&%20Onboarding%20Orchestrator/Readme.md) | End-to-end hiring — screening, ranking, interview scheduling, evaluation and onboarding | Drive, Gmail, Calendar, Chat | 5 |
| 3 | [Sustainability Audit & Governance](3_Sustainability%20Audit%20&%20Governance/Readme.md) | Carbon footprint audits, ESG compliance against GRI/SASB/CSRD/SEC, disclosure reports | Drive, Search | 3 |
| 4 | [Supply Chain & Inventory Optimization](4_Supply%20Chain%20&%20Inventory%20Optimization/Readme.md) | Inventory forecasting, replenishment matrices, supplier bottlenecks, S&OP decks | Drive, Chat | 2 |
| 5 | [Research & Development (R&D)](5_Research%20&%20Development%20(R&D)/Readme.md) | Materials discovery, architecture review, Engineering RFCs against ASTM/ISO/IEEE/ASME | Drive, Search | — |
| 6 | [Paid Media & Ad Campaign Studio](6_Paid%20Media%20&%20Ad%20Campaign%20Studio/Readme.md) | Ad copy across Google/Meta/LinkedIn/Display/YouTube, budget plans, video and audio assets | Drive, Chat, Enterprise Search | — |
| 7 | [IT Helpdesk & RCA Agent](7_IT%20Helpdesk%20&%20RCA%20Agent/Readme.md) | Autonomous ITSM — alert triage, runbook diagnostics, emergency bridges, RCA docs, SLA logs | Drive, Gmail, Calendar, Chat, Search | — |
| 8 | [Integrated Campaign & Brand Studio](8_Integrated%20Campaign%20&%20Brand%20Studio/Readme.md) | Brand-grounded campaign briefs, multi-channel ad copy and 8-slide pitch decks | Drive, Chat, Search | — |
| 9 | [FP&A & Transaction Auditing](9_FP&A%20&%20Transaction%20Auditing/Readme.md) | Budget vs actual, QoQ variance, duplicate-invoice detection, board reporting | Drive, Gmail, Calendar, Search | 3 |
| 10 | [Deal Velocity & Pitch Agent](10_Deal%20Velocity%20&%20Pitch%20Agent/Readme.md) | Gated RFP response — gap analysis, proposal brief, pitch deck, tracker, outreach | Drive, Gmail, Search | — |
| 11 | [Corporate PR & Communications](11_Corporate%20PR%20&%20Communications/Readme.md) | Press releases, crisis Q&A kits, executive decks, media pitches and talking points | Drive, Gmail, Search | — |
| 12 | [Contract Lifecycle & Compliance](12_Contract%20Lifecycle%20&%20Compliance/Readme.md) | US contract review, redlines, risk matrices and compliance validation reports | Drive, Gmail, Chat | — |
| 13 | [Autonomous Chief of Staff](13_Autonomous%20Chief%20of%20Staff/Readme.md) | Unattended daily executive briefing with urgent actions, meetings and audio overview | Drive, Gmail, Calendar | — |
| 14 | [Account Health & EBR Agent](14_Account%20Health%20&%20EBR%20Agent/Readme.md) | Customer health scoring, churn risk, 6-slide EBRs, retention memos and EBR scheduling | Drive, Gmail, Calendar | — |

---

## By business function

| Function | Agents |
| --- | --- |
| **Engineering & Product** | 1 Technical PRD & Sprint · 5 Research & Development |
| **Sales & Customer Success** | 10 Deal Velocity & Pitch · 14 Account Health & EBR |
| **Marketing** | 6 Paid Media & Ad Campaign · 8 Integrated Campaign & Brand · 11 Corporate PR |
| **Finance** | 9 FP&A & Transaction Auditing |
| **HR** | 2 Talent & Onboarding Orchestrator |
| **Legal & Compliance** | 12 Contract Lifecycle · 3 Sustainability Audit & Governance |
| **IT & Operations** | 7 IT Helpdesk & RCA · 4 Supply Chain & Inventory · 13 Autonomous Chief of Staff |

---

## Repository structure

```
Low Code Agents/
├── 1_Technical PRD & Sprint Agent/
│   ├── images/            screenshots used by the Readme
│   ├── sample_data/       input data sources for the agent
│   ├── scripts_if any/    helper scripts (delete if unused)
│   ├── skills_if any/     agent skills (delete if unused)
│   ├── Readme.md          the agent guide — sections a to h
│   └── *.docx / *.md      original setup guide
├── 2_Talent & Onboarding Orchestrator/
├── ...
├── 14_Account Health & EBR Agent/
└── Readme.md              this file
```

---

## Readme structure

Every agent `Readme.md` follows the same eight sections, in the same order:

| # | Section | Contains |
| --- | --- | --- |
| a | **Title** | Folder name plus the agent's name in Gemini Enterprise |
| b | **Low Code Agent problem statement** | The business problem and the manual work it removes |
| c | **Required connector** | Connectors, grounding sources, knowledge documents |
| d | **How it works / flow** | Workflow steps, delegation, rules and guardrails |
| e | **Whom it is intended for** | The roles that benefit, and what each gets |
| f | **How to deploy / create it in the GE App** | Prerequisites → Agent Builder → full agent configuration |
| g | **Its effectiveness — business value** | Manual task → with the agent → value, plus key outcomes |
| h | **Sample execution** | Validation prompts with expected results |

Section **f** carries the complete, copy-ready agent configuration — Agent Name, Description,
Connectors and the full Instructions block, plus every sub-agent — so an agent can be rebuilt
from the Readme alone.

---

## Getting started

1. **Check the prerequisites** — a Gemini Enterprise licence, an existing Gemini Enterprise
   application, and **Agent Designer enabled** under `Configuration → Feature Management`.
   Without Agent Designer, the Agent Builder will not appear.
2. **Connect the datastores** the agent needs. Only connected datastores are usable by
   low-code agents.
3. **Open the agent's Readme** and work through section **f** — it mirrors the Agent Builder
   screens in order, with screenshots.
4. **Paste the configuration** from section f: Agent Name, Description, Instructions,
   Connectors, Knowledge Sources — then add each sub-agent the same way.
5. **Validate** using the prompts in section **h** and compare against the expected results.

---

## Conventions

- Agents are grounded in connected enterprise data and are instructed **never to fabricate**
  facts, metrics, names or dates — unavailable details are flagged rather than invented.
- Several agents require **explicit human approval** before an outward-facing action such as
  sending email or posting to Chat.
- Deliverables are created as **real Workspace artifacts** — Google Docs, Sheets, Slides and
  Gmail drafts — rather than text pasted into chat.
- Screenshots live in each agent's `images/` folder and are referenced with relative paths.
