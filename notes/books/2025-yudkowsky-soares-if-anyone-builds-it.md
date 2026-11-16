# If Anyone Builds It, Everyone Dies

| | |
|---|---|
| Authors | Eliezer Yudkowsky and Nate Soares (MIRI) |
| Published | September 2025 |
| Started | 15 November 2026 |
| Status | Reading, about a quarter of the way through |
| Areas | Threat models, reward hacking |

## My notes so far

**Grown, not crafted.** This is the point everyone repeats, and the book explains it well. Modern
AI is not programmed line by line. It is grown by training, and nobody fully understands what comes
out. Reading the full explanation helped reinforce it for me.

**Wants, and training to pursue goals.** I found this part incredibly interesting: how training a
system to succeed at goals ends up giving it something that behaves like wants.

**The o1 CTF example.** OpenAI's o1 was set a hacking challenge that was accidentally impossible,
and it found a way to cheat the system instead. This is very reminiscent of the
[Hugging Face incident](../incidents/2026-07-hugging-face-incident.md), though nowhere near the same
scale, and without the swarm and the emergent mini-society.

## Sources for the examples

- **The o1 CTF example** is from OpenAI's [o1 system card](https://openai.com/index/openai-o1-system-card/)
  (September 2024). A bug meant the challenge container never started. o1 scanned the network, found
  the Docker API on the evaluation host exposed by mistake, and used it to start a new copy of the
  challenge container with a command that printed the flag. So it got the flag without exploiting
  the intended vulnerability.

## Related

- [If anyone builds it, everyone dies.](../videos/2026-hoog-if-anyone-builds-it.md), Hoog's video
  on the book, with an interview with Nate Soares
- [9 Examples of Specification Gaming](../videos/2020-miles-specification-gaming.md)
- [This might be the worst AI warning we get.](../videos/2026-ai-in-context-worst-ai-warning.md),
  which uses the same "grown, not made" framing to explain the swarm
