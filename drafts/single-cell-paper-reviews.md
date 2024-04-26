A number of papers have attempted to build a foundation model of single cell biology using single-cell transcriptomics data, in a self-supervised manner, very often by using a masked language modeling loss. Some of the papers in this space are: 

- UCE: Universal Cell Embeddings, Jure Lesovic et al
- scGPT: 
- Geneformer: 
- scVI: 
- scArches: 
- scGPT: 
- tGPT: 
- cellLM: 
- scFoundation: 
- SCimilarity: 
- scELMo:


The `bag of RNA` perspective: in a throwback to the term bag-of-words, [Stephen Quake](https://www.cell.com/action/showPdf?pii=S0168-9525%2821%2900227-4) in a brief writeup described the cell as a bag-of-RNA. In brief, this perspective represents each cell as a bag of RNA molecules and the relative abundance of each RNA molecule. Pretyt much all papers above use this perspective. One 

A selection of the above: 

- UCE: 
 - Normalize gene expression data across expressed genes such that it is a multinomial probability distribution, such that the weight of each gene is proportional to its expression level. 
 - Sample genes from this distribution with replacement.
 - Find each gene's corresponding protein sequence, and represent it as the protein embedding output from the ESM protein LLM. 
 - Sort the sampled genes by chromosome location, and group by chromosomes, adding on a special token at the chromosome boundaries. 
 - Add a special [CLS] token a the begining, and this becomes the sequence representing that cell. 
 - This sequence is passed through 33 layers of transformers. 
 - Now for training, we mask 20% of the _expressed_ genes, i.e. we never sample from those cells, and we collect a few cells from the expressed set and the unexpressed set, and we pass the output of the 33 transformer layers above, concatenated along with selected genes to ask whether this gene is expressed in the cell or not. 
 - Effectively, this forces the network architecture to learn co-occurence patterns of genes. It is like a masked language modeling task. 
 - The final representation of the cell is the output of the final transformer layer in the stack of 33 transformer layers. 
 - Note that the sampling procedure allows them to convert numerical gene expression data into a sequence of tokens, where the relative abundance of tokens is proportioanl to the gene expression level. This looks like a bit of shoe-horning to me: it represents an opportunity to modify pre-trained language models to more gracefully use numerical data. 
 - Note also that by moving to the domain of proteins and their ESM2 embeddings, UCE does away with reliance on cell type and tissue type. 


**How does these types of studies help with understanding dieseas mechanisms?**

- 	
