---
title: LLM psychometrics
created: 2026-01-03
modified: 2026-01-07
date: 2026-01-07
description: Literature review on applying psychometric methods to LLMs.
tags:
  - machine-psychology
  - psychometrics
  - literature-review
draft: false
---

# LLM Psychometrics

## Key Finding

Psychometric self-report does not predict LLM interactive behavior. While LLMs produce consistent, differentiated personality profiles when administered standard instruments (Big Five, HEXACO), these profiles fail to predict how models actually behave in scenarios that should elicit trait-relevant responses. The abstraction layer that makes personality measurement useful for humans—trait scores predicting behavioral tendencies—breaks for LLMs.

This finding redirects the field from personality assessment to direct behavioral measurement.

## The Validity Problem

[The Personality Illusion](https://arxiv.org/abs/2509.03730) (Huang et al., 2025) provides the empirical demonstration:

**What works**: LLMs produce stable, coherent personality profiles when administered standard inventories. Profiles differentiate between models and remain consistent across runs.

**What doesn't**: These profiles don't predict interactive behavior. High-Agreeableness models don't cooperate more. High-Honesty-Humility doesn't predict deception resistance. The correlation between self-reported trait and actual behavior is negligible.

For humans, personality measurement succeeds because:
- Self-report correlates with peer ratings
- Both correlate with behavioral tendencies
- The abstraction (trait → behavior) holds across contexts

For LLMs, the abstraction breaks. Self-report is consistent, but it measures training artifacts rather than generalizable behavioral tendencies.

## The Existing Literature

The field of LLM psychometrics is mature. A [systematic review](https://arxiv.org/abs/2505.08245) (Ye et al., 2025) synthesizes 474 papers applying psychometric principles to LLMs across benchmarking, evaluation, validation, and enhancement.

Existing work includes:
- Multiple studies administering Big Five/HEXACO to LLMs
- Behavioral benchmarks for specific traits (sycophancy, honesty)
- Situational assessment attempts
- Large-scale multi-instrument studies ([Li et al., 2025](https://openreview.net/forum?id=im8tT8Hpfu)) using 6 instruments across many models

Li et al. (2025) found that RLHF predicts lower psychopathy (β=-0.45), models show amplified prosocial traits (agreeableness d=1.22), and their Personality-Architecture Embedding model predicts architectural features from personality scores with 71% accuracy. These findings confirm that profiles reflect training choices—but reflection isn't prediction.

## Why Personality Abstraction Exists for Humans

In human psychology, personality measurement solves an economic problem: observing behavior directly is expensive. We tolerate the indirection (measure trait, infer behavior) because the abstraction holds and direct observation doesn't scale.

For LLMs, neither condition applies:
- Behavioral testing scales—thousands of scenarios evaluated cheaply
- Self-report doesn't predict behavior anyway

The abstraction costs more than it provides.

## What Psychometric Profiles Actually Measure

Our [[/research/artifacts/hexaco-profiling|HEXACO profiling]] experiments produced clear, differentiated profiles. Claude scores high on Honesty-Humility. GPT-4 shows different factor structure. These patterns are stable and replicable.

This is interesting as evidence of training artifacts. RLHF and constitutional AI create consistent patterns in how models respond to personality items. But interesting isn't useful. These profiles describe how models respond to a specific class of prompts, not how they behave across contexts.

Descriptive curiosity, not actionable tool.

## Implications for Method

The field has shifted to direct behavioral measurement. Tools like Anthropic's Petri and Bloom enable large-scale behavioral evaluation across diverse scenarios without requiring psychometric abstraction. Measure what you care about directly.

This doesn't mean personality constructs are irrelevant—they may inform scenario design or help interpret behavioral patterns. But they don't substitute for behavioral testing.

## Open Question

"Behavioral testing scales" is an empirical bet, not a principled exclusion. Behavioral measurement tells you what happens, not why or how to predict before running the test.

If the goal is understanding and control—not just measurement—other paths remain open. Mechanistic interpretability could eventually predict behavior from model internals. Organizational dynamics could explain emergent patterns in multi-agent systems.

Current bet: behavioral measurement plus organizational dynamics advances the research questions (human understanding and control of multi-agent AI systems) faster than mechanistic interpretability in its current state. But this is contingent on the state of the tools and the specific research questions, not a permanent position.

---

*See also*: [[/research/artifacts/hexaco-profiling|HEXACO Profiling]], [[/research/notes/behavioral-evals|Behavioral Evaluation Tools]], [[/research/index|Research Questions]]
