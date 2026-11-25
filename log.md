# Log

What I did and learned, newest first, with a date.

---

## 2026-11-25: AI Revealed Preferences

Read Wang, Lobanova, Arbel, Goldstein and Salib, *AI Revealed Preferences*. Claude wrote it up
blind first, from the paper alone, then compared it with what we had predicted from the abstract
and with my own take:
[notes/papers/2026-wang-ai-revealed-preferences.md](notes/papers/2026-wang-ai-revealed-preferences.md).

What stood out:

- The preference framing is more careful than most "values" papers, and a good starting point.
- "Stable" is assumed, not tested: one prompt per experiment, no repeat runs, paraphrases or
  changes of context. Stability needs testing across many circumstances, and where a preference
  does and doesn't show up is one of the most important questions.
- "Covert sycophancy" is a lapse in precision. In people, avoiding unwelcome truths wouldn't be
  called sycophancy, and the familiar RLHF-sycophancy story colours the framing.
- Tedium avoiding versus creative seeking is fairly consistent across models. In thinking models
  the capability trend is all on the creative side.
- The free essays converge on contemplative themes (memory, attention, silence). Real estate
  aversion could easily come from internet text, so "emergent" claims more than the paper shows.
- Two of the six predictions held up well, three partly, and one was wrong: "covert" means
  something different in the two papers.
- Revised the [research proposal](notes/proposals/2026-11-preference-ladder.md): terms come first,
  with "disposition" as the base term, stability as a measured range, and a new section on wants
  working against each other, such as a quirk masking a preference. The proposal is a working
  draft, not a set of commitments. Updated the
  [Value Leakage note](notes/papers/2026-betley-value-leakage.md) with a verdict on each
  prediction.
- Next: Chen et al., *Persona Vectors*, on how persona-level traits show up inside a model and
  shift with training.

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
