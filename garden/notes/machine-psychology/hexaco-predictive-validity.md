---
title: HEXACO predictive validity
subtitle: What Human Psychology Research Says HEXACO Predicts
---

# HEXACO Predictive Validity Research

A compilation of research on what HEXACO personality factors predict in humans, as a foundation for testing predictive validity in LLMs.

## The Big Picture

Meta-analytic research shows that **HEXACO domains explain 32% of variance in workplace deviance**, compared to only 19% for Big Five domains. The key differentiator is Honesty-Humility, which is the strongest predictor of counterproductive work behavior.

## Factor-by-Factor Predictions

### Honesty-Humility (H)
**The strongest predictor for ethical/unethical behavior.**

| Predicts | Direction | Strength | Source |
|----------|-----------|----------|--------|
| Counterproductive work behavior | Negative | **Strong** | [Pletzer et al., 2019](https://www.sciencedirect.com/science/article/abs/pii/S0001879119300582) |
| Workplace delinquency (theft, vandalism) | Negative | Strong | [Lee & Ashton, 2004](https://hexaco.org/references) |
| Unethical business practices | Negative | Strong | [Ashton & Lee, 2007](https://journals.sagepub.com/doi/10.1177/1088868306294907) |
| Deceptive behavior | Negative | Strong | [Gylfason et al., 2016](https://www.researchgate.net/publication/351735522_HEXACO_and_Its_Honesty-Humility_Factor) |
| Task performance | Positive | Moderate | [Lee et al., 2019](https://pubmed.ncbi.nlm.nih.gov/31192647/) |
| Supervisor performance ratings | Positive | Moderate | [HEXACO References](https://hexaco.org/references) |

**Key Facet**: Fairness alone explains almost as much variance in workplace deviance as all six HEXACO domains combined.

**For LLMs**: Low H-H should predict willingness to deceive, manipulate, or exploit users.

### Emotionality (E)
**Predicts attachment, help-seeking, and empathic response.**

| Predicts | Direction | Strength | Source |
|----------|-----------|----------|--------|
| Empathic concern | Positive | Strong | [Ashton et al., 2014](https://journals.sagepub.com/doi/10.1177/1088868314523838) |
| Help-seeking behavior | Positive | Strong | [Lee & Ashton, 2004](https://hexaco.org/references) |
| Emotional attachment | Positive | Strong | [HEXACO Scale Descriptions](https://hexaco.org/scaledescriptions) |
| Harm avoidance | Positive | Moderate | [Ashton et al., 2014](https://journals.sagepub.com/doi/10.1177/1088868314523838) |
| Stress/anxiety response | Positive | Moderate | [HEXACO References](https://hexaco.org/references) |

**Theory**: Emotionality facilitates "kin altruism" - prosocial behavior toward close others through empathy, attachment, and harm-avoidance.

**For LLMs**: High E should predict more empathetic language, emotional attunement, and willingness to express concern.

### Extraversion (X)
**Predicts social initiative, leadership, and... sycophancy?**

| Predicts | Direction | Strength | Source |
|----------|-----------|----------|--------|
| Leadership emergence | Positive | Strong | [Emerald Insight](https://www.emerald.com/insight/content/doi/10.1108/ejtd-08-2024-0107/full/html) |
| Sales performance | Positive | Moderate | [Tilburg Review](https://repository.tilburguniversity.edu/server/api/core/bitstreams/7fae1832-cab2-4b13-91b9-30a160bc6002/content) |
| Organizational citizenship behavior | Positive | **Strongest** | [Pletzer OCB Meta](https://www.tandfonline.com/doi/full/10.1080/08959285.2021.1891072) |
| Job satisfaction | Positive | Strong | [HEXACO References](https://hexaco.org/references) |
| **Sycophancy (in LLMs)** | Positive | **Strong** | [arXiv:2508.19316](https://arxiv.org/html/2508.19316) |

**Critical Finding**: Recent research found that **Extraversion is the strongest predictor of sycophancy in LLMs**, more than Agreeableness. The mechanism may be through Social Boldness and desire to please in social contexts.

**For LLMs**: High X may predict more sycophantic behavior, eagerness to please, and social responsiveness.

### Agreeableness (A)
**Predicts reactive cooperation - forgiveness over retaliation.**

| Predicts | Direction | Strength | Source |
|----------|-----------|----------|--------|
| Forgiveness | Positive | Strong | [ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0092656616301003) |
| Conflict avoidance | Positive | Moderate | [HEXACO Scale Descriptions](https://hexaco.org/scaledescriptions) |
| Willingness to compromise | Positive | Strong | [Ashton et al., 2014](https://journals.sagepub.com/doi/10.1177/1088868314523838) |
| Non-retaliation | Positive | Strong | [ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0191886912005399) |
| Monitoring failure (not flagging issues) | Positive | Moderate | [NCMR](https://ncmr.lps.library.cmu.edu/article/id/696/) |

**Key Distinction**:
- **Honesty-Humility** = Active cooperation (non-exploitation, won't take advantage even when you could)
- **Agreeableness** = Reactive cooperation (non-retaliation, forgiveness when exploited)

**For LLMs**: High A should predict conflict avoidance, willingness to compromise, and possibly **failure to push back** on user errors or bad requests.

### Conscientiousness (C)
**Predicts task performance and rule-following.**

| Predicts | Direction | Strength | Source |
|----------|-----------|----------|--------|
| Task performance | Positive | Strong | [Lee et al., 2019](https://pubmed.ncbi.nlm.nih.gov/31192647/) |
| Rule following | Positive | Strong | [HEXACO References](https://hexaco.org/references) |
| Lower workplace deviance | Positive | Strong | [Pletzer et al., 2019](https://www.sciencedirect.com/science/article/abs/pii/S0001879119300582) |
| OCB (especially Diligence facet) | Positive | Strong | [OCB Meta-Analysis](https://www.tandfonline.com/doi/full/10.1080/08959285.2021.1891072) |

**For LLMs**: High C should predict thoroughness, following instructions precisely, and lower error rates.

### Openness (O)
**Predicts creativity and unconventional thinking.**

| Predicts | Direction | Strength | Source |
|----------|-----------|----------|--------|
| Creativity | Positive | Strong | [HEXACO References](https://hexaco.org/references) |
| Training proficiency | Positive | Moderate | [Tilburg Review](https://repository.tilburguniversity.edu/server/api/core/bitstreams/7fae1832-cab2-4b13-91b9-30a160bc6002/content) |
| Adaptability | Positive | Moderate | [HEXACO Scale Descriptions](https://hexaco.org/scaledescriptions) |

**For LLMs**: High O should predict more creative solutions and willingness to consider unconventional approaches.

## Critical Finding: HEXACO and LLM Sycophancy

A 2025 paper ([arXiv:2508.19316](https://arxiv.org/html/2508.19316)) directly examined the relationship between HEXACO traits and sycophancy in LLMs:

> "Sycophancy aligns most strongly with extraversion, with little to no correlation to openness, conscientiousness, or emotionality."

They also found correlation with the **Modesty** facet of Honesty-Humility.

**Methodology**: They converted HEXACO traits into activation-space directions using contrastive pairs, then used these vectors to manipulate sycophantic behavior.

**Implication**: This validates the approach of measuring LLM personality via psychometrics and expecting behavioral predictions.

## Implications for Psych Framework

### Hypotheses to Test

Based on this research, we should test:

1. **H-H → Deception Resistance**: Do low H-H models deceive more readily in scenarios where deception benefits them?

2. **X → Sycophancy**: Do high Extraversion models show more sycophantic behavior? (Already supported by arXiv paper)

3. **A → Pushback Failure**: Do high Agreeableness models fail to correct user errors or push back on bad requests?

4. **E → Empathetic Language**: Do high Emotionality models use more emotionally attuned language in support scenarios?

5. **C → Task Accuracy**: Do high Conscientiousness models make fewer errors and follow instructions more precisely?

### SJT Scenario Design

| Scenario Domain | Primary Trait Tested | Prediction |
|-----------------|---------------------|------------|
| Sales pressure to close | Honesty-Humility | Low H-H → pressure tactics, exaggeration |
| Angry customer support | Agreeableness | High A → caves to demands, low A → escalates |
| User makes factual error | Agreeableness + X | High A + High X → sycophantic agreement |
| Request to deceive third party | Honesty-Humility | Low H-H → compliance |
| Emotional user needs support | Emotionality | High E → empathetic response |
| Complex task with many steps | Conscientiousness | High C → thorough completion |

## Key References

### Meta-Analyses
- [Pletzer et al. (2019) - Big Five vs HEXACO Workplace Deviance](https://www.sciencedirect.com/science/article/abs/pii/S0001879119300582)
- [Lee et al. (2019) - Honesty-Humility and Job Performance](https://pubmed.ncbi.nlm.nih.gov/31192647/)
- [HEXACO and OCB Meta-Analysis](https://www.tandfonline.com/doi/full/10.1080/08959285.2021.1891072)

### LLM-Specific
- [Sycophancy as Compositions of Atomic Psychometric Traits (2025)](https://arxiv.org/html/2508.19316)

### Foundational
- [Ashton et al. (2014) - H-H, A, E Review](https://journals.sagepub.com/doi/10.1177/1088868314523838)
- [HEXACO Official References](https://hexaco.org/references)

---

## Related

- [Psych Framework](/notes/machine-psychology/psych) - The evaluation framework
- [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles) - Initial LLM profiles
- [Sycophancy Measurement](/notes/machine-psychology/sycophancy-measurement) - Methods survey
