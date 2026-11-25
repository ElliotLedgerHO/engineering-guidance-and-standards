---
layout: principle
order: 1
title: Verify AI-generated work before you trust it
date: 2026-11-24
tags:
  - Artificial intelligence (AI)
  - Generative AI
  - Quality engineering
related:
  sections:
    - title: Related links
      items:
        - text: Humans are accountable for AI-generated work
          href: /principles/humans-are-accountable-for-ai-generated-work/
        - text: Hold AI-generated work to existing standards
          href: /standards/hold-ai-generated-work-to-existing-standards/
        - text: Name an owner for every AI system
          href: /standards/name-an-owner-for-every-ai-system/
        - text: Code reviews
          href: /patterns/code-reviews/
---

You should base your trust in work produced with artificial intelligence (AI) on evidence. Verify AI-generated work independently, and use deterministic checks wherever you can.

You should measure your trust in AI output separately from how much you use it.

---

## Rationale

AI tools generate output probabilistically, so the same prompt can give different results each time. The output can look correct but contain errors, security weaknesses or refer to things that do not exist.

To meet the same expectations as any other work, you should verify AI output independently. Deterministic checks, such as quality gates and security scanning, give the same result every time for the same input. They give repeatable evidence at low cost. They cannot judge everything, such as whether a change meets the user need, so you also need independent review.

Independent review catches problems that the author, or the tool that produced the work, may have missed. Agree what reviewers check before the work starts, so reviews are consistent.

High use of AI tools does not prove high-quality output. If you only measure adoption, you cannot tell whether AI is improving your work or adding hidden risk. Measuring trust directly gives you the evidence to decide where to rely on AI and where to add more checks.

---

## Applications and Implications

To apply this principle, you should:

- have a person or agent other than the author review each AI-generated change against agreed criteria before it progresses, as set out in [Hold AI-generated work to existing standards](/standards/hold-ai-generated-work-to-existing-standards/)
- run deterministic checks, such as quality gates, on AI-generated work before review
- evaluate and test skills and prompts before you share them with other teams, as set out in [Name an owner for every AI system](/standards/name-an-owner-for-every-ai-system/)
- measure trust in AI output with its own metrics, such as the rate at which reviewers reject or change suggestions
- keep trust metrics separate from metrics that track adoption and use of AI tools

---
