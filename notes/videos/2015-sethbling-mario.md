# MarI/O - Machine Learning for Video Games

| | |
|---|---|
| Channel | SethBling |
| Link | https://www.youtube.com/watch?v=qv6UVOQ0F44 |
| Published | June 2015 |
| Length | 6 minutes |
| Areas | Reward hacking (background) |
| Status | Summary drafted by Claude from the transcript on 2026-11-15 |

## Summary of topics

**What it is.** A program that learns to play a Super Mario World level with no prior knowledge of
the game. It is written in Lua and runs inside the BizHawk emulator.

**How it learns.** It uses NEAT (NeuroEvolution of Augmenting Topologies, from Stanley and
Miikkulainen). Instead of training a fixed network with gradient descent, NEAT evolves a population
of small neural networks. The networks that do best breed, with mutations that change weights and
add new neurons and connections, so the structure of the network grows over time.

**Inputs, outputs and fitness.** The input is a simplified grid of the screen around Mario
(ground and blocks versus enemies). The outputs are controller buttons. Fitness is how far right
Mario gets, with a bonus for getting there quickly.

**The result.** After 34 generations, about a day of training, it completes the level. The video
shows the evolved network live as it plays, with the connections that fire as enemies come into
view.

**Why it is interesting for safety.** Nothing told the program how to play. It only had a score,
and it found its own way to raise that score, including odd moves a human would not choose. That
is the same mechanism behind specification gaming: the optimiser follows the measure, not the
intention.

## Related

- [9 Examples of Specification Gaming](2020-miles-specification-gaming.md)
