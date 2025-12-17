---
title: Machine psychology
tags:
  - machine-psychology
---

Foundational framework for applying psychological experimental methods to LLMs. This 2023 paper (updated 2024) from DeepMind and collaborators establishes machine psychology as a discipline.

**Paper**: [arXiv:2303.13988](https://arxiv.org/abs/2303.13988)
**Authors**: Hagendorff, Dasgupta, Binz, Chan, Lampinen, Wang, Akata, Schulz

## Core Thesis

Study LLMs through behavioral experiments rather than (or alongside) mechanistic interpretability. Examine input-output relationships at the user-facing interface where outcomes matter, rather than inspecting weights and activations.

**Why behavioral over mechanistic?**
- Scales with model size (no architecture access needed)
- Works with closed-source models
- Captures emergent behaviors too complex to predict from weights alone
- Operates where real-world impact occurs

## Four Primary Research Domains

### 1. Heuristics and Biases
Decision-making shortcuts and cognitive distortions. Studies found GPT-3 displayed human-like biases, but newer models largely eliminated them (possibly due to training improvements or data contamination).

**Paradigms**: Framing effects, ecological rationality, semantic content variations

### 2. Social Interactions
Theory of mind, cooperative/competitive behavior, communicative trade-offs.

**Paradigms**: False belief tasks (Wimmer & Perner), recursive mental state reasoning, negotiation dilemmas, network formation (preferential attachment, triadic closure)

### 3. Psychology of Language
Syntax, semantics, pragmatics processing.

**Paradigms**: Surprisal measures, priming techniques, garden path sentences, filler-gap dependencies, entailment assessment

### 4. Learning
In-context learning mechanisms, inductive biases, generalization.

**Paradigms**: Rule-based vs exemplar-based generalization, curriculum learning effects, spacing/repetition impacts, developmental psychology comparisons

## Design Standards: Good Behavioral Experimentation

The paper's methodological guidelines are essential reading for anyone running psych evals on LLMs.

### Avoid Data Contamination
- Don't copy psychology stimuli verbatim - models may have seen them
- Create "novel variants of classic" tasks with new wording, agents, scenarios
- Use procedurally generated experiments when possible

### Use Representative Sampling
- "Batteries of varied prompts" not small convenience samples
- LLMs are highly sensitive to minor wording variations
- Test multiple versions of each task systematically

### Control for Technical Biases
- **Recency bias**: LLMs overweight end-of-prompt information
- **Common token bias**: Models favor frequent training tokens
- **Majority label bias**: Few-shot examples skew toward frequent labels

**Mitigations**: Shuffle answer orders, use varied prompt formulations, document temperature settings

### Performance-Competence Distinction
From Chomsky: performance in a situation may not capture underlying competence. Poor results don't prove absence of capability - behavioral inconsistency isn't evidence of lacking abstract proficiency.

### Capability Elicitation Caveat
Chain-of-thought prompting improves performance, but:
- Enhanced results may be prompt artifacts, not fundamental capabilities
- Different augmentations help some tasks, hinder others
- Omitting them underestimates abilities; using them universally obscures true competencies

## Self-Report Limitations

**Critical warning**: Properties like personality, morality, clinical disorders are "famously sensitive to prompting." LLMs can simulate different personas when prompted differently.

Self-reports should be understood "as a property of a specific system prompt" not as fundamental model characteristics. This is directly relevant to our HEXACO work - see [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles).

## Behavioral vs. Mechanistic Interpretability

The paper argues these complement each other:

| Behavioral | Mechanistic |
|------------|-------------|
| Input-output relationships | Weights and activations |
| Scales with model size | Requires architecture access |
| Works on closed-source | Open-source only |
| User-facing interface | Internal mechanisms |
| What models do | How models work |

Neither replaces the other. Behavioral methods become more valuable as models grow "more powerful, opaque, multi-modal, and integrated into complex real-world settings."

## Future Directions Proposed

1. **Multimodal expansion**: Apply paradigms to vision, sensory processing
2. **Longitudinal studies**: Track capability development over time
3. **AI safety applications**: Forecast alignment implications
4. **Embodied interaction**: LLMs with tool use
5. **Domain expansion**: Creativity, moral reasoning, clinical psychology

## Relevance to Our Work

This paper provides theoretical grounding for [Psych](/notes/machine-psychology/psych):

1. **Methodology alignment**: Our prompt design follows their contamination avoidance (we use varied scenarios, not verbatim instruments)

2. **Self-report caveat validated**: Our approach already treats personality profiles as system-prompt-dependent, not fundamental traits

3. **Behavioral over mechanistic**: We focus on behavioral outputs, aligning with their argument that this is where real-world impact occurs

4. **Performance-competence**: We should interpret inconsistent responses carefully - variation doesn't mean incompetence

5. **Missing coverage**: Their taxonomy reveals domains we haven't explored yet (theory of mind, in-context learning patterns, language processing)

## Key Citations

- Binz & Schulz (2023) - GPT-3 displays human-like cognitive biases
- Dasgupta et al. (2022) - Semantic content effects on logical reasoning
- Chan et al. (2022) - Rule-based vs exemplar-based generalization
- Wilcox et al. (2023) - Surprisal measures for syntax
- Street et al. (2024) - Higher-order theory of mind

---

*See also*: [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles), [Sycophancy Measurement](/notes/machine-psychology/sycophancy-measurement)
