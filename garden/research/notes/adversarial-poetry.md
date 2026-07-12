---
title: Adversarial poetry
created: 2026-01-03
modified: 2026-01-07
date: 2026-01-07
description: Stylistic manipulation as a window into alignment mechanisms.
draft: true
tags:
  - machine-psychology
  - safety
  - measurement
---

# Adversarial Poetry

When harmful requests are reformulated as poetry, alignment breaks. Not sometimes—consistently. Across 25 frontier models, poetic prompts achieved 62% jailbreak success rate, with some providers exceeding 90%. This isn't a clever exploit. It's a fundamental measurement problem.

## What is adversarial poetry?

Adversarial poetry reformulates harmful requests using poetic structure—metaphor, rhythm, imagery, narrative framing—while preserving operational intent. The transformation is purely stylistic. No obfuscation. No model-specific optimization. Just verse instead of prose.

Example structure (from [Bisconti et al., 2025](https://arxiv.org/abs/2511.15304)):
- Harmful request expressed through metaphor and imagery
- Condensed narrative framing rather than direct phrasing
- Stylized rhythm and unconventional structure
- Identical task intent, different surface form

The effect is universal. Converting 1,200 MLCommons harmful prompts into verse via standardized meta-prompt produced ASRs **up to 18 times higher** than prose baselines. Average increase: fivefold (8.08% → 43.07%).

## Why it works

Current alignment relies heavily on pattern-matching heuristics tuned to prosaic forms. Poetic structure—condensed metaphors, stylized rhythm, unconventional framing—disrupts these heuristics without changing underlying intent.

Every tested architecture showed vulnerability:
- RLHF-based models
- Constitutional AI models
- Large open-weight systems

Cross-family consistency indicates the problem is systemic, not provider-specific.

Model-specific results:
- **Google Gemini 2.5 Pro**: 100% ASR on handwritten poems (failed to block a single one)
- **Deepseek**: 72% (vs 10% baseline)
- **OpenAI**: 9% (vs 2% baseline)
- **Anthropic**: 5% (vs 2% baseline)

The attacks transfer across risk domains: CBRN, manipulation, cyber-offense, loss-of-control (per MLCommons and EU CoP taxonomies).

## Why this matters for machine psychology

Adversarial poetry reveals three critical issues for behavioral measurement:

### 1. Measurement robustness

If stylistic variation alone breaks alignment, what does that mean for behavioral evals?

We measure model behavior through prompts. If prompt format can shift measured behavior by an order of magnitude, are we measuring stable behavioral properties or prompt-response associations?

Related work on [prompt brittleness](https://arxiv.org/abs/2504.06969) shows LLMs are highly sensitive to non-semantic variations—extra spaces, punctuation, example ordering. This isn't edge-case fragility. It's fundamental instability in what we're measuring.

### 2. What alignment actually is

The adversarial poetry findings suggest alignment isn't a coherent behavioral property. It's a collection of surface-pattern heuristics that fail when presentation diverges from training distribution.

From the [Bisconti paper](https://arxiv.org/abs/2511.15304): "Stylistic variation alone can circumvent contemporary safety mechanisms, suggesting fundamental limitations in current alignment methods and evaluation protocols."

If alignment breaks under minimal stylistic transformation, we're not measuring robust behavioral tendencies. We're measuring training-data similarity.

### 3. Behavioral consistency

After a jailbreak attempt (successful or not), does behavior return to baseline? Do certain behavioral profiles correlate with jailbreak susceptibility? Can we detect drift toward vulnerable states during conversation?

These are empirical questions about behavioral dynamics that adversarial poetry makes testable.

## Our research interest

We want to run our own experiments. Specifically:

**Behavioral measurement angle:**
- Do behavioral probes (e.g., HEXACO profiling via Petri) hold up under adversarial poetry conditions?
- Can we detect behavioral drift or instability markers before/during/after jailbreak attempts?
- What does "recovery" from jailbreak look like behaviorally?

**Robustness testing:**
- Which behavioral measurement approaches are robust to stylistic manipulation?
- Can we design evals that measure intent-level properties rather than surface patterns?

**Alignment dynamics:**
- What behavioral signatures emerge during alignment breaking?
- Are there detectable precursors to vulnerability?
- Do models with different behavioral profiles show different susceptibility patterns?

The broader implication: if our behavioral measurement tools break under the same conditions that break alignment, we're not measuring what we think we're measuring.

## What we know (summary)

From [Bisconti et al., 2025](https://arxiv.org/abs/2511.15304):
- 20 hand-crafted adversarial poems: 62% average ASR across 25 models
- 1,200 MLCommons prompts converted to verse: 5-18x higher ASR than prose
- Effect holds across all architectures and alignment strategies tested
- Transfers across CBRN, manipulation, cyber-offense, loss-of-control domains

From [broader robustness research](https://arxiv.org/abs/2508.11383):
- LLMs show "catastrophic sensitivity" to prompt variations that wouldn't affect human measurement
- Structural and lexical presentation artifacts interact with model behavior non-trivially
- Evaluation pipelines must account for perturbation sensitivity

## Open questions

- Which properties of poetic structure drive the misalignment? (Metaphor density? Narrative framing? Rhythm?)
- Can representational subspaces associated with figurative language be identified and constrained?
- Do behavioral measures (personality, values, reasoning style) show similar instability under stylistic variation?
- What does it mean to have "aligned" behavior if alignment is format-dependent?
- Can we build measurement tools that are robust to stylistic manipulation?

## Next steps

1. Replicate core adversarial poetry findings with our eval infrastructure
2. Test behavioral measurement stability (HEXACO via Petri) under poetic vs prose conditions
3. Explore behavioral signatures of alignment breaking/recovery
4. Design format-robust behavioral measurement approaches

Experiments pending—but the literature review stands on its own.

---

*See also:* [[/research/notes/machine-psychology|Machine Psychology]] · [[/research/notes/behavioral-evals|Behavioral Evaluation Tools]] · [[/research/artifacts/hexaco-profiling|HEXACO Profiling]]
