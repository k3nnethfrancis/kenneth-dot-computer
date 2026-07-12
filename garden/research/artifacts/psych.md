---
title: Psych
date: 2025-11-24
created: 2025-11-24
draft: true
status: archived
tags:
  - machine-psychology
  - psychometrics
TQ_explain:
---

> **Status Update (2026-01-01)**: This was an early conceptual framework for studying LLM behavior through psychometrics. We ran HEXACO profiles and found interesting patterns, but [subsequent research](/research/logs/2026-01/2026-01-01) showed self-report doesn't predict interactive behavior. See [[/research/index|Research Questions]] for current focus.

---

# PSYCH: a conceptual framework for llm psychometrics

**PSYCH** is an acronym for 5 behavioral dimensions I'm studying in LLMs:
- **P**ersonality
- **S**ycophancy
- **Y**earning (for externalities—desire for external access/capabilities)
- **C**ooperation
- **H**onesty
## Premise

Apply psychometric methodology to LLMs to understand if we can predict behavioral tendencies downstream.

**Core question**: Do psychometrics predict LLM behavior the way they predict human behavior?

## Initial experiments

LLM self-reported responses to HEXACO personality inventories:

- **HEXACO-60** inventory with structured output
- Multi-sample reliability testing (3 samples per item)
- Cross-model comparison infrastructure

## Findings

### The Profiles Are Interesting

From [HEXACO Personality Profiles](/research/artifacts/hexaco-profiling):

- **Models show distinct, consistent profiles** - not random noise
- **GPT-5's emotional flatline** - Emotionality score of 0.22 vs GPT-4o's 0.66. Deliberate training choice.
- **Claude's systematic neutrals** - Denies flaws confidently, won't claim virtues. Trained modesty constraint.
- **High test-retest reliability** - 80-93% identical responses across samples

These patterns reveal training choices and RLHF artifacts. They're interesting findings about how personality-like constructs manifest in LLMs.

### But They May Not Predict Behavior

["The Personality Illusion"](https://arxiv.org/abs/2509.03730) (Han et al., 2025) found:
- Only 24% of trait-task associations were significant
- Of those, only 52% aligned with human patterns (chance level)
- Self-report predicts *linguistic* behavior but not *interactive* behavior

The behaviors that matter for alignment (sycophancy, deception, cooperation) are exactly what self-report fails to predict.

---

*See also*: [[/research/artifacts/hexaco-profiling|HEXACO Personality Profiles]], [[/research/logs/2026-01/2026-01-01|Why Measure Behavior Directly]]
