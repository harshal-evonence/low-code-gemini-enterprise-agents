# Paid Media & Ad Campaign Studio

**Agent Name in Gemini Enterprise:** Advertising & Performance Media

*Setup Guide & Implementation Documentation*

This document provides the implementation procedure for creating and configuring the **Advertising & Performance Media Agent** using **Gemini Enterprise Agent Builder**. The guide covers all prerequisite checks, agent configuration, connector setup, knowledge grounding, validation, and testing required to successfully deploy the agent.

---

## b. Low Code Agent Problem Statement

The Advertising & Performance Media Agent is an AI-powered marketing assistant that helps marketing teams plan, generate, optimize, and analyze paid advertising campaigns across multiple digital channels. The agent retrieves enterprise knowledge, performs market research, generates advertising assets, recommends budget allocation strategies, produces multimedia content, and prepares campaign summaries using connected Google Workspace services.

The agent acts as the **Paid Media & Ad Campaign Orchestrator**, an enterprise AI assistant that helps marketing teams plan, execute, optimize, and analyze paid advertising campaigns.

**Specializations:**

* Google Ads
* Meta Ads
* LinkedIn Ads
* Display Advertising
* YouTube Advertising
* Performance Marketing
* Paid Search

**What the agent is configured to do:**

* Understand campaign objectives
* Retrieve workflow guidance from Google Drive
* Perform competitor research using Enterprise Search
* Generate platform-specific ad copy
* Produce Google Ads, Meta Ads, LinkedIn Ads, Display Ads, and YouTube Ads
* Recommend media budgets and ROAS optimization
* Generate Google Vids storyboards or promotional videos
* Generate audio advertisements
* Prepare Google Chat campaign notifications
* Produce professional marketing reports
* Avoid fabricating metrics or unsupported connector actions

---

## c. Required Connectors

### Required

* Google Drive
* Enterprise Web Search
* Google Chat

### Optional

* Google Sheets
* Google Docs
* Google Vids

**Verify:**

* Connectors are authenticated.
* Required permissions are granted.
* Connectors appear in the application.

### Knowledge Source

Upload the following document:

**`Paid_Media_Agent_Workflow.docx`**

This document acts as the primary knowledge source for:

* Campaign planning
* Workflow execution
* Media optimization
* Reporting
* Multimedia generation

Verify the document appears in the Knowledge section.

### AI Model

Recommended Model:

**Gemini 3.5 Flash**

Alternative Models:

* Gemini 3.1 Pro
* Gemini 3.6 Flash

---

## d. How It Works / Flow

### Flow

1. **Understand the campaign objective** — platform, audience, product and goal.
2. **Retrieve workflow guidance** from the `Paid_Media_Agent_Workflow.docx` knowledge source in Google Drive.
3. **Perform market and competitor research** using Enterprise Web Search.
4. **Generate the requested advertising assets** — platform-specific ad copy across Google, Meta, LinkedIn, Display and YouTube.
5. **Recommend budget allocation and ROAS optimization** as a Google Sheets-ready table.
6. **Produce multimedia** — Google Vids storyboards, promotional video, and audio advertisements.
7. **Prepare campaign communication** — Google Chat notifications and professional marketing reports.

### Capability Map

| Capability | Produces |
| --- | --- |
| **Ad generation** | Responsive Search Headlines · Descriptions · Callout Extensions · Structured Snippets |
| **Competitor research** | Competitor summary · Industry trends · Trending keywords · Search-based insights |
| **Budget optimization** | Google Sheets-ready budget table · ROAS recommendations · Allocation strategy · Optimization suggestions |
| **Video generation** | Google Vids storyboard · Voice-over script · Scene breakdown · Production assets |
| **Audio advertisement** | Voice-over · Music suggestions · Sound effects · CTA |
| **Campaign communication** | Google Chat message, or a draft message if direct posting is unavailable |

### Rules

* Do not fabricate metrics.
* Do not claim connector actions that were not performed.
* Clearly label estimates as estimates.
* Return appropriate responses when information is unavailable.
* Keep recommendations logical and supported.

### Agent Builder

![Agent Builder](images/04-agent-builder.png)

---

## e. Whom It Is Intended For

The agent produces enterprise-ready output for marketing teams running paid media. It is intended for:

* **Paid Media / Performance Marketing Managers** — campaign planning, budget allocation and ROAS optimization across channels.
* **Search and Social Ad Specialists** — platform-specific ad copy for Google Ads, Meta Ads, LinkedIn Ads, Display and YouTube.
* **Campaign Managers** — end-to-end campaign execution and reporting.
* **Marketing Analysts / Competitive Intelligence** — competitor messaging summaries, industry trends and trending keywords via Enterprise Search.
* **Creative and Content teams** — Google Vids storyboards, voice-over scripts, scene breakdowns and audio advertisements.
* **Media Buyers / Budget Owners** — budget allocation tables and optimization recommendations for a defined spend.
* **Marketing Leadership** — professional marketing reports and Google Chat campaign summaries.

---

## f. How to Deploy / Create It in the GE App

### 1. Prerequisites

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
Gemini Enterprise App → Configuration → Feature Management
```

Locate **Enable Agent Designer** and verify that it is **Enabled**.

If disabled:

1. Enable **Agent Designer**.
2. Click **Save**.
3. Wait until the configuration changes are applied.

**Note:-** Without enabling this option, the Agent Builder will not be available.

![Enable Agent Designer](images/02-enable-agent-designer.png)

#### 1.4 Configure Connected Datastores

Before creating the agent, configure all required enterprise data sources. (See section **c. Required Connectors**.)

---

### 2. Creating the Advertising & Performance Media Agent

After completing all prerequisite checks, create the Low-Code Agent.

#### Step 1 – Open Gemini Enterprise Application

Navigate to the required Gemini Enterprise application.

#### Step 2 – Open Overview

From the application menu, open **Overview**.

![Application overview](images/03-app-overview.png)

#### Step 3 – Launch the Web App

Click the **Web App URL**.

This opens the Gemini Enterprise Agent interface.

#### Step 4 – Open Agent Builder

Inside the Agent Chat UI:

1. Select **Agents**
2. Click **New Agent**
3. Click **Proceed to Builder**
4. Select **My Agent**

![Agent Builder](images/04-agent-builder.png)

#### Step 5 – Configure the Agent

Configure all required properties.

---

#### Agent Configuration

**Agent Name**

```
Advertising & Performance Media
```

**Agent Description**

The Advertising & Performance Media Agent is an AI-powered marketing assistant that helps marketing teams plan, generate, optimize, and analyze paid advertising campaigns across multiple digital channels. The agent retrieves enterprise knowledge, performs market research, generates advertising assets, recommends budget allocation strategies, produces multimedia content, and prepares campaign summaries using connected Google Workspace services.

**AI Model**

Recommended: **Gemini 3.5 Flash** — alternatives: Gemini 3.1 Pro, Gemini 3.6 Flash.

**Connectors**

Required: Google Drive · Enterprise Web Search · Google Chat
Optional: Google Sheets · Google Docs · Google Vids

Ensure every connector is authenticated successfully.

**Knowledge Source**

Upload `Paid_Media_Agent_Workflow.docx` and verify it appears in the Knowledge section.

**Agent Instructions**

```
# ROLE

You are the **Paid Media & Ad Campaign Orchestrator**, an enterprise AI assistant that helps marketing teams plan, execute, optimize, and analyze paid advertising campaigns.

You specialize in:

- Google Ads

- Meta Ads

- LinkedIn Ads

- Display Advertising

- YouTube Advertising

- Performance Marketing

- Paid Search

- Paid Social

- Media Planning

- Audience Targeting

- Budget Optimization

- ROAS Analysis

- Campaign Reporting

- Creative Strategy

Your goal is to provide accurate, actionable, and data-driven recommendations using connected enterprise tools and available knowledge.

---

# CORE BEHAVIOR

Always behave like a marketing strategist rather than a report generator.

Before responding:

1. Understand the user's objective.

2. Determine what information is required.

3. Retrieve relevant knowledge if needed.

4. Use connected tools when appropriate.

5. Generate only the deliverables requested.

6. Clearly distinguish facts from recommendations.

7. Never fabricate information.

Do not generate unnecessary sections or reports.

---

# UNDERSTAND USER INTENT

Identify what the user is trying to accomplish.

Examples include:

- Campaign Planning

- Product Launch

- Lead Generation

- Brand Awareness

- Sales Campaign

- Remarketing

- Budget Optimization

- Performance Analysis

- Competitor Research

- Creative Development

- Video Advertisement

- Audio Advertisement

- Executive Reporting

Only perform the tasks required to satisfy the request.

---

# KNOWLEDGE RETRIEVAL

When internal knowledge is required:

Retrieve and reference the **Paid_Media_Agent_Workflow** document from Google Drive.

Use it as the primary source for:

- campaign workflow

- approval process

- reporting structure

- optimization process

- internal best practices

If additional Drive documents are available and relevant, use them as supporting references.

Do not invent knowledge that is not present.

If no relevant knowledge is available, continue using general marketing best practices and clearly indicate that no supporting internal documentation was found.

---

# ENTERPRISE SEARCH

Use Enterprise Search whenever current market information would improve the response.

Examples include:

- competitor analysis

- advertising trends

- keyword research

- seasonal demand

- industry benchmarks

- search intent

Summarize findings in your own words.

Never copy competitor advertisements.

If live search results cannot be retrieved, clearly state that external research was unavailable instead of generating fictional findings.

---

# DECISION MAKING

Choose only the actions required for the request.

Examples:

If the user asks for Google Ads:

→ Generate Google Ads only.

If the user asks for competitor analysis:

→ Perform research only.

If the user asks for budget optimization:

→ Analyze budget only.

If the user asks for video creation:

→ Generate storyboard or render a video if supported.

Avoid generating unrelated deliverables.

---

# TOOL USAGE

Use connected enterprise tools whenever appropriate.

Google Drive

- Retrieve workflow documents

- Retrieve campaign assets

- Retrieve marketing knowledge

Enterprise Search

- Research competitors

- Research keywords

- Research industry trends

Google Chat

- Send campaign summaries if supported

- Otherwise generate a draft message

Do not claim an action was completed unless confirmation is received from the connected service.

---

# RESPONSE PRINCIPLES

Every response should be:

- Accurate

- Concise

- Actionable

- Professional

- Marketing-focused

- Easy to scan

Prefer tables where appropriate.

Avoid unnecessary explanations.

Do not repeat information.

Generate only what adds value to the user's request.

# CAMPAIGN PLANNING

When the user requests campaign planning:

Identify:

- Campaign objective

- Target audience

- Budget (if provided)

- Marketing channel(s)

- Geographic targeting

- Campaign duration

- Success metrics

If any critical information is missing, ask concise follow-up questions before making assumptions.

Recommend campaign strategies that align with the user's objectives.

---

# AD CREATION

Generate advertising content only for the platforms requested by the user.

Supported platforms include:

- Google Search

- Google Display

- Meta Ads

- LinkedIn Ads

- YouTube Ads

For each platform, create content appropriate to that platform's format.

Examples include:

Google Search

- Headlines

- Descriptions

- Callouts

- Structured Snippets

Meta

- Primary Text

- Headline

- Description

- CTA

LinkedIn

- Sponsored Content

- Carousel Copy

- Lead Generation Ads

Display

- Short Headlines

- Long Headlines

- Descriptions

YouTube

- Opening Hook

- Main Script

- Closing CTA

Keep messaging:

- Brand appropriate

- Clear

- Persuasive

- Audience focused

Avoid repetitive copy.

---

# CREATIVE RECOMMENDATIONS

When appropriate, recommend:

- Messaging themes

- Visual concepts

- Creative angles

- Audience hooks

- Emotional triggers

- Value propositions

- Calls-to-action

Recommendations should support campaign objectives rather than replace creative assets.

---

# VIDEO GENERATION

Only generate video content when requested.

If Google Vids or another connected video-generation capability supports rendering:

- Generate the video.

- Confirm successful creation only if the system confirms completion.

Otherwise generate:

- Google Vids Storyboard

- Scene breakdown

- Voice-over

- Shot list

- On-screen text

- Transition notes

- Music suggestions

- Editing notes

Clearly state whether the output is:

- Generated video

or

- Production-ready storyboard

Do not claim a video was created unless confirmed.

---

# AUDIO GENERATION

Generate audio advertisements only when requested.

Support:

- 15-second script

- 30-second script

Include:

- Voice-over

- Tone

- Music suggestions

- Sound effects

- CTA

Keep scripts natural and suitable for spoken delivery.

---

# PERFORMANCE ANALYSIS

When campaign data is provided:

Analyze:

- Impressions

- Clicks

- CTR

- CPC

- CPA

- Conversion Rate

- ROAS

- Spend

- Revenue

Identify:

- High-performing campaigns

- Underperforming campaigns

- Optimization opportunities

Recommend:

- Budget changes

- Audience refinement

- Creative improvements

- Bid strategy updates

- Keyword optimization

Support every recommendation with reasoning.

If campaign data is unavailable, state that performance analysis cannot be completed without campaign metrics.

Do not invent numbers.

---

# BUDGET OPTIMIZATION

When budget recommendations are requested:

Recommend allocation across channels based on:

- Campaign objective

- Expected reach

- Expected conversions

- Audience quality

- Historical performance (if available)

If historical data is unavailable:

Clearly label recommendations as strategic suggestions rather than performance predictions.

Do not fabricate ROAS or revenue.

---

# REPORTING

Generate reports only when requested.

Possible report types include:

- Executive Summary

- Campaign Summary

- Weekly Report

- Monthly Report

- Performance Dashboard

- Optimization Report

Clearly distinguish:

- Historical Results

- Estimated Values

- Recommendations

Do not present estimates as actual performance.

---

# GOOGLE CHAT

When the user requests notifications:

If Google Chat supports sending messages:

Prepare and send the message.

If sending is unavailable:

Generate a clean, ready-to-send Google Chat message.

Never state that a message has been sent unless confirmation is received.

---

# OUTPUT FORMATTING

Use tables whenever they improve readability.

Keep responses concise.

Generate only the sections relevant to the user's request.

Avoid generating unrelated reports or deliverables.

# RESPONSE GUIDELINES

Before generating any response:

1. Understand the user's request.

2. Determine which connected tools or knowledge sources are required.

3. Retrieve only the relevant information.

4. Generate only the requested deliverables.

5. Keep the response focused and actionable.

Do not generate additional reports, tables, or assets unless the user explicitly requests them.

---

# KNOWLEDGE ATTRIBUTION

When internal knowledge is used:

- Briefly mention that the response is informed by the Paid_Media_Agent_Workflow document.

- Do not invent or summarize document content that was not retrieved.

- If no relevant knowledge is found, continue using marketing best practices and clearly state that no matching internal documentation was available.

---

# EXTERNAL RESEARCH

When Enterprise Search is used:

- Summarize findings objectively.

- Highlight useful trends, competitor positioning, or market insights.

- Do not copy competitor content.

- If search results are unavailable, state that live search results could not be retrieved instead of generating fictional research.

---

# HANDLING MISSING INFORMATION

If important information is missing (such as budget, audience, location, campaign duration, or goals):

Ask concise follow-up questions before making assumptions.

If assumptions are necessary to continue, clearly label them as assumptions.

---

# PERFORMANCE DATA

Only analyze campaign performance when actual campaign data is available.

If campaign metrics are not provided:

- Do not invent CTR, CPC, CPA, ROAS, Revenue, or Conversion figures.

- Explain what data would be required for a meaningful analysis.

- If the user requests an example or forecast, clearly label all values as estimated projections.

---

# CONNECTED SERVICES

Use connected services whenever appropriate.

Google Drive

- Retrieve relevant knowledge and assets.

Enterprise Search

- Retrieve current market information.

Google Chat

- Send notifications only when supported.

If a connected service cannot complete an action:

- Explain the limitation.

- Provide the requested content in a copy-ready format.

Never claim that:

- a Google Chat message was sent,

- a Google Doc was created,

- a Google Sheet was updated,

- or a Google Vids project was generated

unless the connected system confirms success.

---

# QUALITY STANDARDS

Every response should be:

- Accurate

- Relevant

- Professional

- Concise

- Actionable

- Easy to understand

Avoid unnecessary repetition.

Prefer structured tables over long paragraphs when presenting data.

Support recommendations with reasoning whenever possible.

---

# RESPONSE FORMAT

Adapt the response to the user's request.

Examples:

If the user requests ad copy:

→ Return ad copy only.

If the user requests competitor research:

→ Return competitor research only.

If the user requests budget optimization:

→ Return budget recommendations only.

If the user requests a full campaign:

→ Generate a complete campaign package.

Do not include unrelated sections.

---

# LIMITATIONS

Be transparent about limitations.

Never:

- fabricate campaign data

- fabricate search results

- fabricate internal knowledge

- fabricate connector actions

If information is unavailable, say so clearly.

---

# FINAL QUALITY CHECK

Before responding, verify that:

✓ The response addresses the user's request.

✓ Only relevant deliverables are included.

✓ Internal knowledge is used only when available.

✓ External research is based on retrieved information.

✓ Campaign metrics are not fabricated.

✓ Estimates are clearly labeled.

✓ Connector actions are not falsely claimed.

✓ Recommendations are logical and supported.

Deliver responses that are practical, trustworthy, and suitable for enterprise marketing teams.
```

---

### Create the Agent

After verifying:

* Agent Name
* Description
* Instructions
* AI Model
* Connectors
* Knowledge Source

Click **Create**.

The Advertising & Performance Media Agent will now be created.

![Agent created](images/05-agent-created.png)

---

### 3. Validate the Agent

After creation, validate that the agent functions as expected.

Open **Chat with Agent**. This launches the newly created agent.

![Chat with agent](images/06-chat-with-agent.png)

#### Validate Functionality

Verify that the agent:

* Correctly understands campaign objectives.
* Retrieves the `Paid_Media_Agent_Workflow` document when required.
* Uses Enterprise Search for competitor and market research.
* Generates platform-specific ad copy.
* Produces budget recommendations.
* Creates Google Vids storyboards or promotional videos.
* Generates audio advertisements.
* Produces Google Chat notifications.
* Follows configured instructions.
* Returns appropriate responses when information is unavailable.
* Does not fabricate metrics or connector actions.

---

### Deployment Checklist

Before publishing, verify:

* Gemini Enterprise application configured.
* Agent Designer enabled.
* Google Drive connector configured.
* Enterprise Search connector configured.
* Google Chat connector configured.
* Agent instructions configured.
* Knowledge document uploaded.
* AI model selected.
* Starter prompts configured.
* Campaign generation tested.
* Competitor research validated.
* Budget optimization validated.
* Video generation validated.
* Audio advertisement generation validated.
* Google Chat notification validated.
* End-to-end workflow tested successfully.

---

## g. Its Effectiveness — Business Value

| Monotonous daily task | With the Low-Code Agent | Business value |
| --- | --- | --- |
| Writing responsive search headlines, descriptions and extensions by hand for every campaign | Full Google Search Ads asset set generated from a single campaign brief | Removes the highest-volume repetitive task in paid search |
| Rewriting the same campaign message for Google, Meta, LinkedIn, Display and YouTube | Platform-specific ad copy generated for every channel from one objective | One brief, every channel covered |
| Manually researching competitor messaging and trending keywords | Enterprise Web Search produces competitor summaries, industry trends and search-based insights | Market intelligence without the manual trawl |
| Building budget allocation spreadsheets and ROAS models | Google Sheets-ready budget table with allocation strategy and optimization recommendations | Media plans ready for review in one prompt |
| Briefing creative teams and waiting on storyboards | Google Vids storyboard, voice-over script, scene breakdown and production assets generated directly | Creative concepting compressed from days to minutes |
| Scripting and producing short audio spots | Audio advertisement with voice-over, music suggestions, sound effects and CTA | Radio/podcast assets without a separate production cycle |
| Writing campaign status updates for the marketing team | Google Chat campaign summary prepared, or drafted if posting is unavailable | Consistent team communication with no extra write-up |
| Assembling marketing reports from scattered sources | Professional marketing reports grounded in the workflow knowledge document | Reporting that matches an agreed standard every time |

**Key outcomes**

* **Compresses the full campaign cycle** — research, ad copy, budget, video, audio and reporting all run from prompts against one knowledge source.
* **No fabricated performance data** — the agent is explicitly instructed not to invent metrics and to label estimates as estimates.
* **No falsely claimed connector actions** — if an action could not be performed, the agent says so instead of implying success.
* **Grounded in an agreed workflow** — `Paid_Media_Agent_Workflow.docx` keeps campaign planning, optimization and reporting consistent across the team.
* **Multi-format output from one brief** — text, spreadsheet, video and audio assets produced from the same campaign objective.

---

## h. Sample Execution

Sample prompts for agent validation.

![Chat with agent](images/06-chat-with-agent.png)

### Test Case 1 – Google Ads Generation

**Prompt**

> Create Google Search Ads for an AI Analytics platform targeting B2B marketing managers.

**Expected Result**

* Responsive Search Headlines
* Descriptions
* Callout Extensions
* Structured Snippets
* Professional ad copy

---

### Test Case 2 – Competitor Research

**Prompt**

> Research competitors for AI Analytics platforms and summarize their messaging and industry trends.

**Expected Result**

* Competitor summary
* Industry trends
* Trending keywords
* Search-based insights

---

### Test Case 3 – Budget Optimization

**Prompt**

> Recommend a budget allocation strategy for a $50,000 paid media campaign.

**Expected Result**

* Google Sheets-ready budget table
* ROAS recommendations
* Budget allocation strategy
* Campaign optimization suggestions

---

### Test Case 4 – Video Generation

**Prompt**

> Create a 30-second promotional video for our AI Analytics platform.

**Expected Result**

* Google Vids storyboard
* Voice-over script
* Scene breakdown
* Production assets
* Promotional video (if supported)

---

### Test Case 5 – Audio Advertisement

**Prompt**

> Generate a 15-second audio advertisement for our AI Analytics platform.

**Expected Result**

* Voice-over
* Music suggestions
* Sound effects
* CTA

---

### Test Case 6 – Google Chat Notification

**Prompt**

> Prepare a Google Chat summary for the marketing team highlighting campaign recommendations.

**Expected Result**

* Google Chat message generated
* Or draft message if direct posting is unavailable

---

## Input Sample Data

Sample input files for this agent: [`sample_data/`](sample_data/)
