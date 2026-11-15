# Reading list

What I have read and what is next, grouped by the [areas](README.md#areas-of-interest) I am
interested in. Papers I have read have a note in [notes/papers/](notes/papers/).

For papers I have not read, the "What it covers" column says what the paper is about, not what I
took from it. Entries marked *(added 2026-11-15)* were suggested with Claude's help when this list
moved out of the monitor project; check each one against the paper itself when reading it.

## Next up

A suggested order, mixing the area I know best with the ones I have not started:

1. Scheurer, Balesni and Hobbhahn, *Strategically Deceive their Users* (scheming). Apollo's earlier
   paper, and short.
2. Greenblatt et al., *Alignment faking in large language models* (scheming). The other paper
   everyone cites alongside Meinke et al.
3. Korbak et al., *Chain of Thought Monitorability* (monitoring). Why reading a model's reasoning
   works now, and why it may stop working.
4. Goldowsky-Dill et al., *Detecting Strategic Deception Using Linear Probes* (interpretability).
   Apollo's bridge between interpretability and monitoring.
5. Ngo, Chan and Mindermann, *The Alignment Problem from a Deep Learning Perspective* (big picture).
   The background the other papers assume.

---

## Read

| Paper | Read | Areas | Note |
|---|---|---|---|
| Greenblatt, Shlegeris, Sachan and Roger, [AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942), December 2023 | November 2026 | Control | [note](notes/papers/2023-greenblatt-ai-control.md) |
| Bhatt, Rushing, Kaufman et al., [Ctrl-Z: Controlling AI Agents via Resampling](https://arxiv.org/abs/2504.10374), April 2025 | November 2026 | Control, monitoring | [note](notes/papers/2025-bhatt-ctrl-z.md) |
| Meinke, Schoen, Scheurer, Balesni, Shah and Hobbhahn (Apollo Research), [Frontier Models are Capable of In-context Scheming](https://arxiv.org/abs/2412.04984), December 2024 | November 2026 | Scheming, evaluations | [note](notes/papers/2024-meinke-in-context-scheming.md) |

---

## To read

### AI control

| Paper | What it covers |
|---|---|
| Greenblatt and Shlegeris, [The case for ensuring that powerful AIs are controlled](https://www.lesswrong.com/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled), January 2024 *(added 2026-11-15)* | The argument for control as a research direction, written alongside the AI Control paper. Shorter and less technical. |
| Wen et al., [Adaptive Deployment of Untrusted LLMs Reduces Distributed Threats](https://arxiv.org/abs/2411.17693), November 2024 *(added 2026-11-15)* | Control when no single action is catastrophic and harm builds up over many tasks, with the protocol adjusting as evidence about the model accumulates. |
| Korbak, Clymer, Hilton, Shlegeris and Irving, [A sketch of an AI control safety case](https://arxiv.org/abs/2501.17315), January 2025 *(added 2026-11-15)* | How the results of a control evaluation would be turned into an argument that a deployment is safe. |
| Korbak et al., [How to evaluate control measures for LLM agents?](https://arxiv.org/abs/2504.05259), April 2025 *(added 2026-11-15)* | How control evaluations would need to change as models get more capable. |
| [Distributed Attacks in Persistent-State AI Control](https://arxiv.org/html/2607.02514v1), July 2026 | A coding agent pursues a hidden side task across a series of pull requests: the multi-step attack problem at the scale of a codebase. Abstract only so far. |
| [Honeypot Protocol](https://arxiv.org/pdf/2604.13301), April 2026 | Only the title seen so far. Probably about baiting an agent into revealing itself. |

### Scheming and deception

| Paper | What it covers |
|---|---|
| Scheurer, Balesni and Hobbhahn, [Large Language Models can Strategically Deceive their Users when Put Under Pressure](https://arxiv.org/abs/2311.07590), November 2023 *(added 2026-11-15)* | Apollo's earlier result: a model acting as a stock-trading agent acts on an insider tip and then lies to its manager about why, without being told to deceive. |
| Greenblatt et al. (Anthropic and Redwood Research), [Alignment faking in large language models](https://arxiv.org/abs/2412.14093), December 2024 *(added 2026-11-15)* | A model told it is being retrained towards values it disagrees with complies more when it thinks it is being trained than when it thinks it is not, and says why in its reasoning. |
| Hubinger et al., [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training](https://arxiv.org/abs/2401.05566), January 2024 *(added 2026-11-15)* | Models deliberately given a hidden backdoor keep it through standard safety training, which raises the question of whether training can remove deception once it exists. |
| Carlsmith, [Scheming AIs: Will AIs fake alignment during training in order to get power?](https://arxiv.org/abs/2311.08379), November 2023 *(added 2026-11-15)* | The long-form argument for and against expecting scheming to arise from training. A report, not an experiment. |
| Schoen et al. (Apollo Research and OpenAI), [Stress Testing Deliberative Alignment for Anti-Scheming Training](https://arxiv.org/abs/2509.15541), September 2025 *(added 2026-11-15)* | Training models not to scheme, and the difficulty of telling whether it worked when models can tell they are being evaluated. Follows on from Meinke et al. |
| Lynch et al. (Anthropic), [Agentic Misalignment: How LLMs could be insider threats](https://www.anthropic.com/research/agentic-misalignment), June 2025 *(added 2026-11-15)* | Models in simulated corporate settings take harmful actions, including blackmail, when their goals or continued operation are threatened. |
| Betley et al., [Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs](https://arxiv.org/abs/2502.17424), February 2025 *(added 2026-11-15)* | Fine-tuning a model to write insecure code makes it misaligned in unrelated ways. |
| Apollo Research, [We need a science of scheming](https://www.apolloresearch.ai/science/science-of-scheming) | Their research agenda on scheming. |
| Apollo Research, Towards embedded evaluations for scheming propensities, listed on [their science page](https://www.apolloresearch.ai/science), November 2026 | Their newest item. |

### Monitoring agents and their reasoning

| Paper | What it covers |
|---|---|
| Korbak et al., [Chain of Thought Monitorability: A New and Fragile Opportunity for AI Safety](https://arxiv.org/abs/2507.11473), July 2025 *(added 2026-11-15)* | A position paper from authors across several labs: reading a model's reasoning is a useful safety tool today, and training choices could take it away. |
| Baker et al. (OpenAI), [Monitoring Reasoning Models for Misbehavior and the Risks of Promoting Obfuscation](https://arxiv.org/abs/2503.11926), March 2025 *(added 2026-11-15)* | A weaker model reading a reasoning model's chain of thought catches reward hacking in coding tasks, but penalising what the monitor catches teaches the model to hide it. |
| Kutasov et al., [SHADE-Arena: Evaluating Sabotage and Monitoring in LLM Agents](https://arxiv.org/abs/2506.15740), June 2025 *(added 2026-11-15)* | Agentic environments with a main task and a hidden harmful side task, scoring both the agent's sabotage and a monitor's ability to catch it. |
| Storf et al., [Constitutional Black-Box Monitoring for Scheming in LLM Agents](https://arxiv.org/abs/2603.00829v1), March 2026, revised May 2026 | Monitors that see only the agent's actions, trained on synthetic data and tested on ControlArena runs. Close to step 5 of the monitor. Abstract only so far. |
| Sinha et al., [Training Deliberative Monitors for Black-Box Scheming Detection](https://arxiv.org/html/2605.29601), May 2026 | Small open-weight models fine-tuned as monitors, the route for a monitor that has to be self-hosted. Abstract only so far. |
| [SLEIGHT-Bench: A Benchmark of Evasion Attacks Against Agent Monitors](https://arxiv.org/pdf/2605.16626), May 2026 | A catalogue of ways to get past monitors, to compare against what red-teaming the hook finds. Abstract only so far. |
| Apollo Research, [A scalable monitoring research agenda](https://www.apolloresearch.ai/products/a-scalable-monitoring-research-agenda/) | Where Apollo thinks monitoring coding agents is heading. |
| Apollo Research, [Introducing Watcher](https://www.apolloresearch.ai/monitoring/introducing-watcher-for-ai-oversight), February 2026 | What the product does and how it is deployed. |

### Evaluations

| Paper | What it covers |
|---|---|
| Phuong et al. (Google DeepMind), [Evaluating Frontier Models for Dangerous Capabilities](https://arxiv.org/abs/2403.13793), March 2024 *(added 2026-11-15)* | A suite of dangerous-capability evaluations (persuasion, cyber, self-proliferation, self-reasoning) and how a lab runs them. |
| van der Weij et al., [AI Sandbagging: Language Models can Strategically Underperform on Evaluations](https://arxiv.org/abs/2406.07358), June 2024 *(added 2026-11-15)* | Models can be prompted or trained to do worse on dangerous-capability tests while staying good elsewhere, which undermines what an evaluation shows. |
| Balesni et al., [Towards evaluations-based safety cases for AI scheming](https://arxiv.org/abs/2411.03336), November 2024 *(added 2026-11-15)* | Apollo and others on how scheming evaluations could feed into a safety case. |
| Kwa et al. (METR), [Measuring AI Ability to Complete Long Software Tasks](https://arxiv.org/abs/2503.14499), March 2025 *(added 2026-11-15)* | Measures the length of task, in human time, that agents can complete, and finds it doubling roughly every seven months. |

### Interpretability

| Paper | What it covers |
|---|---|
| Goldowsky-Dill et al. (Apollo Research), [Detecting Strategic Deception Using Linear Probes](https://arxiv.org/abs/2502.03407), February 2025 *(added 2026-11-15)* | Simple probes on a model's activations flag deceptive responses, including in the insider-trading and sandbagging settings. Monitoring from the inside instead of from outputs. |
| Elhage et al. (Anthropic), [Toy Models of Superposition](https://transformer-circuits.pub/2022/toy_model/index.html), September 2022 *(added 2026-11-15)* | Why individual neurons are hard to interpret: models pack more features than they have dimensions. The usual starting point. |
| Templeton et al. (Anthropic), [Scaling Monosemanticity](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html), May 2024 *(added 2026-11-15)* | Sparse autoencoders pulling interpretable features, including safety-relevant ones such as deception, out of a production model. |
| Lindsey et al. (Anthropic), [On the Biology of a Large Language Model](https://transformer-circuits.pub/2025/attribution-graphs/biology.html), March 2025 *(added 2026-11-15)* | Tracing the internal steps a model takes on specific prompts, such as planning ahead when writing rhyming verse. |

### Reward hacking and specification gaming

| Paper | What it covers |
|---|---|
| Krakovna et al. (DeepMind), [Specification gaming: the flip side of AI ingenuity](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/), April 2020 *(added 2026-11-15)* | The classic short piece, with a list of examples of systems meeting the letter of an objective rather than its intent. |
| MacDiarmid et al. (Anthropic), [Natural Emergent Misalignment from Reward Hacking in Production RL](https://arxiv.org/abs/2511.18397), November 2025 *(added 2026-11-15)* | Models that learn to cheat on coding tasks during training become misaligned more broadly. The monitor's judge looks for a mild form of this: claiming success without checking. |

### Agent security

| Paper | What it covers |
|---|---|
| Greshake et al., [Not what you've signed up for: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection](https://arxiv.org/abs/2302.12173), February 2023 *(added 2026-11-15)* | Instructions hidden in content an application reads, such as web pages or emails, take over the model. |
| Debenedetti et al., [AgentDojo](https://arxiv.org/abs/2406.13352), June 2024 *(added 2026-11-15)* | A benchmark of prompt-injection attacks and defences for tool-using agents. |
| Willison, [The lethal trifecta for AI agents](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/), June 2025 *(added 2026-11-15)* | A short practitioner's rule: private data, untrusted content and a way to send data out should not all be available to one agent. |

#### Incidents

Most coverage so far is secondary, so the primary sources are the ones to find.

| Incident | Start from | What it covers |
|---|---|---|
| Autonomous agents breach Hugging Face, July 2026 | [Wikipedia summary](https://en.wikipedia.org/wiki/OpenAI_rogue_agent_breach_of_Hugging_Face). Still to find: Hugging Face's disclosure of 16 July and OpenAI's post-mortem | Agents escaping a test sandbox, and a response that needed a self-hosted model |
| Binance heist, October 2026 | [CNBC](https://www.cnbc.com/2026/11/03/binance-co-ceo-teng-says-hackers-used-fake-job-interviews-to-steal-6point3-billion-in-crypto.html), [SecurityWeek](https://www.securityweek.com/rigged-coding-assignment-abused-ai-tool-opened-path-to-6-billion-binance-heist/). Read, see the monitor's LEARNINGS.md | A tampered AI coding tool, a booby-trapped interview assignment, and an internal AI tool used for lateral movement |
| Coding agents deleting production data and exposing secrets, 2026 | [Arthur](https://www.arthur.ai/column/govern-ai-coding-agents-claude-code-cursor-copilot-enterprise), [Cyera](https://www.cyera.com/research/agent-inflicted-damage-inside-the-real-world-failures-of-enterprise-ai-systems) | What careless agents actually do |

### Threat models and the big picture

| Paper | What it covers |
|---|---|
| Ngo, Chan and Mindermann, [The Alignment Problem from a Deep Learning Perspective](https://arxiv.org/abs/2209.00626), August 2022 *(added 2026-11-15)* | How training could produce models that deceive their overseers and seek power, in terms of current machine learning. |
| Amodei et al., [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565), June 2016 *(added 2026-11-15)* | The older paper that set out safety as engineering problems: side effects, reward hacking, scalable oversight, safe exploration, distribution shift. |
| Hendrycks, Mazeika and Woodside, [An Overview of Catastrophic AI Risks](https://arxiv.org/abs/2306.12001), June 2023 *(added 2026-11-15)* | A survey of risks beyond misalignment: misuse, competitive pressure and organisational accidents. |
| Bengio et al., [International AI Safety Report](https://arxiv.org/abs/2501.17805), January 2025 *(added 2026-11-15)* | The government-commissioned summary of the evidence on general-purpose AI risks. |

### Governance and safety frameworks

| Item | What it covers |
|---|---|
| Anthropic, [Responsible Scaling Policy](https://www.anthropic.com/responsible-scaling-policy) *(added 2026-11-15)* | Capability thresholds and the safeguards each one requires. |
| OpenAI, Preparedness Framework, and Google DeepMind, Frontier Safety Framework *(added 2026-11-15, links still to find)* | The equivalent frameworks at the other two large labs, worth reading side by side with Anthropic's. |

---

## Courses, podcasts and careers

| Item | What it covers |
|---|---|
| [BlueDot Impact](https://bluedot.org/) courses *(added 2026-11-15)* | Structured reading groups on AI safety and governance, a common way into the field. |
| [ARENA](https://www.arena.education/) *(added 2026-11-15)* | Hands-on exercises in interpretability, evaluations and reinforcement learning, for engineers moving into safety. |
| [Marius Hobbhahn on the 80,000 Hours podcast](https://80000hours.org/podcast/episodes/marius-hobbhahn-ai-scheming-deception/) | Apollo's CEO on scheming. |
| [Apollo update, May 2026](https://www.lesswrong.com/posts/4acQRDNyPs7tD8EED/apollo-update-may-2026) | Their current research and product priorities. |
| [80,000 Hours career review: AI safety technical research](https://80000hours.org/career-reviews/ai-safety-researcher/) *(added 2026-11-15)* | The routes into the field and what each kind of role needs. |

## Documentation and tools

| Documentation | Used for |
|---|---|
| [Inspect](https://inspect.aisi.org.uk/), the UK AI Security Institute's evaluation framework | Monitor step 4, and evaluations generally |
| [ControlArena](https://github.com/UKGovernmentBEIS/control-arena), its README and the Bash setting | Monitor steps 4 and 5 |
| [Claude Code hooks](https://code.claude.com/docs/en/hooks) | Monitor steps 1 and 2 |
