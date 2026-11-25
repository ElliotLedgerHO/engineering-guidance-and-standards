---
layout: standard
order: 1
title: Hold AI-generated work to existing standards
date: 2026-11-24
id: SEGAS-00024
tags:
  - Generative AI
  - Artificial intelligence (AI)
  - Quality engineering
  - Ways of working
related:
  sections:
    - title: Related links
      items:
        - text: Humans are accountable for AI-generated work
          href: /principles/humans-are-accountable-for-ai-generated-work/
        - text: Verify AI-generated work before you trust it
          href: /principles/verify-ai-generated-work-before-you-trust-it/
        - text: Managing the security of software dependencies
          href: /standards/managing-security-software-dependencies/
        - text: Code reviews
          href: /patterns/code-reviews/
        - text: Developer testing
          href: /standards/developer-testing/
        - text: Quality assurance and testing
          href: /principles/quality-assurance-and-testing/
---

Teams must hold work produced with artificial intelligence (AI) to the same standards and quality expectations as work created by people. An independent reviewer must check each AI-generated change before the team releases or uses it.

AI-generated work is any output that an AI tool or agent wrote, changed or suggested, in full or in part. This standard applies to all teams that use AI tools to produce code, configuration, documentation or other outputs.

---

## Requirement(s)

- [AI-generated work MUST meet existing standards and quality expectations](#ai-generated-work-must-meet-existing-standards-and-quality-expectations)
- [Teams MUST NOT use AI as a reason to lower or skip a standard](#teams-must-not-use-ai-as-a-reason-to-lower-or-skip-a-standard)
- [An independent reviewer MUST check AI-generated changes before release or use](#an-independent-reviewer-must-check-ai-generated-changes-before-release-or-use)
- [Teams MUST verify AI-suggested interactions with third parties](#teams-must-verify-ai-suggested-interactions-with-third-parties)

### AI-generated work MUST meet existing standards and quality expectations

AI-generated work must meet the same standards and quality expectations as work created by people. Quality expectations include readability, maintainability and test coverage, as set out in [Developer testing](/standards/developer-testing/) and [Quality assurance and testing](/principles/quality-assurance-and-testing/).

The way a team produced the work does not change the risk it carries once it is in a service.

### Teams MUST NOT use AI as a reason to lower or skip a standard

Teams must not use AI as a reason to bypass, weaken or defer an existing standard. This includes lowering quality expectations because AI produced the output quickly or in large amounts.

### An independent reviewer MUST check AI-generated changes before release or use

A reviewer independent of the author must review each AI-generated change before the team releases or uses it. Any agent that produced the change counts as the author. Teams must agree the review criteria in advance.

Reviewers should apply the same scrutiny to AI-generated work as to any other change, however polished it looks. AI output can look complete and confident while containing errors.

### Teams MUST verify AI-suggested interactions with third parties

Teams must check that any third party an AI tool suggests exists and is legitimate before they adopt it. Interactions with third parties include dependencies, such as packages, and integrations, such as external services and APIs.

AI tools can suggest packages or services that do not exist, or that have names similar to real ones. Attackers can publish malicious packages under those names. Teams must also assess the security of any dependency, as set out in [Managing the security of software dependencies](/standards/managing-security-software-dependencies/).

---
