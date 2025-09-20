---
layout: post
title: "The structure of a protein"
date: 2024-08-15
mathjax: true
---

Understanding the 3D structure of a protein is a bit of a rabbit-hole for someone new to the field: there is a lot of jargon, and correspondingly a lot of intricate detail: backbone, alpha carbons, alpha helices, beta sheets, primary, secondary, teriary quaternary structure, etc. etc. I'm going to try to put all this and more down here, as systematically as I can. 

**The pre-requisites**
- Amino acid: An amino acid is the basic building block of proteins. Think of it like a Lego brick: all bricks share the same connector shape so they can link up, but each brick can have a different color/pattern that changes how it behaves.

```
    H     O
    |     ||
H2N–C–C–OH
    |
    R
```
Lets analyze this molecule piece by piece:
- H2N (–NH₂) → this is the amino group (hence “amino acid”).
- COOH (–COOH) → this is the carboxyl group (the “acid” part).
- C (the middle one, called C-alpha, Cα) → holds everything together.
- R → the variable side chain with 20 common possibilityes. This is the only part that changes between amino acids. This is like the personality of the Lego brick. Examples:
  - R = just H → glycine (the simplest, very flexible).
  - R = CH₃ → alanine (small and boring).
  - R = big aromatic ring → tryptophan (bulky, absorbs UV light).
  - R = acidic group → glutamate/aspartate (negatively charged).
  - R = basic group → lysine/arginine (positively charged).

How do the amino acids join to form a chain? The amino group of one amino acid reacts with the carboxyl group of the next. They form a peptide bond (–CO–NH–), releasing water. Because every amino acid has the same backbone, they link neatly into a chain. The chain’s “decorations” (the side chains R) stick out like charms on a bracelet.
- Residue: When amino acids join to make a protein, the carboxyl group (–COOH) of one and the amino group (–NH₂) of the next react, forming a peptide bond (–CO–NH–). In the process, a water molecule is removed (–OH from one, –H from the other). That means each amino acid loses a little piece of itself (the parts that formed water) the name we use for an amino acid once it’s joined into a chain (because it “leaves behind” water during linking).  After amino acids have joined in the chain, what remains of each original amino acid is called a residue — because it’s the “residue” (the leftover part) of the original whole amino acid once the water is gone. For example: Take glycine (NH₂–CH₂–COOH). As a free amino acid, it has both amino + carboxyl ends. Once in a chain, it no longer has both ends — the middle parts are tied into peptide bonds. What remains in the chain is called the glycine residue.

- Peptide bond: the link between amino acids; formed by removing water between the carboxyl (–COOH) of one and amino (–NH₂) of the next. It’s planar (partial double-bond character), which matters for what angles are allowed.

Two key backbone rotation angles:
- φ (phi): around N–Cα
- ψ (psi): around Cα–C
Not every combination is allowed—steric clashes limit them (see Ramachandran plot), and those allowed zones give rise to the recurring shapes below.
