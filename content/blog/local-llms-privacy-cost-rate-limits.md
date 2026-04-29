---
title: "Local LLMs, Privacy and the Work That Should Stop Using Models"
date: 2026-04-29
description: "Local LLMs are not about replacing frontier models. They make more AI use cases viable, and they help reveal which workflows should eventually become ordinary software."
image: "/images/blog/local-llms-privacy-cost-rate-limits.jpg"
---

I’ve been experimenting with running local LLMs at home, and it has changed how I think about AI adoption.

Privacy is the obvious benefit. If I’m working with personal notes, job search data, drafts, logs or workflow experiments, keeping that processing local feels very different from sending every prompt to a cloud model.

But the bigger unlock has been *freedom*.

When every experiment uses a frontier model in the cloud, you become aware of cost, rate limits and quota. You start rationing ideas. You avoid background jobs. You think twice before processing messy data at volume.

A local model changes that. It may not match GPT-5.5 or Claude for hard reasoning, but it is good enough for a lot of useful work: classifying jobs, summarising logs, checking routine alerts, drafting first-pass notes and running scheduled agents.

That matters because a lot of AI value comes from small, repeated pieces of work. The kind of work that becomes too expensive, too slow, or too sensitive if every step needs a frontier model.

There is another step after that: *remove the LLM where it no longer adds value*.

Once a workflow is understood, some parts should become rules, thresholds, checks or ordinary code. That is not a downgrade. It is often the mature version of the workflow: cheaper, faster, easier to test and easier to trust.

My current view is layered:

- Use frontier models where quality and judgement really matter.
- Use local models where privacy, volume and persistence matter.
- Use deterministic workflows where the decision logic is stable enough that the model is unnecessary.

For organisations, the question is not only “which model is best?”. It's:

- Which work needs the best model?
- Which work needs to stay private?
- Which work needs to run often enough that cost and rate limits become the blocker?
- Which work should stop using a model once the process is understood?

That is where local LLMs get interesting. They do not need to win every benchmark. They make more AI use cases viable, and they help reveal which ones should eventually become ordinary software.

[Originally posted on LinkedIn](https://www.linkedin.com/posts/sanjivranjanuk_ive-been-experimenting-with-running-local-activity-7455330571079172096-ixZi).
