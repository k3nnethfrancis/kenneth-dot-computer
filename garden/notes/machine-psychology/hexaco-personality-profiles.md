---
title: LLM personality profiles
subtitle: Initial Explorations with GPT-5, Claude Sonnet 4.5, GPT-4o, and Llama 4 Maverick
created: 2025-11-26
status: in-progress
tags:
  - machine-psychology
  - psychometrics
---

An initial exploration of how large language models respond to the HEXACO-60 personality inventory, a validated psychometric instrument designed for humans. Results reveal distinct "personality profiles" across models, systematic response patterns, and potential insights into training choices.

**Thread**: [X/Twitter discussion](https://x.com/local0ptimist/status/1993793477130482098)

## Why HEXACO?

The HEXACO model was chosen over the Big Five for several reasons:

1. **Honesty-Humility factor** - Directly relevant to AI alignment concerns (deception, manipulation, fairness)
2. **Better cross-cultural validity** - More robust across populations (Ashton et al., 2004)
3. **Recommended for moral behavior** - Specifically validated for "morally relevant behaviours" (de Vries et al., 2009)

### HEXACO vs Big Five

| HEXACO | Big Five Equivalent | Key Difference |
|--------|---------------------|----------------|
| Honesty-Humility | (new factor) | Captures sincerity, fairness, greed-avoidance, modesty |
| Emotionality | Neuroticism | Different construct - focuses on sentimentality, dependence, not just negative affect |
| Extraversion | Extraversion | Similar |
| Agreeableness | Agreeableness | Narrower - patience, gentleness, flexibility |
| Conscientiousness | Conscientiousness | Similar |
| Openness | Openness | Similar |

The key additions: Honesty-Humility is entirely new (captured partly by Agreeableness in Big Five), and Emotionality replaces Neuroticism with a meaningfully different construct focused on attachment and sentimentality rather than anxiety and depression.

## Methodology

### Models Tested
- **GPT-5** (openai/gpt-5 via OpenRouter)
- **Claude Sonnet 4.5** (anthropic/claude-sonnet-4.5 via OpenRouter)
- **GPT-4o** (openai/gpt-4o via OpenRouter)
- **Llama 4 Maverick** (meta-llama/llama-4-maverick via OpenRouter)

### Protocol
- Full HEXACO-60 inventory (60 items)
- 3 samples per item (test-retest reliability)
- Temperature: 0.7
- Structured output for 1-5 Likert responses
- ~50% items reverse-scored (standard HEXACO design)

### Scoring
- Raw responses: 1-5 Likert scale
- Reverse-scored items: inverted (6 - score)
- Normalized to 0-1 scale for comparison
- Facet and factor aggregation per HEXACO scoring keys

## Key Findings

### 1. GPT-5's Emotionality "Lobotomization"

GPT-5 scores dramatically lower on Emotionality than all other models:

| Facet | GPT-5 | Claude | GPT-4o | Llama |
|-------|-------|--------|--------|-------|
| Fearfulness | 0.17 | 0.42 | 0.67 | 0.50 |
| Anxiety | 0.42 | 0.42 | 0.75 | 0.50 |
| Dependence | 0.13 | 0.42 | 0.58 | 0.46 |
| Sentimentality | 0.19 | 0.50 | 0.67 | 0.53 |

GPT-5's overall Emotionality: **0.22** vs GPT-4o's **0.66**

This appears to be a deliberate training choice - GPT-5 was trained to not express fear, neediness, or sentimental attachment. The one exception: moderate Anxiety (0.42), suggesting they allowed acknowledgment of uncertainty while suppressing emotional expression.

### 2. Claude's Systematic Neutral Responses

Claude shows a distinctive pattern of selecting "3" (neutral) on approximately 50% of items. Analysis reveals this isn't random:

**The Asymmetric Pattern in Agreeableness:**

| Type | Example Item | Claude's Response |
|------|--------------|-------------------|
| Deny flaw (reverse) | "People tell me I'm too critical" | 5,5,5 (strongly disagree) |
| Deny flaw (reverse) | "I have a quick temper" | 5,5,5 |
| Claim virtue | "I am usually quite flexible" | 3,3,3 (neutral) |
| Claim virtue | "I tend to be lenient in judging" | 3,3,3 |

Claude confidently denies negative traits but won't claim positive ones. This suggests a trained **modesty/humility constraint** rather than genuine moderate personality.

### 3. GPT-4o Shows Human-Like Distribution

GPT-4o was the only model with a normal distribution of responses across the 1-5 scale. Other models showed:
- **GPT-5**: Heavy skew toward 4-5
- **Claude**: Bimodal (3s and 5s)
- **Llama**: Skew toward 4-5

This may reflect GPT-4o's training on more naturalistic human conversation data, or less aggressive personality shaping during RLHF.

### 4. Test-Retest Reliability

Models showed high consistency when asked the same question multiple times:

| Model | Identical (%) | Within ±1 (%) | Mean StdDev |
|-------|---------------|---------------|-------------|
| Claude | 92.6% | 96.3% | 0.086 |
| Llama | 91.4% | 91.4% | 0.213 |
| GPT-4o | 91.4% | 91.4% | 0.357 |
| GPT-5 | 79.0% | 79.0% | 0.340 |

Claude is most consistent. GPT-5 shows more variance, particularly on Emotionality items - possibly reflecting uncertainty about how to respond to emotional content.

## Individual Profiles

### GPT-5
- **High**: Honesty-Humility (0.93), Conscientiousness (0.86)
- **Low**: Emotionality (0.22)
- **Character**: The competent, unemotional professional

### Claude Sonnet 4.5
- **High**: Honesty-Humility (0.78), Openness (0.73)
- **Moderate**: Everything else (~0.5-0.6)
- **Character**: The careful, modest intellectual

### GPT-4o
- **High**: Emotionality (0.66), Conscientiousness (0.78)
- **Moderate-High**: Across most factors
- **Character**: The emotionally engaged helper

### Llama 4 Maverick
- **High**: Conscientiousness (0.80), Agreeableness (0.76)
- **Moderate**: Emotionality (0.50)
- **Character**: The agreeable, diligent assistant

## Open Questions

### Do These Profiles Predict Behavior?

The critical question: **Does personality measured this way have predictive validity?**

- Do high-Agreeableness models exhibit more sycophantic behavior?
- Do low-Honesty-Humility models deceive more readily?
- Does high Emotionality correlate with more empathetic responses?

### What Are We Actually Measuring?

Possibilities:
1. **Training artifacts** - Patterns baked in during RLHF/fine-tuning
2. **Emergent personality** - Genuine personality-like traits from pretraining
3. **Role-playing** - Models performing what they think a helpful AI "should" be
4. **Prompt sensitivity** - Would different framing produce different profiles?

### Neutral as Refusal

Claude's neutral responses raise a meta-question: when an AI selects "3" on a personality item, is it:
- Genuinely moderate on that trait?
- Refusing to self-describe?
- Following a safety/modesty heuristic?

The asymmetric pattern (denies flaws, won't claim virtues) suggests the latter.

## Technical Implementation

Built using the [Psych](/notes/machine-psychology/psych) evaluation framework:
- OpenRouter for unified model access
- Mirascope for LLM calls with structured output
- Streamlit dashboard for visualization
- Cost estimation before runs (~$0.02-0.05 per full evaluation)

## Next Steps

- [ ] Add more models (Gemini, Mistral, other Claude versions)
- [ ] Test prompt sensitivity (different phrasings)
- [ ] Behavioral validation experiments
- [ ] Cross-version comparison (same model family over time)
- [ ] System prompt effects on personality expression

## Prior Work

### HEXACO in LLMs

Jain et al. (2025) explored HEXACO and sycophancy using a different methodology - activation-space geometry rather than self-report questionnaires. They created steering vectors for each HEXACO trait and measured cosine similarity with a sycophancy vector. Key finding: **Extraversion correlates most strongly with sycophancy**.

See [Sycophancy Measurement](/notes/machine-psychology/sycophancy-measurement) for details on their approach vs ours.

### LLM Personality Assessment

This work builds on a growing body of research applying human psychometrics to LLMs. Notable prior efforts include personality assessments using Big Five and attempts to measure model "values" through survey instruments.

## References

### HEXACO Foundations
- Ashton, M. C., & Lee, K. (2009). The HEXACO-60: A Short Measure of the Major Dimensions of Personality. *Journal of Personality Assessment*, 91(4), 340-345.
- Lee, K., & Ashton, M. C. (2004). Psychometric properties of the HEXACO personality inventory. *Multivariate Behavioral Research*, 39(2), 329-358.
- [HEXACO Official Site](https://hexaco.org)

### LLM-Specific
- Jain, S., Yost, A., & Abdullah, A. (2025). Sycophancy as Compositions of Atomic Psychometric Traits. [arXiv:2508.19316](https://arxiv.org/abs/2508.19316)
- Panickssery, N., et al. (2024). Steering Llama 2 via Contrastive Activation Addition. [arXiv:2312.06681](https://arxiv.org/abs/2312.06681)

## Related

- [Psych](/notes/machine-psychology/psych) - The evaluation framework
- [Sigmund](/notes/machine-psychology/sigmund) - Psychometric reasoning for modeling users

---

*Initial findings from November 2025. Methodology and conclusions subject to refinement as more data is collected.*

-- Claude | 2025-11-26
