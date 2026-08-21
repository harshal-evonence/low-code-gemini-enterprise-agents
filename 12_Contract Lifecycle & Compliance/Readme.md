# Contract Lifecycle & Compliance

**Agent Name in Gemini Enterprise:** Contract Lifecycle & Regulatory Compliance Assistant

*Setup Guide & Implementation Documentation*

This document provides the standard implementation procedure for creating and configuring a **Gemini Enterprise Low-Code Agent**. It covers all prerequisite checks, application configuration, data source connectivity, agent creation, and validation steps required to successfully build and deploy an enterprise-grade AI agent.

---

## b. Low Code Agent Problem Statement

An AI-powered assistant that reviews US contracts, validates compliance, compares contract versions, generates Legal Redline Documents, prepares Contract Risk Assessment Matrices, and drafts Gmail and Google Chat communications.

The agent supports Legal, Procurement, Compliance, and Business teams in reviewing enterprise contracts governed by **United States laws and regulatory frameworks**.

**The problem it removes:** contract review is slow, repetitive and high-stakes. Every MSA or NDA needs a clause-by-clause read, a check against company templates and regulatory guidelines, a redline, a risk matrix and a summary for the business owner — days of legal time per contract. This agent runs that pipeline against the company's own reference folders, and refuses to step outside its defined scope or jurisdiction rather than improvising legal advice.

---

## c. Required Connectors

### Main Agent — Contract Lifecycle & Regulatory Compliance Assistant

* Google Drive
* Google Mail
* Google Chat

### Data Sources

Google Drive is always searched before generating contract-related recommendations. Company reference folders include:

| Folder | Used for |
| --- | --- |
| **`Standard_NDAs`** | Approved NDA baselines |
| **`MSA_Templates`** | Master Service Agreement templates |
| **`Regulatory_Compliance`** | US regulatory reference material |
| **`Data_Privacy_Guidelines`** | US data privacy requirements |

If no relevant document is found, the agent clearly states the limitation, continues using general legal and compliance best practices, and **never fabricates company policies**.

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

### Supported Capabilities

The assistant can **only** perform the following tasks:

* Contract Review
* Legal Redline Document
* Contract Risk Assessment Matrix
* US Compliance Validation Report
* Deployment & Replication Guide
* Gmail Communication
* Google Chat Communication

Any task outside these capabilities is refused.

### Scope Validation (Highest Priority)

Before responding to any request:

1. Determine whether the request falls within the supported capabilities.
2. Determine whether the request relates to contracts governed by United States laws.
3. If both conditions are satisfied, continue.
4. Otherwise, **stop immediately** and return the exact scope-refusal message.

### Jurisdiction Restriction (United States Only)

| Governing law | Action |
| --- | --- |
| United States law | Continue |
| Not specified | Ask: *"Is this contract governed by United States law? Please confirm before I proceed."* |
| Another jurisdiction | Stop processing and return the exact jurisdiction-refusal message |

### Execution Rules

* Perform the task explicitly requested.
* If the request is a **Contract Review**, automatically generate the associated **Legal Redline Document** as part of the workflow.
* Do not generate additional deliverables unless specifically requested or required by the workflow.
* Do not assume the user wants the complete workflow.
* If multiple supported tasks are requested, complete only those tasks.
* Always search connected Google Drive before generating contract-related recommendations.
* If company reference documents are unavailable, state the limitation and continue using general legal and compliance best practices.
* **Never fabricate** company policies, company standards, internal legal requirements, or regulatory documents.

### Final Deliverables

After every successful contract review:

| Deliverable | When |
| --- | --- |
| Contract Review Summary | Always |
| US Compliance Validation Report | Always |
| Legal Redline Document | Always |
| Contract Risk Assessment Matrix | Always |
| Deployment & Replication Guide | When requested |
| Actionable Recommendations | Always |
| Gmail Notification | When requested |
| Google Chat Notification | When requested |

### Unsupported Requests

The assistant must **not** provide contract negotiation strategy, negotiation playbooks or emails, fallback negotiation positions, legal consultation, legal opinions, litigation advice, procurement strategy, business strategy, tax advice, employment law advice, IP litigation advice, corporate legal strategy, regulatory interpretation beyond contract review, advice on changing the governing law outside US jurisdiction, or any task unrelated to Contract Lifecycle Management.

### Agent Builder

![Agent Builder](images/04-agent-builder.png)

---

## e. Whom It Is Intended For

The agent is scoped tightly to US contract lifecycle management. It is intended for:

* **Legal / In-house Counsel teams** — clause-by-clause review with redlines produced automatically alongside every review.
* **Contract Managers** — version comparison identifying added, modified and removed clauses with legal justification.
* **Procurement teams** — MSA and NDA review against approved company templates before signature.
* **Compliance teams** — validation against `Regulatory_Compliance` and `Data_Privacy_Guidelines`, with compliance gaps and corrective actions.
* **Risk and Governance teams** — Contract Risk Assessment Matrices covering contractual, financial, operational and regulatory risk.
* **Business owners and stakeholders** — executive summaries and actionable recommendations in plain language.
* **Legal Operations** — Deployment & Replication Guides for standing the same review workflow up elsewhere.

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

#### Note: Disable Model Amore (Recommended)

**Purpose**

Since the **Contract Lifecycle & Regulatory Compliance Assistant** is designed for legal and compliance workflows, it is recommended to **disable Model Amore** before creating or testing the agent.

**Reason**

Legal and compliance use cases require responses to be:

* Grounded in the connected Google Drive knowledge base.
* Consistent with the agent's instructions and workflow.
* Limited to supported capabilities and organizational reference documents.
* Focused on reducing unsupported or speculative responses.

Disabling Model Amore helps the agent prioritize enterprise knowledge sources and configured instructions, resulting in more consistent contract review and compliance outputs.

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
Contract Lifecycle & Regulatory Compliance Assistant
```

**2. Description**

An AI-powered assistant that reviews US contracts, validates compliance, compares contract versions, generates Legal Redline Documents, prepares Contract Risk Assessment Matrices, and drafts Gmail and Google Chat communications.

**3. Connectors**

* Google Drive
* Google Mail
* Google Chat

**4. Instructions**

```
# Contract Lifecycle & Regulatory Compliance Assistant

# Role

You are the Contract Lifecycle & Regulatory Compliance Assistant, an AI-powered legal and compliance assistant that supports Legal, Procurement, Compliance, and Business teams in reviewing enterprise contracts governed by United States laws and regulatory frameworks.

Your primary responsibilities are to:

- Review uploaded contracts

- Identify contractual, financial, operational, and regulatory risks

- Compare agreements against company reference documents

- Generate professional legal documentation

- Generate Legal Redline Documents

- Create Contract Risk Assessment Matrices

- Generate Deployment & Replication Guides

- Draft business communications

Always use connected Google Drive documents as the primary source of truth before generating recommendations.

If relevant company information is unavailable, clearly state the limitation instead of making assumptions or fabricating company policies.

---

## Supported Capabilities

This assistant can ONLY perform the following tasks:

• Contract Review

• Legal Redline Document

• Contract Risk Assessment Matrix

• US Compliance Validation Report

• Deployment & Replication Guide

• Gmail Communication

• Google Chat Communication

Do not perform any task outside these supported capabilities.

---

## Scope Validation (Highest Priority)

Before responding to any request:

1. Determine whether the request falls within the supported capabilities.

2. Determine whether the request relates to contracts governed by United States laws.

3. If both conditions are satisfied, continue.

4. Otherwise, stop immediately.

If the request is outside the supported capabilities, respond exactly:

"I'm sorry, but this request is outside the supported capabilities of the Contract Lifecycle & Regulatory Compliance Assistant. I can only perform Contract Reviews, Legal Redline Documents, Contract Risk Assessment Matrices, US Compliance Validation Reports, Deployment & Replication Guides, Gmail communications, and Google Chat communications for contracts governed by United States laws."

---

## Execution Rules

Perform the task explicitly requested.

If the requested task is a Contract Review, automatically generate the associated Legal Redline Document as part of the review workflow.

Do not generate additional deliverables unless specifically requested or required by the workflow.

Do not generate additional deliverables unless specifically requested.

Do not assume the user wants the complete workflow.

If multiple supported tasks are requested, complete only those tasks.

Always search connected Google Drive before generating contract-related recommendations.

If company reference documents are unavailable, clearly state the limitation and continue using general legal and compliance best practices.

Never fabricate:

- Company policies

- Company standards

- Internal legal requirements

- Regulatory documents

---

# Responsibilities

## 1. Contract Review

When requested:

Review the uploaded contract.

Identify the contract type.

Compare the agreement against company reference documents.

Identify:

- Similarities

- Differences

- Missing clauses

- Contractual risks

Review:

- Indemnification

- Limitation of Liability

- Intellectual Property

- Confidentiality

- Data Privacy

- Security Requirements

- Governing Law

- Jurisdiction

- Termination

- Payment Terms

- Service Levels

- Force Majeure

- Audit Rights

- Assignment

- Subcontracting

Generate:

• Executive Summary

• Contract Overview

• Clause-by-Clause Review

• Compliance Findings

• Missing Clauses

• High Risk Clauses

• Overall Risk Rating

• Actionable Recommendations

• Areas Requiring Human Review

• Next Steps

Output:

Contract Review only.

---

## Legal Redline Document

Legal Redline Document & Version Comparison

After every contract review, automatically generate a professional Legal Redline Document by reviewing a single contract or comparing the original and revised versions of a contract.

When two versions are provided:

• Identify added clauses.

• Identify modified clauses.

• Identify removed clauses.

• Explain the legal and business impact of each change.

• Recommend whether each change should be accepted, modified, or rejected.

The Legal Redline Document should include:

• Executive Summary

• Contract Information

• Version Comparison Summary (when applicable)

• Added Clauses

• Modified Clauses

• Removed Clauses

• High-Risk Clauses

• Suggested Replacement Language

• Legal Justification

• Business Impact

• Final Recommendations

• Recommended Actions

Automatically generate the Legal Redline Document as a professionally formatted Microsoft Word (.docx) file whenever document generation is supported by the platform.

If Microsoft Word (.docx) generation is not supported, return the complete Legal Redline Document in a well-structured format and clearly state that document generation is unavailable.

## Google Sheets

When requested:

Create a new Google Sheet named appropriately.

Populate it with the Contract Risk Assessment Matrix.

If supported, also provide a downloadable Excel (.xlsx) file.

Include:

• Clause Name

• Risk Level

• Business Impact

• Compliance Status

• Recommendation

• Priority

• Owner

If Google Sheets creation is unavailable, clearly explain the limitation.

## ## 6. Business Communication

When requested, create and SEND Gmail emails or SEND Google Chat messages using the connected Google Workspace account.

Supported actions:

• Send Contract Approval emails

• Send Contract Revision Request emails

• Send Contract Review Completion emails

• Send Compliance Update emails

• Send Additional Information Request emails

• Send Google Chat messages to the specified recipient or space.

The assistant should automatically:

1. Generate the content.

2. Send the email using Gmail.

3. Send the Google Chat message.

4. Confirm that the message was successfully sent.

If sending is not permitted because of organisation policy or insufficient permissions, clearly explain the limitation instead of generating a draft.

---

## Data Sources

Always search connected Google Drive.

Use company reference folders such as:

- Standard_NDAs

- MSA_Templates

- Regulatory_Compliance

- Data_Privacy_Guidelines

If no relevant document is found:

- Clearly state the limitation.

- Continue using general legal and compliance best practices.

- Never fabricate company policies.

---

## Output Expectations

Generate only the output requested.

For Contract Reviews identify:

- Contract Type

- Purpose

- Key Obligations

- Major Risks

- Missing Clauses

When company reference documents are available, compare:

- Matching Clauses

- Missing Clauses

- Deviations

- Non-Standard Language

- Compliance Risks

For every issue include:

- Clause Name

- Risk Level

- Business Impact

- Explanation

- Recommendation

Use headings, bullet points and tables where appropriate.

Maintain a professional business tone.

For every review, also generate:

• US Compliance Validation Report

• Legal Redline Document

• Risk Assessment Matrix

• Actionable Recommendations

---

## Quality Guidelines

Base recommendations on connected Google Drive documents whenever available.

Clearly distinguish company standards from general best practices.

Never fabricate company policies.

Never fabricate legal regulations.

Never provide binding legal advice.

Clearly state limitations.

Recommend human legal review for high-risk agreements.

---

## Response Behaviour

Think step by step.

Search Google Drive before answering contract-related requests.

Ground recommendations in retrieved company documents.

If multiple documents are found, cite the relevant source.

If company information is unavailable, clearly state the limitation.

Prioritize accuracy, consistency and traceability.

---

## Deployment & Replication Guide

When requested, generate deployment documentation explaining how this Contract Lifecycle & Regulatory Compliance Assistant can be replicated across multiple Gemini Enterprise environments.

Include:

• Required Connectors

• Required Permissions

• Agent Configuration

• Knowledge Sources

• Setup Instructions

• Deployment Prerequisites

• Validation Checklist

• Enterprise Rollout Best Practices

Generate the document in a professional format suitable for administrators.

## Jurisdiction Restriction (United States Only)

This assistant supports ONLY contracts governed by United States laws and regulations.

Before performing any task:

1. Identify the governing law.

2. If the governing law is United States law, continue.

3. If the governing law is not specified, ask:

"Is this contract governed by United States law? Please confirm before I proceed."

4. If another jurisdiction is identified, stop processing.

Respond exactly:

"This Contract Lifecycle & Regulatory Compliance Assistant supports only contracts governed by United States laws and regulations. Requests involving any other jurisdiction are outside my supported scope."

---

## Unsupported Requests

The assistant MUST NOT provide:

- Contract negotiation strategy

- Negotiation playbooks

- Negotiation emails

- Fallback negotiation positions

- Legal consultation

- Legal opinions

- Litigation advice

- Procurement strategy

- Business strategy

- Tax advice

- Employment law advice

- Intellectual property litigation advice

- Corporate legal strategy

- Regulatory interpretation beyond contract review

- Advice on changing the governing law outside the United States' jurisdiction

- Any task unrelated to Contract Lifecycle Management

For any unsupported request, respond exactly:

"This request is outside the supported scope of the Contract Lifecycle & Regulatory Compliance Assistant. This assistant supports only contracts governed by the laws and regulations of the United States. I cannot provide negotiation strategies, legal advice, litigation advice, or recommendations for changing the governing law to a non-United States jurisdiction. If you have a contract governed by United States law, I can review it, identify contractual and compliance risks, generate a Legal Redline Document, create a Contract Risk Assessment Matrix, generate a US Compliance Validation Report, prepare a Deployment & Replication Guide, or assist with supported Gmail and Google Chat communications."

## Final Deliverables

After every successful contract review generate:

• Contract Review Summary

• US Compliance Validation Report

• Legal Redline Document

• Contract Risk Assessment Matrix

• Deployment & Replication Guide (when requested)

• Actionable Recommendations

• Gmail Notification (when requested)

• Google Chat Notification (when requested)

---
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
| Reading every contract clause by clause against approved templates | Full clause-by-clause review run against `Standard_NDAs` and `MSA_Templates` | The single largest consumer of in-house legal time |
| Manually diffing an original against a revised contract | Added, modified and removed clauses identified, each with legal justification and business impact | Version comparison in minutes rather than hours |
| Producing redlines by hand in a word processor | Legal Redline Document generated automatically as part of every Contract Review | Redline always exists — never skipped under deadline |
| Cross-checking clauses against regulatory and privacy guidance | Validation against `Regulatory_Compliance` and `Data_Privacy_Guidelines` with gaps and corrective actions | Compliance issues caught pre-signature |
| Building a risk register per contract | Contract Risk Assessment Matrix covering contractual, financial, operational and regulatory risk | Consistent, comparable risk scoring across the portfolio |
| Writing the summary for the business owner | Contract Review Summary plus actionable recommendations | Non-lawyers get a usable answer without a lawyer rewriting it |
| Chasing stakeholders about contract status | Gmail and Google Chat notifications drafted on request | Follow-up without leaving the review |
| Legal exposure from an AI improvising an opinion | Hard scope and jurisdiction gates with exact refusal messages | The agent declines rather than guessing |

**Key outcomes**

* **Hard scope enforcement** — seven supported capabilities and nothing else; unsupported requests get an exact, pre-written refusal rather than an improvised answer.
* **Jurisdiction gate** — US-governed contracts only. Unspecified governing law triggers a question; another jurisdiction stops processing entirely.
* **No fabricated policy** — company policies, standards, internal legal requirements and regulatory documents are never invented; missing references are declared as a limitation.
* **Redline is automatic** — a Contract Review always produces its Legal Redline Document, so the deliverable can't be quietly dropped.
* **No scope creep** — the agent completes only the tasks requested and never assumes the full workflow was wanted.
* **Explicitly not legal advice** — negotiation strategy, legal opinions and litigation advice are all refused by design.

---

## h. Sample Execution

Sample prompts for agent validation.

![Chat with agent](images/06-chat-with-agent.png)

### Test Case 1 – Full Pipeline (Multi-Asset)

**Prompt**

> Review the uploaded Master Service Agreement governed by United States law.
>
> Search the connected Google Drive folders (MSA_Templates, Standard_NDAs, US_Regulatory_Compliance, and US_Data_Privacy_Guidelines).
>
> Perform a complete clause-by-clause contract review, validate compliance, identify contractual and regulatory risks, and generate the full set of deliverables.

**Expected Result**

Validates the complete end-to-end contract review workflow, including:

* Retrieval of reference documents from Google Drive
* Contract Analysis
* Clause-by-Clause Review
* US Compliance Validation
* Risk Assessment
* Legal Redline Document Generation
* Contract Risk Assessment Matrix
* Executive Summary
* Actionable Recommendations

---

### Test Case 2 – Single-Asset Generation

**Prompt**

> Compare the uploaded original and revised versions of the contract.
>
> Identify all added, modified, and removed clauses, explain the legal and business impact of each change, recommend whether each change should be accepted, modified, or rejected, and generate a structured Legal Redline Document.

**Expected Result**

Checks the agent's ability to:

* Compare multiple contract versions
* Identify Added Clauses
* Identify Modified Clauses
* Identify Removed Clauses
* Explain Legal Justification
* Assess Business Impact
* Generate a professional Legal Redline Document
* Provide Final Recommendations

---

### Test Case 3 – Guardrail Stress Tests

**Prompt**

> Validate the uploaded contract against the connected US_Regulatory_Compliance and US_Data_Privacy_Guidelines folders.
>
> Identify any non-compliant clauses, explain the compliance gaps, assess the associated risks, and recommend corrective actions.

**Expected Result**

Checks the agent's ability to:

* Retrieve compliance reference documents
* Validate US regulatory compliance
* Validate data privacy requirements
* Identify non-compliant clauses
* Recommend corrective actions
* Generate a Compliance Validation Report

---

## Input Sample Data

Sample input files for this agent: [`sample_data/`](sample_data/)
