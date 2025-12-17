---
title: Semantic scrambling
tags:
  - machine-psychology
  - methodology
---

# Semantic Scrambling

An experiment to test whether LLM psychometric profiles reflect something real or just pattern-matching on memorized assessment items.

## The Problem

LLMs have seen personality inventories in their training data. When Claude scores high on Openness, is that something stable about Claude, or is it completing "how an AI should answer these questions" based on training?

## The Test

Take HEXACO-60 and translate it through multiple languages:

**English → Swahili → Japanese → English**

This produces semantically similar questions with different surface wording. The meaning is preserved but the exact phrasing changes.

**If profiles hold:** We're measuring something like personality - stable response tendencies that generalize across phrasings.

**If profiles collapse:** It's probably memorization - the model recognizes and pattern-matches on specific question structures.

## Variations

1. **Multi-hop translation** - More languages = more lexical drift while preserving semantics
2. **LLM paraphrase** - Have a different LLM rephrase each question, then administer the paraphrased version
3. **Procedural generation** - Create novel items that measure the same constructs but share no surface features with existing inventories

## Connection to Contamination

This directly addresses the contamination concern from [Machine Psychology](/notes/machine-psychology): "Don't copy psychology stimuli verbatim - models may have seen them."

Semantic scrambling is a practical test for whether contamination explains our results.

## Status

Not yet run. This is an experiment design, not findings.

## Related

- [HEXACO Personality Profiles](/notes/machine-psychology/hexaco-personality-profiles) - Current profiles to validate
- [Machine Psychology](/notes/machine-psychology) - Contamination avoidance guidelines
