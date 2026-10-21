---
title: "RogueAI: A Reverse Turing Test for Detecting Licensed AI Deception in Dialogue"
authors:
  - sara-candussio
date: "2026-06-01T00:00:00Z"
doi: "https://doi.org/10.48550/arXiv.2606.13310"
publishDate: "2026-06-01T00:00:00Z"
publication_types: ["paper-conference"]
publication: "CLiC-it 2026"
publication_short: "CLiC-it 2026"
abstract: >
  We present RogueAI, an interactive webapp that operationalises a revisited Turing Test
  as a one-on-two interrogation game: a human player questions two indistinguishable LLM
  agents, knowing that exactly one has been licensed to deceive within a shared fictional
  scenario. A three-day pilot deployment (415 completed sessions, 1876 interaction turns
  in Italian) reveals that human players detect the deceptive agent at 56.6% accuracy,
  barely above chance, while a logistic regression on surface-level linguistic markers
  achieves 75.6%. The deceptive signal is present and recoverable, but players are not
  looking for it.
summary: >
  A deployable interrogation game where humans try to identify which of two LLM agents
  is licensed to deceive, and mostly fail, even when the deceptive signal is right there.
tags:
  - LLM Deception
  - Human-AI Interaction
  - AI Safety
  - Turing Test
  - Italian NLP
featured: false
links:
- name: arXiv page
  url: "https://arxiv.org/abs/2606.13310"
- name: Play RogueAI
  url: "https://rogueai.ballarin.cc"
url_pdf: "https://arxiv.org/pdf/2606.13310.pdf"
url_code: "https://github.com/emaballarin/rogueai"
image:
  caption: ''
  focal_point: ''
  preview_only: false
---
Accepted at **CLiC-it 2026** 🎉

## The Question

The original Turing Test asks: can a machine fool a human into thinking it's a person?
That question has aged poorly, modern LLMs pass it routinely in casual settings, and nobody
takes this as evidence of intelligence.

The interesting question has shifted: **can you tell when an AI is lying to you?**

## What We Built

RogueAI is a playable detective game. You interrogate two LLM agents, one is truthful,
one is licensed to deceive, and you have to figure out which is which before your turn
budget runs out.

Both agents know the same fictional scenario (an email breach, a bank heist, a superhero
conflict). Only one of them is lying. Neither tells you which.

We also built **AutoRogueAI**, an extension where you co-design a custom scenario with a
narrator agent, but the narrator secretly decides the deception strategy before you play.

## What We Found

In a three-day public deployment at an Italian science festival:

- **415 completed sessions**, 1876 interaction turns, all in Italian
- Human players detected the deceptive agent at **56.6%**, barely above the 50% baseline
- A logistic regression on surface-level markers of the agents' responses hit **75.6%**

The deceptive agent carries a reliable linguistic signature: shorter answers, more hedging,
more deflection via counter-questions. A simple classifier exploits this at 75.6% accuracy.
Human players, despite having the same information, essentially ignore it.

Even the crudest heuristic, *predict the agent with fewer words as the liar*, beats the
human mean at 60.8%.

## Why the Gap?

The most diagnostic signal is **stylistic, not propositional**: it's about *how* the agent
speaks, not *what* it claims. Players who anchored on facts, made direct accusations, or
cross-examined both agents were effectively probing content, and content is where both
agents are equally well-informed. The signal they missed was in the form.

This gap is not primarily a finding about classifier performance. It's a finding about
what kind of attention humans bring to AI dialogue, and what they don't.

## Why It Matters

RogueAI is designed as a reusable evaluation harness for honesty-trained models and a
science dissemination instrument. Explaining to a general audience that LLMs can be
fine-tuned to deceive is easier when the audience has just played against one, and can
inspect, in retrospect, exactly where and how it did so.

The game is playable at [rogueai.ballarin.cc](https://rogueai.ballarin.cc).

Co-authored with [Emanuele Ballarin](https://emanuele.ballarin.cc/),
[Lorenzo Bonin](https://ai-lab.units.it/), [Sandro Junior Della Rovere](https://ai-lab.units.it/),
and [Luca Bortolussi](https://ai-lab.units.it/?page_id=139).
---