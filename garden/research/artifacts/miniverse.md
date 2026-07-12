---
title: Miniverse
description: Python library for running generative agent simulations.
date: 2025-11-01
tags:
  - tools
  - multi-agent
  - simulation
---

# Miniverse

Python library for running Stanford-style generative agent simulations.

**Repository**: [github.com/miniverse-ai/miniverse](https://github.com/miniverse-ai/miniverse)

## Overview

Multi-agent dynamics research needs a platform for controlled experiments:
- Vary agent profiles, observe coordination outcomes
- Test different team compositions
- Replicate phenomena (information diffusion, role emergence, conflict patterns)
- Generate behavioral data for analysis

Miniverse allows developers to create simulated environments for experimenting with multi-agent systems.

Generate agents with profiles, goals, and memory interacting over time. Agents decide actions, communicate, move through environments. Information spreads, coordination emerges (or fails), behavior patterns become observable.

The [Stanford Generative Agents paper](https://arxiv.org/pdf/2304.03442) ran 25 agents for ~17,000 time steps with sophisticated memory systems. Miniverse generalizes their approach and enables rapid experimentation through a minimalist library which can be fully ingested into AI context and used to essentially *vibe code* simulations.

---

*See also*: [[/research/artifacts/valentines-replication|Valentine's Replication]]
