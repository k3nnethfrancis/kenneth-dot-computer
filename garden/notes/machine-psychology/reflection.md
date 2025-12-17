---
title: Reflection
tags:
  - machine-psychology
---

# Reflection

Does adding reflection modules to LLM agents change their psychometric profiles?

## The Question

Stanford's generative agents had a reflection module - periodically generating higher-level insights from memories ("Klaus is dedicated to his research"). This improved task performance. But did it change the agent's *personality*?

Would an LLM with reflection show different HEXACO scores than one without?

## Why This Matters

If reflection changes profiles, it means architecture choices shape personality, not just capability. We'd need to think about agent design differently - not just "what can it do" but "who does it become."

If profiles stay stable regardless of reflection, personality might be more fundamental to the base model than to the scaffolding around it.

## Experiments

**Reflection ablation**: Run identical simulations with and without reflection modules. Profile agents before and after extended runs.

**Architecture comparison**: Same persona across different memory systems:
- Simple FIFO (first-in-first-out)
- Importance-weighted retention
- Semantic retrieval

Which produces more stable profiles over time?

**Long-horizon drift**: Run extended simulations (simulated weeks). When do profiles drift without reflection? Does reflection prevent drift or just slow it?

## Connection to Self-Modeling

Related question: what happens if we give an LLM explicit access to its own response patterns? Let it reflect on its own tendencies?

This is different from memory-based reflection (which is about the world). Self-modeling reflection is about the agent's own behavior. Does behavior change? Does it become more or less predictable?

## Status

Not yet tested. These are experiment designs.

## Related

- [Valentine's Day](/notes/agent-simulations/stanford-valentines) - Proof-of-concept simulation (no reflection)
- [Research log](/notes/research-log) - Research roadmap
- [Functionalism](/notes/cybernetics/functionalism) - Framework for thinking about cognitive functions
