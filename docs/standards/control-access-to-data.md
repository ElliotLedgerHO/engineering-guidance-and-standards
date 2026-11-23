---
layout: standard
order: 1
title: Control access to data
date: 2026-11-23
id: SEGAS-00021
tags:
  - Generative AI
  - Artificial intelligence (AI)
  - Data
  - Security
---

Teams must only make data available to a tool, service or integration when they have assessed and understood the risk, and the accountable data owner has explicitly approved the use. This applies to all tools and services, including artificial intelligence (AI) tools, models, agents and AI-enabled integrations. This standard also sets out the requirements that are specific to AI.

In this standard, "data" includes production and non-production data, documents, source code, logs, telemetry, configuration and contextual information. For AI, it also includes prompts, retrieval sources, embeddings (numerical representations of content that AI uses to search and compare), vector stores (databases that hold embeddings) and outputs derived from those sources.

---

## Requirement(s)

- [Teams MUST assess data sensitivity and business impact before use](#teams-must-assess-data-sensitivity-and-business-impact-before-use)
- [Teams MUST assess threat and privacy risks before use](#teams-must-assess-threat-and-privacy-risks-before-use)
- [The accountable data owner MUST approve use](#the-accountable-data-owner-must-approve-use)
- [Teams MUST only use sensitive data with approved services](#teams-must-only-use-sensitive-data-with-approved-services)
- [Teams MUST access data only through approved interfaces that limit and log access](#teams-must-access-data-only-through-approved-interfaces-that-limit-and-log-access)
- [Teams MUST provide independent evidence of controls before approval](#teams-must-provide-independent-evidence-of-controls-before-approval)
- [Approval MUST be reviewed when conditions change](#approval-must-be-reviewed-when-conditions-change)

### Teams MUST assess data sensitivity and business impact before use

Teams must formally assess the sensitivity of the data, and the business impact of its potential exposure, misuse or loss, before they make it available to a tool or service. This includes AI capabilities. The assessment gives the data owner the information they need to make an approval decision.

Before use, teams must complete a Business Impact Assessment. They must not treat the absence of personal information as evidence that data is safe to use – non-personal data can still carry significant business, operational, security, commercial or reputational risk.

### Teams MUST assess threat and privacy risks before use

Teams must assess each proposed use of data by a tool or service against credible threat scenarios. The scenarios must be specific to the tool, model, integration, environment and use case.

The threat assessment must consider, where relevant:

- unauthorised disclosure or exfiltration (data being copied out of the organisation's control)
- retrieval of information outside the user's authorised scope
- retention by the service provider (for AI, the model provider as well)
- leakage through logs, caches or telemetry
- cross-user, cross-tenant or cross-environment data exposure
- inference or re-identification
- poisoning or manipulation of source data
- insecure integrations, plugins or APIs
- supply-chain and third-party compromise
- failure to delete data in line with retention requirements

For AI, the threat assessment must also consider, where relevant:

- prompt injection, where an attacker hides instructions in an input to change what the AI does
- indirect prompt injection, where the hidden instructions are in content the AI retrieves or reads
- use of organisational data for model training or service improvement
- leakage through prompts, outputs or embeddings
- reconstruction of data from models or outputs
- insecure Model Context Protocol (MCP) servers, which connect AI tools to data and other systems

Where teams process personal data, or processing could materially affect individuals, they must complete a Data Protection Impact Assessment (DPIA). If a DPIA already exists, they must explicitly review and update it. The DPIA must cover:

- the role of the tool or service (for AI, the role of the AI capability)
- data flows
- lawful basis
- necessity
- proportionality
- data-subject impact, meaning the impact on the people the data is about
- retention
- international transfers
- mitigations

Teams must complete the threat assessment and DPIA early enough to influence design. They must not produce them retrospectively to justify a decision already made.

### The accountable data owner MUST approve use

The accountable data owner must approve the use of the data for a specified tool or service and use case before teams enable access. For AI, the approval must name the AI tool, model and use case. The accountable data owner is the Information Asset Owner (IAO), the Senior Responsible Owner (SRO) or another formally delegated data owner.

The approval must be based on a risk decision document. This document must let the data owner understand the nature, likelihood and impact of the residual risk they are accepting. Residual risk is the risk that remains after controls are applied. Teams must explain technical terms in the document, and must not reduce risk acceptance to a generic statement that the owner "accepts the risk".

The approval applies only to the specific combination of:

- data
- tool or service
- model (for AI)
- use case
- users
- interfaces and integrations
- hosting and processing location
- operating environment

A material change to any of these must trigger reassessment and, where the risk changes, renewed approval.

### Teams MUST only use sensitive data with approved services

Teams must not submit the following to an externally hosted service or third-party service, including externally hosted AI models and AI services, unless the service and the specific processing activity have been explicitly approved:

- personal data
- special category data
- law-enforcement data
- operationally sensitive data
- other business-sensitive information

The approval must confirm that:

- the supplier is authorised to process the relevant data categories
- processing and storage locations are known and acceptable
- retention and deletion arrangements are defined
- the supplier will not use organisational data for service improvement unless explicitly authorised (for AI, this includes model training, prompts and outputs)
- tenant, customer and user data is appropriately segregated
- access is authenticated, authorised and logged
- contractual, data-protection and security obligations are met
- processing stays within the conditions recorded in the Technology Register and in the data owner's approval, as set out in [the data owner approval requirement](#the-accountable-data-owner-must-approve-use)

Teams must not assume that de-identification, redaction, anonymisation or pseudonymisation is effective. They need evidence that is proportionate to the re-identification and inference risk.

### Teams MUST access data only through approved interfaces that limit and log access

Tools, services and AI agents must access organisational data only through approved interfaces. These interfaces enforce the permissions, filtering, purpose limitations and logging that the approved use case needs.

An interface must appear on the Technology Register for the approved use case. An interface is an API, retrieval service, integration or, for AI, an MCP server. Each interface must:

- authenticate the user, service or agent
- enforce least privilege and source-level permissions
- restrict retrieval to the minimum data required
- apply relevant filtering, redaction or data loss prevention (DLP) controls
- log requests, retrieved sources, actions and access decisions
- support suspension or revocation of access

For AI, each interface must also:

- prevent the AI capability from expanding its own access
- keep credentials and secrets from being exposed to the model

Teams must not use personal accounts, personal access tokens, copied credentials, direct database connections or other workarounds to bypass an approved interface.

### Teams MUST provide independent evidence of controls before approval

Teams must support the controls they rely on to protect data with objective evidence. A statement from a team or supplier that a control exists is not enough.

Acceptable evidence can include:

- system-generated configuration exports
- access-control and permission reports
- audit logs and monitoring records
- test results showing allowed and denied behaviour
- penetration-test or security-assessment findings
- DLP test results
- for AI, model and prompt-security test results
- supplier contractual commitments backed by technical configuration
- retention and deletion test results
- independent review by an authorised security, privacy, architecture or assurance function

Evidence must demonstrate both:

- that a control can mitigate the identified risk (design)
- that the control is implemented and working in the relevant environment (operating effectiveness)

Teams must keep evidence with the approval record. Evidence must be current and attributable to the specific tool and environment.

Where teams cannot obtain evidence, they must record this as a residual risk for the data owner to consider explicitly. They must not represent it as an implemented control.

### Approval MUST be reviewed when conditions change

A data owner's approval must be reviewed whenever a material change occurs to the data, the tool or service, or the environment it covers. This keeps the approval based on the risk as it is now, not the risk when it was first given.

Material changes include:

- a new data source or category
- a change in sensitivity or classification
- a new supplier, hosting region or processing location
- a new integration, plugin or API
- wider user access
- a change to retention or service-improvement arrangements
- a material security incident or control failure
- a significant change to the threat assessment or DPIA
- expiry of an approval condition or review period
- for AI, a new model or model family, a new MCP server, increased autonomy or a change to training arrangements

Teams must suspend or restrict access where a required control is no longer effective and the resulting risk falls outside approved tolerance.

---
