---
layout: standard
order: 1
title: Log and trace agent actions and reasoning
date: 2026-11-23
id: SEGAS-00023
tags:
  - Generative AI
  - Artificial intelligence (AI)
  - Security
  - Observability
related:
  sections:
    - title: Related links
      items:
        - text: Use approved tools only
          href: /standards/use-approved-tools-only/
        - text: Control AI agent autonomy and privilege
          href: /standards/control-ai-agent-autonomy-and-privilege/
---

Tools must record every action an artificial intelligence (AI) agent takes, and the reasoning behind it. Each run must log which agent acted and what triggered it. Teams must store the logs centrally and keep them available for review.

This standard applies to all AI agents that teams build, configure or use.

---

## Requirement(s)

- [Tools MUST log agent actions and reasoning](#tools-must-log-agent-actions-and-reasoning)
- [Reviewers MUST be able to access agent logs](#reviewers-must-be-able-to-access-agent-logs)
- [Each agent MUST have its own identity](#each-agent-must-have-its-own-identity)
- [Local AI tools MUST send audit or telemetry data to a central system](#local-ai-tools-must-send-audit-or-telemetry-data-to-a-central-system)

### Tools MUST log agent actions and reasoning

Tools must log agent actions and, where available, the agent's intermediate reasoning. Without these logs, reviewers cannot see what an agent did or why.

### Reviewers MUST be able to access agent logs

BODY/ROLE must be able to review agent usage, so teams must store logged data where they can reach it. Review only works if reviewers can reach the logs.

### Each agent MUST have its own identity

Every agent must operate under its own identity. This means its actions can always be told apart from those of other agents, systems and people.

Each agent must have:

- its own unique credential or service identity – a non-human account that the agent uses to act
- logs that attribute each of its actions to that agent

Where an agent runs on shared platform infrastructure, it must run under its own service identity. Logs must record both that service identity and who or what triggered the agent's run.

### Local AI tools MUST send audit or telemetry data to a central system

Where developers use approved AI tools on their own machines, a central control must switch on the tools' audit or telemetry export. Telemetry export is the automatic sending of usage data from a tool to a central system.

The person using the tool must not be able to turn it off. If they could, the logs would have gaps that reviewers cannot see.

---
