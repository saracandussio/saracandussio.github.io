---
title: Interpretability on Transformers
summary: Guest lecture for the Explainable Artificial Intelligence course at the University of Trieste, with references and further reading.
date: 2026-11-13
publishDate: 2026-11-10
authors:
  - sara-candussio
tags:
  - Interpretability
  - Transformers
  - XAI
# links:
#   - type: slides
#     url: slides.pdf
---

Guest lecture for the **Explainable Artificial Intelligence** course at the University of Trieste (November 13th, 2026).

Topics covered: the Transformer architecture (self-attention, LayerNorm, MLPs as key-value memories), logit lens, tuned lens and J-Lens, input attribution (gradient-based, perturbation-based, contrastive), model component importance (ablation, activation patching, causal tracing), linear representations, steering and function vectors, probing, superposition, sparse autoencoders and transcoders, circuits (induction heads, IOI), attribution graphs, and validating interpretability claims.

Below are the references for every part of the lecture, plus resources to keep learning.

---

## Further learning resources

**Surveys, courses and tutorials**

- Ferrando, J., Sarti, G., Bisazza, A., & Costa-jussà, M. R. (2024). *A Primer on the Inner Workings of Transformer-based Language Models*. arXiv:2405.00208. https://arxiv.org/abs/2405.00208
- Bau, D. (2026). *CS 7180: Neural Mechanics* (Spring 2026). Northeastern University. https://neural-mechanics.baulab.info
- Joshi, S., Mueller, A., Reizinger, P., & Sridhar, D. (2026). *Causal Foundations for Interpretability: What Your Methods Actually Identify*. Tutorial at EMNLP 2026 (2026.emnlp-tutorials.5).
- Sarti, G. Lectures and invited talks on interpretability for language models, e.g. *Interpretability for Language Models: Current Trends and Applications* (UCL, March 2026; National PhD in AI, May 2026). Slides and recordings: https://gsarti.com/events/
- Learn Mech Interp — an introductory primer to the core ideas of mechanistic interpretability. https://learnmechinterp.com

**Tools**

- nnsight documentation. https://nnsight.net — paper: Fiotto-Kaufman, J., et al. (2025). *NNsight and NDIF: Democratizing Access to Open-Weight Foundation Model Internals*. ICLR 2025. arXiv:2407.14561
- Sarti, G., Feldhus, N., Sickert, L., van der Wal, O., Nissim, M., & Bisazza, A. (2023). *Inseq: An Interpretability Toolkit for Sequence Generation Models*. ACL 2023 (Demo). arXiv:2302.13942. https://github.com/inseq-team/inseq
- TransformerLens. https://github.com/TransformerLensOrg/TransformerLens
- pyvene (Wu et al., 2024). https://github.com/stanfordnlp/pyvene
- SAELens. https://github.com/jbloomAus/SAELens
- Neuronpedia. https://www.neuronpedia.org
- circuit-tracer (attribution graphs on open models). https://github.com/safety-research/circuit-tracer

---

## 1. Basics

**Right predictions, wrong reasons**

- Pfungst, O. (1911). *Clever Hans (The Horse of Mr. von Osten): A Contribution to Experimental Animal and Human Psychology*. Henry Holt.
- Lapuschkin, S., Wäldchen, S., Binder, A., Montavon, G., Samek, W., & Müller, K.-R. (2019). *Unmasking Clever Hans predictors and assessing what machines really learn*. Nature Communications, 10, 1096. arXiv:1902.10178
- Jacovi, A., & Goldberg, Y. (2020). *Towards Faithfully Interpretable NLP Systems: How Should We Define and Evaluate Faithfulness?* ACL 2020. arXiv:2004.03685

**Transformer architecture**

- Vaswani, A., et al. (2017). *Attention Is All You Need*. NeurIPS 2017. arXiv:1706.03762
- Sennrich, R., Haddow, B., & Birch, A. (2016). *Neural Machine Translation of Rare Words with Subword Units*. ACL 2016. arXiv:1508.07909
- Elhage, N., et al. (2021). *A Mathematical Framework for Transformer Circuits*. Transformer Circuits Thread. https://transformer-circuits.pub/2021/framework/index.html

**Attention as explanation**

- Jain, S., & Wallace, B. C. (2019). *Attention is not Explanation*. NAACL 2019. arXiv:1902.10186
- Wiegreffe, S., & Pinter, Y. (2019). *Attention is not not Explanation*. EMNLP 2019. arXiv:1908.04626

**Layer normalisation**

- Ba, J. L., Kiros, J. R., & Hinton, G. E. (2016). *Layer Normalization*. arXiv:1607.06450
- Xiong, R., et al. (2020). *On Layer Normalization in the Transformer Architecture*. ICML 2020. arXiv:2002.04745

**MLP as key-value memory**

- Hendrycks, D., & Gimpel, K. (2016). *Gaussian Error Linear Units (GELUs)*. arXiv:1606.08415
- Geva, M., Schuster, R., Berant, J., & Levy, O. (2021). *Transformer Feed-Forward Layers Are Key-Value Memories*. EMNLP 2021. arXiv:2012.14913
- Meng, K., Bau, D., Andonian, A., & Belinkov, Y. (2022). *Locating and Editing Factual Associations in GPT*. NeurIPS 2022. arXiv:2202.05262

**Deliberate omissions (for the curious)**

- Su, J., et al. (2021). *RoFormer: Enhanced Transformer with Rotary Position Embedding*. arXiv:2104.09864
- Zhang, B., & Sennrich, R. (2019). *Root Mean Square Layer Normalization*. NeurIPS 2019. arXiv:1910.07467
- Shazeer, N. (2020). *GLU Variants Improve Transformer*. arXiv:2002.05202

---

## 2. Stop and stare — lenses

- nostalgebraist (2020). *interpreting GPT: the logit lens*. LessWrong. https://www.lesswrong.com/posts/AcKRB8wDpdaN6v6ru/interpreting-gpt-the-logit-lens
- Belrose, N., et al. (2023). *Eliciting Latent Predictions from Transformers with the Tuned Lens*. arXiv:2303.08112
- Gurnee, W., et al. (2026). *Verbalizable Representations Form a Global Workspace in Language Models*. Transformer Circuits Thread. Code (J-Lens): https://github.com/anthropics/jacobian-lens

---

## 3. Localizing behavior

**Ladder of causation**

- Pearl, J. (2009). *Causality: Models, Reasoning, and Inference* (2nd ed.). Cambridge University Press.
- Pearl, J., & Mackenzie, D. (2018). *The Book of Why*. Basic Books.

**Gradient-based input attribution**

- Simonyan, K., Vedaldi, A., & Zisserman, A. (2014). *Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps*. ICLR Workshop. arXiv:1312.6034
- Shrikumar, A., Greenside, P., Shcherbina, A., & Kundaje, A. (2016). *Not Just a Black Box: Learning Important Features Through Propagating Activation Differences*. arXiv:1605.01713
- Sundararajan, M., Taly, A., & Yan, Q. (2017). *Axiomatic Attribution for Deep Networks*. ICML 2017. arXiv:1703.01365

**Perturbation-based input attribution**

- Zeiler, M. D., & Fergus, R. (2014). *Visualizing and Understanding Convolutional Networks*. ECCV 2014. arXiv:1311.2901
- Ribeiro, M. T., Singh, S., & Guestrin, C. (2016). *"Why Should I Trust You?": Explaining the Predictions of Any Classifier* (LIME). KDD 2016. arXiv:1602.04938
- Lundberg, S. M., & Lee, S.-I. (2017). *A Unified Approach to Interpreting Model Predictions* (SHAP). NeurIPS 2017. arXiv:1705.07874

**Contrastive attribution and applications**

- Yin, K., & Neubig, G. (2022). *Interpreting Language Models with Contrastive Explanations*. EMNLP 2022. arXiv:2202.10419
- Sarti, G., Chrupała, G., Nissim, M., & Bisazza, A. (2024). *Quantifying the Plausibility of Context Reliance in Neural Machine Translation* (PECoRe). ICLR 2024. arXiv:2310.01188
- Qi, J., Sarti, G., Fernández, R., & Bisazza, A. (2024). *Model Internals-based Answer Attribution for Trustworthy Retrieval-Augmented Generation* (MIRAGE). EMNLP 2024. arXiv:2406.13663

**Model component importance: ablation, patching, causal tracing**

- Vig, J., et al. (2020). *Investigating Gender Bias in Language Models Using Causal Mediation Analysis*. NeurIPS 2020. arXiv:2004.12265
- Geiger, A., Lu, H., Icard, T., & Potts, C. (2021). *Causal Abstractions of Neural Networks*. NeurIPS 2021. arXiv:2106.02997
- Meng, K., et al. (2022). *Locating and Editing Factual Associations in GPT*. NeurIPS 2022. arXiv:2202.05262
- Zhang, F., & Nanda, N. (2024). *Towards Best Practices of Activation Patching in Language Models: Metrics and Methods*. ICLR 2024. arXiv:2309.16042
- Heimersheim, S., & Nanda, N. (2024). *How to use and interpret activation patching*. arXiv:2404.15255

---

## 4. Representations and concepts

**Linear representation hypothesis and steering**

- Park, K., Choe, Y. J., & Veitch, V. (2024). *The Linear Representation Hypothesis and the Geometry of Large Language Models*. ICML 2024. arXiv:2311.03658
- Marks, S., & Tegmark, M. (2023). *The Geometry of Truth: Emergent Linear Structure in Large Language Model Representations of True/False Datasets*. arXiv:2310.06824
- Turner, A. M., et al. (2023). *Steering Language Models With Activation Engineering* (ActAdd). arXiv:2308.10248
- Rimsky, N., et al. (2024). *Steering Llama 2 via Contrastive Activation Addition*. ACL 2024. arXiv:2312.06681

**Function and task vectors**

- Todd, E., Li, M. L., Sharma, A. S., Mueller, A., Wallace, B. C., & Bau, D. (2024). *Function Vectors in Large Language Models*. ICLR 2024. arXiv:2310.15213
- Hendel, R., Geva, M., & Globerson, A. (2023). *In-Context Learning Creates Task Vectors*. Findings of EMNLP 2023. arXiv:2310.15916
- Liu, S., Ye, H., Xing, L., & Zou, J. (2024). *In-context Vectors: Making In Context Learning More Effective and Controllable Through Latent Space Steering*. ICML 2024. arXiv:2311.06668

**Probing**

- Alain, G., & Bengio, Y. (2016). *Understanding intermediate layers using linear classifier probes*. arXiv:1610.01644
- Hewitt, J., & Liang, P. (2019). *Designing and Interpreting Probes with Control Tasks*. EMNLP 2019. arXiv:1909.03368
- Belinkov, Y. (2022). *Probing Classifiers: Promises, Shortcomings, and Advances*. Computational Linguistics, 48(1). arXiv:2102.12452

**Superposition**

- Elhage, N., et al. (2022). *Toy Models of Superposition*. Transformer Circuits Thread. arXiv:2209.10652

**Sparse autoencoders**

- Bricken, T., et al. (2023). *Towards Monosemanticity: Decomposing Language Models With Dictionary Learning*. Transformer Circuits Thread. https://transformer-circuits.pub/2023/monosemantic-features
- Cunningham, H., Ewart, A., Riggs, L., Huben, R., & Sharkey, L. (2024). *Sparse Autoencoders Find Highly Interpretable Features in Language Models*. ICLR 2024. arXiv:2309.08600
- Templeton, A., et al. (2024). *Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet*. Transformer Circuits Thread. https://transformer-circuits.pub/2024/scaling-monosemanticity
- Engels, J., Riggs, L., & Tegmark, M. (2024). *Decomposing The Dark Matter of Sparse Autoencoders*. arXiv:2410.14670

**Transcoders and cross-layer transcoders**

- Dunefsky, J., Chlenski, P., & Nanda, N. (2024). *Transcoders Find Interpretable LLM Feature Circuits*. NeurIPS 2024. arXiv:2406.11944
- Ameisen, E., et al. (2025). *Circuit Tracing: Revealing Computational Graphs in Language Models*. Transformer Circuits Thread. https://transformer-circuits.pub/2025/attribution-graphs/methods.html

---

## 5. Models of reason — circuits

**Circuits and circuit discovery**

- Olah, C., et al. (2020). *Zoom In: An Introduction to Circuits*. Distill. https://distill.pub/2020/circuits/zoom-in/
- Conmy, A., Mavor-Parker, A. N., Lynch, A., Heimersheim, S., & Garriga-Alonso, A. (2023). *Towards Automated Circuit Discovery for Mechanistic Interpretability* (ACDC). NeurIPS 2023. arXiv:2304.14997
- Syed, A., Rager, C., & Conmy, A. (2023). *Attribution Patching Outperforms Automated Circuit Discovery*. arXiv:2310.10348
- Bhaskar, A., Wettig, A., Friedman, D., & Chen, D. (2024). *Finding Transformer Circuits with Edge Pruning*. NeurIPS 2024. arXiv:2406.16778

**Induction heads and IOI**

- Olsson, C., et al. (2022). *In-context Learning and Induction Heads*. Transformer Circuits Thread. arXiv:2209.11895
- Wang, K., Variengien, A., Conmy, A., Shlegeris, B., & Steinhardt, J. (2023). *Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 small*. ICLR 2023. arXiv:2211.00593

**Limits of circuits**

- McGrath, T., Rahtz, M., Kramár, J., Mikulik, V., & Legg, S. (2023). *The Hydra Effect: Emergent Self-repair in Language Model Computations*. arXiv:2307.15771
- Rushing, C., & Nanda, N. (2024). *Explorations of Self-Repair in Language Models*. ICML 2024. arXiv:2402.15390
- Hanna, M., Pezzelle, S., & Belinkov, Y. (2024). *Have Faith in Faithfulness: Going Beyond Circuit Overlap When Finding Model Mechanisms*. COLM 2024. arXiv:2403.17806
- Miller, J., Chughtai, B., & Saunders, W. (2024). *Transformer Circuit Faithfulness Metrics are not Robust*. COLM 2024. arXiv:2407.08734

**Attribution graphs**

- Ameisen, E., et al. (2025). *Circuit Tracing: Revealing Computational Graphs in Language Models*. Transformer Circuits Thread. https://transformer-circuits.pub/2025/attribution-graphs/methods.html
- Lindsey, J., et al. (2025). *On the Biology of a Large Language Model*. Transformer Circuits Thread. https://transformer-circuits.pub/2025/attribution-graphs/biology.html

---

## 6. Validating explanations

- Joshi, S., Mueller, A., Klindt, D., Brendel, W., Reizinger, P., & Sridhar, D. (2026). *Position: Causality is Key for Interpretability Claims to Generalise*. arXiv:2602.16698
- Joshi, S., Mueller, A., Reizinger, P., & Sridhar, D. (2026). *Causal Foundations for Interpretability: What Your Methods Actually Identify*. Tutorial at EMNLP 2026.
- Mueller, A., et al. (2025). *MIB: A Mechanistic Interpretability Benchmark*. ICML 2025. arXiv:2504.13151
