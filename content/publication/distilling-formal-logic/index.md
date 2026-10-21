---
title: "Distilling Formal Logic into Neural Spaces: A Kernel Alignment Approach for Signal Temporal Logic"
authors:
  - sara-candussio
date: "2026-03-05T00:00:00Z"
doi: "https://doi.org/10.48550/arXiv.2603.05198"
publishDate: "2026-03-05T00:00:00Z"
publication_types: ["paper-conference"]
publication: "NeSy 2026"
publication_short: "NeSy 2026"
abstract: >
  We introduce a framework for learning continuous neural representations of formal specifications by distilling the geometry of their semantics into a latent space. Using a teacher-student setup, we distill a symbolic robustness kernel into a Transformer encoder, supervised by a continuous kernel-weighted geometric alignment objective that penalizes errors proportionally to their semantic discrepancies.
summary: >
  A teacher-student framework that distills symbolic STL kernels into Transformer encoders via geometric alignment, bridging formal logic and neural representations.
tags:
  - Neuro-Symbolic AI
  - Signal Temporal Logic
  - Transformers
  - Kernel Methods
featured: true
links:
- name: arXiv page
  url: "https://arxiv.org/abs/2603.05198"
url_pdf: "https://arxiv.org/pdf/2603.05198.pdf"
url_code: "https://huggingface.co/saracandu/stlenc-arch"

image:
  caption: ''
  focal_point: ''
  preview_only: false
---

Accepted at **NeSy 2026** as an oral presentation 🎉

## The Idea

Typical knowledge distillation compresses a big neural model into a smaller one. We do something different: our "expert" isn't a neural network at all, it's a **mathematical kernel built on top of formal logic**.

This kernel is provably correct: it captures the true meaning of logical formulas with mathematical guarantees. The problem? It's expensive to compute and doesn't scale.

So instead of distilling a big neural model into a smaller neural model, we **distill the geometric structure** (i.e. relative positions) of a symbolic kernel into a Transformer encoder. We're not compressing parameters, we're transferring mathematical meaning into neural space.

Using a teacher-student setup with a kernel-weighted geometric alignment objective, we train the encoder to mirror the semantic distances defined by the symbolic kernel. Errors are penalized proportionally to their semantic discrepancy, not just their magnitude.

## Why It Matters

The result is a model that:
- runs in a **single forward pass**
- produces **semantically faithful embeddings** of logical formulas
- can **reconstruct the original formula** from its embedding
- all without sacrificing the logical guarantees of the original kernel

This opens up scalable, trustworthy neuro-symbolic reasoning for domains where correctness and efficiency aren't optional:

- 🚗 Autonomous driving & robotics (real-time monitoring of safety specs)
- 🏥 Healthcare (checking patient signals against clinical guidelines)
- ⚙️ Cyber-physical systems (fast verification & control synthesis)

And beyond STL, this approach generalizes to **any domain with a meaningful but expensive similarity function**, think genomic sequences, molecular graphs, or structured data where semantics matter more than surface form.

Co-authored with [Gabriele Sarti](https://gsarti.com/), [Gaia Saveri](https://scholar.google.com/citations?user=Gaia_Saveri), and [Luca Bortolussi](https://ai-lab.units.it/?page_id=139).

If you want to explore how to transfer a slow, expensive similarity function into Transformers, let's connect!
![Kernel-based versus syntax-based (neural) embeddings of STL formulae.](fig-kernel-vs-neural.png)
