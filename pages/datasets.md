---
layout: page
title: Datasets
includelink: true
---

**A (growing) list of useful datasets/databases:**

- [ChemBL](https://www.ebi.ac.uk/chembl/): A large database of various biologically active compounds. It 'brings together chemical, bioactivity and genomic data to aid the translation of genomic information into effective new drugs.'


- [UniProtKB/UniRef90](https://www.uniprot.org/help/uniref): ~106M Protein sequences, covering the entire tree of life. The protein data is organized at multiple levels of clustering. For example, Uniref90 is created by clustering proteins in the Uniref100 data, which is unclustered.  

- [pfam](http://pfam.xfam.org/): Protein Families database. About 31M proteins, clustered into evolutionarily-related families.

- [proteinNET](https://github.com/aqlaboratory/proteinnet?tab=readme-ov-file): A curated dataset of proteins. Seeks to be the Imagenet of the bioinfomatics world. Not sure how actively it is maintained. 

- [DISEASES](https://diseases.jensenlab.org/About): DISEASES is a weekly updated web resource that integrates evidence on disease-gene associations from automatic text mining, manually curated literature, cancer mutation data, and genome-wide association studies.

- [CellXGene corpus](https://cellxgene.cziscience.com/): single cell data. Looks like its run by the Chan Zuckerberg initiative.  



**The nature of data**

Biological data has several nuances to be aware of. Just as someone new to computer vision would have no idea what R/G/B channels are, someone new to proteins or genomics needs to be careful in understanding nuances of data. This is a work-in-progress document that I will constantly update as and when I learn new things.

- Protein data:
  - The most fundamental type of data for proteins is protein sequences, usually prepresented as a text string of capital letters drawn from a volcabulary of 20 possible letters, which represent 20 possible amino acids. There are 5 more letters that are meant to capture rare cases such as very rare forms of amino acids, and unknown amino acids. This protein sequence is called the 'primary structure' of a protein.
  - The number of known protein sequences in all of biology (not just in humans) is growing rapidly and currently stands at 600M (as of March 2024). The number of known proteins in the human body is about 300,000.
  - The secondary structure of a protein is a 3-way annotation for each amino acid that says whether that amino acid is part of an alpha-helix, a beta-sheet or neither.
  - The tertiary structure of a protein specifies the exact 3-dimensional coordinates of each alpha-carbon in the peptide backbone, upto roatations and translations of the entire protein. Predicting the teriary structure is the subject of the CASP challenge, which the now-famous AlphaFold2 model did very well at.
  - There are several datasests associated with the properties of proteins, apart from structure, and these are often things that biologists care about predicting. For example: whether the protein lives in a cell's cytoplasm, or on the membrane, what the melting point of a protein is (the temp at which it looses its tertiary structure, the, etc.

- Genomics data:
  - scRNA (single cell RNA) data: This type of data consists of measurements made from a single cell at a time. It measures the _expression level_ (i.e. intensity level) of each gene in an organism's DNA. The way it does this is by measuring the relative abundance of the mRNA corresponding to each gene. One row of data is a single cell's measurements, each column is a gene, and each value is a continuous measurement that indicates the relative abundance of mRNA from that gene. The measurements are normalized to account for the fact that some genes are much longer than others and therefore would naturally lend themselves to greater abundance of mRNA. Most, in fact the vast majority of genes, are likely to be unexpressed, i.e. to have mRNA measurments of 0. The reason this type of data is relevant is that even though each cell has the same DNA, it _expresses_ its genes differently from other cells -- this is what allows cells to become specialized: liver cells, muscle cells, skin cells, etc -- and a cell also expresses its genes differently at different _times_, depending on its environment and stimili it may be experiencing at that time. Therefore scRNA measurements are not just cell-specific, they are also time-specific. 
  - Straight up gene sequences consisting of the genome of several individuals of many species. A genome is simply a long sequence of base-pairs. The lenght of the sequence is typically measured in units of kb -- kilo base-pairs. 
  - A 3rd type of dataset is a graph between genes, or a gene-gene network, that is meant to encode interactions between genes. 


**What is FASTA format?**

FASTA format is a text-based format for representing either nucleotide sequences or peptide sequences, in which base pairs or amino acids are represented using single-letter codes. A sequence in FASTA format begins with a single-line description, followed by lines of sequence data. The description line is distinguished from the sequence data by a greater-than (">") symbol in the first column. It is recommended that all lines of text be shorter than 80 characters in length.
An example sequence in FASTA format is:

```
>gi|186681228|ref|YP_001864424.1| phycoerythrobilin:ferredoxin oxidoreductase
MNSERSDVTLYQPFLDYAIAYMRSRLDLEPYPIPTGFESNSAVVGKGKNQEEVVTTSYAFQTAKLRQIRA
AHVQGGNSLQVLNFVIFPHLNYDLPFFGADLVTLPGGHLIALDMQPLFRDDSAYQAKYTEPILPIFHAHQ
QHLSWGGDFPEEAQPFFSPAFLWTRPQETAVVETQVFAAFKDYLKAYLDFVEQAEAVTDSQNLVAIKQAQ
LRYLRYRAEKDPARGMFKRFYGAEWTEEYIHGFLFDLERKLTVVK
```

Sequences are expected to be represented in the standard IUB/IUPAC amino acid and nucleic acid codes, with these exceptions:
lower-case letters are accepted and are mapped into upper-case;
a single hyphen or dash can be used to represent a gap of indeterminate length;
in amino acid sequences, U and * are acceptable letters (see below).
any numerical digits in the query sequence should either be removed or replaced by appropriate letter codes (e.g., N for unknown nucleic acid residue or X for unknown amino acid residue).

The nucleic acid codes are:
```
        A --> adenosine           M --> A C (amino)
        C --> cytidine            S --> G C (strong)
        G --> guanine             W --> A T (weak)
        T --> thymidine           B --> G T C
        U --> uridine             D --> G A T
        R --> G A (purine)        H --> A C T
        Y --> T C (pyrimidine)    V --> G C A
        K --> G T (keto)          N --> A G C T (any)
                                  -  gap of indeterminate length
```

The accepted amino acid codes are:

```
    A ALA alanine                         P PRO proline
    B ASX aspartate or asparagine         Q GLN glutamine
    C CYS cystine                         R ARG arginine
    D ASP aspartate                       S SER serine
    E GLU glutamate                       T THR threonine
    F PHE phenylalanine                   U     selenocysteine
    G GLY glycine                         V VAL valine
    H HIS histidine                       W TRP tryptophan
    I ILE isoleucine                      Y TYR tyrosine
    K LYS lysine                          Z GLX glutamate or glutamine
    L LEU leucine                         X     any
    M MET methionine                      *     translation stop
    N ASN asparagine                      -     gap of indeterminate length
```


**Structure of MSA files with extension .a3m**

- First Line (Query Sequence ID and Description): The first line of an .a3m file typically starts with a > character, followed by the identifier (ID) of the query protein and possibly a description. This line is used to identify the query sequence around which the alignment is constructed.

- Second Line (Query Sequence): The second line provides the amino acid sequence of the query protein. In .a3m files, the sequence is presented in a single-letter amino acid code, and this line represents the primary sequence without any gaps.

- Subsequent Lines (Aligned Sequences): After the initial two lines for the query sequence, each pair of lines represents an aligned sequence from the database. The first line of each pair again starts with > and includes the database sequence identifier and possibly a description. The second line of the pair shows the aligned sequence, where:

- Uppercase letters represent residues that are aligned with the query sequence.
- Lowercase letters indicate residues that are present in the aligned sequence but not in the query (these are often insertions relative to the query).
Dots (.) or dashes represent alignment gaps in the database sequence relative to the query sequence.

- Lines Starting with >tr: Lines that start with >tr (or similar prefixes) are sequence identifiers, where the prefix often indicates the source database or specific annotations related to the sequence. Specifically, >tr is commonly associated with sequences from the UniProtKB/TrEMBL database, a manually annotated, non-redundant protein sequence database which provides high-quality functional information on proteins.

- tr Prefix: The tr in >tr specifically refers to TrEMBL, a section of the UniProt Knowledgebase. TrEMBL (Translated EMBL) contains protein sequences associated with computationally analyzed annotations and is designed to provide a supplement to UniProtKB/Swiss-Prot, which contains manually annotated records. The tr identifier is used to denote sequences that have been sourced from this database.
In summary, each pair of lines after the query sequence in an .a3m file represents an alignment with another protein sequence from the database. The lines starting with >tr or similar prefixes identify the source and ID of these database sequences, followed by lines that show how these sequences align with the query sequence, using a combination of uppercase letters, lowercase letters, and dots to represent the alignment details.



