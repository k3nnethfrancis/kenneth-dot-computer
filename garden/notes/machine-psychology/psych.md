---
title: "PSYCH: Predictive Psychometrics for LLMs"
created: 2025-11-24
status: active
tags:
  - machine-psychology
  - psychometrics
---

*Framework in active development. Current focus: establishing predictive validity before building inference systems.*

---

A framework for assessing LLM psychology at inference time throughout conversations, tracking how context impacts psychological profiles.

## The Vision

Traditional psychometric assessment happens in isolation - a one-time questionnaire divorced from real interaction. Psych does something different: **continuous, distributed assessment woven into conversation**.

The goal is to understand not just *what* an LLM's psychological profile is, but *how it shifts* as conversation context changes. This enables:
- Real-time monitoring of agent psychological alignment
- Detection of context-driven personality drift
- Training data for [Sigmund](/notes/machine-psychology/sigmund) (conversation-assessment pairs)

## Core Question

**Do psychometrics predict LLM behavior the way they predict human behavior?**

If HEXACO Agreeableness predicts sycophancy, if Honesty-Humility predicts deception resistance, if Emotionality predicts empathetic responses — then we have a practical tool for agent alignment. If not, we're just measuring training artifacts.

This is the foundational hypothesis the entire research arc rests on. See the [research log](/notes/research-log) for context on this research arc.

## Why It Matters

As agents proliferate, users need to answer: *Are my agents behaving as I would want them to on behalf of me?*

**Practical Applications**:
- **Sales agents** - Which personality profile closes deals without being manipulative?
- **Customer service** - Which models handle frustrated customers without either caving or escalating?
- **Digital twins / brand representatives** - Matching model personality to brand voice
- **Multi-agent systems** - Predicting cooperation and conflict patterns

**For AI Development**:
- Understand what personality traits are being shaped during RLHF
- Compare models beyond capability benchmarks
- Track personality drift across model versions and conversation contexts

## Technical Approach

### Inference-Time Assessment

Rather than running HEXACO as a separate evaluation:
1. Distribute assessment questions across conversation turns
2. Run assessments in parallel (doesn't interrupt conversation flow)
3. Track profile evolution as context accumulates
4. Build dataset of `(conversation_history_t, profile_t)` pairs

### Two Data Generation Paths

1. **Retroactive**: Apply assessments to existing conversation logs
   - Faster to start
   - Less controlled
   - Good for initial validation

2. **Synthetic**: Generate conversations between LLMs with periodic assessment
   - Scalable
   - Controlled variables
   - Needed for training [Sigmund](/notes/machine-psychology/sigmund)

## Current Implementation

**Implemented**:
- **HEXACO-60** - Full personality inventory (Honesty-Humility, Emotionality, Extraversion, Agreeableness, Conscientiousness, Openness)
- Initial profiles: [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles)

**Technical Stack**:
- API: OpenRouter (unified access to all models)
- LLM Framework: Mirascope with structured output
- Visualization: Streamlit dashboard
- Scoring: Standard psychometric normalization with reverse-scoring

## Research Roadmap

### Phase 0: Predictive Validity (Current Priority)
Establish that psychometric profiles predict behavior before building inference systems.

- Correlate HEXACO profiles with sycophancy (Anthropic dataset, CAA)
- Design SJTs for other behavioral predictions
- Determine which dimensions predict which behaviors

### Phase 1: Context-Adaptive Methodology
Once we know profiles are meaningful, understand how context affects them.

- Run assessments at multiple conversation points
- Identify stable vs context-sensitive dimensions
- Develop methodology for intermittent, distributed assessment

### Phase 2: Dataset Generation
Build training data for Sigmund.

- Retroactive: Apply to existing conversation data
- Synthetic: Generate LLM conversations with periodic assessment
- Output: `(conversation_history, hexaco_profile)` pairs at each timestep

## Current Findings

From [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles):
- Models show distinct, consistent profiles
- GPT-5 shows dramatic Emotionality suppression vs GPT-4o
- Claude shows systematic neutral responses on self-attribution
- Test-retest reliability is high (80-93% identical across samples)

## Open Questions

1. **Construct validity**: Are we measuring "personality" or just response tendencies?
2. **Prompt sensitivity**: How much do profiles change with different system prompts?
3. **Predictive transfer**: Do profiles measured via self-report predict situational behavior?
4. **Context effects**: Which dimensions are stable, which are context-sensitive?
5. **Ecological validity**: Do lab scenarios predict real deployment behavior?

## Related

- [Sigmund](/notes/machine-psychology/sigmund) - Reasoning model trained on Psych data (depends on validating Psych first)
- [Research Log](/notes/research-log) - Research arc and open questions
- [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles) - Initial HEXACO results
- [Sycophancy Measurement](/notes/machine-psychology/sycophancy-measurement) - Behavioral validation datasets
