---
layout: post
title: "Introduction to drug design"
date: 2024-02-05
mathjax: true
---

(1) 'Drug design' is an overloaded term. It can mean many things. One way to systematize the term is to subdivide it into two separate areas: small molecule design and protein design. These are two classes of therapeutics. 
(2) A therapeutic is a substance meant to be introduced into the body to help alleviate disease -- in general terms. The mechanism of action is not specified. 
(3) A very common mechanism of action is related to the geometry of the molecule being introduced, whether small molecule or protein. This is because a common mechanism is for the therapeutic molecule to bind to a target particle in the body or bloodstream, and this binding is enabled by a specific geometrical shape, that depends on the geometry of the target. 
(4) Therefore it is important to know what the target is that we want to bind to. 
(5) Drugs/therapeutics, whether small molecule or protein, also have their own properties: solubility, toxicity to humans, etc. etc., some of which are desirable and some are undesirable. 
(6) There exist databases for both small molecules and proteins that capture such properties for some large number of molecules, some of which are drugs in use today, but most are not. 
(7) Proteins belong to a class of large molecules called biomolecules. They are composed of a chain of amino acids, with a backbone comprising alpha carbons. Because they are so big, they fold into specific low energy shapes at resting state, the lowest energy of which is called the native state. Small molecules do not have this compexity - they have just one geometric shape because they are small. 
(8) Protein based drugs have been growing in market share -- they have the advantage of lower side effects because they are biomolecules rather than chemical compounds, but the disadvantage is that they are currently harder to produce (is this because of discovery, or manufacturing?)
(9) The virtual screening problem: given a small molecule, predict its properties, including suitability as a drug for a disease. (how is this encoded?) 
(10) The inverse problem: given desirable properties, what small molecule would have those properties. This requires creating a generative model that outputs molecular graphs as small molecules, when conditioning on desirable propreties as inputs (reference?)
(11) Similarly, for proteins: the protin folding problem: is where we take a protein sequence as input and predict its 3D structure in the native state. Recall that shape is important becuase the structure of a protein dictates its function. 
(12) The inverse problem is called the protein-design problem: given a desirable shape, what protein sequence would have that shape? Such a protein may not even exist in nature, but there are ways to create proteins in a wetlab given an amino acid sequence. 
(13) Points 9,10,11,12 is where ML comes in. 9 and 11 are discriminative problems (given a molecule, predict something about it), while 10 and 12 are generative problems (generate molecules/proteins with desired properties). Generative problems are generally solved using either VAE, Diffusion or Flow based methods. 
(14) The core ML modeling construct useful in 9/10/11/12 is the gemoetric graph neural network, because molecules can be modelled as graphs. However, molecules are not 2-dimensional graphs but rather 3-dimensional graphs, with specific forces, coordinates and interactions between atoms. These effects are not captured by plain vanilla GNNs which only model the relational structure of a graph. 
(15) The remedy to this problem is Geometric GNNs, which is the topic of the review paper 'Hitchhiker's guide... '. GGNNs come in 3 flavors: Invariant, Equiariant and Unconstrained. Invariant GGNNs are those for which a Euclidean transformation like rotation, reflection or translation has no effect on the output of the model. Equivariant GGNNs are those where such equclidean transormations on the input graph produce the same trransformation on the output. Unconstrained GGNNs are ? 
(16) Invariant GGNNs: are those where an approximation is made by converting vector forces and other such quantities into scalar features at each atom in the graph. After this one-time pre-calculation, the rest of the modeling exercise is treated as a vanilla GNN. 
(17) Equivariant GGNNs require some additional tensor math to understand how to do careful book-keeping over the vector forces etc. as we pass through various NN layers. 
(Need to understand this better)


