---
title: "Give Your AI Agents a North Star"
date: 2026-03-03
description: "Most organisations give their AI agents tasks. The ones that succeed give them purpose — and guardrails to check every decision against it."
image: "/images/blog/give-your-ai-agents-a-north-star.jpg"
---

Klarna's AI agent reduced customer resolution times from 11 minutes to 2 in its first month.

Then customers started leaving.

The agent was brilliant at closing tickets fast. But that was the wrong goal. Klarna's real objective wasn't speed — it was building lasting customer relationships in a competitive fintech market. A human agent knows when to flex a policy, when to spend an extra few minutes because the customer's tone says they're about to churn. The AI knew none of that. It had instructions, yes. It didn't have *purpose*.

Most organisations deploying AI agents today are making similar mistakes. They give agents tasks without giving them the bigger picture — what the organisation actually cares about, what trade-offs are acceptable, and what damage looks like.

## The Pattern That Already Works

Software engineers have started solving this. In AI-assisted coding, there's a pattern where structured files like `AGENTS.md` sit in a project and tell the agent: here's how we work, here's what good looks like, here are the boundaries. The agent checks its work against these files before acting. It works remarkably well.

The question is: why aren't we doing this for organisations?

OKRs align humans to shared objectives — but they assume human judgment about trade-offs and exceptions. AI agents don't absorb company culture at all-hands meetings. They can't read between the lines. They need it written down, structured, and checkable.

## INTENT.md — The Organisational North Star

Imagine an `INTENT.md` file — the organisational equivalent of `AGENTS.md` — that gives every AI agent in your business access to an agent-readable document that defines:

🎯 **What the organisation is actually trying to achieve** — not vague aspirations, but specific goals with measurable signals

🎯 **Guardrails that prevent harm** — before any decision is executed, the agent checks it won't negatively impact customers, revenue, reputation, or compliance

🎯 **Trade-off hierarchies** — when speed conflicts with quality, or cost conflicts with customer experience, here's how to resolve it

🎯 **Escalation boundaries** — what the agent can decide alone, and what must go to a human

The critical piece is the guardrails. Klarna's agent didn't check whether "resolve this faster" was degrading the thing that actually mattered. An agent with proper guardrails would have flagged: "I can close this in 90 seconds, but the customer's sentiment suggests they're about to churn — escalating."

## This Isn't Science Fiction

The pattern already works in software development. The shift is applying the same structured, machine-readable discipline to business objectives, values, and decision frameworks.

The companies that win at AI will be the ones that give their agents a north star — and the guardrails to check every decision against it.

Klarna gave its agent a metric. It needed to give it a mission.
