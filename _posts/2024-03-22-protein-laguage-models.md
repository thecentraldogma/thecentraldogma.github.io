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

- Remote Homology prediction: Two proteins with very different sequences can sometimes have very similar 3D structures. Often, this happens when two proteins have evolutionarily descended from the same ancestor protein and perform very similar functions and hence have similar structure, but their sequences have diverged quite a lot. Remote homology detection is typically cast as a classification task where each protein is mapped to a single class corresponding to a brad characterization of its 3D structure. 

- Secondary structure prediction: This is a token-level task, i.e. one output per amino acid. It is typically cast as a classification task where each amino acid is in one of 3 configurations: Helix ("H"), Beta strand ("E"), or Coil ("C"). 

- Contact Prediction: This task has to do with the tertiary structure of the protein, i.e. how th protein folds. It is a classification task for each pair of tokens, i.e. each pairs of amino acids in the protein are either within a certain threshold distance (usually < 8 Angstroms), or not. This results in a 'contact map' consisting of a N x N binary matrix, where N is the number of amino acids.  

- Stability prediction: This is a regression task at the protein level.

- Disorder prediction: 

- Flourescence prediction: This is a regression task at the protein level. 


Benchmarks for evaluating transfer learning from protein LLMs: 

- TAPE

 

