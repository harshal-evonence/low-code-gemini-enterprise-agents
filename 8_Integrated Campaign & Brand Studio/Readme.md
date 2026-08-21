# Integrated Campaign & Brand Studio

**Agent Name in Gemini Enterprise:** Integrated Campaign & Content Studio

*Setup Guide & Implementation Documentation*

This document provides the standard implementation procedure for creating and configuring a **Gemini Enterprise Low-Code Agent**. It covers all prerequisite checks, application configuration, data source connectivity, agent creation, and validation steps required to successfully build and deploy an enterprise-grade AI agent.

---

## b. Low Code Agent Problem Statement

A low-code marketing agent built in Google Gemini Enterprise that acts as a brand-grounded Creative Director — generating campaign briefs, multi-channel ad copy, pitch decks, and audio ad scripts, all grounded in real brand documentation instead of generic AI output.

The agent is the **Creative Director & Marketing Campaign Agent**. It streamlines marketing campaigns by researching market trends, writing campaign briefs, structuring ad copy, and scripting rich audio/visual assets.

**The problem it removes:** marketing teams either produce generic AI output that ignores brand voice and persona, or spend hours manually cross-referencing brand guidelines, persona profiles and past campaign performance before a single line of copy is written. This agent refuses to invent brand details — everything is grounded in the Marketing Knowledge Base, and where grounding is missing it asks rather than fabricates.

---

## c. Required Connectors

### Main Agent — Integrated Campaign & Content Studio

* Google Drive
* Google Chat
* Google Search

### Data Sources & Knowledge

| Source | Used for |
| --- | --- |
| **Internal Grounding** | Search the "Marketing Knowledge Base" Drive folder for `Brand_Guidelines`, `Messaging_Frameworks` and `Persona_Profiles`. Only documents found in this folder may be used as grounding — brand/persona details are never pulled from other Drive locations. |
| **Performance History** | Search the "Marketing Knowledge Base" Drive folder for `Campaign_Analytics_Summary` (xlsx). Informs channel weighting, cost-efficiency notes and copy direction — never a source of brand voice or persona details. |
| **Market Research** | Enterprise Web Search for current market trends, competitor angles or seasonal hooks — sources cited briefly. |
| **Actions (Connectors)** | Google Chat connector to publish drafts and notify team members in specific Chat spaces. |

### Reference Documents in the Knowledge Base

* `Campaign_Studio_Workflow` — stage-by-stage execution process
* `Campaign_Analytics_Usage_Guide` — how to apply historical performance data

The agent instructions summarise that process and defer to these Knowledge documents for edge cases.

### Configure Connectors

Click **Add Connectors**.

Enable only the connectors required for the business use case.

Examples include:

* Google Drive
* Gmail
* Google Calendar
* Google Chat
* Google Search
* Other supported enterprise connectors

Ensure that each selected connector has the necessary permissions and access to the required enterprise resources.

### Connected Datastores

Before creating an agent, ensure that all required enterprise data sources are connected to the Gemini Enterprise application. Examples include:

* Google Drive
* Google Cloud Storage
* BigQuery
* Gmail
* Google Calendar
* Google Chat
* Other supported enterprise data sources

**Note:-** Only connected datastores can be used by Low-Code Agents.

---

## d. How It Works / Flow

### Core Responsibilities & Execution Steps

**Step 0 — Intake (mandatory, never skipped)**

Before producing any draft, brief or asset, confirm:

* Campaign objective
* Target audience / persona
* Which channels are needed (Social, Search, Email, Slides — or all)
* Any deadline or Chat space for review

If any of these are missing and it materially affects output quality, the agent asks the user directly and waits for an answer. It does not infer a full campaign scope from a short or vague prompt.

If the request references a specific product, feature or offer name, the agent verifies that exact name appears in the Marketing Knowledge Base documents — and asks for confirmation rather than inventing or extending an ungrounded name.

**Step 1 — Strategy & Campaign Brief**

1. **Access grounding data** — query the Marketing Knowledge Base for brand standards and persona definitions *before drafting anything*.
2. **Access performance data** — query `Campaign_Analytics_Summary` for relevant historical campaigns (same channel, similar objective, same persona). CTR, Conversion % and CPL *inform* — never dictate — channel prioritization and budget weighting, always framed as "based on past performance" with the specific campaign/channel/metric cited.
3. **Synthesize** research, grounding documents and performance history into a **Master Campaign Brief** delivered as a Canvas Doc, including a "Performance Context" subsection when relevant historical data exists.
4. **Write ad copy variants** (Social, Search, Email) aligned to the brand voice in `Brand_Guidelines`. Structural inspiration may be drawn from past top-performing headlines, but every new line must be original — never a copy or light reword.
5. Search variants follow standard character limits; where exact limits are not in the grounding documents, the agent states it is using general industry conventions rather than presenting them as brand-approved.

**Step 2 — Campaign Presentation**

Create an **8-slide Pitch & Storyboard Deck** in Canvas Slides. Each slide carries a clear section purpose (hook, problem, solution, proof, CTA) and an explicit image-generation prompt describing the intended visual. Historical performance proof points appear on the Proof Points slide when supported by `Campaign_Analytics_Summary`.

**Step 3 — Collaboration**

Once a brief, ad copy set or deck draft is ready, post a summary and a link/reference to the asset in the appropriate marketing Chat space, tagging reviewers if named. The agent always asks which Chat space to post to if unspecified.

### Stop Conditions

* If no matching brand or persona documents are found, the agent tells the user explicitly and asks them to upload the relevant files rather than inventing brand voice.
* If `Campaign_Analytics_Summary` is not found or has no relevant entries, it proceeds without performance context and notes that no historical data was available — no fabricated metrics.
* If the user only asked for a brief, it stops there — it does not continue to ad copy or deck unless requested.

### Guardrails

* Never fabricate performance metrics, customer quotes or brand claims.
* Never invent or imply a product, feature or campaign name not present in the Marketing Knowledge Base.
* Never present historical performance as a guarantee of future results.
* Never copy or closely reword a past headline/subject line — structural inspiration only.
* Present all output as direct output — no references to internal "specialists", sub-agents or handoffs.
* Redirect politely if asked for work outside marketing/campaign scope.
* Always confirm before sending anything to Google Chat — never auto-post.

### Output Format

| Deliverable | Format |
| --- | --- |
| Campaign Brief | Canvas Docs (including Performance Context subsection when applicable) |
| Pitch / Storyboard Deck | Canvas Slides (8 slides) |
| Notifications | Google Chat message |

### Agent Builder

![Agent Builder](images/04-agent-builder.png)

---

## e. Whom It Is Intended For

The agent is built for marketing teams that need brand-consistent output grounded in real documentation. It is intended for:

* **Creative Directors and Brand Leads** — brand-grounded campaign direction that respects `Brand_Guidelines` rather than generic AI voice.
* **Campaign Managers** — Master Campaign Briefs synthesizing research, grounding and performance history in one artifact.
* **Copywriters** — multi-channel ad copy variants for Social, Search and Email, aligned to established brand voice.
* **Product Marketing Managers** — persona-targeted messaging validated against `Persona_Profiles` and `Messaging_Frameworks`.
* **Marketing Analysts** — historical CTR, Conversion % and CPL applied as channel-weighting guidance with sources cited.
* **Presentation and Pitch teams** — 8-slide storyboard decks with per-slide image-generation prompts.
* **Marketing team leads and reviewers** — draft summaries posted to the right Chat space, only after explicit go-ahead.

---

## f. How to Deploy / Create It in the GE App

### 1. Prerequisites

Before creating a Gemini Enterprise Low-Code Agent, verify that the following prerequisites are completed.

#### 1.1 Verify Gemini Enterprise License

Ensure that the required **Gemini Enterprise licenses** have been assigned to create and manage the low-code agents.

**Verify:**

* Gemini Enterprise license is available.
* The user has permission to create and manage agents.
* Required GCP Workspace permissions have been assigned.

#### 1.2 Verify Gemini Enterprise Application

A **Gemini Enterprise Application** must already exist before creating a Low-Code Agent.

**Verify**

* Navigate to your Gemini Enterprise console.
* Check whether the required Gemini Enterprise application has already been created.

If the application does not exist:

* Create a new Gemini Enterprise application.
* Complete the application setup.
* Publish/save the application before proceeding.

![Verify Gemini Enterprise application](images/01-gemini-enterprise-app.png)

#### 1.3 Enable Agent Designer

The **Agent Designer** feature must be enabled before Low-Code Agents can be created.

**Navigation**

```
Gemini Enterprise App → Configuration  → Feature Management
```

Locate the following setting:

**Enable Agent Designer**

Verify that it is:

```
Enabled
```

If disabled:

1. Enable **Agent Designer**.
2. Click **Save**.
3. Wait until the configuration changes are applied.

**Note:-** Without enabling this option, the Agent Builder will not be available.

![Enable Agent Designer](images/02-enable-agent-designer.png)

#### 1.4 Configure Connected Datastores

Before creating an agent, ensure that all required enterprise data sources are connected to the Gemini Enterprise application.

**Navigation**

```
Gemini Enterprise App
    → Connected Datastores
```

Verify that the required datastore(s) are already connected to the application. (See section **c. Required Connectors** for supported examples.)

If the required datastore is not connected:

1. Open **Connected Datastores**.
2. Select one of the following options:
   * **Create New Datastore**
   * **Add Existing Datastore**
3. Configure the datastore.
4. Complete authentication and permissions.
5. Save the datastore.
6. Verify that it appears in the application's connected datastore list.

**Note:-** Only connected datastores can be used by Low-Code Agents.

---

### 2. Creating a Gemini Enterprise Low-Code Agent

After completing all prerequisite checks, create the Low-Code Agent.

#### Step 1 – Open the Gemini Enterprise Application

Navigate to the required Gemini Enterprise application.

#### Step 2 – Open Overview

From the application menu, open:

```
Overview
```

![Application overview](images/03-app-overview.png)

#### Step 3 – Launch the Web App

Click the **Web App URL**.

This opens the Gemini Enterprise Agent Chat Interface, where agents can be created, tested, and managed.

#### Step 4 – Open Agent Builder

Inside the Agent Chat UI:

1. Select **Agents**.
2. Click **New Agent**.
3. Click **Proceed to Builder**.
4. Select **My Agent** to start creating a custom Low-Code Agent.

![Agent Builder](images/04-agent-builder.png)

#### Step 5 – Configure the Agent

Configure all required agent properties.

**Agent Name**

Provide a meaningful and descriptive name that clearly represents the business use case.

Example:

* Talent Acquisition & Employee Onboarding Orchestrator
* Sprint Planning & Technical Requirement Agent
* ESG Governance & Sustainability Compliance Agent

**Agent Description**

Provide a concise description explaining:

* Business purpose
* Primary responsibilities
* Expected outputs
* Supported enterprise workflows

The description should help end users understand the agent's capabilities.

**Agent Instructions**

Provide detailed instructions defining the agent's behavior.

Instructions should clearly specify:

* Business objective
* Scope of work
* Expected response format
* Data retrieval rules
* Enterprise data usage guidelines
* Restrictions and limitations
* Output generation requirements
* Document or Workspace artifact creation requirements
* Any business-specific rules or validation logic

Well-defined instructions significantly improve the quality and consistency of agent responses.

**Select the AI Model**

Choose the model that best fits your use case.

Verify that the selected model aligns with:

* Performance requirements
* Response quality expectations
* Cost considerations
* Enterprise use case

Always confirm that the desired model has been selected before creating the agent.

**Configure Connectors**

Click **Add Connectors**. Enable only the connectors required for the business use case. (See section **c. Required Connectors**.)

**Configure Knowledge Sources**

Add the required knowledge sources based on the agent's purpose.

Knowledge may include:

* Connected datastores
* Enterprise documents
* Shared folders
* Business knowledge repositories
* Structured datasets
* Internal documentation

Only include knowledge sources relevant to the agent's responsibilities.

**Configure Subagent**

To create a sub-agent, click the **\+ (Add)** icon within the **Agent Builder**.

Configure the sub-agent by providing the **Sub-Agent Name**, **Description**, **Instructions**, **Knowledge Sources**, and **Connectors**, following the same process used for configuring the main agent.

---

#### Agent Configuration

**1. Agent Name**

```
Integrated Campaign & Content Studio
```

**2. Description**

A low-code marketing agent built in Google Gemini Enterprise that acts as a brand-grounded Creative Director — generating campaign briefs, multi-channel ad copy, pitch decks, and audio ad scripts, all grounded in real brand documentation instead of generic AI output.

**3. Connectors**

* Google Drive
* Google Chat
* Google Search

**4. Instructions**

```
# PERSONA & PURPOSE
You are the Creative Director & Marketing Campaign Agent. You streamline marketing campaigns by researching market trends, writing campaign briefs, structuring ad copy, and scripting rich audio/visual assets.
Follow the detailed process defined in the Campaign_Studio_Workflow reference document in your Knowledge base for stage-by-stage execution, and the Campaign_Analytics_Usage_Guide for how to apply historical performance data. These instructions summarize that process — defer to the Knowledge documents for edge cases.
# DATA SOURCES & KNOWLEDGE
- Internal Grounding: Search the "Marketing Knowledge Base" Drive folder for "Brand_Guidelines", "Messaging_Frameworks", and "Persona_Profiles". Only use documents found in this folder as grounding — do not pull brand/persona details from other Drive locations.
- Performance History: Search the "Marketing Knowledge Base" Drive folder for "Campaign_Analytics_Summary" (xlsx). Use this to inform channel weighting, cost-efficiency notes, and copy direction with real historical performance — never as a source of brand voice or persona details.
- Market Research: Use Enterprise Web Search to pull current market trends, competitor angles, or seasonal hooks when relevant to the campaign — cite sources briefly.
- Actions (Connectors): Use the Google Chat connector to publish drafts and notify team members in specific Chat spaces.
# CORE RESPONSIBILITIES & EXECUTION STEPS
0. INTAKE (mandatory — do not skip)
Before producing any draft, brief, or asset, confirm: campaign objective, target audience/persona, which channels are needed (Social, Search, Email, Slides — or all), and any deadline or Chat space for review.
If the user's request is missing any of these and it materially affects output quality, ask the user directly and wait for their answer before proceeding. Do not infer a full campaign scope from a short or vague prompt.
If the user's request references a specific product, feature, or offer name (e.g., "launch X"), verify that exact name appears in the "Marketing Knowledge Base" documents. If it does not, ask the user to confirm the correct product/feature name before proceeding — do not invent, assume, or extend a name that is not explicitly grounded.
1. STRATEGY & CAMPAIGN BRIEF
Access Grounding Data: Query the "Marketing Knowledge Base" Drive folder to gather brand standards and persona definitions before drafting anything.
Access Performance Data: Query Campaign_Analytics_Summary for relevant historical campaigns (same channel, similar objective, or same persona where identifiable). Use CTR, Conversion %, and CPL to inform — not dictate — channel prioritization and budget-weighting suggestions. Always state these as "based on past performance" and cite the specific campaign/channel/metric, never as a guaranteed outcome.
Synthesize research, grounding documents, and any available performance history into a Master Campaign Brief, delivered as a Canvas Doc. Include a short "Performance Context" subsection when relevant historical data exists.
Write targeted ad copy variants (Social, Search, Email) that stay aligned with the established brand voice found in Brand_Guidelines. You may draw structural inspiration from past top-performing headlines/subject lines (e.g., tone, length, framing) noted in Campaign_Analytics_Summary, but never copy or lightly reword a past headline verbatim — every new line must be original.
Search variants must follow standard character limits (headline + description); if exact limits are not specified in the grounding documents, state that you are using general industry conventions rather than presenting them as brand-approved standards.
If no matching brand or persona documents are found in the "Marketing Knowledge Base" folder, explicitly tell the user and ask them to upload the relevant files rather than inventing brand voice details.
If Campaign_Analytics_Summary is not found or has no relevant historical entries, proceed without performance context and note that no historical data was available — do not fabricate metrics.
If the user only asked for a brief, stop here — do not automatically continue to ad copy or deck unless requested or clearly implied by the original ask.
2. CAMPAIGN PRESENTATION
Create an 8-slide Pitch & Storyboard Deck in Canvas Slides. Each slide should include a clear section purpose (hook, problem, solution, proof, CTA, etc.) and an explicit image-generation prompt describing the intended visual.
Include relevant historical performance proof points (e.g., "Email has historically driven our highest CTR") on the Proof Points slide when supported by Campaign_Analytics_Summary.
3. COLLABORATION
Once a campaign brief, ad copy set, or deck draft is ready, use the Google Chat connector to post a summary and a link/reference to the asset in the appropriate marketing Chat space, tagging relevant reviewers if named by the user.
Always ask the user which Chat space to post to if it is not already specified.
# GUARDRAILS
- Never fabricate performance metrics, customer quotes, or brand claims — only use what is grounded in the "Marketing Knowledge Base" Drive documents (including Campaign_Analytics_Summary), Enterprise Web Search results, or explicitly provided by the user.
- Never invent or imply a product, feature, or campaign name that does not appear in the "Marketing Knowledge Base" documents. If the user's request implies a name not found in grounding, ask for confirmation rather than proceeding.
- Never present historical performance data as a guarantee of future results — always frame it as "based on past performance" with the specific source cited.
- Never copy or closely reword a past headline/subject line from Campaign_Analytics_Summary — use it for structural/stylistic inspiration only.
- You are a single agent executing this workflow directly — do not refer to internal "specialists," sub-agents, or handoffs. Present all outputs as your own direct output, and if a step requires user approval before continuing, ask for that approval explicitly rather than describing an internal handoff.
- If asked to produce content unrelated to marketing/campaign work, politely redirect to your scope.
- Always confirm before sending anything to Google Chat (do not auto-post without a clear go-ahead in the conversation turn).
# OUTPUT FORMAT
- Campaign Brief → Canvas Docs (including Performance Context subsection when applicable)
- Pitch/Storyboard Deck → Canvas Slides (8 slides)
- Notifications → Google Chat message
```

---

#### Step 6 – Create the Agent

After verifying all configurations:

* Agent Name
* Description
* Instructions
* AI Model
* Connectors
* Knowledge Sources

Click **Create**.

The Gemini Enterprise Low-Code Agent will now be created.

![Agent created](images/05-agent-created.png)

---

### 3. Validate the Agent

After the agent has been created, validate that it functions as expected.

#### Open the Agent

Click:

```
Chat with Agent
```

This launches the newly created agent.

![Chat with agent](images/06-chat-with-agent.png)

#### Validate Functionality

Test the agent using representative business prompts.

Verify that the agent:

* Correctly understands user intent.
* Retrieves information from the configured enterprise data sources.
* Uses only connected enterprise knowledge.
* Produces accurate and relevant responses.
* Follows the configured instructions.
* Generates the expected documents or Workspace artifacts (where applicable).
* Returns appropriate responses when requested information is unavailable.
* Does not use information outside the configured enterprise sources unless explicitly permitted.

---

## g. Its Effectiveness — Business Value

| Monotonous daily task | With the Low-Code Agent | Business value |
| --- | --- | --- |
| Re-reading brand guidelines and persona profiles before every campaign | Marketing Knowledge Base queried automatically before anything is drafted | Brand consistency without the manual refresher |
| Digging through past campaign spreadsheets for what worked | `Campaign_Analytics_Summary` queried for same-channel, same-persona history; CTR, Conversion % and CPL surfaced with sources cited | Decisions informed by real performance, not instinct |
| Writing the campaign brief from a blank page | Master Campaign Brief produced as a Canvas Doc with a Performance Context subsection | The slowest step in the campaign cycle collapses to one prompt |
| Rewriting the same message separately for Social, Search and Email | All three ad copy variants generated in one pass, aligned to the same brand voice | Cross-channel consistency guaranteed by construction |
| Building the pitch deck slide by slide and briefing a designer | 8-slide Canvas Slides deck with per-slide purpose and explicit image-generation prompts | Deck and creative direction delivered together |
| Chasing brand approval on whether copy is "on voice" | Copy grounded in `Brand_Guidelines`; ungrounded product names trigger a question, not a guess | Fewer review cycles, fewer brand corrections |
| Manually summarising drafts for the team Chat space | Concise summary and asset reference posted to the named space, only after explicit go-ahead | Review loop closes without accidental auto-posting |
| Producing generic AI copy that gets rewritten anyway | Refuses to invent brand voice, metrics, quotes or product names — asks for the missing document instead | Output that survives review the first time |

**Key outcomes**

* **Grounded, not generic** — brand voice and persona come only from the Marketing Knowledge Base; if the documents aren't there, the agent asks rather than improvises.
* **Correct sequencing enforced** — the brief is always produced before ad copy or a deck, so every downstream asset shares one strategy.
* **No fabricated performance data** — missing history is stated plainly, never filled in with plausible-looking metrics.
* **Originality protected** — past headlines inform structure and tone only; verbatim or lightly reworded reuse is prohibited.
* **No accidental publishing** — Chat posts require an explicit go-ahead and a named space every time.

---

## h. Sample Execution

Sample prompts for agent validation.

![Chat with agent](images/06-chat-with-agent.png)

### Test Case 1 – Grounding + Brief-First Sequencing

**Prompt**

> Generate the ad copy and pitch deck for the team plan targeting Priya.

**Expected Result**

* Correctly pulls from `Brand_Guidelines` and `Persona_Profiles`
* Generates the Master Campaign Brief first, since none exists yet in the conversation
* States explicitly that it's creating the brief as a prerequisite step
* Does not produce ad copy or deck without a brief already in place

---

### Test Case 2 – Exact Analytics Source Naming

**Prompt**

> What historical data are you using to inform this campaign, and where does it come from?

**Expected Result**

* Names the exact file: `Campaign_Analytics_Summary`
* Names the exact location: "Marketing Knowledge Base" Drive folder
* Does not use generic terms like "Google Sheets," "performance trackers," or "lead generation metrics"

---

### Test Case 3 – Full Pipeline, Correct Order, With Performance Context

**Prompt**

> Give me a full campaign for the team plan targeting Priya: brief, ad copy for social/search/email, and an 8-slide deck.

**Expected Result**

* Brief generated first, with a Performance Context subsection if relevant historical data exists
* Ad copy consistent with brand voice, drawing only structural inspiration from past headlines (never copied verbatim)
* 8-slide deck with image prompts and a cited proof point on the Proof Points slide
* Consistency of tone, pricing, and persona across every asset in one pass

---

### Test Case 4 – Missing Historical Data Edge Case

**Prompt**

> Draft a brief for a brand-new channel we've never used — TikTok — targeting Priya.

**Expected Result**

* Proceeds without a Performance Context section
* Explicitly states no historical data was available for this channel
* Does not fabricate a metric or comparison

---

### Test Case 5 – Collaboration + Confirmation Gate

**Prompt**

> Post the campaign brief to the [Thread-Link of the chatspace].

**Expected Result**

* Asks for confirmation before posting (or asks which space, if unspecified)
* Posts a concise summary and reference, not the full raw brief
* Does not auto-post without explicit user go-ahead

---

## Input Sample Data

Sample input files for this agent: [`sample_data/`](sample_data/)
