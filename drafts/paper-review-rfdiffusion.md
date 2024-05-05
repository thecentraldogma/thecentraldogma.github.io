Paper review for RFDiffusion "De Novo Design of Protein Structure and Function using RFDiffusion".

Reading and understanding the RFDiffusion paper, and its supplementary materials has been hugely instructional. I view RFDiffusion to be the current SoTA effort in generative modeling of proteins, and the most relevant single paper to drug design. Ofcourse it has several dependencies that need to be understood -- chiefly, RosettaFold and ProteinMPNN. There is a follow up paper called RFDiffusion/RosettaFold-all-atom, which I'll be reviewing in a separate post. 

Here are the main highlights of RFDiffusion: 

- Unconditional and conditional generation of protein _structures_ using a diffusion modeling approach. 
- During training, known protein structures from the pDB are noised by adding noise to the spatial coordinates of the residues: 
  - Translational 3D spherical Gaussian noise is added to the alpha carbons, and rotational noise is added to the two torional angles. 
  - The two types of noise are added indepentently.
  - Each residue is noised independently.
  - Similarly the denoising process also denoises the translational and reotational parts independently. 
- The diffusion model reuses the RosettaFold neural network. 
  - Details: 
- After having trained the diffusion model, one can generate unconditional proteins easily. 
- To check whether a generated protein is 'realistic': 
  - Apply ProteinMPNN to convert the generated structure A to a sequence. 
  - Use this sequence to infer a structure B using AlphaFold2. 
  - Compare the structures A and B using metrics like RMSD and TM-score. 
  - The above is called 'self-consistency' or 'recapitulation'
  - Further validate by actual experimentation (wet lab). 
- The more interesting part is conditional generation, because what we really care about is generating proteins that can bind to specific targets, and have specific properties like solubility and non-toxicity. If we can condition on such criteria, and generate proteins with the desired properties with high probability, then a combination of recpitulation and experimental validation gives us a good AI-driven drug design pipeline. 
- How RFDiffusion conditions: 
  - There are mainly 4 types of conditioning problems: 
    - Motif scaffolding: where we know the structure of a motif that we want and the rest of it, _viz_ the scaffolding part can be anything. 
    - Binder design: here we are given the structure of a target and we want to design a protein structure that will bind to it. 
    - Symmetric design
    - 

**Critique**: The specific manner in which noise is added to residue frames is that independent 3D translational noise and 3D rotational noise is added to each residue independently of other residues. This means that the fullly noised state does not consist of a continuous chain of residues anymore. Since all proteins consist of continuous chains of residues, the denoising process needs to learn this fact. This feels like an inefficient use of data from a sample complexity view. I'm guessing one of the reaons the authors chose this route is that when generating we don't know what the sequence of amino acids is, and this approach allows for diverse sequences to form. However, what if we add a different type of noise that always maintains the continuity of the backbone during noising/denoising: by adding rotations between each pair of successive residues, and by adding discrete noise that flips between the 20 possible amino acids? 
