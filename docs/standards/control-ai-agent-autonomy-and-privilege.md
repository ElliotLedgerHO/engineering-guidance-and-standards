---
layout: standard
order: 1
title: Control AI agent autonomy and privilege
date: 2026-11-23
id: SEGAS-00022
tags:
  - Generative AI
  - Artificial intelligence (AI)
  - Security
  - Secure development
related:
  sections:
    - title: Related links
      items:
        - text: Use approved tools only
          href: /standards/use-approved-tools-only/
        - text: Control access to data
          href: /standards/control-access-to-data/
---

Teams must give an artificial intelligence (AI) tool or agent only the access its task needs, and only as much autonomy as the potential impact of its actions allows. Agents must use scoped credentials without seeing them. A person must approve any action an agent takes that is hard to reverse, through a control the agent cannot bypass.

An approval mode sets what an agent can do without asking a person first. An environment's reach is how far an agent's actions can affect other systems and data. This standard applies to all AI agents that teams build, configure or use.

---

## Requirement(s)

- [Agent permissions MUST be scoped to the task and granted just-in-time](#agent-permissions-must-be-scoped-to-the-task-and-granted-just-in-time)
- [Agents MUST use credentials without being able to see them](#agents-must-use-credentials-without-being-able-to-see-them)
- [Agents MUST only use tools on an approved list](#agents-must-only-use-tools-on-an-approved-list)
- [Agents MUST only delegate to agents on an approved list](#agents-must-only-delegate-to-agents-on-an-approved-list)
- [Teams MUST choose the least autonomous approval mode that can do the task](#teams-must-choose-the-least-autonomous-approval-mode-that-can-do-the-task)
- [Teams MUST cap the autonomy of an agent by the reach of its environment](#teams-must-cap-the-autonomy-of-an-agent-by-the-reach-of-its-environment)
- [Hard-to-reverse actions MUST have human approval through a gate the agent cannot bypass](#hard-to-reverse-actions-must-have-human-approval-through-a-gate-the-agent-cannot-bypass)

### Agent permissions MUST be scoped to the task and granted just-in-time

Teams must scope an agent's permissions to its specific task. Agents must:

- have only the access their task needs
- have privileges granted just-in-time, meaning for the duration of the task and not left in place indefinitely
- not be able to increase or broaden their own permissions

The owner of an agent should review its permissions regularly to confirm they are still the minimum the task needs.

### Agents MUST use credentials without being able to see them

Teams must give agents credentials through a scoped mechanism that never shows the underlying secret to the agent. Teams must not put real credentials, keys or sensitive information in a prompt.

Agents must not use real keys, certificates or other sensitive credentials. Teams must use synthetic (made-up) equivalents for testing instead.

### Agents MUST only use tools on an approved list

An agent must only use tools that appear on an explicitly approved list for its use case.

Teams must keep the approved tool list under version control. A person must approve any change to the list.

### Agents MUST only delegate to agents on an approved list

An agent must only delegate to other agents that its approved use case explicitly includes.

Teams must keep the list of approved agents under version control. A person must approve any change to the list.

### Teams MUST choose the least autonomous approval mode that can do the task

Teams must give an AI agent the least autonomous approval mode that can complete its task efficiently.

In the table, an allowlist is a list of commands that a team has approved in advance. A classifier is a tool that judges whether an action is safe.

The approval modes, from least to most autonomous, are:

| Approval mode | AI agent does | Human does | Typical use |
| --- | --- | --- | --- |
| Advice only | Proposes code or answers. Cannot change files or run commands. | Applies any changes. | Questions, code review and high-risk work where the agent should not act. |
| Approve each step | Makes changes and runs commands, but only after approval. | Approves each step or batch before it runs. | New or unfamiliar tasks, repositories or tools, and any work where no allowlist exists yet. |
| Pre-approved commands | Runs only commands on an allowlist the team has approved in advance. Asks for anything else. | Approves anything not on the allowlist. | Most day-to-day development using narrow commands, such as reading and searching files, and read-only `git` and diagnostic commands. |
| Automatic approval | Acts without asking when a classifier or tool setting judges the action safe. | Sets the rules and reviews the result. | Reversible work such as code edits and tests. |
| Unattended | Acts with no approval, or with permission checks off. | Nothing. | Experimental or throwaway work and long-running tasks, in an isolated sandbox only. |

Automatic approval is not human approval and is not a security boundary, because a classifier can be wrong or manipulated. Teams must only use it for reversible work.

### Teams MUST cap the autonomy of an agent by the reach of its environment

The reach tier of an environment sets the most autonomous mode an agent can run in. Higher reach permits only lower autonomy. An agent must run in the lower of the mode its task needs and the cap for its environment.

The table shows the cap for each reach tier:

| Environment reach tier | Most autonomous mode allowed | Conditions |
| --- | --- | --- |
| An isolated sandbox | Unattended | The sandbox has no internet access, no real data and no credentials to real systems. It has no outbound network access beyond the disposable sandbox. |
| The local working copy or branch | Automatic approval | Changes are reversible and go through pull request review. |
| Ephemeral non-production environments created for the task – read-only | Automatic approval | The agent's access is limited to that environment, with no network path to production. Test data is not real personal data. The environment is isolated from other users and torn down when the task ends. |
| Shared non-production systems – read-only | Pre-approved commands | The agent's access is limited to that environment, with no network path to production. Test data is not real personal data. Teams must verify that credentials cannot write. Teams make changes as code, and these go through pull request review and the approved continuous integration and continuous delivery (CI/CD) pipeline. |
| Production – read-only | Pre-approved commands | The agent reaches production through a team-run route, such as a Model Context Protocol (MCP) server, that holds the credential, enforces the allowlist and logs every request. An MCP server is a service that connects AI tools to data and other systems. Sources must be free of personal data and secrets. Teams must verify that the credential cannot write. Outbound network access must be restricted. The agent can use operational data only (logs, metrics and deployment history), with no database access. The Technical Design Authority (TDA) must approve the use case. |
| Production – read-write | Not allowed | Agents must not have read-write access to production systems. Teams make changes as code, and these go through approved pull requests and CI/CD pipelines. |

### Hard-to-reverse actions MUST have human approval through a gate the agent cannot bypass

A person must explicitly approve any action an agent takes that would be difficult to reverse, and teams must audit the approval. Teams must enforce this through a gate the agent cannot bypass.

---
