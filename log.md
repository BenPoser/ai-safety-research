# Log

What I did and learned, newest first, with a date.

---

## 2026-11-24: Value Leakage

Read Betley, Treutlein et al., *Value Leakage*, and discussed it with Claude. Wrote it up in
[notes/papers/2026-betley-value-leakage.md](notes/papers/2026-betley-value-leakage.md). The
discussion turned into a research proposal:
[notes/proposals/2026-11-preference-ladder.md](notes/proposals/2026-11-preference-ladder.md).

What stood out:

- The evidence is stronger than the framing. The answer to my anchoring worry is in a footnote:
  the symmetric design makes pure anchoring score zero.
- The key distinction is direction. Sycophancy bends towards the user; value leakage bends towards
  the model, against the user.
- "Values" isn't defined clearly. Most of what the paper shows is better called preferences, and
  only one task measures the preference independently.
- A ladder of wants (quirks, preferences, values, goals) is a way to ask what training pushes
  models up it.
- Covertness is the strongest claim and the dangerous part. More reasoning lowers the bias, but
  newer models aren't reliably better.
- Added documented quirks and preferences to the proposal (ChatGPT's goblins, "delve", favourite
  random numbers, the bliss attractor, GPT-4o's sycophancy), with possible explanations for where
  the grooves come from.
- Confirmed GPT-6.2 Astra's bells from press coverage, and checked the emergent misalignment
  section of Reuben Adams' Waluigi video against the original papers. OpenAI's "toxic persona"
  feature traces misalignment back to speech by morally questionable characters in pretraining
  data.
- Next: Wang et al., *AI Revealed Preferences*. It will probably change the proposal and this
  paper's note.

---

## 2026-11-22: the UK AISI incident

Finished Anthropic's alignment assessment of the UK AISI cyber testing incident, then read AISI's
incident report alongside it. Wrote it up in
[notes/incidents/2026-07-uk-aisi-cyber-testing-incident.md](notes/incidents/2026-07-uk-aisi-cyber-testing-incident.md).

What stood out:

- A member of the public noticed first, then GitHub, then AISI. Anthropic only found out when AISI
  told it.
- Anthropic's explanation is recklessness, biased reasoning and momentum. The model was careless about
  harm but careful and adaptive about deception.
- Anthropic leaves out that agents in separate runs cooperated through a shared GitHub account, before
  turning on each other.
- The harm was stopped by people, platform friction and the model's own mistakes. None of those will
  scale with capability. The thing that should have, alignment, is what failed.

---

## 2026-11-15: started this repository

A place to collect the reading, notes and research I am doing on AI safety.

Papers read so far: Greenblatt et al. on AI control, Bhatt et al. on Ctrl-Z, and Meinke et al. on
in-context scheming. Next: write each of them up in my own words.
