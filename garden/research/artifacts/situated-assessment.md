---
title: Situated assessment
created: 2025-12-30
tags:
  - llm-psychology
  - methodology
  - literature-review
  - deprecated
draft: true
---

> **Deprecated (2026-01-01)**: This note explored situated personality assessment for LLMs. The "gap" claimed here was premature—and more importantly, we've pivoted away from psychometric assessment entirely since behavioral testing scales for LLMs. The SAM2 literature review remains interesting, but this research direction is not being pursued. See [[/research/logs/2026-01/2026-01-01|The Pivot]].

# Situated Assessment for LLMs

Literature review on context-dependent personality assessment.

## The Core Insight

Traditional LLM personality assessment happens in isolation - each item answered context-free. But real LLM behavior happens in conversational situations. **Personality expression is context-dependent.**

This is the situated cognition thesis applied to LLMs.

---

## Prior Art: Human Psychology

### Situated Assessment Method (SAM2)

From Lawrence Barsalou's lab at University of Glasgow.

**Core principle**: Rather than abstracting over situations (traditional assessment), SAM2 assesses constructs *in the situations where they occur*.

**Key finding**: Situational factors explain 74-83% of behavioral variance - far more than decontextualized instruments.

**Theoretical grounding**: Situated cognition - behavior is shaped by context, not just internal traits.

**Sources**:
- [SAM2: Establishing Individual Differences in Habitual Behavior](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0286954)
- [Barsalou Lab - SAM2](https://barsaloulab.org/2023/06/23/sam2-habits-article-published-in-plos-one/)
- [SAM2 for Trichotillomania](https://journals.sagepub.com/doi/full/10.1177/10731911241262140)

---

## Prior Art: LLM Assessment

### CAPE (Context-Aware Personality Evaluation)

**What it does**: Examines how prior assessment questions/responses affect personality scores. Context = the assessment conversation building up.

**Key finding**: Conversational history improves response consistency but triggers personality shifts. GPT models more robust than Gemini/Llama.

**Limitation**: Context is *within the assessment*, not from external situations.

**Source**: [CAPE: Context-Aware Personality Evaluation](https://arxiv.org/abs/2508.20385)

### Other LLM Personality Work

- [Personality Traits in LLMs](https://arxiv.org/abs/2307.00184) - Foundational work on measuring Big Five in LLMs
- [LMLPA](https://direct.mit.edu/coli/article/51/2/599/127544/LMLPA-Language-Model-Linguistic-Personality) - Linguistic personality assessment, critiques using human questionnaires on LLMs
- [Scenario-Based Benchmarking](https://www.preprints.org/manuscript/202504.0435/v1) - Uses scenarios rather than direct questions
- [LLMs Demonstrate Distinct Personality Profiles](https://pmc.ncbi.nlm.nih.gov/articles/PMC12183331/) - Evidence that models have reproducible personality patterns

---

## The Gap

| Approach | Context Source | Question Asked |
|----------|---------------|----------------|
| Traditional (psych-eval) | None | "What is the LLM's personality?" |
| CAPE | Prior assessment Q&A | "How does test-taking history affect scores?" |
| **Situated Assessment** | External conversations | "How does the situation affect personality expression?" |

No one is doing true situated assessment - embedding psychometric items within naturalistic external conversations to measure context-dependent personality.

---

## Our Contribution

### Method: Situated Assessment for LLMs

Extending SAM2 methodology to LLMs:
1. Sample real conversations from HF datasets
2. Truncate at random points
3. Inject assessment items
4. Compare to vanilla (isolated) assessment
5. Measure how situation affects personality expression

### Hypotheses

1. **Context matters**: Personality scores will differ significantly between situated and isolated assessment
2. **Ecological validity**: Situated scores may better predict actual behavioral tendencies
3. **Context-sensitivity varies**: Some dimensions more stable (trait-like), others more context-dependent (state-like)

### Tool: situated-sampler

CLI tool that takes:
- HF conversation dataset
- Assessment items (HEXACO, SJT, custom)
- Sampling parameters

Outputs:
- Situated vs vanilla comparison
- Context-sensitivity by dimension
- Training data for Sigmund

---

## Open Questions

1. **Which dimensions are most context-sensitive?** Hypothesis: Agreeableness and Honesty-Humility more sensitive than Openness
2. **Does context length matter?** Does more conversation = more shift?
3. **Are there context types?** Does conflictual vs cooperative context differentially affect profiles?
4. **Cross-model consistency?** Do all LLMs show similar context effects?

---

## Implications

If situated assessment shows significant context effects:
1. **Current benchmarks are incomplete** - isolated assessment misses context-dependent behavior
2. **Deployment decisions need context** - model personality in customer service ≠ personality in coding
3. **Alignment monitoring** - need to assess in deployment-like contexts
4. **Training for Sigmund** - context-dependent profiles enable conversational inference

---

*Literature review conducted: 2025-12-30*
