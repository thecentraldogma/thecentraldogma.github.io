---
layout: post
title: "Protein Language Models"
date: 2024-03-22
mathjax: true
---

Protein-LMs are BERT-style (encoder only) models trained on protein sequences, typically using a masked-language-modeling objective. The goal is to to self-supervised repreesntation learning, so that the learnt protein representations can perform well on downstream tasks by virtue of transfer learning, or the learnt model can be fine-tuned using a labelled dataset for a downstream task. 

A number of Protein-LLMs have been proposed by groups in academia and industry: 

- ProteinBERT (2022, Hebrew University of Jerusalem)

- ESM (Facebook AI Research)

- TAPE-Transformer

- ProtTrans

- UniRep

Downstream tasks for protein modeling: 

- Remote Homology prediction: 

- Secondary structure prediction: 

- Disorder prediction: 

- 


Benchmarks for evaluating transfer learning from protein LLMs: 

- TAPE

 

