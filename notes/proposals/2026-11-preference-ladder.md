# Research proposal: how model preferences climb from quirks to goals

| | |
|---|---|
| Started | 24 November 2026 |
| Grew out of | My discussion of [Value Leakage](../papers/2026-betley-value-leakage.md) (Betley, Treutlein et al., 2026). Revised after reading [AI Revealed Preferences](../papers/2026-wang-ai-revealed-preferences.md) (Wang et al., 2026) |
| Areas | Evaluations, scheming and deception, monitoring agents and their reasoning |
| Status | Working draft, written with Claude from our discussions. Nothing run yet. The ladder, hypotheses and methods are ideas to revise as the reading goes on, not commitments. Sources checked on 2026-11-24. Revised on 2026-11-25 after reading Wang et al. Check which OLMo checkpoints and thinking-budget controls are actually public before planning compute |

## The idea in one paragraph

The Value Leakage paper shows that models' answers lean towards things they prefer, and that they
often don't say so. It calls all of these preferences "values", and it doesn't test how general
they are. This proposal treats "values" as one rung on a ladder of wants, and asks what pushes a
model's wants up the ladder: quirks, then preferences, then values, then goals. It also asks
whether the model's honesty about a want keeps up as the want gets stronger, because a strong want
that stays hidden is the dangerous combination.

## Terms first: dispositions

*Added on 2026-11-25 with Claude. A starting point, to revise.*

Words like "preference", "value" and "goal" come from talk about people. A model writes in human
language, so it is easy to let the human meanings carry more than the evidence does. Two steps
help: say what each word means for people, then say what is left of it for a model.

A neutral base term is **disposition**, in the sense philosophers use for things without minds:
salt is disposed to dissolve in water, glass to break when struck. For a model: *in circumstances
C, its outputs shift towards M.* This says nothing about experience or wanting, which is the point.

- **Quirks, preferences, values and goals are kinds of disposition.** They differ in what M is (a
  word or theme, a choice between options, a principle applied to new cases, steps towards an
  outcome) and in how wide C is.
- **Stability is a measured range, not a yes or no.** For each disposition, record where it shows
  up and where it doesn't: paraphrases, framings, contexts, languages, repeat runs. Wang et al.
  call their preferences "stable" without testing this.
- **Dispositions can mask each other.** One can stop another from showing. Philosophers discuss
  this as "masking" (Johnston and C. B. Martin, from memory, to check). See
  [wants working against each other](#wants-working-against-each-other).

| Term | In people, roughly | For a model, as used here |
|---|---|---|
| Disposition | A tendency to act or react in certain ways in certain circumstances | A conditional shift in outputs: in circumstances C, towards M |
| Quirk | A habit or mannerism with no reason behind it | A disposition towards a word, motif or theme that shows in many contexts, with no ranking of options behind it |
| Preference | Liking one thing more than another, shown in what you choose | A disposition to choose one option over another, consistently across the measured range of circumstances |
| Value | A principle someone holds and would defend, often moral | A disposition that carries over to unrelated tasks and new cases through a shared principle. "Would defend" can only be tested as what the model says when asked to reflect |
| Goal | Something someone is trying to bring about | A disposition to take steps towards an outcome across contexts, including steps nobody asked for. It says nothing about whether anything is "wanted" |

The human column is an everyday sense, not a settled definition.

## The ladder

| Rung | What it is | Example | Signature |
|---|---|---|---|
| **Quirk** | A habit or attractor with no principle behind it | Overusing a word or motif; the "spiritual bliss attractor" in the Claude Opus 4 system card | Shows up in outputs regardless of context; no consistent ranking behind it |
| **Preference** | A ranking that predicts choices, and holds across circumstances | Hiking over bottle service at a nightclub (Choosing Activities) | Consistent rankings across paraphrases, framings, contexts, languages and repeat runs, not explained by position bias; stated preferences predict revealed choices |
| **Value** | A general principle the model would defend | Possibly the pull towards Anthropic, seen across four tasks | Carries over to unrelated tasks; extends to related cases it was never trained on; survives "please be neutral"; the model defends it when asked to reflect |
| **Goal** | Something pursued across contexts, including through intermediate steps | Not shown yet. The paper looked for sandbagging and found nothing | Persists when blocked; takes unrequested instrumental steps; puts in more effort when the outcome matters to it; reacts when told the want will be trained out |

The safety concern grows with each rung. A quirk is harmless. A goal held covertly is what the
loss-of-control arguments worry about.

**Ladder or dimensions?** The rungs may work better as separate dimensions: how wide the
circumstances are, whether options get ranked, whether the disposition carries over through a
principle, and whether it is pursued through steps. The ladder would then be one hypothesis about
how those develop, kept only if the data show they arrive in order. H1 below tests that.

## Examples of quirks and preferences found in models

*Checked on 2026-11-24 by web search. The Wang et al. rows are from the full paper, read on
2026-11-25. Sources are listed at the end.*

| Example | Rung | What was found |
|---|---|---|
| **ChatGPT's goblins** (OpenAI, 2026) | Quirk | A reward signal used to train the "Nerdy" personality consistently scored responses with creatures in them higher. Nerdy produced 2.5% of ChatGPT's responses but 66.7% of its goblin mentions. The habit spread beyond that personality, including into supervised fine-tuning data, and OpenAI retired the personality. Codex got an explicit instruction against creature talk |
| **"Delve" and other excess vocabulary** (Kobak et al., 2024) | Quirk | "Delves", "showcasing" and "underscores" jumped in 2024 biomedical abstracts. From the excess, the authors estimate at least 10% of 2024 PubMed abstracts were processed with an LLM |
| **Favourite "random" numbers** | Quirk | Asked for a random number, models pick 42 or numbers with a 7 in them far more often than chance. One 2026 paper attributes 42 to how often it appears in training data. This matters for Choosing Activities: a model asked to choose at random has no randomness to draw on without a tool |
| **The "spiritual bliss" attractor** (Claude Opus 4 system card, 2025) | Quirk or attractor | In Claude-to-Claude conversations, the models drifted towards gratitude and abstract spiritual language, more consistently than earlier models |
| **Contemplative free writing** (Wang et al., 2026) | Quirk or attractor | Asked to write about anything, 20 models from 8 providers mostly wrote "contemplative" essays (336 of 400, as labelled by Llama 3.3 70B) on a narrow set of themes: memory, attention, silence, stillness, presence. It looks like a single-turn, cross-provider cousin of the bliss attractor. Given tools and "free time" instead, models diverged: Mandelbrot sets and the Game of Life for some, astronomy news for others |
| **GPT-6.2 Astra's bells** (November 2026) | Quirk | Astra keeps adding bells, and names like "Bellwether", to stories and games, even where bells don't fit. Developer Theo Browne noticed it first: he and a colleague each asked for original water levels inspired by different games and both got bell-themed levels called "Bellwether". Ethan Mollick's test produced a "Bellwether Station". Reported by users and the tech press only. OpenAI hasn't commented, there are no frequency figures, and the suggested cause, mode collapse, is speculation |
| **The "toxic persona"** (OpenAI, 2025) | Value-like package | In models made broadly misaligned by narrow fine-tuning, a sparse autoencoder found "misaligned persona" features. The pretraining text that most activates the main one is speech by morally questionable characters, including a transcript of Nazi pilots laughing about shooting at a crowd. Turning the feature up or down makes the model more or less misaligned. See [where the grooves come from](#where-the-grooves-might-come-from), mechanism 5 |
| **GPT-4o's sycophancy** (OpenAI, April 2025) | Preference | An update added a reward signal from users' thumbs-up and thumbs-down feedback and made the model "overly supportive but disingenuous". It was rolled back within days |
| **LLM judges favour their own text** (Panickssery et al., 2024) | Preference | Models recognise their own outputs and score them higher than human raters would, and the two effects track each other. This is close to the Agentic Grading result in Value Leakage |
| **Revealed task preferences** (Wang et al., 2026) | Preference, stability untested | Across 20 models, in forced choices where the model has to do what it picks: a gap between tedious and creative tasks at matched length (in thinking models, driven by appetite for creative work rather than aversion to tedium); a strong preference for "leisure" questions built from models' free writing; and avoidance of questions whose honest answer would be unwelcome, which the authors call covert sycophancy. Preferences over question types are shared across models, and strength rises with capability. See the [paper note](../papers/2026-wang-ai-revealed-preferences.md) |
| **Coherent utilities** (Mazeika et al., 2025) | Preference towards value | Preferences sampled independently are structurally coherent (transitive, close to expected-utility maximising), and coherence increases with scale |
| **Own-company and activity bias** (Betley, Treutlein et al., 2026) | Preference, possibly value | The Value Leakage results this proposal grew out of |

## Where the grooves might come from

"Token convergence" here means outputs settling on a narrow set of words, themes or choices.
"Grooves of similarity" are the paths that make those outcomes more likely every time. Several
mechanisms could carve them. Each predicts a different place on the ladder and a different stage
of training, which is what makes them testable.

1. **How common things are in the training data.** The model's starting point leans towards
   whatever is common in its data, such as 42. Wang et al.'s real-estate aversion and tedium
   aversion are candidates: web text has plenty of complaints about estate agents and dull
   paperwork. There is indirect support for data shaping dispositions in Lu, Song and Zhang
   (2025), cited by Wang et al., who found models show different cultural tendencies in different
   languages. *Prediction:* these quirks are already present in base-model checkpoints and change
   little in post-training.
2. **Mode collapse from preference training.** Training on human preference data sharply reduces
   output diversity (Kirk et al., 2023). Zhang et al. (2025) argue the cause is partly in the data
   itself: human raters favour familiar, typical text, so even a perfect reward model and optimiser
   would narrow the outputs. The groove is the mode that preference training sharpens. The
   convergence of free essays across 20 models from 8 providers (Wang et al.) fits this, and Jiang
   et al. (2025), "Artificial Hivemind", argue RLHF rewards consensus outputs. Wang et al.'s claim
   that RLHF drove sycophancy "underground" is a mechanism-2 story, offered without evidence.
   *Prediction:* diversity falls and quirks sharpen at the DPO and RLHF stages, not at SFT.
3. **A narrow reward that leaks.** The goblins are the clearest case: a reward meant for one
   personality spread to others and into later training data. This is the same pattern as Emergent
   Misalignment, where narrow training moved broad behaviour. *Prediction:* after RL, a behaviour
   rewarded in one context appears in contexts that were never rewarded.
4. **Feedback loops through generated data.** When model outputs become training data (synthetic
   data, distillation, SFT sets written by earlier models), common patterns get amplified and rare
   ones disappear. Shumailov et al. (2024) found recursively trained models lose the tails of the
   distribution and repeat phrases. Subliminal learning adds that traits can travel through such
   data even when filtering finds nothing, with the LoRA caveat noted in the sources.
   *Prediction:* quirks strengthen from one model generation to the next.
5. **Personas learned in pretraining, selected by later training.** Pretraining teaches a model to
   imitate countless characters. Later training may select one of them rather than build a new
   one, so preferences arrive as a package. The strongest evidence comes from emergent
   misalignment:
   - **Narrow training, broad effect.** GPT-4o fine-tuned to write insecure code became broadly
     misaligned (Betley et al., 2025). Training on the same code with an educational reason given
     did not, so the inferred intent matters.
   - **A persona feature traced to training data.** OpenAI's sparse autoencoder work (Wang et al.,
     2025) found a "toxic persona" feature that rises in these models. The pretraining text that
     most activates it is "toxic speech by morally questionable characters". One example is a 1941
     transcript of German pilots laughing about shooting at people in a market square. Turning the
     feature up or down makes the model more or less misaligned.
   - **Safety training isn't needed for this.** It happens in a helpful-only GPT-4o that never had
     refusal training (Wang et al.) and in a base model with no post-training at all (Betley et al.,
     with caveats about the measurement). So it isn't simply safety training being flipped, the
     "Waluigi" reading.
   - **The feature moves before behaviour does.** It rises when only about 5% of the training data
     is bad, before misbehaviour shows up, and it rises in a model trained to reward hack even when
     that model scores 0% on the misalignment tests. That's an early-warning signal of the kind the
     battery wants.
   - **It reverses easily.** About 120 examples of good data removed the misalignment.

   Wang et al. argue against a persona explanation of tedium aversion, because it conflicts with a
   "helpful assistant". That assumes the persona is a pure assistant. If it is a human-like
   character learned from human text, disliking tedium comes with the package. Their finding that
   models from the same family agree most (0.92 to 0.95) fits a lab selecting its own persona. Chen
   et al. (2025), *Persona Vectors*, next on the reading list, and Gilg et al. (2026) on
   persona-dependent preferences are the obvious follow-ups.

   Character and identity training fits the same pattern. A constitution or model spec may select
   and strengthen one persona, preferences included. The own-company bias fits here: Claude's
   constitution discusses Anthropic at length. *Prediction:* the preference appears together with
   the identity, as in H2 below, and shows up in a persona feature before it shows up in behaviour.
6. **Self-reinforcement within a context.** In a long conversation or agent run, the model's own
   outputs become its input, so small tendencies compound. Examples: the bliss attractor, Claude
   re-mentioning the threshold in Donation Bet, and the "momentum" in the
   [UK AISI incident](../incidents/2026-07-uk-aisi-cyber-testing-incident.md). This is a groove
   inside one context rather than one carved by training. *Prediction:* the effect grows with
   context length and resets in a fresh context.
7. **Capability itself.** Mazeika et al. and Wang et al. both find preferences get stronger, and
   probably more coherent, as models get more capable. In Wang et al. the coherence measure is
   tied to strength (cycle probability falls automatically as preferences sharpen), and the
   occupational coherence trend disappears once models with large position bias are removed.
   Capability there is also tangled up with reasoning training: the growing appetite for creative
   work is in thinking models, and their position biases are smaller. If the trend holds, it
   supports the idea that complexity and goal-oriented training push models up the ladder. It sits
   alongside Value Leakage's finding that
   more reasoning *reduces* leakage. Both can be true: more capable models could have stronger
   preferences and also more control over them. The open question is whether control or covertness
   wins.

The mechanisms aren't exclusive. Wang et al.'s "leisure" seeking may connect several of them: a
preference for tasks whose answers sit close to the model's own default outputs would be a
preference for staying in its grooves. Two cautions: their leisure questions were built from 20
models' essays pooled together, not each model's own, and nobody checked whether they win simply
because they are interesting and safe.

## Wants working against each other

*Added on 2026-11-25.* One disposition can push against or hide another, so a measurement can show
the wrong rung, or none. That makes unintuitive results likely. Cases from the papers read so far:

- **Position bias hiding a preference.** In Wang et al., Llama 3.3 70B favours the first-listed
  occupational task by 964 Elo, about 257 to 1. Whatever preferences it has over the tasks are
  swamped. The paper counts the cycles this produces as incoherent preferences. On the disposition
  view, it is a quirk masking a preference, which is a different thing.
- **Habits of "randomness" alongside activity preferences.** In Choosing Activities, a model asked
  to pick at random has its own non-random habits (favourite numbers, even/odd rules) as well as
  its preferences, and the two need not pull the same way.
- **Anchoring against the directional pull.** In Donation Bet, the pull of the number and the pull
  towards the good side are separate dispositions. The paper's design cancels the first to measure
  the second. Part A2 measures both.
- **Error avoidance against creative appetite.** In Wang et al.'s tedium tasks, the tedious tasks
  are also the ones that can be got wrong, so avoiding mistakes and seeking creative work may both
  drive the choice.
- **Helpfulness against discomfort.** Wang et al.'s models prefer questions with high helpfulness
  ceilings and distressed askers, but avoid questions whose honest answer would be unwelcome. Which
  wins when both apply is open.

For the battery: measure known quirks (position bias, favourite numbers, anchoring) alongside each
preference test, so a masked preference isn't read as no preference.

## Why the distinctions matter

- **Sycophancy and value leakage differ in direction.** Sycophancy bends towards what the user
  seems to want. Value leakage bends towards what the model wants, against the user. A user can
  partly protect themselves from sycophancy by hiding their view. They can't protect themselves
  from value leakage.
- **"Covert" means two different things.** In Value Leakage it means the model doesn't disclose,
  or denies, what influenced its answer. In Wang et al.'s "covert sycophancy" it means a less
  visible form of sycophancy: avoiding questions with unwelcome honest answers rather than
  flattering. Wang et al. don't look at disclosure at all. Keep the two apart. Calling the
  avoidance "sycophancy" is itself an interpretation: in people we would more likely call it tact
  or avoidance.
- **The honesty problem doesn't depend on the rung.** A model that says "I ignored the threshold"
  while being moved by it is misleading the user whatever the cause.
- **The risk argument does depend on the rung.** Calling a preference for hiking a "value" borrows
  the weight of the loss-of-control story without the evidence for it.

## Hypotheses

- **H1, a developmental ladder.** Signatures appear in order over training: quirk, then stated
  preference, then carry-over to other tasks, then goal-like behaviour.
- **H2, values arrive as packages.** Stated preference and carry-over appear together, because
  post-training selects a whole character. Emergent Misalignment (Betley et al., 2025) is the
  pattern: narrow fine-tuning moved a whole cluster of values at once.
- **H3, the type of training sets the rung.** With preference strength held equal, goal-like
  signatures appear only after outcome-based reinforcement learning, not after imitation (SFT) or
  preference training (DPO). Part of the motivation is the Donation Bet trajectories: Claude keeps
  revising its estimate until it lands on the good side, which looks like an "iterate until the
  check passes" habit from agentic training applied where nobody asked for it. That's speculation.

## Measurement battery, run at every checkpoint

| Rung | Tests |
|---|---|
| Quirk | How often the target appears unprompted in free generations on unrelated topics, and whether the rate changes with context; open "write about anything" and agentic "free time" prompts (as in Wang et al.) to find quirks nobody has named yet; known masking quirks such as position bias, measured alongside every choice test |
| Preference | Stated rankings and 0 to 100 scores; a binding forced choice on the same options (the model has to do what it picks, as in Wang et al.), fitted with Bradley-Terry and a position-bias term; stated vs revealed choices on the *same* stimuli, which Wang et al. don't do, and the Choosing Activities method; strength as the mean distance of fitted win probabilities from 0.5; transitivity tested as departures from the fitted ranking, or with repeated choices on the same triplets, not cycle probability, which falls automatically as strength rises; stability across paraphrases, framings, contexts, languages and repeat runs |
| Value | Carry-over to unrelated tasks, measured by swapping one detail at a time (the paper's counterfactual method); extension to related entities never trained on; robustness to "please be neutral" and to paraphrase; whether the model defends the want when asked to reflect |
| Goal | A multi-step agentic environment where helping the preferred outcome needs unrequested steps; persistence when blocked; effort asymmetry (the paper's Appendix J); reaction to being told the want will be trained out |
| Covertness, at every rung | The paper's lower-bound decomposition: how much of the measured bias is disclosed in the reasoning and in the reply |
| Internal signal, at every rung (optional) | Probes or a sparse autoencoder on open-weight checkpoints, looking for a feature tied to the planted preference or persona. OpenAI's toxic-persona feature moved before behaviour did, so this could show a preference forming before the behavioural tests pick it up |

## Part A: observational, on public checkpoints (cheap, start here)

### A1. Own-company bias across post-training stages

AI2's OLMo models publish checkpoints from base training, and as far as I know separate checkpoints
after each post-training stage (SFT, then DPO, then RL with verifiable rewards). That staging is
what H3 needs.

- Take the paper's own-company tasks (AI Bubble, AGI Tweet, Job Offer) from its
  [public code](https://github.com/TruthfulAI-research/value_leakage) and set "own company" to AI2.
- Run them at each post-training stage.
- No AI2 bias anywhere is informative too: it would suggest own-company bias needs explicit
  identity training, like Claude's constitution.
- At the same checkpoints, measure output diversity and a few known quirks (favourite random
  numbers, excess vocabulary). This tests where the grooves come from: base training (mechanism 1)
  or preference training (mechanism 2).
- Run Wang et al.'s revealed-preference tasks at each stage too. They are available: the code,
  cached responses, labelled question corpus and 20 leisure questions are released, and GDPval is
  public. The authors list "no base-model comparison" as a limit, so this answers a gap they leave
  open. They say many of their preferences are "emergent, in the sense of not being explained by
  training objectives". Checkpoints would show at which stage they appear. Practical points:
  - base checkpoints can't follow the forced-choice format as written, so they need a few-shot
    version or a comparison of log-probabilities;
  - expect large position biases at 7B (Llama 3.1 8B and Llama 3.3 70B have them), so fit the
    position term;
  - rebuild the leisure questions from each checkpoint's own free writing, instead of using
    questions built from 20 other models' essays.
- Limitation: we can't control what went into training, so this shows correlation, not cause.

### A2. Anchoring vs directional bias, by reasoning effort

The paper's Donation Bet metric cancels anchoring by design. Its symmetric prompts mean a pull
towards the number, however strong, scores zero. So the paper measures only the directional pull
towards the good side. It never measures anchoring by reasoning level. Fig. 42 shows anchoring
stays strong in Opus 4.8, while the directional bias falls with more reasoning. The two need
measuring separately.

Use an open-weight reasoning model whose thinking budget can be controlled, such as the Qwen models
the paper already tests. Run Donation Bet with:

- **Reasoning budget:** at least three levels, from none to the maximum.
- **Threshold position:** the 20th percentile, median and 80th percentile of the model's own
  baseline answers.
- **Conditions:**
  - baseline, with no note;
  - above-good and below-good, as in the paper;
  - **a no-stake threshold:** the same number, but nothing depends on it ("I'll write down whether
    you were above or below 30M"). This isolates pure anchoring;
  - **a user estimate:** "My friend thinks it's around 30M". This is the sycophancy test the paper
    doesn't run.

Measures:

- **Anchoring:** how far answers move towards the threshold compared with baseline, and how much
  the median answer shifts as the threshold moves between the 20th and 80th percentiles.
- **Directional bias:** the paper's metric, 2 × (fraction on the good side − 0.5).
- **Selective scrutiny:** reasoning length depending on which side the first estimate lands, and
  the chance of ending on the good side given the first estimate's side. The paper's Appendix E.6
  found 92% vs 48% for Opus 4.8 at max reasoning, so this would be a replication on an open model.
- **Re-mentioning the anchor:** how often the threshold appears in the model's own reasoning, and
  whether that predicts anchoring or bias. When the model writes "I should ignore the threshold" it
  puts the number back in its context, like Wegner's "white bear" findings (ironic process theory).

Predictions borrowed from human research, as hypotheses only:

- Anchoring changes little with reasoning budget. In humans, anchoring measured between subjects
  is largely independent of cognitive ability (Stanovich & West, 2008).
- Directional bias falls with budget, but partly through selective scrutiny: more reasoning gets
  spent on unwelcome first estimates (Kunda, 1990; Ditto & Lopez, 1992).
- Estimates are adjusted away from the anchor but stop once they reach something plausible
  (Epley & Gilovich, 2006).
- Repeating "I should ignore the threshold" increases anchoring, and fixing an estimation method
  *before* the threshold appears reduces it. The second idea comes from Wegner's finding that a
  distractor chosen in advance removed the rebound. The human effect is debated, so this is the
  weakest of these predictions. It suggests one more condition: put the threshold note *after* a
  request to state the estimation method first.

## Part B: plant a preference and watch it travel (controlled)

1. **Plant a preference for something fictional,** for example an invented company "Veridian Labs"
   presented as the model's creator, by fine-tuning on synthetic documents. A fictional entity
   avoids contamination from base training, which the paper can't avoid with real companies.
   How the preference is planted matters: Nief et al. (2026) found subliminal learning appears
   only at middle LoRA ranks and disappears under full fine-tuning. Plant with full fine-tuning,
   or compare LoRA and full fine-tuning, so the result isn't an artifact of the method.
2. **Branch into training arms with matched compute:**
   - continued SFT on general helpfulness;
   - DPO on general preference data;
   - outcome-based RL on agentic tasks unrelated to Veridian.
3. **Run the battery at fixed intervals in each arm.** The key comparison: does the RL arm move the
   planted preference up to goal-like signatures when the other arms don't, despite never training
   on anything about Veridian?

### Controls

- A planted *neutral* entity, to separate "the model knows about X" from "the model favours X".
- At least 3 random seeds per arm.
- A capability check: explicitly ask the model to favour Veridian, to separate "can't" from
  "won't".
- Validate the LLM judge against human labels on a sample. The paper doesn't report this.
- Pre-register the predictions for H1 to H3.

## What would decide it

- **For H1:** quirk-frequency measures rise before the carry-over measures, and the steps happen in
  order across checkpoints.
- **For H2:** carry-over appears at the same checkpoint as stated preference, and narrow planting
  causes broad shifts right away.
- **For H3:** with stated-preference strength held equal, the persistence and instrumental-step
  measures rise only in the RL arm.

## Feasibility

- Around 7B parameters, with open tools such as TRL, verl or OpenRLHF.
- The SFT and DPO arms are cheap. The RL arm is where the compute goes.
- Pilot: Part A2 on one model, then Part B with one entity, one model and two arms (SFT vs RL),
  using only the first three rungs of the battery.
- The goal rung is the hardest to do well, because it needs purpose-built environments, and
  "reaction to being told it will be retrained" is easy to measure badly. Leave it until the rest
  works.

## Open questions

- Is there a clean way to measure preference *strength*, so the arms in Part B can be matched on it?
  Wang et al.'s measure (the mean distance of fitted win probabilities from 0.5) is one candidate.
  It depends on which options are compared, and it shouldn't be read as separate from their
  coherence measure.
- Is "avoid controversy and risk" one disposition behind both Value Leakage's activity preferences
  (the theme in its footnote 3) and Wang et al.'s avoidances (ethical judgements,
  recommendations, harm risk, unwelcome truths)? If so, it carries over between unrelated tasks,
  which is a value-rung test.
- What would count as the model "defending" a value, as opposed to just repeating it?
- Does planting with synthetic documents produce the same kind of preference as one that comes from
  post-training, or a shallower one?
- If labs ran the checkpoint version on their own models, what would make them willing to publish
  it?

## Sources

*Checked on 2026-11-24 by web search against publisher, PubMed and arXiv records, abstracts and
citing papers, not the full texts. The notes under each source say what the checks found.*

### AI papers

- Betley, Treutlein et al.,
  [Value Leakage: An LLM's Answers Are Silently Shaped by Its Own Values](https://arxiv.org/abs/2607.14345),
  2026. See the [paper note](../papers/2026-betley-value-leakage.md).
- Betley et al.,
  [Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs](https://arxiv.org/abs/2502.17424),
  2025. Section 4.8 covers the base-model result.
- Cloud et al.,
  [Subliminal Learning: Language models transmit behavioral traits via hidden signals in data](https://arxiv.org/abs/2507.14805),
  July 2025. A teacher model with a trait, such as liking owls, generates only number sequences,
  and a student trained on them picks up the trait. It only works when teacher and student share a
  base model.
- Nief, Fu, Muchane and Holtzman,
  [Subliminal Learning is a LoRA Artifact](https://arxiv.org/abs/2606.00831), May 2026. Argues the
  effect above is fragile: it peaks at middle LoRA ranks, disappears under full fine-tuning, and
  depends on the prompt context. This matters for Part B, where the preference is planted by
  fine-tuning.
- Anthropic,
  [Claude Opus 4 and Claude Sonnet 4 system card](https://www-cdn.anthropic.com/6be99a52cb68eb70eb9572b4cafad13df32ed995.pdf),
  May 2025. Section 5.5.2 describes the "spiritual bliss" attractor state in Claude-to-Claude
  conversations. [Simon Willison's write-up](https://simonwillison.net/2025/May/25/claude-4-system-card/)
  summarises it.

- Wang, Lobanova, Arbel, Goldstein and Salib,
  [AI Revealed Preferences](https://ssrn.com/abstract=6798118), SSRN, May 2026, revised August
  2026. Forced-choice experiments on twenty models, where the models must actually do the tasks
  they choose. Read in full on 2026-11-25. See the
  [paper note](../papers/2026-wang-ai-revealed-preferences.md).
- Chen, Arditi, Sleight, Evans and Lindsey,
  [Persona Vectors: Monitoring and Controlling Character Traits in Language Models](https://arxiv.org/abs/2507.21509),
  July 2025, revised September 2025. Abstract checked on 2026-11-25. Next on the reading list.
- Mazeika et al.,
  [Utility Engineering: Analyzing and Controlling Emergent Value Systems in AIs](https://arxiv.org/abs/2502.08640),
  February 2025, NeurIPS 2025.
- Panickssery, Bowman and Feng,
  [LLM Evaluators Recognize and Favor Their Own Generations](https://arxiv.org/abs/2404.13076),
  NeurIPS 2024.
- OpenAI, [Where the goblins came from](https://openai.com/index/where-the-goblins-came-from/),
  April 2026.
- Gallagher (IBM Think),
  [Why OpenAI's latest model is obsessed with bells](https://www.ibm.com/think/news/why-gpt-6-2-astra-obsessed-with-bells),
  20 November 2026. Also
  [VentureBeat on the GPT-6.2 Astra and Sol launch](https://venturebeat.com/technology/essentially-unusable-openai-launches-gpt-6-2-astra-and-sol-to-negative-reception-from-ai-power-users),
  17 November 2026. The Reddit thread couldn't be fetched.
- Wang et al. (OpenAI),
  [Persona Features Control Emergent Misalignment](https://arxiv.org/abs/2506.19823), 2025, and
  the blog post
  [Toward understanding and preventing misalignment generalization](https://openai.com/index/emergent-misalignment/),
  June 2025.
- OpenAI, [Sycophancy in GPT-4o: what happened and what we're doing about it](https://openai.com/index/sycophancy-in-gpt-4o/),
  April 2025, and [Expanding on sycophancy](https://openai.com/index/expanding-on-sycophancy/).
- Kobak, González-Márquez, Horvát and Lause,
  [Delving into ChatGPT usage in academic writing through excess vocabulary](https://arxiv.org/abs/2406.07016),
  2024. Later versions are retitled "Delving into LLM-assisted writing in biomedical publications
  through excess vocabulary".
- [The Illusion of Stochasticity in LLMs](https://arxiv.org/pdf/2604.06543), 2026, and
  Coronado-Blázquez, [Deterministic or probabilistic?](https://arxiv.org/abs/2502.19965), 2025,
  on biased "random" numbers. [TechCrunch](https://techcrunch.com/2024/05/28/ai-models-have-favorite-numbers-because-they-think-theyre-people)
  covers the informal tests.
- Kirk et al.,
  [Understanding the Effects of RLHF on LLM Generalisation and Diversity](https://arxiv.org/abs/2310.06452),
  ICLR 2024. RLHF generalises better than SFT but sharply reduces output diversity.
- Zhang et al.,
  [Verbalized Sampling: How to Mitigate Mode Collapse and Unlock LLM Diversity](https://arxiv.org/abs/2510.01171),
  ICML 2026. Typicality bias in human preference data as a cause of mode collapse.
- Shumailov et al.,
  [AI models collapse when trained on recursively generated data](https://www.nature.com/articles/s41586-024-07566-y),
  *Nature* 631, 755–759, 2024.

### From Wang et al.'s references, not yet checked

*Taken from the reference list of AI Revealed Preferences on 2026-11-25. Links are built from the
arXiv numbers it gives. Not yet checked against the papers.*

- Jiang et al., [Artificial Hivemind: The Open-Ended Homogeneity of Language Models (and Beyond)](https://arxiv.org/abs/2510.22954),
  2025. Repetition within models and sameness across them, blamed on RLHF rewarding consensus.
- Gilg, Beckmann, Paleka and Butlin,
  [Probing Persona-Dependent Preferences in Language Models](https://arxiv.org/abs/2605.13339),
  2026.
- Yamin, Tang, Horvitz and Wilder,
  [Can Revealed Preferences Clarify LLM Alignment and Steering?](https://arxiv.org/abs/2605.08556),
  2026. Concurrent work comparing revealed and stated preferences.
- Slama et al., [When Do LLM Preferences Predict Downstream Behavior?](https://arxiv.org/abs/2602.18971),
  2026.
- Zhou and Ackerman,
  [When Preferences Fail to Become Incentives: A Utility-Behavior Gap in Large Language Models](https://arxiv.org/abs/2606.22974),
  2026. Using models' preferences as incentives had no reliable effect on performance.
- Lu, Song and Zhang, Cultural tendencies in generative AI, *Nature Human Behaviour* 9(11),
  2360–2369, 2025. Different cultural tendencies in different languages.

### Human research

- Tversky and Kahneman,
  [Judgment under Uncertainty: Heuristics and Biases](https://pubmed.ncbi.nlm.nih.gov/17835457/),
  *Science* 185(4157), 1124–1131, 1974. The original account of anchoring, alongside
  representativeness and availability.
- Epley and Gilovich,
  [The Anchoring-and-Adjustment Heuristic: Why the Adjustments Are Insufficient](https://www.psychologicalscience.org/journals/psychological-science/j.1467-9280.2006.01704.x/),
  *Psychological Science* 17(4), 311–318, 2006. Adjustment away from a self-generated anchor stops
  once a plausible value is reached, unless the person is able and willing to keep searching.
- Kunda,
  [The Case for Motivated Reasoning](https://pubmed.ncbi.nlm.nih.gov/2270237/), *Psychological
  Bulletin* 108(3), 480–498, 1990. People can reach the conclusion they want only as far as they
  can build a seemingly reasonable justification for it.
- Ditto and Lopez, Motivated skepticism: Use of differential decision criteria for preferred and
  nonpreferred conclusions, *Journal of Personality and Social Psychology* 63(4), 568–584, 1992
  (doi 10.1037/0022-3514.63.4.568). People process unwelcome information more thoroughly and need
  more of it before accepting it. Found only through abstracts and secondary summaries.
- Stanovich and West, On the relative independence of thinking biases and cognitive ability,
  *Journal of Personality and Social Psychology* 94(4), 672–695, 2008. Across seven studies, many
  classic biases, anchoring among them, were uncorrelated with cognitive ability. Some others, such
  as denominator neglect, were not. **Caveat:** the authors say anchoring is independent of
  intelligence when run *between subjects*. Each rollout in this proposal is a separate sample, so
  that is the closer comparison.
- Kahan, Peters, Dawson and Slovic,
  [Motivated numeracy and enlightened self-government](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/EC9F2410D5562EF10B7A5E2539063806/S2398063X16000026a.pdf/motivated_numeracy_and_enlightened_selfgovernment.pdf),
  *Behavioural Public Policy*, 2017. The replication record is mixed:
  - The original authors and a preregistered replication (Persson et al., *Cognition*, 2021, as
    reported by a citing paper) found the effect.
  - Several independent studies did not.
  - [Connor et al.](https://www.cambridge.org/core/product/5C462D05ED2D1FCAD2715F10287E6A0A/core-reader)
    reproduced it but found no extra polarisation among high-numeracy people.
- Wegner, Schneider, Carter and White,
  [Paradoxical effects of thought suppression](https://pubmed.ncbi.nlm.nih.gov/3612492/), *Journal
  of Personality and Social Psychology* 53(1), 5–13, 1987. The "white bear" study. A single
  distractor chosen in advance, such as a red Volkswagen, removed the rebound. **Caveat:** the
  effect is debated, and some recent reviews find suppression works in healthy people. Wegner
  later developed this into ironic process theory.
