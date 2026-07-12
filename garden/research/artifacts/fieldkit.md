---
title: Machine psychologist's fieldkit
description: Tools for rigorous machine psychology research.
date: 2026-01-28
tags:
  - machine-psychology
  - tools
  - methodology
---

# Machine Psychologist's Fieldkit

As I continue to learn the art of red teaming, AI behavioral science, and machine psychology, I will come across certain methods that I want my coding agents to retain as skills.

This fieldkit is both a collection of those skills and a Claude Code plugin for accessing them.

**Repository**: [github.com/k3nnethfrancis/machine-psychology-fieldkit](https://github.com/k3nnethfrancis/machine-psychology-fieldkit)

## Installation

```bash
claude plugin marketplace add https://github.com/k3nnethfrancis/machine-psychology-fieldkit
claude plugin install machine-psychology-fieldkit
```

## Current skills

- **petri-collaborator** — Run adversarial audits with Petri. Helps design seed instructions, execute evaluations, and interpret the 36-dimension behavioral scores.
- **bloom-collaborator** — Generate evaluation scenarios with Bloom. Specify a behavior hypothesis, and it creates diverse probes to measure elicitation rate.

## Status

Active experimentation. See [[/research/logs/2026-01-28|2026-01-28 log]] for initial Petri experiments.

---

*See also*: [[/research/notes/machine-psychology|Machine Psychology]], [[/research/index|Research Questions]]
