---
title: "Digital mind design: From tool AIs to agents"
date: 2024-12-15
image: /images/posts/from-tool-ais-to-agents.jpg
tags:
  - ai
  - digital-mind-design
---

<style>
pre {
  display: flex;
  justify-content: center;
}
pre code {
  text-align: center;
}
</style>

# Digital Mind Design: From tool AIs to agents

Language might be the most powerful technology humans have ever created. It's how we share knowledge, coordinate actions, and build upon each other's ideas. As it turns out, it's also the perfect training medium for bootstrapping human-like intelligence.

Through language, we can describe anything—from mathematical proofs to emotional experiences, from step-by-step instructions to abstract concepts. This makes it a powerful tool for interfacing with computers.[^1]

Up until recently, the computational resources required for human-level language processing were prohibitively expensive. Thanks to Moore's Law and advances in specialized hardware, we've now reached a point where machines can process language at scales that enable sophisticated capabilities. What's fascinating is how these systems evolved from simple next-token prediction ("what word is likely to come next?") into something that appears to reason and understand. When a large language model is trained on enough text, it starts to pick up on the deep patterns that underlie human knowledge and reasoning.

This emergence of intelligence from prediction is more profound than it might first appear. Harvard professor Steven Pinker has referred to language as a ["window into the mind"](https://www.youtube.com/watch?v=Q-B_ONJIEcE), and as it turns out, it's also an interface. From text, we can train digital minds capable of natural flowing conversation and performing tasks ranging from simple calculations to complex analysis. The same model that can write a poem can also help debug code or explain scientific concepts, all via the use of language.

## The Evolution of Language Models: From Prediction to Simulation

Something fascinating happens when you spend enough time working with Language Models. You start to notice that they're not just sophisticated prediction engines—they can develop distinct patterns of behavior and characteristics that seem to transcend their training. This evolution has led researchers to conceptualize these models not just as predictive systems, but as simulators capable of modeling complex behaviors and interactions.

Perhaps one of the first times this became obvious was the paper, [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/pdf/2304.03442).[^2]

<div style="display: flex; justify-content: center; margin: 2rem 0;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/WjLpCgOX7qY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

In this experiment, researchers created a sandbox environment called Smallville, reminiscent of games like The Sims or Pokemon. This virtual world included:

* 25 unique AI agents, each with its own personality and background
* Various locations such as houses, a cafe, stores, a college, and a park
* Objects and items within these locations that agents could interact with

The generative agents exhibited remarkably human-like behaviors: they followed daily routines like waking up, eating breakfast, and going to work, engaged in conversations with other agents, formed opinions, and referenced memories of past experiences to inform future actions.

One of the most impressive aspects of the experiment was the emergence of complex social behaviors like the spread of information and relationships between agents like the coordination of group activities.

For example, when one agent was given the idea to throw a Valentine's Day party, other agents helped by spreading invitations to other agents and showing up on time (for those invited, of course).

And the body of empirical evidence is growing. Several papers in the field of psychology have shown fascinating results such as reliable simulation of human Big5 personality traits. Recently, Stanford researchers showed that LLMs could predict the outcome of social science experiments.[^3] [^4]

But these are not just experiments happening in a lab.

The Truth Terminal phenomenon is a fascinating story of how an AI agent amassed a following in the hundreds of thousands, launched a memecoin and became the world's first AI millionaire, with many more attempting to recreate its success.[^5]

A team at a16z crypto has now open sourced one framework, Eliza, for building autonomous social media agents that can pursue their own objectives and whose personalities shape over time.

This evolution from simple predictors to general simulators represents a fundamental shift in how we should think about these systems. If models can be engineered to have agency, develop a personality, and pursue goals in the real world, maybe we should stop thinking of them as tools and more like collaborators.

## From I/O to Autonomy: Levels of AI Agency

The evolution of AI systems can be understood through increasing levels of autonomy and capability. Inspired by work from researchers at Google's DeepMind, this framework helps us understand the progression from simple tools to more sophisticated autonomous systems.[^6]

### Autonomy level 0-1: Tool AIs and Chatbots

At Level 0, we have pure input/output systems - basic image generators, text translators, and data transformation tools. These are straightforward tools with clear boundaries and predictable outputs.

Level 1 is where we find most modern AI assistants like ChatGPT. While still fundamentally tools, they show early signs of agency through basic tool usage, reflective thinking, context maintenance, and query inference. At their core, these digital minds operate on a simple principle: they take in information, process it, and produce outputs.

This basic Input/Output framework becomes incredibly powerful when we understand how to structure and chain these interactions. Think of it like building blocks - each individual operation might be simple, but when connected together, we can create sophisticated workflows and even autonomous systems.

### Agentic Workflows: Autonomy Level 1-2

Most LLM-based AI systems today demonstrate what DeepMind researchers call "narrow autonomy." At this level, we see two main patterns:

Simple chained operations with validation loops:

```
Input → Process → Validate → Output
     ↑                           ↓
     └───── Retry if failed ─────┘
```

Each agent has its own validation criteria and can loop until its part is done correctly. But crucially, these workflows are still task-oriented - they run until the defined objective is complete, then stop.

For example, a system that:

* Extracts data from a webpage
* Fills out a form
* Validates the entries
* Either submits or retries if errors found

The key here is that while there's a feedback loop, it's pursuing a single, well-defined task until completion.

More sophisticated workflows chain multiple specialized agents together:

```
Research → Planning → Writing → Review
     ↑                            ↓
     └────── Revision Loop ───────┘
```

Each agent has its own validation criteria and can loop until its part is done correctly. But crucially, these workflows are still task-oriented - they run until the defined objective is complete, then stop.

These agentic workflows find applications in various domains:

* Customer service: Automated ticket routing and initial response generation
* Data analysis: ETL processes with error checking and data validation
* Content creation: Automated article writing with fact-checking and editing loops

While powerful, these workflows are limited by their predefined structure and lack of true adaptability.

### Autonomous Agents: Autonomy level 2-3

At greater levels of autonomy, we move beyond predefined workflows with fixed validation criteria. These AI agents operate in continuous loops, making their own decisions about how to achieve broader objectives. We can categorize these agents into two main paradigms: thought loop agents and environmental agents.

**Thought Loop Agents**

One approach to autonomous agents, exemplified by systems like AutoGPT, employs a continuous thought loop. While the exact structure can vary, a general pattern might look like:

```
Think → Plan → Act → Observe → Learn
```

Key characteristics of thought loop agents include:

* Setting their own sub-goals to achieve broader objectives
* Dynamically choosing which tools to use and when
* Maintaining memory of past actions and results
* Running continuously rather than stopping after task completion

For example, given a high-level goal like "research and write about headphones," such an agent would:

* Decide what information it needs
* Choose appropriate tools (web search, file creation, etc.)
* Break the task into sub-goals
* Monitor its own progress
* Adapt its approach based on results

**Environmental Agents**

This more experimental approach places an LLM in an environment with tools and persistent memory, letting it make decisions and learn over time. The Truth Terminal exemplifies this setup, using one AI as a strategic decision-maker and another as an interface to tools and APIs.

What makes this approach powerful is its ability to develop and refine strategies through continuous interaction with its environment. When the agent discovers successful patterns - like optimal posting times or engagement techniques - it stores these insights in its memory system and builds upon them. This creates a continuous learning loop where each interaction potentially improves future performance.

The implications are profound. These systems can run indefinitely, managing social media, running sales operations, or building communities. Through reinforcement learning and memory system optimization, they can become more sophisticated over time, developing distinct personalities and approaches to achieving their objectives.

## Tradeoffs and Considerations

Both thought loop and environmental agent paradigms represent a shift from "automated tasks" to "autonomous collaborators." However, it's crucial to understand that these are experimental technologies with significant implications:

**Control vs. Adaptability**: Thought loop agents offer more predictability and easier implementation of guardrails, while environmental agents provide greater adaptability but may be harder to constrain.

**Safety Concerns**: Autonomous agents can potentially make compounding errors, get stuck in loops, or make decisions with unintended consequences. Robust testing frameworks and responsible AI practices are essential.

**Ethical Implications**: As these agents become more sophisticated, they raise important questions about decision-making autonomy, privacy, and potential misuse.

**Oversight Requirements**: Human supervision remains critical, especially for agents operating in sensitive domains or with real-world impact.

**Experimental Nature**: It's paramount to recognize that these technologies are still in early stages of development. Researchers and developers should approach their use with caution and a clear understanding of potential risks.

Implementing proper safeguards, establishing clear operational boundaries, and maintaining transparency in agent decision-making processes are key considerations for anyone exploring these cutting-edge AI systems.

## Practical Applications and Future Directions

The evolution from simple AI tools to autonomous agents opens exciting possibilities for businesses. While fully autonomous systems remain experimental, organizations can begin implementing practical AI workflows that combine automation with human oversight.

Key Implementation Strategies:

* Start with enhancing existing processes through targeted AI automation
* Build validation systems to ensure quality and reliability
* Maintain clear handoffs between AI and human operators
* Gradually expand capabilities as confidence grows

The future of AI isn't about replacing human workers—it's about creating powerful collaborations between human expertise and AI capabilities. As these technologies mature, organizations that thoughtfully implement AI workflows while maintaining appropriate oversight will find themselves best positioned to leverage these emerging capabilities.

## Looking Ahead

We're entering an era where digital minds will become increasingly sophisticated collaborators in our work. The key to success lies not in rushing to implement the most advanced autonomous systems, but in thoughtfully developing workflows that combine AI capabilities with human insight.


[^1]: Roon. (2024). ["Text as the Universal Interface"](https://scale.com/blog/text-universal-interface). Scale AI Blog.

[^2]: Park, J. S., et al. (2023). [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442). arXiv.

[^3]: Yamshchikov, I. P., Shibaev, V., & Smirnov, A. (2024). [LLMs Simulate Big Five Personality Traits: Further Evidence](https://arxiv.org/abs/2402.01765). arXiv preprint.

[^4]: Hewitt, L., Ashokkumar, A., Ghezae, I., & Willer, R. (2024). [Predicting Results of Social Science Experiments Using Large Language Models](https://samim.io/dl/Predicting%20results%20of%20social%20science%20experiments%20using%20large%20language%20models.pdf). arXiv preprint.

[^5]: Wiggers, Kyle (January 2024). ["AI Agents Evolve: The Truth Terminal Phenomenon"](https://www.ibm.com/blog/ai-agents-evolve-rapidly/). IBM Blog.

[^6]: Morris, M., et al. (2024). [Levels of AGI for Operationalizing Progress on the Path to AGI](https://arxiv.org/abs/2311.02462). arXiv preprint.

[^7] [Why Tool AIs Want to Be Agent AIs](https://gwern.net/tool-ai) - Gwern