---
layout: post
title: "Diffusion models in drug design"
date: 2024-04-22
mathjax: true
---

A number of papers in the last 2 years have trained diffusion models relevant to drug design: 

- RFDiffusion
- RFDiffusion all-atom
- Chroma
- DSM for co-generation of sequences and 3D structures
- Protpardelle	
- FrameDiff
- GENIE
- ProteinSGM
- ProtDiff
- FoldingDiff
- DiffAB

This post assumed basic familiarity with the Variational Autoencoder, and is broken down into the following parts: 

-- How do diffusion models work in general? 
-- How are they used in generating images? 
-- How is conditional generation achieved? 
-- What is different when it comes to drug design? 
-- How are diffusion models used in drug design? 

Sander Dieleman has an excellent set of posts on his blog about various aspects and interpretations of Diffusion Models and how conditional diffusion models work. I found these to be particularly approachable. Jason Yim et al have put out a nice review of diffusion modeling methods for protein design and for small molecule ligand docking - this is also a great read!
