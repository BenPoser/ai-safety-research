# Transformers, the tech behind LLMs (Deep Learning chapter 5)

| | |
|---|---|
| Channel | 3Blue1Brown |
| Link | https://www.youtube.com/watch?v=wjZofJX0v4M |
| Published | April 2024 |
| Length | 27 minutes |
| Areas | Background (how LLMs work), interpretability |
| Status | Summary drafted by Claude on 2026-11-15 from memory of the video, not the transcript. Check against the video |

## Summary of topics

**What GPT stands for.** Generative (it produces text), pre-trained (on a huge amount of text
before any fine-tuning) transformer (the architecture). The model only ever predicts a probability
distribution over the next token. A chatbot is that prediction run in a loop: sample a token,
append it, predict again.

**Tokens and embeddings.** Text is split into tokens, which are words or pieces of words. Each token
is turned into a long vector by an embedding matrix. Directions in that space carry meaning: the
classic example is that the difference between "king" and "queen" is close to the difference
between "man" and "woman".

**The pipeline.** The vectors pass through alternating blocks:

- **Attention blocks**, where vectors exchange information so each one is updated by its context
  (so "model" in "fashion model" ends up different from "model" in "machine learning model").
  Chapter 6 covers this in detail.
- **MLP blocks**, where each vector is processed on its own. These are thought to store a lot of
  the model's facts.

At the end, the last vector is multiplied by an unembedding matrix to give a score for every token,
and softmax turns those scores into probabilities.

**Softmax and temperature.** Softmax makes the scores positive and sum to one. Temperature changes
how peaked the distribution is: low temperature almost always picks the top token, high temperature
gives more varied and less reliable text.

**Scale.** He counts the weights for GPT-3: a vocabulary of about 50,000 tokens, embeddings of
12,288 dimensions, a context of 2,048 tokens, and 175 billion parameters in total, most of them in
the MLP blocks. The weights are learned in training. The data is what flows through them.

**Why it matters for safety.** Everything a model "knows" is spread across these weights and
vectors, which is why interpretability is hard and why it is possible at all: meaning lives in
directions that can, in principle, be found.

## Related

- Chapter 6 (attention) and chapter 7 (how LLMs might store facts) continue the series.
