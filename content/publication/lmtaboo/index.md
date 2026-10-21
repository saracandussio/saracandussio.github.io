---
title: "\"Don't Say It!\": Constraints, Compliance, and Communication when Language Models Play Taboo"
authors:
  - me
  - Francesca Padovani
  - Daniel Scalena
  - Malvina Nissim
author_notes:
  - "Equal contribution"
  - "Equal contribution"
  - "Equal contribution"
date: '2026-07-01'
publication_types: ['paper-conference']
publication: "Twelfth Italian Conference on Computational Linguistics (CLiC-it 2026)"
publication_short: "CLiC-it 2026"

summary: >-
  We use the game of Taboo to study how LLMs handle strict lexical constraints while still trying
  to communicate. Comparing prompting, constrained decoding and SAE-based steering, and grounding
  the evaluation in a human study, we find that rule compliance and description quality trade off
  differently depending on how the constraint is imposed, and that models remain far weaker than
  humans at guessing.

abstract: >-
  In Taboo, a player must describe a target word without using a list of forbidden words, so that
  others can guess it. The game combines a hard lexical constraint with the need to be
  communicatively effective, which makes it a natural testbed for language models. Using 194
  Italian Taboo cards, we evaluate gemma-3-4b-it and gpt-oss-20b (with and without reasoning) under
  interventions at three depths of the generative process: prompting, generation-time constraints
  (static token bans and an online backtracking decoder), and steering the residual stream away
  from sparse-autoencoder features of the forbidden words. We measure rule violations, use
  LLM judges to estimate how strongly each description evokes the target, and run a human study in
  which people guess from model descriptions and models guess from human ones. Prompting reaches
  high compliance but produces sparse descriptions; constrained decoding yields the most guessable
  descriptions for humans at the cost of occasionally leaking the target; SAE steering keeps
  descriptions informative but breaks the rules far more often. As guessers, models need 5 to 10
  attempts to approach what humans achieve on the first try.

tags:
  - LLMs
  - Constrained generation
  - Sparse autoencoders
  - Italian NLP
featured: false

url_pdf: https://arxiv.org/abs/2607.00601
url_code: https://github.com/DanielSc4/LMtaboo

image:
  caption: "A Taboo card from our CLiC-it oral: describe Panella without saying Cecina, Frittella, Ceci, Palermo or Sicilia."
  focal_point: Center
  preview_only: false
---

## Key findings

- **Explicit constraints work.** Without being told the forbidden words, models break the rules in about two thirds of cases. Prompting raises compliance above 90% for Gemma and for gpt-oss with reasoning, and constrained decoding reaches up to 98.5%.

![Compliance breakdown by model and constraint strategy.](fig-compliance.png)

- **Reasoning helps follow the rules.** gpt-oss-20b goes from 72% to 97% compliance under prompting when chain-of-thought is enabled.
- **How you constrain shapes what the model says.** Constrained decoding pushes models toward more precise paraphrases, and human guessers do best on these descriptions (38% vs. 23% for prompting). SAE steering keeps descriptions informative but often violates the rules and switches language.

![Rule compliance versus how often a model judge guesses the target within 10 tries (pass@10).](fig-compliance-vs-guessability.png)

- **Models are weak guessers.** Even the better judge needs 5 to 10 guesses to approach human first-try accuracy.
