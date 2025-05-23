---
layout: post
title: "Protein Language Models"
date: 2024-03-22
mathjax: true
---

Protein-LMs are BERT-style (encoder only) models trained on protein sequences, typically using a masked-language-modeling objective. The goal is to do self-supervised repreesntation learning, so that the learnt protein representations can perform well on downstream tasks by virtue of transfer learning, or the learnt model can be fine-tuned using a labelled dataset for a downstream task. 

A number of Protein-LLMs have been proposed by groups in academia and industry. Below is an (opinionated) history of the developments in the last few years: 

- Transformer based protein language models were introduced in the 2019 preprint "Biological structure and function emerge from scaling unsupervised learning to 250 million protein sequences", from the Meta AI protein research team (which has since disbanded). 

- ProteinBERT (2022, Hebrew University of Jerusalem)

- ESM (Facebook AI Research)

- TAPE-Transformer

- ProtTrans

- UniRep

- ProtGPT2, University of Bayeruth

- LM-Design, ByteDance


**Embeddings produced by protein-LLMs**: 
In the general case, one can utilize the output of the last layer of the network as embeddings -- this produces a tensor of shape 'Number of residues' x 'Embedding dimension'. But one can also take the mean of all the embeddings across residues to get a single vector for the entire protein as a point in embedding space. It is also possible to pull representations from earlier layers too of course. Finally, as in BERT, it can be more meaningful to use the embedding corresponding to the BEGIN token as the protein embedding for downstream tasks, rather than taking a mean over all amino acids.

**What a protein embedding replaces**: 
MSA or multiple sequence alignment is a function that takes in a protein sequence and returns a variable number of related sequences. Here 'related' corresponds to preservation of subsegments of a protein. This is a useful function because it serves as a way to represent the input protein better -- because it allows us to extract features from not just the input protein as well as other rlated proteins. Its a bit like: say I wanted to represent you as a person via a list of features - then I might benfit by also knowing who your friends and coworkers are, to obtain a richer set of features. However, MSA is a cumbersome procedure and it cannot be made part of an end to end learning architecture. A protein language model serves as a substitute for MSA -- it allows us to use the protein embedding produced by the PLM as the representation of the protein in a downstream task -- and, even better, the PLM can be made part of a longer chained model, and the whole thing optimized/fine tuned end to end - this is not possible with MSA> 

**Downstream tasks for protein modeling**:

- Remote Homology prediction: Two proteins with very different sequences can sometimes have very similar 3D structures. Often, this happens when two proteins have evolutionarily descended from the same ancestor protein and perform very similar functions and hence have similar structure, but their sequences have diverged quite a lot. Remote homology detection is typically cast as a classification task where each protein is mapped to a single class corresponding to a brad characterization of its 3D structure. 

- Secondary structure prediction: This is a token-level task, i.e. one output per amino acid. It is typically cast as a classification task where each amino acid is in one of 3 configurations: Helix ("H"), Beta strand ("E"), or Coil ("C"). 

- Contact Prediction: This task has to do with the tertiary structure of the protein, i.e. how th protein folds. It is a classification task for each pair of tokens, i.e. each pairs of amino acids in the protein are either within a certain threshold distance (usually < 8 Angstroms), or not. This results in a 'contact map' consisting of a N x N binary matrix, where N is the number of amino acids.  

- Stability prediction: This is a regression task at the protein level.

- Disorder prediction: 

- Flourescence prediction: This is a regression task at the protein level. 

- Predicting where a protein appears, with respect to a cell: on the membrance, in the cytoplasm, etc.: the DeepLoc-2 dataset: https://services.healthtech.dtu.dk/services/DeepLoc-2.0/

- Predicing post-translational modifications: this is a per-token (amino acid) classification task. Essentially, here we are interested in predicting which residues will undergo some kind of change after the protein has been created. 

- $T_m$ prediction: Predicting the meltime temperature of a protein, which is the temperature at which the protein looses its stable 3D configuration. This is a prtein-level regression task. 


Benchmarks for evaluating transfer learning from protein LLMs: 

- TAPE

 

