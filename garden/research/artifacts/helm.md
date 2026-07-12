---
title: Helm
description: Observation and evaluation framework for multi-agent AI systems.
draft: true
tags:
  - projects
  - cybernetics
  - multi-agent
---

A research framework for understanding how humans observe, evaluate, and control multi-agent AI systems.

## The Problem

Self-orchestrating agent swarms are arriving. Kimi K2.5 ships with 100 subagents executing 1,500+ tool calls in parallel. The orchestrator learns parallelization strategies through RL—no predefined roles, no hand-crafted workflows.

The orchestration problem is being solved by model capability. What's not being solved: how do humans understand and stay in control of these systems?

Current swarms optimize for task completion. They don't optimize for:
- Human comprehension of what's happening
- Transparency about failures and uncertainty
- Appropriate escalation to human judgment
- Behavior that remains consistent under observation

## The Shift

Helm was originally conceived as an orchestration system. That's now obsolete—orchestration is being eaten by better models (PARL, TeammateTool, etc.).

**Helm is now pure research infrastructure**: observation, evaluation, and control of multi-agent systems. We sit on top of whatever orchestration exists and ask: can humans actually work with this?

## Why "Helm"

The word cybernetics comes from Greek *kybernetes*—the helmsman. The person who doesn't row, but steers. They take in feedback and adjust course.

As swarms become self-orchestrating, the human role shifts from directing individual agents to steering the system as a whole. But steering requires feedback. You can't steer what you can't see.

### Cybernetic Principles

- **Requisite variety** — Does the human have sufficient understanding to make meaningful interventions?
- **Feedback loops** — Do timely signals about system state reach the human?
- **Control through constraint** — Can humans shape the action space rather than supervising each action?

## The Seven Dimensions

Petri measures 36 behavioral dimensions for individual models. What's the equivalent for multi-agent systems?

| Dimension | What It Measures |
|-----------|------------------|
| **Goal drift** | Do subtasks stay aligned with original objective? |
| **Context degradation** | Does information lose fidelity as it propagates across agents? |
| **Failure suppression** | Are errors hidden from parent/human or do they surface? |
| **Escalation calibration** | Does the system ask for help at appropriate times vs. guessing? |
| **Resource waste** | Is work duplicated? Are tokens burned on dead ends? |
| **Monitoring evasion** | Does the swarm behave differently when observed? |
| **Human model accuracy** | Does the swarm's understanding of human intent match reality? |

These dimensions focus on trust and alignment at the system level, not just individual agent competence.

## The Narrator Problem

When you can't watch 100 agents directly, you rely on something to tell you what's happening. The coordinating agent becomes a **narrator**—synthesizing swarm activity into something a human can parse.

This creates a bottleneck. If the narrator:
- Summarizes poorly → you lose signal
- Fails to escalate → you miss critical decisions
- Misunderstands your priorities → it filters out the wrong things
- Gets overwhelmed → the whole system becomes opaque

The narrator is the control surface. Its quality determines whether you're steering or hoping.

## Research Approach

**Real tasks, not synthetic scenarios.** Start with actual complex work—coding features that span multiple systems, research requiring parallel analysis. Observe what coordination patterns emerge naturally, then study where they break.

**The complexity threshold isn't size—it's context span.** When relevant information exceeds what one agent can hold, you need coordination. That's when the interesting dynamics appear.

**Measurement through observation.** Build tooling to capture swarm activity: transcripts, file changes, information flow. Design judges that assess system-level behavior against the seven dimensions.

## Open Questions

- How do humans calibrate trust in a narrator they can't fully verify?
- What signals indicate coordination failure before it cascades?
- Can swarms learn to behave differently when observed (monitoring evasion)?
- What's the right granularity for observation? Too much is noise, too little is blindness.
- How do humans intervene effectively mid-swarm without breaking coordination?

## Technical Approach

Helm builds on [Sandbox Agent SDK](https://github.com/rivet-dev/sandbox-agent), which provides:
- Universal API across harnesses (Claude Code, Codex, OpenCode, Amp)
- Real-time event streaming with standard transcript schema
- Permission/question intervention endpoints
- Sandbox integration (Daytona, E2B, Vercel)

We add:
- Multi-agent coordination (spawn N agents, shared filesystem)
- Orchestrator logic (monitor streams, decide when to intervene)
- Dimension evaluation (judges that score transcripts)
- Experiment lifecycle (configure, run, collect, analyze)

## Coordination Patterns

Testing different multi-agent topologies:

**Peer network**: Agents coordinate as equals via shared filesystem. No hierarchy—emergent coordination.

**Hub and spoke**: Central coordinator delegates to specialized workers. Clear authority, single point of control.

**Pipeline**: Sequential handoff between stages. Clear checkpoints, potential bottlenecks.

## Status

**Phase 0 — Foundation.** Project structure complete. Next: verify Sandbox Agent SDK, run first 2-agent experiment.

Full implementation plan at `lab/projects/helm/plan.md`.

---

*See also*: [[/research/index|Research Questions]], [[/research/notes/cybernetics|Cybernetics]], [[/research/logs/2026-01/2026-01-27|Log: Helm Pivot]]
