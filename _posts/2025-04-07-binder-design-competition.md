---
layout: post
title: "Binder design competition hosted by Adaptyv Bio"
date: 2025-04-07
mathjax: true
---


Binder design competition hosted by Adaptyv Bio - a company that serves as a wetlab partner to computational biology clients, i.e. it performs in-vitro testing of in-silico designs. 

**Competition Goal**

The goal of this competition was to design novel single-chain proteins that bind the extracellular domain of EGFR (Epidermal Growth Factor Receptor), a critical therapeutic target in cancer. Designs had to be at least 10 amino acids different from any known therapeutic antibodies.

Entries (up to 10 per designer) were ranked using three computational metrics:

- AlphaFold2 PAE interaction (interface Predicted Aligned Error)
- AlphaFold2 ipTM (inter-chain predicted TM-score)
- ESM2 log-likelihood (how "natural" the sequence looks)

The average rank across these determined the top 100 selections for experimental validation, with an additional 100 chosen for novelty or creative methodology.


**Competition Outcomes & Statistics**

400 designs were tested in Adaptyv’s high-throughput wet lab: 100 from top computational rankings and 300 additional designs chosen for diversity. Results were quite interesting:

- 95% expression success rate
- 14% binders (53 designs)—a 5x improvement from Round 1
- Some binders matched or exceeded Cetuximab’s performance (Merck's clinically approved antibody)


**Top Approaches & Insights**
- Winner: Cradle — Optimization of Existing Binder. A variant of Cetuximab with 10 stabilizing framework mutations (not in the binding CDR loops). Achieved KD = 1.21 nM -- 8x better than a Cetuximab scFv (~9.9 nM), and 4x better than the nearest competitor (~5.2 nM). The cradle.bio group has a blog post about their winning entry here: https://www.cradle.bio/blog/adaptyv-protein-design-competition

- Approaches using hallucination (gradient-based optimization in AlphaFold2) and SolubleMPNN inverse-folding showed strong performance in Round 1 and influenced Round 2 submissions.


The takeaway: design strategies can broadly be categorized into:

- De novo generation (e.g., RFdiffusion backbone synthesis + ProteinMPNN sequence design)
- Diversification of existing binders + filtering by metrics
- Hallucination via AlphaFold2 optimization
- Unsupervised protein language model–guided optimization (e.g., active learning)
- Physics-based docking and molecular dynamics, often followed by score filtering

Popular pipelines included RFdiffusion → ProteinMPNN → AlphaFold-based filtering


**Broader Lessons & Future Directions**

Optimization of known scaffolds (like antibodies) was very effective and even outperformed de novo strategies.
Despite control over computational scores, a major challenge remains predicting which designs truly bind in experiments. The in silico → in vitro gap is still large.
Model biases exist:

- Sequences similar to training data (peptides, common folds) tend to perform better with metrics from ESM2 and AlphaFold2.
- Novel antibodies (esp. with CDR diversities) were often penalized by these models, suggesting the need for context-specific scoring.

