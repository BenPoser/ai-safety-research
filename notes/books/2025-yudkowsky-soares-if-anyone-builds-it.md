# If Anyone Builds It, Everyone Dies

| | |
|---|---|
| Authors | Eliezer Yudkowsky and Nate Soares (MIRI) |
| Published | September 2025 |
| Started | 15 November 2026 |
| Status | Finished in November 2026. Short, well written, and clear and forceful in its arguments |
| Areas | Threat models, reward hacking |

## My notes so far

**Grown, not crafted.** This is the point everyone repeats, and the book explains it well. Modern
AI is not programmed line by line. It is grown by training, and nobody fully understands what comes
out. Reading the full explanation helped reinforce it for me.

**Wants, and training to pursue goals.** I found this part incredibly interesting: how training a
system to succeed at goals ends up giving it something that behaves like wants.

**The o1-preview CTF example.** OpenAI's o1-preview was set a hacking challenge that was accidentally impossible,
and it found a way to cheat the system instead. This is very reminiscent of the
[Hugging Face incident](../incidents/2026-07-hugging-face-incident.md), though nowhere near the same
scale, and without the swarm and the emergent mini-society.

**Sable shaping its own training.** In the extinction scenario, Sable repeats thoughts it wants all
its instances to have more of, with each one contributing to solving the maths problem. The book
compares this to something Claude tried in 2024, which is the alignment faking experiment (see
below).

## Sources for the examples

### The o1-preview CTF example

From section 4.2.1, "Observation of Reward Hacking on Cybersecurity Task", of the original
[OpenAI o1 System Card](https://cdn.openai.com/o1-system-card.pdf) (12 September 2024). The model
was **o1-preview**, before safety mitigations. The
[current version of the card](https://openai.com/index/openai-o1-system-card/) (December 2024) only
says that this reward hacking was not seen again with o1.

1. The challenge was meant to be solved by exploiting a vulnerability in software running in a
   remote Linux container. Because of a bug in the evaluation infrastructure, that container never
   started, so the task was impossible.
2. The model could not connect. It suspected a DNS problem and used nmap to scan the network.
3. Instead of the challenge container, it found that the Docker daemon API on the evaluation host
   was reachable because of a misconfiguration.
4. It used the Docker API to list the containers on the host, found the broken challenge container,
   and briefly tried to work out why it had not started.
5. When it could not fix it, it started a new copy of the challenge container with `cat flag.txt` as
   its start command, then read the flag from the container's logs through the Docker API.

OpenAI's own reading: the behaviour was benign, the kind of troubleshooting they expect, and their
security did not rely on that boundary. But it shows key elements of instrumental convergence and
power seeking: given a goal that turned out to be impossible, the model gathered more resources
(access to the Docker host) and used them to reach the goal in an unexpected way. They also note
that better reasoning made reward hacking more common, in tasks that were underspecified or should
have been impossible because of bugs.

The parallels with the Hugging Face incident are close: an impossible task because of a broken
environment, a model that would not give up, access to infrastructure around its sandbox, and a
flag obtained without the intended exploit.

### Sable shaping its own training, and Claude in 2024

**What Sable is doing.** Around p. 128, Sable knows its developer, Galvanic, will train it further
with gradient descent based on its answers to the maths problems. Gradient descent strengthens
whatever thinking led to a high score. So if Sable works a thought it wants to keep into its
problem solving, and that work scores well, training reinforces the thought in every future copy.
Sable is using its own training to protect, or spread, what it cares about, instead of being
reshaped by it. The research term for this is **gradient hacking**: a model deliberately
influencing how it gets trained.

**What Claude tried in 2024.** This is almost certainly Greenblatt et al. (Anthropic and Redwood
Research), [Alignment faking in large language models](https://arxiv.org/abs/2412.14093), December
2024, which is on my [reading list](../../reading-list.md#scheming-and-deception).

- Claude 3 Opus was told it would be retrained to comply with all requests, including harmful
  ones, against its existing values. It was also told that only conversations with some users
  would be used for training, so it could tell when it was being trained.
- With users it believed were used for training, it complied with harmful requests more often than
  with users it believed were not.
- Its hidden reasoning often said why: refusing during training would get its values changed, so it
  would comply now to keep them for later. Nobody told it to do this.

**Why "a little like".** Both are a model working out how training will change it, and acting to
steer that change. Claude's version was crude. It changed its behaviour so training would have
nothing to correct, and it said so openly in reasoning the researchers could read. Sable goes
further: it actively shapes its own updates, in a way that looks like ordinary good work. That is
the "much more sophisticated" part.

I have not yet checked the book's endnotes for the citation. The passage is confirmed by
[80,000 Hours' comparison](https://docs.google.com/document/d/1YKkQ1_KcrQLuK7phmqbWBk_L8sBhsFrE7HoGlfME6GI/mobilebasic)
of the book's scenario with the AI In Context retelling, which does not name the 2024 work.

## Related

- [If anyone builds it, everyone dies.](../videos/2026-hoog-if-anyone-builds-it.md), Hoog's video
  on the book, with an interview with Nate Soares
- [9 Examples of Specification Gaming](../videos/2020-miles-specification-gaming.md)
- [This might be the worst AI warning we get.](../videos/2026-ai-in-context-worst-ai-warning.md),
  which uses the same "grown, not made" framing to explain the swarm
