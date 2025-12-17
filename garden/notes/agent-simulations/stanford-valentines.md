---
title: Valentine's Day
subtitle: A proof-of-concept simulation
status: active
tags:
  - agent-simulations
---

# Valentine's Day in Miniverse

This is a proof-of-concept for [Miniverse](https://github.com/miniverse-ai/miniverse), a Python library I built for running Stanford-style generative agent simulations. The scenario recreates the Valentine's Day party coordination from the original Generative Agents paper—but dramatically simplified.

It's not a research finding. It's a sanity check that the tool works and a starting point for actual experiments.

## What I was testing

The Stanford paper showed 25 agents autonomously coordinating a Valentine's Day party over ~17,000 time steps. Information about the party spread from one agent to 13 through natural conversation.

I wanted to see if the core phenomenon—information diffusion through agent communication—would show up in a much simpler setup. Five agents, 10 time steps, basic memory. If it works, I have a tractable baseline for running many variations. If it doesn't, I need more infrastructure.

## The setup

**Agents**: 5 (Isabella the cafe owner, Maria the grad student, Klaus the musician, Ayesha the journalist, Tom the hardware store owner)

**Time**: 10 ticks at 3-hour intervals (30 simulated hours, Feb 13-14)

**Actions**: Just two—`communicate` and `move_to`

**Memory**: Simple recent-message storage. No semantic retrieval, no reflection, no importance scoring.

**Goal injection**: Isabella's profile includes "Host a Valentine's Day party at the cafe on Feb 14, 5-7pm." Other agents don't know about it initially.

Here's what Isabella's system prompt looks like:

```
I am Isabella Rodriguez.
I am 28 years old.
I work as a cafe owner.
Background: I opened Hobbs Cafe to bring people together.
My personality is warm and social.
My skills include: hospitality (expert), event_planning (expert), cooking (advanced).
My goals are: Build a thriving community hub, Host a Valentine's Day party at the cafe on Feb 14, 5-7pm.
My relationships with others:
- maria: Friend; knows she likes Klaus
- klaus: Occasional customer
```

Other agents get neutral starting contexts—Maria's working on her thesis, Klaus is composing music, etc.

## What happened

**Tick 1**: Isabella reached out to Maria about the party. Maria contacted Klaus (her goal is to reconnect with him). Ayesha contacted Isabella (seeking story leads). Everyone started moving toward connections that made sense given their profiles.

**By tick 10**: All 5 agents knew about the party. Information spread through multiple paths—Isabella told Maria and Ayesha directly; Maria passed it to Klaus; Tom learned through business coordination with Isabella.

The agents behaved consistently with their profiles. Ayesha looked for a story angle. Maria saw the party as a chance to see Klaus. Tom offered promotional support. Nobody did anything weird or out of character.

## What this shows (and doesn't show)

**Shows**: Miniverse can run a basic simulation where information spreads and agents act consistently with their profiles. The library works.

**Doesn't show**: That this is robust, that it would replicate with different random seeds, that these results generalize, or that we've learned something about LLM social behavior.

This was one run of one scenario. The Stanford paper ran thousands of time steps with 25 agents. Proper experiments would need many runs with controlled variation—different personality profiles, different network structures, different scenarios.

## Comparison to Stanford

| | Stanford (2023) | This demo |
|---|---|---|
| Agents | 25 | 5 |
| Time steps | ~17,000 (10-sec) | 10 (3-hour) |
| Memory | Retrieval + reflection | Simple FIFO |
| Diffusion | 4% → 52% | 20% → 100% |

The full diffusion in my run is probably because 5 agents is a dense network—everyone's connected to everyone through Isabella. With 25 agents, information has to hop through intermediaries.

## What I want to try next

- **Personality variation**: Give agents different HEXACO profiles, see if behavior changes predictably
- **Multiple runs**: Same scenario, different seeds, see how much variance there is
- **Sparse networks**: Agents who aren't all connected to each other
- **Longer simulations**: See if behavior stays coherent over more ticks, or if it drifts without reflection

## Running it yourself

```bash
git clone https://github.com/miniverse-ai/miniverse.git
cd miniverse
uv sync

export LLM_PROVIDER=openai
export LLM_MODEL=gpt-4o-mini
export OPENAI_API_KEY=your_key

uv run python examples/smallville/valentines_party.py
```

There's also a Jupyter notebook at `examples/smallville/valentines_party.ipynb` that shows the prompts and walks through what's happening.

---

## Related

- [Generative Agents paper](https://arxiv.org/abs/2304.03442) — The original Stanford work
- [Miniverse repo](https://github.com/miniverse-ai/miniverse) — The library
- [Research log](/notes/research-log) — Research roadmap
