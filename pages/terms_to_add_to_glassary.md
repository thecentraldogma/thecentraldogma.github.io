Ca, Cb
Rosetta
Physically base approaches
Diffusion in the context of protein folding and protein design
Evoformer
Row attention, column attention
MSA, and how its used in Alphafold2/3

What is a protein language model - how does it help folding and inverse folding: a PLM is basically a bert-style encoder-only model for representation learning of protein sequences. The model here takes a new protein seuqneces or arbitrary lenght as input, and produces an embedding of the sequence in vector space. Protein language models avoid the need for MSA - multiple seuqence alignment, during protein folding because MSA is typically used to gather additional features from related sequences, while the embedding of a protein from a PLM already contains contextual information from other proteins. 

Inverse folding problem: hsa a specific meaning - given a folding, we wan to find a sequence that folds to that shape and not some other shape, i.e. we want the given shape to be the lowest enrgy conformation. 

-- RFDiffusion

-- RosettaFold

-- chroma

-- What is diffusion doing here

-- how does unconditional and ocnditinal diffusion work? 

-- complexes

-- protein-protein interactions

-- How des alphaFold3 help with p-p interactions?




