---
title: research
description: Notes on AI behavior and human-AI control.
tags:
  - research
---
# research

Notes on AI behavior and human-AI control.

As AI systems grow more capable, understanding their behavior becomes critical. [[/research/notes/machine-psychology|Machine psychology]] is emerging as a discipline to meet this need. Open Phil is funding [black-box LLM psychology](https://www.openphilanthropy.org/grants/) research. OpenAI says [AI safety needs social scientists](https://openai.com/index/ai-safety-needs-social-scientists/). These notes are my contribution to that conversation.

## Core questions

I'm primarily interested in two overlapping research areas related to human-AI coordination. My frame of reference for these questions is influenced by my background in industrial/organizational psychology. More specifically, I am attempting to integrate the learnings and methodologies of behavioral science and sociotechnical theory through the lens of [[/research/notes/cybernetics|cybernetics]].

### How do humans remain in control in an increasingly multi-agent world?

What are the technical and organizational structures that enable humans to understand and control increasingly complex AI systems? As multi-agent systems become more capable and less intelligible, how do we stay in the loop?

### Can AI systems learn to reason about psychology?

Evidence from systems like [Plastic Labs' Neuromancer](https://www.plasticlabs.ai/) suggests reasoning models can learn to track psychological constructs. If AI can hold a psychological model and reason about it, this opens several possibilities:

1. **Better state inference**: Inferring from the psychological states of users (humans or other AIs) from conversation or unstructured data
2. **Real-time intervention**: Situational assessment and response strategies—detecting problems and responding to de-escalate, steer, or even shut down engagements
3. **Agent orchestration:** Improving how agents orchestrate other agentic systems by enabling them with better state inference to apply real-time intervention strategies that lead to better performance and greater visibility for human orchestrators
4. **Scientific advancement:** Building autonomous behavioral scientists and machine psychologists that can properly reason about these domains
5. **Applied domains**: Psychotherapy, interviewing, negotiation, influence

Of these, I'm particularly interested in *3. agent orchestration* and *4. scientific advancement*, which I believe are downstream of *1. better state inference* and *2. real-time intervention*. I hope that people who read my work can also improve outcomes for *5. applied domains*.

It is possible that this leads to the need for interpretability research. I focus on behavioral approaches because they tend to be more scalable—experiments are more likely to translate from one model to the next, regardless of size. They do not require access to the underlying model weights, and are more implementable by practitioners in the field, who will likely far outnumber the AI neuroscientists. And frankly, it's where I'm most useful. Mechanistic interpretability can produce more causal explanations, and the two complement each other—I discuss this further in my note on [[/research/notes/machine-psychology|machine psychology]].

Ultimately, my goal is to help push the needle forward on practical AI safety, corrigibility, and control research.

---
