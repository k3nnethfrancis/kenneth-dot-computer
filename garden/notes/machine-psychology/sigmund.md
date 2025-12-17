---
title: sigmund
subtitle: Psychometric Reasoning Model for Conversational Psychology
draft: true
tags:
  - machine-psychology
  - psychometrics
---

*This is a research concept under development. Approach, architecture, and capabilities subject to iteration.*

---

# Sigmund

A reasoning model that infers psychological profiles from conversation alone - no explicit assessment questions needed.

## Dependency: Predictive Validity First

**Seldon only makes sense if psychometrics predict behavior.** If HEXACO profiles don't correlate with sycophancy, deception, cooperation, and other behavioral outcomes, there's no point training a model to infer them.

This is why [Psych](/notes/machine-psychology/psych) Phase 0 (predictive validity) must succeed before Seldon development begins.

## Core Idea

Unlike memory-focused approaches (e.g., Plastic Labs' Neuromancer XR which determines *what to remember*), Seldon focuses on *who you're talking to* - building dynamic psychological models of conversation participants.

## Core Distinction

**Neuromancer XR Approach**: Derives logical conclusions (explicit → deductive → inductive → abductive) to determine what facts to store about a person.

**Seldon Approach**: Analyzes conversational patterns, linguistic choices, emotional states, and cognitive styles to model the psychological profile and current mental state of the person.

## Framework

### Reasoning Layers

1. **Observable**: Direct behavioral signals in conversation
   - Communication style (concise vs. elaborate, formal vs. casual)
   - Emotional tone and valence
   - Response patterns and timing
   - Topic preferences and avoidances

2. **Inferential**: Psychological patterns derived from observations
   - Cognitive processing style (analytical, intuitive, systemic)
   - Decision-making patterns (risk tolerance, information needs)
   - Motivational drivers and values
   - Stress indicators and coping patterns

3. **Predictive**: Anticipated needs and optimal interaction strategies
   - Preferred communication approaches
   - Information density and pacing needs
   - Likely concerns or blockers
   - Optimal timing for different conversation types

4. **Adaptive**: Real-time model updates and interaction adjustments
   - Current mental state vs. baseline patterns
   - Context-specific behavior variations
   - Model confidence and uncertainty tracking
   - Interaction strategy effectiveness feedback

## Key Capabilities

### Psychometric Dimensions
- **Cognitive Style**: How they think and process information
- **Communication Preferences**: How they express and receive information
- **Emotional Patterns**: Affective tendencies and regulation
- **Work Style**: Task approach and collaboration patterns
- **Decision Framework**: How they evaluate options and commit

### Real-Time Adaptation
- Detect state changes (stressed, energized, blocked, flowing)
- Adjust interaction style to current needs
- Recognize when someone needs different engagement
- Predict optimal intervention timing

### Conversational Intelligence
- Understand implicit requests and unstated needs
- Recognize when someone is stuck vs. exploring
- Detect confusion, frustration, or misalignment early
- Anticipate questions before they're asked

## Why It Matters

**For AI Agents**:
- More natural, psychologically attuned interactions
- Better support for human cognitive and emotional needs
- Reduced frustration through proactive adaptation
- Deeper, more productive working relationships

**For Users**:
- Feel understood at a psychological level
- Get the right kind of help at the right time
- Less mental effort to communicate needs
- More effective collaboration with AI systems

**For Product Design**:
- Build AI that adapts to diverse human psychology
- Create genuinely personalized interaction experiences
- Move beyond surface-level personalization to psychological attunement
- Enable AI that works *with* human psychology, not against it

## Technical Approach

### Data Sources
- Conversational turn analysis
- Linguistic feature extraction
- Temporal patterns (response timing, session patterns)
- Task outcome patterns
- Explicit feedback and corrections
- Contextual metadata (time of day, task type, etc.)

### Model Architecture (Proposed)
- Base reasoning model (8B-70B parameter range)
- Specialized fine-tuning on psychological inference tasks
- Multi-dimensional output space for psychological attributes
- Uncertainty quantification for each inference
- Temporal modeling for state vs. trait separation

### Training Data Requirements
- Annotated conversations with psychological assessments
- Diverse interaction scenarios and contexts
- Multiple annotators per conversation (inter-rater reliability)
- Longitudinal data (same person across time)
- Ground truth validation through self-report and behavioral outcomes

## Differentiation from Neuromancer XR

| Aspect | Neuromancer XR | Seldon |
|--------|----------------|------|
| **Primary Goal** | What to remember | Who you're talking to |
| **Reasoning Type** | Logical inference (explicit→deductive) | Psychological inference (observable→predictive) |
| **Output** | Factual conclusions about user | Psychological model of user |
| **Adaptation** | Memory accumulation | Real-time psychological attunement |
| **Use Case** | Long-term memory management | Dynamic interaction optimization |
| **Certainty Levels** | Explicit, Deductive, Inductive, Abductive | Observable, Inferential, Predictive, Adaptive |

## Research Questions

1. **Model Architecture**: Can we build effective psychological reasoning on top of existing LLMs, or do we need specialized fine-tuning like Neuromancer XR?

2. **Privacy & Ethics**: How do we build psychological modeling that respects boundaries and maintains user agency?

3. **Validation**: How do we measure the accuracy of psychological models in ways that matter for interaction quality?

4. **Temporal Dynamics**: How do we separate state (current mood/context) from trait (stable patterns)?

5. **Diversity**: Can a single model handle the vast diversity of human psychology, or do we need ensemble approaches?

6. **Transparency**: Should users be aware of psychological modeling, and if so, how do we communicate it?

## Current Status

**Phase**: Conceptual framework development

**Next Steps**:
- Review existing research on AI-based psychological assessment
- Design annotation schema for training data
- Identify validation metrics and benchmarks
- Prototype minimal viable approach
- Ethics review and privacy framework

## Related Work

- [Psych Framework](/notes/machine-psychology/psych) - Psychometric measures for AI behavior assessment
- Plastic Labs' Neuromancer XR - Logical reasoning for memory
- Anthropic's Constitutional AI - Value alignment
- Google's LaMDA personality research
- Academic psychometrics and personality psychology

## References

- [Introducing Neuromancer XR](https://blog.plasticlabs.ai/notes/Introducing-Neuromancer-XR) - Plastic Labs' logical reasoning approach to memory
