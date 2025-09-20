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
- H2N (–NH₂-): this is the amino group (hence “amino acid”).
- COOH (–COOH): this is the carboxyl group (the “acid” part).
- C (the middle one, called C-alpha, Cα) → holds everything together.
- R → the variable side chain with 20 common possibilityes. This is the only part that changes between amino acids. This is like the personality of the Lego brick. Examples:
  - R = just H => glycine (the simplest, very flexible).
  - R = CH₃ => alanine (small and boring).
  - R = big aromatic ring => tryptophan (bulky, absorbs UV light).
  - R = acidic group => glutamate/aspartate (negatively charged).
  - R = basic group => lysine/arginine (positively charged).

How do the amino acids join to form a chain? The amino group of one amino acid reacts with the carboxyl group of the next. They form a peptide bond (–CO–NH–), releasing water. Because every amino acid has the same backbone, they link neatly into a chain. The chain’s “decorations” (the side chains R) stick out like charms on a bracelet.

- Residue: When amino acids join to make a protein, the carboxyl group (–COOH) of one and the amino group (–NH₂) of the next react, forming a peptide bond (–CO–NH–). In the process, a water molecule is removed (–OH from one, –H from the other). That means each amino acid loses a little piece of itself (the parts that formed water) the name we use for an amino acid once it’s joined into a chain (because it “leaves behind” water during linking).  After amino acids have joined in the chain, what remains of each original amino acid is called a residue — because it’s the “residue” (the leftover part) of the original whole amino acid once the water is gone. For example: Take glycine (NH₂–CH₂–COOH). As a free amino acid, it has both amino + carboxyl ends. Once in a chain, it no longer has both ends — the middle parts are tied into peptide bonds. What remains in the chain is called the glycine residue.

- Peptide bond: When two amino acids join, they form a peptide bond:

```
…C=O – NH…
```
Note that the left portion has dropped an OH and the right portio has dropped an H. That C–N bond is a double bond - which can’t freely rotate, so this C–N peptide bond is rigid and planar. That means the atoms around it (C, O, N, H, and the two α-carbons) all lie roughly in the same plane, like a flat tile.

A major source of variation in the shapes that proteins fold to comes from the angles of rotation of two specific bonds: 
- φ (phi): around N–Cα
- ψ (psi): around Cα–C
The alpha carbon (Cα) is the one that is attached to the COOH, the R, the H and the amino group NH2. Not every combination of these two angles is allowed, because steric clashes limit them. The allowed combinations limit the shapes that can be produced. The combinations that are possible result mostly in _alpha-helices_ and _beta sheets_, which lead us to the next level of detail of protein structure: the secondary structure of a protein.

**Primary structure**
Primary structure is basically the sequence of amino acids in a protein chain. When we say this, we are talking about the order of the side chains (R groups) along the chain. Every amino acid has the same backbone skeleton (–N–Cα–C–). What makes one amino acid different from another is the R group attached to the alpha carbon. So when we write a sequence like:

```
Met – Lys – Gly – Phe – 
```
what we’re really specifying is:
- First residue has R = –CH₂–S–CH₃ (methionine)
- Next residue has R = –(CH₂)₄–NH₃⁺ (lysine)
- Next residue has R = –H (glycine)
- Next residue has R = –CH₂–phenyl (phenylalanine)
…and so on.

**Secondary structure**
The next level of detail as we zoom out consists of local recurring shapes. 
These are short segments (a few to ~30 residues) that adopt regular, repeating backbone patterns stabilized mostly by backbone–backbone hydrogen bonds. Backbone–backbone hydrogen bonds are the attraction between the “O” from the carbonyl group (C=O) of one residue and the “H” from the amide group (N–H) of another. 
These weak links stitch the protein chain into stable shapes like helices and sheets. The two most common patterns are _α-helices_ and _β-sheets_. In between them are connector regions called _turns_ and _loops_.

α-helix:
- Pattern: each carbonyl (CO) oxygen of residue i H-bonds to the amide (NH) hydrogen of residue i+4.
- Geometry: ~3.6 residues/turn; rise ~1.5 Å per residue; right-handed in natural L-amino acids.
- Side chains (the R's): project outward like bristles on a bottle brush.

β-sheet:
- β-strand: To understand a beta-sheet, we first need to understant a beta-strand. A β-strand is a stretch of polypeptide chain that is extended, not coiled like a helix. In this conformation, the backbone zig-zags a little, and the side chains (R groups) alternate pointing above and below the strand
```
  R ↑          R ↑
N–Cα–C–N–Cα–C–N–Cα–C–
        R ↓
```
- This alternating pattern is important — it lets strands pack together without the side chains clashing.
- Multiple β-strands line up side by side.
- Hydrogen bonds form between backbone N–H (donor) of one strand and backbone C=O (acceptor) of the neighboring strand. So the strands are zippered together.
- These H-bonds run perpendicular to the strand direction, like rungs on a ladder.
- Antiparallel β-sheet: Neighboring strands run in opposite N→C directions
- Parallel β-sheet: Neighboring strands run in the same N→C directions
- Despite the name, β-sheets are twisted, not really flat. This swit makes them more stable and allow them to form structures like beta-barrels (i.e. cylinders) and beta-sandwiches (2 sheets packed together)

**Tertiary structure**
This is the overall 3D arrangement of all atoms (or of the backbone) for one polypeptide chain—how its helices, sheets, and loops are packed into a fold (often subdivided into domains). The forces that shape it are several:

- Hydrophobic effect (the big one): nonpolar side chains pack inward away from water; polar/charged faces solvent.
- Van der Waals packing: tight interior packing of side chains.
- Hydrogen bonds: within backbone (secondary) and side-chain networks.
- Salt bridges: ionic pairs (e.g., Lys–Asp) tuned by local dielectric.
- Disulfide bonds: covalent Cys–Cys crosslinks that lock topology (common in secreted/extracellular proteins).
- Metal coordination / cofactors: Zn²⁺ fingers, heme in globins, Fe–S clusters—often define active sites.
- Proline & glycine effects: Proline restricts φ (helix breaker/turn former); Gly is flexible (favored in tight turns).

Generally, tertiary structure is obtained experimentally using x-ray crystallography or NMR.

**Quaternary structure**
The 3D arrangement of two or more polypeptide chains (subunits) into a functional oligomer or complex.


