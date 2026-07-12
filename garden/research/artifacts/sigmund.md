---
title: Sigmund
subtitle: AI Co-Scientist for Machine Psychology
draft: true
tags:
  - machine-psychology
  - ai-scientist
  - research-tools
---

# Sigmund

An AI co-scientist trained for machine psychology research.

## What Sigmund Is

Sigmund is a specialized model we're training to conduct machine psychology research - designing behavioral experiments, analyzing agent interactions, synthesizing literature, and making discoveries about AI systems.

Not a chatbot. Not an assistant. A research collaborator with deep expertise in psychology and the skills to study AI behavior scientifically.

## Core Capabilities

**Experiment design** - Generate novel experimental protocols for studying AI behavior. Translate research questions into testable hypotheses with appropriate controls.

**Behavioral analysis** - Analyze conversational and behavioral data from AI systems. Identify patterns, anomalies, and psychologically meaningful signals.

**Literature synthesis** - Connect findings across machine psychology, cognitive science, and AI safety. Identify gaps and contradictions in existing research.

**Tool creation** - Build new instruments and evaluation frameworks when existing tools are insufficient.

**Discovery** - Find genuinely novel patterns in AI behavior that advance understanding of how these systems work.

## The Ideal Form

A mature Sigmund would:
- Produce novel experiments using behavioral evaluation tools (Anthropic's Petri, Bloom, etc.)
- Create new evaluation frameworks when existing tools are insufficient
- Make discoveries about AI behavior that humans wouldn't find alone
- Write research that meets publication standards
- Operate with graduated autonomy - from co-pilot (human reviews everything) to autopilot (routine analysis runs independently)

## Training Strategy

Still in development. Current thinking:

**Approach**: Two-stage training following recent AI scientist literature:
1. Conversation priming on research dialogue patterns (establishes internal reasoning structure)
2. Rubric-based reinforcement learning where evaluation criteria encode what counts as good machine psychology research

**Base model**: 32B parameter range - runs inference on local hardware (96GB M3 Mac Studio), trains on cloud (Tinker or similar)

**Training data**:
- Research traces from ongoing work (session logs, experiment designs, literature reviews)
- General research reasoning corpus (Meta RPG's 22K samples show cross-domain transfer)
- Domain-specific rubrics defining quality criteria for machine psychology

**Key insight from literature**: Level II learning (revising how you learn) separates useful AI scientists from failures. Systems without self-correction show 42% failure rates and majority hallucinated results ([Sakana evaluation](https://arxiv.org/abs/2502.14297)).

## Why This Matters

Machine psychology is a nascent field studying AI behavior using methods from psychology. The research questions are clear:
- How do AI systems actually behave (vs. what they say they'll do)?
- How do humans understand and control multi-agent AI systems?
- What behavioral patterns emerge in agent interactions?

But the field lacks dedicated research tools. Sigmund is an attempt to build one - a model that understands psychology deeply enough to study AI systems rigorously.

## Status

**Phase**: Training strategy development

Currently:
- Collecting research traces through ongoing work
- Studying existing behavioral evaluation tools (Petri, Bloom)
- Reviewing AI co-scientist literature to refine training approach
- Defining rubrics for machine psychology research quality

The capability profile is ambitious. We're figuring out what's actually trainable.

---

*See also*: [[/research/artifacts/psych|Psych]], [[/research/artifacts/hexaco-profiling|HEXACO Profiling]], [[/research/index|Research Questions]]

**Key references**:
- [SAGA: Scientific Autonomous Generation Agent](https://arxiv.org/abs/2512.21782) - Bi-level architecture with objective evolution
- [Google AI Co-Scientist](https://arxiv.org/abs/2502.18864) - Tournament-based hypothesis generation
- [Meta RPG: Rubric-based rewards for research](https://arxiv.org/abs/2512.23707) - Training methodology
- [Societies of Thought](https://arxiv.org/abs/2601.10825) - Internal reasoning structure in trained models
- [Towards Scientific Intelligence Survey](https://arxiv.org/abs/2503.24047) - Landscape mapping
