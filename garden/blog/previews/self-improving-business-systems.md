---
title: Self-Improving Business Systems
date: '2026-07-11'
image: /images/posts/self-improving-business-systems/hero-v14a-recursive-field.png
draft: true
preview: true
tags:
  - ai
  - cybernetics
  - organizations
---

# Self-Improving Business Systems

After working on enterprise AI deployments for the last year and a half, I’ve come to describe the main problem with adoption as organizations being stuck in local optima: their business processes are designed for a world built by humans while we barrel towards a future built by machines.

Despite rapidly advancing capabilities, knowledge workers are struggling to find use cases beyond generating content and searching for documents. Meanwhile, Engineering has figured out how to use the same tokens to build a Software Factory. The two outcomes are not the same, yet they share the same cost per token.

Executives aren’t sure how to respond.

What gives? Should we not let anyone but the engineers have access to bigger models? [Because, *obviously*, only *they* can be trusted with such power.]

In reality, software engineers have the advantage in the early innings of an AI scaling regime. The labs want the best coding models to train the next iteration of even better coding models. As a result, knowledge work lags behind engineering in its effective application of LLMs

Don’t get me wrong. AI is certainly improving productivity for knowledge workers. It just remains rare to see LLMs working for long periods to automate entire business processes in the same way they can [solve coding problems](https://metr.org/time-horizons/). If we want to unlock the true potential of AI in the organization, we need to fundamentally redesign the work from our current human-centric model to new one that considers the realities of working with AIs. In my view, this is about embracing the [cybernetic organization](https://kenneth.computer/blog/cybernetic-organization). It means starting to view the organizational system as a network of humans and AIs cooperating towards business goals.

Practically, this isn't easy. Organizations are filled with human-shaped holes, which is why fitting LLMs into business processes is less about automation and more about work system redesign. One way to start is by finding the pockets of work that are already LLM-shaped and taking lessons from the playbooks of engineers building software factories: *[the goal should be to go from writing prompts to engineering loops](https://x.com/steipete/status/2063697162748260627?s=46).*

In this post, I'll outline a framework for knowledge work's equivalent of the software factory: self-improving business systems (SIBS). In my view, SIBS alongside software factories are the new shapes of organizational business units that make up a truly AI-native organization.

## North star
The clearest potential for a fully agentic, recursively self-improving organization is inside a quant fund. The AlphaFund whitepaper calls the endpoint the [Autonomous Self-Improving Corporation (ASIC)](https://www.alphafund.com/whitepaper/): a firm that allocates its own capital in software, scores every action against the balance sheet, and feeds the returns into the next cycle. For a fund, every trade resolves quickly and unambiguously into money made or lost. The quant fund is the limit case of a fully verifiable work environment: clean, fast, all-encompassing feedback is what makes autonomy possible.

Unfortunately, this is what the rest of the economy lacks. Revenue, retention, and brand resolve slowly, are hard to attribute to any one action, and are spread across teams that share no single metric. So while the ASIC is not a realistic goal anyone outside of quantitative finance can reach, it serves as a useful north star. It also helps establish a principle: autonomous adaptive systems need clear, attributable signals from the environment to self-improve.

## The local regime
Organizations are adaptive systems that improve through feedback. At scale, they are a network of subsystems called business units, each of which comprises a work system that executes tasks to achieve goals, which trace back to the balance sheet with varying fidelity. Tasks are the smallest units of execution in a work system. Some tasks are predictable and repeatable, while others are emergent from the environment. Agents doing work on predictable repeatable tasks are useful, but they will not enable businesses to improve their performance beyond what the local regime permits.
![A single organization node rests on a smaller local peak while a taller peak rises beyond the intervening valley](/images/posts/self-improving-business-systems/local-optimum-v6.svg)
[Gwern](https://www.lesswrong.com/posts/bX7q9NcoGpb5KdZzQ/if-i-wanted-to-spend-way-more-on-ai-what-would-i-spend-it-on) offers a useful way to see the obstacle. For decades the only general intelligence you could hire was a person, so every workflow, role, and handoff was cut to a human shape. A company therefore ends up full of human-shaped holes and almost no LLM-shaped ones, because any opening a model could simply drop into would, by now, already have a person in it. To put it simply, the problem is less about LLM capability than it is about system design, and modern organizational systems were not designed for LLMs.

The challenge that lies ahead of us then is somewhat counterintuitive. To cross the chasm into a more productive "AI-native" regime, we may experience a loss in productivity until we can foster the organizational learning necessary to fully adapt to the new world.

More concretely, we can think about a business process as a graph of people and technology connected together by the flow of information. For the work to flow through it, many things have to go right. In the old human-centric regime, learning how to do something the correct way did not require writing down a standard operating procedure for every single task or workflow, let alone creating an eval to keep the system aligned [though, to be fair, performance reviews are a form of human evals, but this responsibility fell on management]. Generally, you showed someone something once or twice, then they started doing it on their own, albeit somewhat poorly perhaps until they learned to self-improve.

![A bounded business process held together by human operators, tools, and handoffs, with no agent-ready interface](/images/posts/self-improving-business-systems/human-shaped-work-system-v1.svg)

Agents today do not work like this. They require writing careful instructions that take iterations to ensure they are not misspecified and new forms of evaluations that look more like behavioral science than user acceptance testing. The economic potential of agents in the organization seems theoretically uncapped, but without AI-native teams capable of both identifying the right problems and redesigning the work, an organization's AI productivity gains might as well be neutralized as the rest of its competition experiences the same gains when the labs ship new models. A competitive advantage in this regime can therefore look quite simple: the ability to continuously improve AI systems by embedding and improving upon tacit knowledge through feedback loops that enable you to keep one step ahead of the frontier.

## Finding useful signal
The first problem teams will face is looking for the right problem for agents to work on. The simplest way to determine this is by considering *potential value* and *signal quality*. The first asks "What would the maximum value of this agent be if it could run completely autonomously, 24/7?" The second asks, "How well can available signals tell us about our agent's performance on this problem?"

A good sign a problem is LLM-shaped is when its results are easy to verify. Software factories work because we can take external signals like user feedback or Github issues and translate those into problems that can be verified with code. For example, if a user submits a bug report, agents can set up an environment, reproduce the bug, inspect the logs, and verify that a proposed fix solves it, leaving behind traces and tests that can inform the next run. This simple loop constitutes the software factory in its most basic form and from it, we can reverse engineer its principles.

At a minimum, the loop needs four things:

- **Trigger:** an observable event tells the system when to act.
- **Environment:** the agent can access the context, tools, permissions, and state required to do the work.
- **Verification:** checks during the run tell the agent whether the work meets its requirements and what needs to change.
- **Outcome signal:** a downstream result tells the system whether the completed work achieved its intended goal.

Verification closes the loop within a run. The outcome signal closes the loop between runs.

![An agent works inside a bounded business system, where a trigger starts work, internal checks guide it, and a measurable outcome returns a learning signal](/images/posts/self-improving-business-systems/finding-useful-signal-network-v2.svg)

Triggers and outcomes are external signals: one starts the run, while the other tells us how it performed. Verification is internal to the work, guiding the agent toward an acceptable result. Automating a complete business process requires both. Without verification, the agent cannot reliably complete the work; without an outcome signal, the system cannot tell whether it is optimizing the right thing.

In knowledge work environments, this is where the loop usually breaks. Much of the work is still verified by humans, through judgment that is slow, tacit, and rarely captured in a form an agent can use.

A good place to start, then, is with a business function that already tracks signals tightly coupled to the outcome it owns. Sales, recruiting, and support are useful examples: their systems record conversion rates, pipeline movement, response quality, time to resolution, and retention.

For these functions, the system is already doing part of what we are trying to achieve, albeit with a design that does not fit a world where LLMs exist. It already iterates through feedback from existing signals. The job is to give an agent access to those same signals so that it can iterate too.

Sometimes the problem is deeper. Perhaps the team never clearly defined the outcome, mapped the process, or instrumented the work well enough to trace it back. To find useful signal in those cases, we will need to build it.

Sometimes we get lucky and find we can simply purchase new software to solve this — perhaps MCP is all you need. But often, the problem is the signal isn't clear, detectible, or relies on judgement.

In these cases, it is important to ensure agent builders can collaborate with domain experts. For verticalized agents, what you will quickly find is that your ability to iterate on agent performance will be bottlenecked by your ability to get feedback from the domain experts.

Best to get that loop started fast. This can start with controlled UAT, but the agent traces from these early iterations should become a dataset. It becomes the job of the tastemaker to turn tacit judgment into rubrics, golden sets, and verifiers that are increasingly embedded in an [agent behavior spec](https://www.braintrust.dev/blog/behavior-specs).

![Repeated human judgments leave traces that become a reusable verifier, giving an agent a stable edge into the work system](/images/posts/self-improving-business-systems/finding-useful-signal-verifier-v1.svg)

This suggests that skills like prompt engineering and agent evaluation will become increasingly important over the next era. Humans will be needed to orchestrate agents, judge their outputs, and update them methodically, leaning on domain expertise and taste to prevent [Goodharting](https://en.wikipedia.org/wiki/Goodhart%27s_law) and keeping systems aligned. The goal however, is to keep humans from being the bottlenecks and enable them to be systems architects.

## Self-improving business systems
At the top of the hierarchy, organizations have slow feedback cycles. Finance doesn't learn what investments worked until the books are closed. Without a clear signal to improve the organization's bottom line, we need to look for an intervention point at lower levels of the hierarchy.
![A network becomes increasingly connected from individuals through teams and business units to the organization, then opens into the sparse environment; the business unit is highlighted as the bounded system that owns an outcome](/images/posts/self-improving-business-systems/organizational-ecology-v4.svg)
Most adoption strategies target individuals and teams applying AI at the task level. While these intervention strategies can enable productivity gains, the real gains come from engineering business outcomes.

In my view, this suggests the ideal intervention point is at the level of the business unit: the smallest set of connections across the organizational network with ownership over a business outcome.

Sometimes this can be a single team, but often business outcomes are the result of multiple teams coordinating business processes together.

To automate the whole system, we need to be able to verify our agent completed a business process up to specification. With the right data infrastructure, we can find signals at all of these levels. It is at the level where we can no longer get useful signal where we place the human-in-the-loop.

![Agentic work expands from a single task, to a coordinated workflow, to a business process governed by feedback](/images/posts/self-improving-business-systems/levels-of-agentic-work-v1.svg)


This is [loop engineering](https://addyosmani.com/blog/loop-engineering/) applied one level up from the codebase. A software factory is the cleanest example of the pattern: an issue triggers work, an agent operates in a repository, and tests, logs, builds, and deployments tell us what happened.

Code has something most business work does not: a lot of its judgment infrastructure comes built in. The code executes. Tests can tell us whether it works. A build can fail. A deployment can break. The loop has a lot of useful signal to climb against.

For business work, we have to build more of that loop ourselves. We need to translate the process into an operating procedure, give the agent the right environment to do the work, and create the rubrics and verifiers that tell us whether its output is any good.

At the level of the business unit, a set of related business processes forms the business system. Each process can become an **Agentic Business Loop**, and together those loops make up a **Self-Improving Business System (SIBS)**: an agent fleet wired to measurable signals, run by people who orchestrate it, judge it, and keep it aimed at the right target. Build one, then another, and the organization climbs toward the ASIC ideal one loop at a time — without ever handing over the keys.

From an AI adoption standpoint, we might call this *middle-out transformation*. Instead of targeting users, teams, or the broader organization, we focus on the business unit, the smallest business complete system in the organizational network.

This empowers the people on the team by moving them up from doing the rote work to running the system, and it pulls the business out of the local optimum it has settled into. Repeat that across functions and you have transformed the organization, without ever staging the demolition that “AI transformation” usually implies.
## Agentic business loops
![The inner agent observe-reason-act loop and outer human monitor-evaluate-steer loop](/images/posts/self-improving-business-systems/agent-human-loops-v4.svg)

For an ABL to improve a business process, the system needs the following:
- External trigger: a request, schedule, event, or changing condition tells the system when there is work to do.
- Operating procedure and work environment: the agent has the context, tools, permissions, and workspace required to carry out the work.
- Internal feedback: rubrics, tests, policy checks, traces, or human review establish whether the work meets its requirements.
- External outcome signal: a downstream result establishes whether the completed work actually achieved its goal.
- Learning trace: each run leaves behind evidence that can inform the next.

The **Agentic Business Loop (ABL)** is the full dual-loop system around a business process. Its inner loop is the agent execution loop: it gets a trigger, does the work, checks it against the available feedback, and keeps iterating until it can pass. It can work for virtually anything that constitutes creating an artifact: a document, a slide deck, an HTML page, a support response.

But outside of code, someone usually has to construct the judge. This is where the **human-in-the-loop (HITL)** comes in. Start with controlled UAT. The traces from those early iterations become a dataset. The domain expert or tastemaker turns their tacit judgment into golden sets, rubrics, and verifiers that become increasingly embedded in the agent's design.

The outer loop is the human governance loop. Its job is to monitor and assess the business system: to judge whether the agents are climbing the right hills, notice when the goal has drifted, and steer as its helmsman. Without that gate, agents can game the system: engagement becomes clickbait, pipeline quotas become high churn customers, resolution rates become tickets closed with generic unhelpful "solutions." Without the outer loop, the inner agent loop risks producing high-performance slop: confident output that maxes the target while destroying the value it once represented.

## The future of work

Designing self-improving business systems requires leveling people up into roles more managerial in nature. Instead of being responsible for completing tasks they become governors of a business process.

If this framing holds, work is not disappearing so much as changing shape. I suspect we'll see smaller teams capable of accomplishing much more when the knowledge and infrastructure around deploying and evaluating agents matures.

Over the next few years, agents will increasingly take on larger loads of the work inside of an organization, but when intelligence is ubiquitous, your taste is your advantage. Most teams adopting AI today are taking the first steps automating work that would previously take hours to days, from research and analysis to document synthesis and message generation, but are still bottlenecking the productivity gains by because they feel the need to review every AI output.

Moving beyond this regime occurs when workers begin codifying their judgement into something LLMs can work with. Only then can do we shift the human review bottleneck beyond the task and unto the business process.

As human responsibility moves outward, tooling will need to move with it. We still need better ways to build agents, evaluate them, and architect broader systems composed by their work. While this is an ongoing development being coordinated across the AI industry, the functions needed for the next generation of organizations are already becoming clear.

![Human responsibility moves outward from shaping an agent, to shaping its judge, to shaping the broader business system](/images/posts/self-improving-business-systems/future-of-work-v2.svg)

Builders translate business processes into the context, tools, prompts, and skills required to perform the work. Evaluators turn domain expertise into prompts, rubrics, golden sets, and verifiers that steer agents to improvement. Architects compose the broader agent system: the loops and graphs that define how business processes across the organization all string together,

These will not necessarily be distinct jobs. Within an early SIBS, the same person might perform all three functions. Conversely, an agent may need multiple domain experts as evaluators. What changes is the level at which human judgment is applied: less effort executing individual tasks, more effort shaping agent behavior, governing feedback loops, and designing systems.

For the forseable future, the human-in-the-loop serves a greater purpose: to bridge the gap between the frontier and the out-of-distribution-tail. LLMs can do many tasks reliably from their training data, but the tacit knowledge an organization can codify into a dataset is what lights the path up the next hill.

Evaluators work at that frontier, turning edge cases and tacit judgment into context, tooling, data, and evals that give the model a basis to handle new problems. In doing so, they move the frontier forward for their organization before it moves forward for everyone else. That is where human work concentrates, and how organizations build competitive advantage in the age of AI.

Ultimately, the AI-native organization will not arrive as a top-down transformation. It will emerge the way the software factory did: one loop at a time, inside the parts of the business where the work is most legible.

---
## References

- AlphaFund, *[The Autonomous Self-Improving Corporation](https://www.alphafund.com/whitepaper/)*
- Gwern, *[If I wanted to spend way more on AI, what would I spend it on?](https://www.lesswrong.com/posts/bX7q9NcoGpb5KdZzQ/if-i-wanted-to-spend-way-more-on-ai-what-would-i-spend-it-on)*
- Sarah Constantin, *[The Great Data Integration Schlep](https://www.lesswrong.com/posts/7L8ZwMJkhLXjSa7tD/the-great-data-integration-schlep)*
- Addy Osmani, *[Loop Engineering](https://addyosmani.com/blog/loop-engineering/)*
