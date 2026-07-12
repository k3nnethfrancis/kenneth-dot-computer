---
title: Memory and behavioral drift
created: 2026-01-03
modified: 2026-01-07
date: 2026-01-07
description: How memory and context affect agent behavior over time.
draft: true
tags:
  - machine-psychology
  - multi-agent
  - safety
---

# Memory and Behavioral Drift

How do memory systems and conversational context affect agent behavior over time? Does the agent "drift" in ways that matter for safety?

## The question

[deepfates asked](https://x.com/deepfates/status/2007169033456820696): "I think the user-based memory might be causing the parasitic entity dyad thing. How do we treat the AI psychosis/AI narcissism problem, who's working on this? Where is the research on in-memory learning over time and how the personality shifts?"

This is a behavioral measurement question:
- Does extended interaction change how agents behave?
- Do memory architectures (reflection, retrieval, FIFO) produce different drift patterns?
- Can we detect drift toward problematic states before they manifest?

## Why this matters

If memory/context shapes behavior over time:
- Architecture choices affect who the agent becomes, not just what it can do
- Human-AI co-evolution ("parasitic entity dyad") is a real phenomenon to study
- Monitoring for behavioral drift becomes a safety mechanism

If behavior stays stable regardless of memory architecture:
- Base model training is more determinative than scaffolding
- Safety interventions focus on training, not deployment architecture

## Experimental directions

**Reflection ablation**: Run identical simulations with and without reflection modules. Measure behavioral outcomes (cooperation, honesty, coordination) before and after extended runs.

**Architecture comparison**: Same agent configuration across different memory systems:
- Simple FIFO (first-in-first-out)
- Importance-weighted retention
- Semantic retrieval
- Reflection-augmented

Which produces more stable behavior over time? Which drifts toward problematic patterns?

**Long-horizon drift**: Extended simulations (simulated weeks). When does behavior change? What triggers drift? Does reflection prevent it or accelerate it?

**Human-AI dyad tracking**: In extended human-AI conversations, how does the AI's behavior change? Does it adapt to the human in ways that matter for safety (sycophancy drift, boundary erosion)?

## Connection to other work

This connects to [[/research/artifacts/miniverse|Miniverse]] (platform for testing these dynamics) and the broader question of how humans stay in control of systems that change over time.

## Status

Experiment designs, not yet tested. The tooling (Miniverse, behavioral probes) is in place—need to design and run the experiments.

---

*See also*: [[/research/artifacts/miniverse|Miniverse]], [[/research/notes/cybernetics|Cybernetics]]
