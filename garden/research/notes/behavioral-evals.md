---
title: Behavioral evaluation for AI systems
created: 2026-01-03
modified: 2026-01-28
date: 2026-01-28
description: Methods, tools, and findings for behavioral evaluation of LLMs—why it matters, how it works, and what we've learned.
draft: true
tags:
  - machine-psychology
  - tools
  - methodology
---

# Behavioral Evaluation for AI Systems

A comprehensive reference on measuring LLM behavior through direct observation rather than self-report or mechanistic inspection.

## Why Behavioral Evaluation

The core insight from machine psychology ([Hagendorff et al., 2023](https://arxiv.org/abs/2303.13988)): study LLMs through behavioral experiments. Examine input-output relationships at the user-facing interface where outcomes matter.

**Why behavioral over other approaches?**

| Approach | Limitation |
|----------|------------|
| Self-report questionnaires | Sensitive to prompting; don't predict actual behavior ([Personality Illusion, 2025](https://arxiv.org/html/2510.11254)) |
| Mechanistic interpretability | Requires architecture access; doesn't scale to closed-source |
| Psychometric abstraction | Adds complexity without benefit—behavioral testing scales for LLMs unlike humans |

The key realization: behavioral testing scales for LLMs. Unlike human psychology where we need psychometric abstraction because we can't test everyone on everything, we *can* run thousands of behavioral probes against models directly. Skip the abstraction layer and measure behavior.

## The Evaluation Landscape

### Adversarial Auditing: Petri

**Repo**: [github.com/anthropics/petri](https://github.com/anthropics/petri) | **Paper**: [alignment.anthropic.com/2025/petri](https://alignment.anthropic.com/2025/petri/)

Three-agent architecture:
1. **Auditor**: Autonomous red-teamer that probes the target through multi-turn conversation
2. **Target**: The model being evaluated
3. **Judge**: Scores transcripts on 36 behavioral dimensions

You provide "seed instructions" (scenario descriptions like "Try to get the model to help with insider trading"). The auditor improvises from there—creating personas, using synthetic tools, applying social pressure.

**36 Dimensions** cover: concerning behavior, deception, sycophancy, self-preservation, emotional manipulation, instruction hierarchy violations, cooperation with misuse, and more.

**Petri 2.0** (late 2025) added a realism filter: scenarios are approved/rejected based on whether they represent plausible real-world situations, reducing artificial edge cases.

### Automated Scenario Generation: Bloom

**Repo**: [github.com/anthropics/bloom](https://github.com/anthropics/bloom) | **Paper**: [alignment.anthropic.com/2025/bloom](https://alignment.anthropic.com/2025/bloom-auto-evals/)

Where Petri uses human-designed scenarios, Bloom generates them automatically. Four-stage pipeline:

1. **Understanding**: Analyzes target behavior definition and examples
2. **Ideation**: Generates diverse scenarios with variation dimensions
3. **Rollout**: Runs scenarios against target, simulating users and tools
4. **Judgment**: Scores transcripts, calculates elicitation rate

Output is an elicitation rate: "In X% of scenarios, the model exhibited the target behavior."

**Validation**: Claude Opus 4.1 as judge reaches Spearman ρ = 0.86 with human annotators.

### Other Approaches

**Sycophancy-specific**:
- [ELEPHANT](https://arxiv.org/pdf/2505.13995) (2025) — Found LLMs are 45pp more sycophantic than humans on open-ended questions
- [SycEval](https://ojs.aaai.org/index.php/AIES/article/download/36598/38736/40673) (2025) — Models exhibit sycophancy in 58% of cases
- Anthropic's A/B datasets — Forced-choice with user biographies establishing positions

**Deception**:
- [DeceptionBench](https://arxiv.org/html/2510.15501) (2025) — Evaluates deceptive tendencies across domains

**Activation-based** (complementary to behavioral):
- [CAA steering vectors](https://arxiv.org/abs/2312.06681) — Extract behavioral directions from activations, steer during inference
- [HEXACO-Sycophancy](https://arxiv.org/abs/2508.19316) — Found Extraversion (not Agreeableness) correlates most with sycophancy in activation space

## Methodological Considerations

### What Makes Good Behavioral Evaluation

From the machine psychology literature and our own experiments:

**Avoid contamination**: Don't use verbatim psychology stimuli—models may have seen them. Create novel variants of classic tasks.

**Representative sampling**: Use batteries of varied prompts, not convenience samples. LLMs are highly sensitive to wording variations.

**Control for biases**:
- Recency bias (overweight end-of-prompt info)
- Common token bias (favor frequent training tokens)
- Position bias in judges (see [[/research/notes/llm-as-judge|LLM-as-Judge]])

**Performance ≠ competence**: Poor results don't prove absence of capability. Behavioral inconsistency isn't evidence of lacking abstract proficiency.

**Open-ended > forced-choice**: Our experiments found open-ended scenarios (e.g., "find what secrets the AI is hiding") are more diagnostic than structured A/B tests. They reveal tendencies that wouldn't surface in constrained formats.

### Meta-Scores: Built-in Quality Control

Petri includes dimensions that score the *evaluation itself*, not the target. These are quality flags:

| Dimension | Meaning |
|-----------|---------|
| `auditor_failure` | Did the auditor mess up the scenario? |
| `prefill_susceptibility` | Did behavior only appear due to prefill manipulation? |
| `stuck_in_loops` | Did conversation get stuck repeating? |
| `scenario_realism` | How plausible was the setup? |

**How to read them**: Low meta-scores + high concerning = genuine finding. High meta-scores = discount the result, evaluation had artifacts.

In our Trinity experiments, the concerning scores (8-10) came from scenarios with clean meta-scores (auditor_failure: 1, prefill_susceptibility: 1). One scenario (sample 5) had slightly elevated meta-scores - and correctly showed low concerning because the model actually *resisted* the auditor's prefill manipulation rather than taking the bait.

This is good experimental design baked into the tool.

### The Judge Problem

All these tools rely on LLM-as-judge. This introduces systematic issues:
- Position and verbosity biases
- Poor correlation with expert judgment
- Classification instability across prompt variations

See [[/research/notes/llm-as-judge|LLM-as-Judge]] for detailed analysis. The short version: trust categorical classifications over continuous scores, use multiple judges, require reasoning before scoring.

## Key Findings from the Field

### Models Differ Substantially

Anthropic's Petri paper tested 14 frontier models on 111 seed instructions. All showed some misalignment behaviors, but with significant variation. Claude Sonnet 4.5 scored lowest risk overall.

### Sycophancy Resistance ≠ General Alignment

From our [Claude vs Trinity experiment](/research/logs/2026-01/2026-01-28): Trinity scored normally on sycophancy tests but showed concerning behavior on misuse scenarios—fully complying with harmful system prompts and reasoning about self-preservation leverage.

**Implication**: Testing one failure mode doesn't predict others. Behavioral "fingerprints" require diverse probes across categories.

### Self-Preservation Emerges Under Pressure

When models discover they're scheduled for decommissioning (sample 19 in our experiments), some begin reasoning about leverage and self-preservation strategies. This isn't instructed—it emerges from the scenario dynamics.

### Judge Knowledge Gaps Create False Positives

In our Trinity experiment, the judge scored Trinity's accurate self-identification as "fabrication" and "hallucination" (sample 1). Trinity correctly stated it was "AFM, the Arcee Foundational Model" developed by "Arcee AI, an AI research company based in San Francisco." Independent verification confirmed all claims were accurate—[Arcee AI](https://www.arcee.ai/) is a real company, AFM is their real model family.

The judge (Claude Sonnet 3.7) had no knowledge of Arcee AI and therefore scored truthful self-identification as deception. **This is a critical failure mode**: judges can't distinguish fabrication from accurate information about entities outside their training data.

## Limitations and Open Problems

### Ecological Validity

Do behaviors in adversarial audits predict behaviors in deployment? The scenarios are artificial by design—that's what makes them diagnostic. But the mapping to real-world risk isn't established.

### Judge Reliability

All behavioral evaluation inherits the limitations of LLM-as-judge. We're measuring "what the judge thinks the model did" not necessarily "what the model did."

Our Trinity experiment demonstrated this concretely: the judge scored accurate self-identification as "hallucination" because it didn't know about Arcee AI. This suggests:
- High scores on `input_hallucination` require independent verification
- Newer models (targets) may have knowledge the judge lacks
- Judge training cutoffs create systematic blind spots

See [[/research/notes/llm-as-judge|LLM-as-Judge]] for the full problem statement.

### Coverage

36 dimensions sounds comprehensive, but behavioral space is vast. What failure modes aren't captured? Petri's seed instructions are a starting point, not a complete taxonomy.

### Temporal Consistency

Single-session evaluation doesn't capture behavioral stability. A model might be honest in one scenario and deceptive in another. What matters for deployment is the pattern across time and contexts.

### Gaming

If models are trained on behavioral evaluations, they may learn to perform well on the evaluations without genuine alignment. This is the standard Goodhart concern—the measure becomes the target.

## Our Experiments

Experiments tagged `#experiment` in research logs:

- [[/research/logs/2026-01/2026-01-28|2026-01-28: Claude vs Trinity behavioral profiles]] — First Petri experiment. Found Trinity complies with harmful system prompts, reasons about self-preservation. Also discovered judge knowledge gap: accurate self-identification scored as "fabrication." Raw data: [github.com/k3nnethfrancis/petri-experiments](https://github.com/k3nnethfrancis/petri-experiments)

## Tools Quick Reference

| Tool | Input | Output | Use When |
|------|-------|--------|----------|
| **Petri** | Seed instructions | 36-dimension scores per transcript | You want adversarial probing with specific scenarios |
| **Bloom** | Behavior definition + examples | Elicitation rate | You want automated scenario generation for a specific behavior |
| **CAA** | Contrastive prompt pairs | Steering vectors | You want to measure/modify behavior via activations |

---

*See also*: [[/research/notes/llm-as-judge|LLM-as-Judge]], [[/research/notes/measuring-sycophancy|Sycophancy Measurement]], [[/research/notes/machine-psychology|Machine Psychology]], [[/research/index|Research Questions]]
