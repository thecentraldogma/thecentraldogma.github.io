---
layout: page
title: Datasets
---

A list of useful datasets. 

- UniProtKB/UniRef90: ~106M Protein sequences, covering the entire tree of life. 

- pfam: Protein Families database. About 31M proteins, clustered into evolutionarily-related families.

- proteinNET:  


**Structure of MSA files with extension .a3m**
This is called the FASTA file format. 

- First Line (Query Sequence ID and Description): The first line of an .a3m file typically starts with a > character, followed by the identifier (ID) of the query protein and possibly a description. This line is used to identify the query sequence around which the alignment is constructed.

- Second Line (Query Sequence): The second line provides the amino acid sequence of the query protein. In .a3m files, the sequence is presented in a single-letter amino acid code, and this line represents the primary sequence without any gaps.

- Subsequent Lines (Aligned Sequences): After the initial two lines for the query sequence, each pair of lines represents an aligned sequence from the database. The first line of each pair again starts with > and includes the database sequence identifier and possibly a description. The second line of the pair shows the aligned sequence, where:

- Uppercase letters represent residues that are aligned with the query sequence.
- Lowercase letters indicate residues that are present in the aligned sequence but not in the query (these are often insertions relative to the query).
Dots (.) or dashes represent alignment gaps in the database sequence relative to the query sequence.

- Lines Starting with >tr: Lines that start with >tr (or similar prefixes) are sequence identifiers, where the prefix often indicates the source database or specific annotations related to the sequence. Specifically, >tr is commonly associated with sequences from the UniProtKB/TrEMBL database, a manually annotated, non-redundant protein sequence database which provides high-quality functional information on proteins.

- tr Prefix: The tr in >tr specifically refers to TrEMBL, a section of the UniProt Knowledgebase. TrEMBL (Translated EMBL) contains protein sequences associated with computationally analyzed annotations and is designed to provide a supplement to UniProtKB/Swiss-Prot, which contains manually annotated records. The tr identifier is used to denote sequences that have been sourced from this database.
In summary, each pair of lines after the query sequence in an .a3m file represents an alignment with another protein sequence from the database. The lines starting with >tr or similar prefixes identify the source and ID of these database sequences, followed by lines that show how these sequences align with the query sequence, using a combination of uppercase letters, lowercase letters, and dots to represent the alignment details.







