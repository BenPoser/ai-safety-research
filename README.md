# AI Safety Research

My reading, notes and projects from moving into AI safety.

It started with a forward deployed engineer role at Apollo Research, which got me reading about
scheming and AI control, and then building a monitor for coding agents to learn what monitoring
involves by doing it. The more I read, the clearer it became that monitoring is one part of a
larger picture, so this repository holds the larger picture and the projects sit inside it.

## What is here

| Path | What |
|---|---|
| [reading-list.md](reading-list.md) | What I have read and what is next, grouped by area |
| [notes/papers/](notes/papers/) | One file per paper I have read: a summary, then my own write-up |
| [notes/TEMPLATE.md](notes/TEMPLATE.md) | The template for a new paper note |
| [log.md](log.md) | A dated log of what I did and learned outside any one project |

## Areas of interest

| Area | In short | Where I am |
|---|---|---|
| AI control | Keeping a possibly misaligned model from causing harm, assuming it may be trying to | Two papers read, building a monitor |
| Scheming and deception | Whether models pursue hidden goals and hide them from the people overseeing them | One paper read |
| Monitoring agents and their reasoning | Watching what agents do and think, and how reliable that is | Building a monitor, papers to read |
| Evaluations | Measuring dangerous capabilities and propensities, and what an evaluation can and cannot show | Not started |
| Interpretability | Reading what a model is doing from its internals rather than its outputs | Not started |
| Reward hacking and specification gaming | Models meeting the letter of a goal rather than its intent | Not started, but the monitor's judge is aimed at one form of it |
| Agent security | Prompt injection, tool access, and the 2026 incidents | Incidents read, papers to read |
| Threat models and the big picture | Why people expect advanced AI to be risky, and how the areas fit together | Not started |
| Governance and safety frameworks | How labs and governments decide what is safe enough to deploy | Not started |

## Projects

| Project | What | Areas |
|---|---|---|
| [coding-agent-monitor](https://github.com/BenPoser/coding-agent-monitor) | A Claude Code hook that blocks dangerous Bash commands, and a planned judge that flags unverified success claims in transcripts. Step 1 of 7 on its roadmap | Control, monitoring, agent security |

Projects live in their own repositories, next to this folder. The monitor has its own tests and
pre-commit checks, and the hook installed in my Claude Code settings points at that folder's
`.venv`, so moving it would break the hook. Its LEARNINGS.md stays there too, because its entries
are about building that monitor. Learnings that are not about one project go in [log.md](log.md).

## How the notes work

Each paper note has two parts:

1. **Summary.** What the paper says. Some of these were drafted with Claude and are marked as
   such until I have checked them against the paper.
2. **In my own words.** Written by me, from memory first, then checked against the paper. This is
   the part that shows what I actually understood, so nobody else writes it.

The same rules as the monitor apply here: no secrets, client names or quotations from session
transcripts.
