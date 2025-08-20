---
layout: post
title: "Introduction to drug design"
date: 2024-02-05
mathjax: true
---

Disease has been with humans for as long as we have historical records: from infectious diseases like cholera and malaria to the much more recent 'lifestyle diseases' like diabetes and heart disease, which are understood to result in large part due to a mismatch between the conditions we humans evolved for and the conditions in which we not live. Modern medicine has used many terms to describe treatments for diseases: medicines, therapeutics, and 'drugs'. Early medicines were often the result of either accident (e.g. pennicilin) or intense study and labor using laboratory techniques. In the last few years, there have been major advances in the field of drug-design, i.e. the design of specific molecules to treat specific diseases. This has been possible because we now understand something quite extraordinary that would have seemed miraculous to the scientists of the early 20th century: that the function of particles and molecules in the human body is determined by their 3-dimensional geometry! This is because particles interact with other particles and with cells of specific organs, in specific ways by way of a specific geometry -- often by fitting or locking into the 3D geometry of another partile or cell surface. 

This basic understanding unlocks and entirely new field -- computational drug design. That is, if we understand the mechanism by which a disease progresses, and the identities and 3D geometries of the particles involved, it might be possible to design particles that have a specific 3D geometry that would interact with one of the particles culpable in the disease mechanism and thereby block or inhibit the disease. 

One way to systematize the field is to subdivide it into two separate areas: small molecule design and protein design. Protein design refers to computationally designing new proteins, even those that may not ever have been discovered, with 3D geometry that would interact with some particle in a disease pathway, for example binding to a given target molecule. Small molecule design is the same thing but with much smaller molecules than proteins. In addition to having the right 3D gemetry, these molecules also need to have other properties/ Some of these are (not an exhastive list): 

- They must not be toxic. 
- They must have good solubility. 
- They must be specific, i.e they must interact with the intended target but not with other unintended targets, so that it doesnt disrupt other bilogical processes in our body. 

Obviously it is important to know what particle we want our designed drug to interact with -- this particle is typically called the **target**. Biologists and chemists still need to do the difficult and foundational work of deciphering the precise mechanism of a disease, and what  particles are involved, so that some candidate targets can be idnetified. Protein based drugs have been growing in market share -- they have the advantage of lower side effects because they are biomolecules rather than chemical compounds, but the disadvantage is that they are currently harder to manufacture. 

Modern machine learning methods enable us to computationally create molecules that are likely to have the right properties to interact with a specific target. The design of
proteins with a desirable 3D-gemetry is the inverse of the protein folding problem. That is, while the protein folding problem asks: 'given a protein sequence, what 3D struc
ture does it spontaneously fold to?'. The inverse problem asks: 'given a desired 3D shape, what protein sequence(s) will sponteneously fold to it?'. We still ned the protein
 to have the other desirable properties (solubility, non toxicity, specificity, etc.). If we can computationally figure out a set of protein sequences that are likely to hav
e the right properties, i.e. in silico,, then we can verify if they really do have those properties in a wet-lab, i.e. in vitro. 

One can see how this can be cast as a generative AI problem. Just as text LLMs allow a prompt to be completed with text that is likely to 'make sense' given a large body of training data that encodes statistic patterns, a generative model for molecules can be 'prompted' by specifying that the molecule to be generated must have a portion with a specific 3D gemetry (this usually called a **motif**), and given this constraints and other real-world constraints that encode the basic structural chemistry of chemical bonds, and free energy, the generativ model must sample candidate molecules. This is the premise behind RFDiffusion from the baker lab, and Chroma, another paper using diffusion models. The fidelity with which we can do this depends on the quantity and quality of the data used to train a generative model, as well as on the model itself. In particular, the data we need must pair chemical molecules and protein sequences to their 3D geometry. The structure of small molecules is realtively easy to predict because of number of atom-atom interactions is relatively small. But the 3D geometry of a protein is notoriously difficult to predict. Only a tiny fraction of known proteins have ever had their structure resolved in a laboratory. However, in 2021, our ability to know the structure of a preotein dramatically improved - thanks to AlphaFold2. AlphaFold2 is a machine learning model trained on available data at the time, that can be used to predict the 3D structure of a new protein, and it turns out that, with some exceptions, it does extremely well at predicting structure of unknown proteins. This means that while we still do not have lab-verified structure for many more proteins, we do have alphaFold2 predictions at the press of a button. And this data can potentially serve as input in the drug design problem. 





