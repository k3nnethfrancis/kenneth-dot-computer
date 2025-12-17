---
title: Agent simulations
tags:
  - machine-psychology
---

# Agent Simulations

Can we simulate multiple agents interacting and get behavior that matches how humans with similar profiles would act?

## Core Questions

**Do profiles predict social behavior?**

If agents have HEXACO profiles, do they behave accordingly in groups? Does high-Extraversion initiate more conversations? Does high-Agreeableness coordinate more easily? Does Honesty-Humility predict trustworthy behavior?

If profiles predict group behavior, we can design agent teams the way organizational psychologists think about human teams.

**Do agent dynamics match human social psychology?**

If we replicate classic experiments - information diffusion, coordination games, group polarization - do agents behave like humans with similar profiles would?

This would let us use agent simulations as a cheap proxy for human studies in some domains.

**What's the minimum viable simulation?**

Stanford ran 25 agents for ~17,000 time steps with sophisticated memory. The [Valentine's Day](/notes/agent-simulations/stanford-valentines) proof-of-concept ran 5 agents for 10 ticks with simple queues. Information diffusion and role-consistent behavior showed up in both.

How much infrastructure is actually necessary? If you can run 50 variations in an afternoon instead of a month, you can test hypotheses systematically.

## Experiments

**Personality variation**: Run identical scenarios with different HEXACO profiles. Does high-Agreeableness Isabella coordinate differently than high-Honesty-Humility Isabella?

**Network topology**: Dense vs sparse connections. What happens when information has to hop through intermediaries?

**Prediction from profiles**: Given agent profiles, can we predict diffusion patterns, coordination success, conflict emergence *before* running the simulation?

**Human comparison**: Run agents with profiles derived from real humans. Compare agent behavior to how those humans say they'd behave in the same scenario.

## Why This Matters

Agents will negotiate, plan, make decisions in groups. Multi-agent dynamics shape outcomes - cooperation, conflict, information flow, consensus formation.

If we can simulate these dynamics with fidelity to human behavior, we can test agent team compositions before deployment. Better to catch bad coordination patterns in simulation than production.

## Related

- [Valentine's Day](/notes/agent-simulations/stanford-valentines) - Proof-of-concept simulation
- [Reflection](/notes/machine-psychology/reflection) - Architecture effects on behavior
- [Research log](/notes/research-log) - Research roadmap
