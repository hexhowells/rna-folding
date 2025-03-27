# RNA Folding Research

Can we understand RNA-folding and start to figure out how to solve it?

---

## Questions
| Section    | Questions                                                                                                                       |
|------------|---------------------------------------------------------------------------------------------------------------------------------|
| Background | - what is RNA folding? <br>- how is it different to protein folding? <br>- what is its purpose?                                         |
| Problem    | - how do we model the problem? <br>- what do the inputs look like? <br>- what do the outputs look like?                                 |
| Data       | - what does the data look like? <br>- what datasets are currently available?                                                        |
| SOTA       | - what is the current state of the art in this domain? <br>- are there similar domains (protein folding?) that can be applied here? |

---

# Current Models
Model         | Code | Paper
--------------|------|------
AlphaFold     | https://github.com/google-deepmind/alphafold/tree/main/alphafold/model | https://www.nature.com/articles/s41586-024-07487-w
Ribonanza     | https://github.com/Shujun-He/RibonanzaNet | https://pmc.ncbi.nlm.nih.gov/articles/PMC10925082/pdf/nihpp-2024.02.24.581671v2.pdf
RhoFold       | https://github.com/ml4bio/RhoFold | https://www.nature.com/articles/s41592-024-02487-0
DrFold        | https://github.com/leeyang/DRfold2 | https://www.biorxiv.org/content/10.1101/2025.03.05.641632v1 
trRosettaRNA  | ? | https://www.nature.com/articles/s41467-023-42528-4
Chai-1        | https://github.com/chaidiscovery/chai-lab | https://www.biorxiv.org/content/10.1101/2024.10.10.615955v2
Boltz-1       | https://github.com/jwohlwend/boltz | https://doi.org/10.1101/2024.11.19.624167
Pro-1         | https://github.com/michaelhla/pro-1 | https://michaelhla.com/blog/pro1.html
Protenix      | https://github.com/bytedance/Protenix | AlphaFold 3 implementation



# Papers / links

- [Thoughts on how to think (and talk) about RNA structure](https://www.pnas.org/doi/epub/10.1073/pnas.2112677119)
- [Ribonanza: deep learning of RNA structure through dual crowdsourcing](https://pmc.ncbi.nlm.nih.gov/articles/PMC10925082/pdf/nihpp-2024.02.24.581671v2.pdf)
- [Protein Data Bank](https://www.rcsb.org/)
- [Geometric nomenclature and classification of RNA base pairs](https://pmc.ncbi.nlm.nih.gov/articles/PMC1370104/pdf/11345429.pdf)
- [trRosettaRNA: automated prediction of RNA 3D structure with transformer network](https://www.nature.com/articles/s41467-023-42528-4)
- [The Cost of Sequencing a Human Genome](https://www.genome.gov/about-genomics/fact-sheets/Sequencing-Human-Genome-cost)
- [The Illustrated AlphaFold](https://elanapearl.github.io/blog/2024/the-illustrated-alphafold/)
- [DRfold2: Ab initio RNA structure prediction with composite language model and denoised end-to-end learning](https://github.com/leeyang/DRfold2)
- [FastFold: Reducing AlphaFold Training Time from 11 Days to 67 Hours](https://arxiv.org/abs/2203.00854)
- [Pro-1: reasoning models for protein stability](https://michaelhla.com/blog/pro1.html)
- [Protenix: A trainable PyTorch reproduction of AlphaFold 3](https://github.com/bytedance/Protenix)
- [Deep learning for RNA structure prediction](https://www.sciencedirect.com/science/article/pii/S0959440X25000090)
- [CASP16](https://predictioncenter.org/casp16/index.cgi)
- [RNA-Puzzles](https://www.rnapuzzles.org/)
- [University of Missouri Computational RNA Biophysics - Research](https://vfold.missouri.edu/research.html)
- [RNA-Puzzles Round V: blind predictions of 23 RNA structures](https://www.nature.com/articles/s41592-024-02543-9)
- [RhoFold+: Accurate RNA 3D structure prediction using a language model-based deep learning approach](https://github.com/ml4bio/RhoFold)
- [Boltz-1](https://github.com/jwohlwend/boltz)
- [Chai-1](https://github.com/chaidiscovery/chai-lab)
- [Introduction to Protein Data Bank Format](https://www.cgl.ucsf.edu/chimera/docs/UsersGuide/tutorials/pdbintro.html)
- [RNA function follows form – why is it so hard to predict?](https://www.nature.com/articles/d41586-025-00920-8)
- [ATOM-1: A Foundation Model for RNA Structure and Function Built on Chemical Mapping Data](https://www.biorxiv.org/content/10.1101/2023.12.13.571579v1)


# Background


RNA folding is where a strand of RNA folds into a low energy state. RNA shape can help determine the RNA's function, for example:
- tRNA folding allows it to bring amino acids to the ribosome
- Ribozymes need precice folding to act like enzymes
- mRNA folding affects translation and stability

RNA has 3 primary structures:
1. Primary structure - the initial linear sequence of nucleotides (our input)
2. Secondary structure - local structures in the RNA (hairpin loops, stems, bulges, internal loop, etc)
3. Tertiary structure - the full 3D shape of the RNA

<p>
  <img src="https://github.com/hexhowells/rna-folding/blob/main/images/secondary-structs.png" height="250" />
  <br>
  <em>Common RNA secondary structures. Source: https://www.nature.com/articles/s41467-021-21194-4</em>
</p>

## RNA structure

RNA is made up of two fundamental components

 - ribose-phosphate chain (negatively charged) (makes up 2/3 the necleotides mass)
 - bases: adenine (A), uracil (U), cytosine (C), guanine (G)


# How do we model the problem?

The input of the model is the RNA nucleotide sequence, we can also use MSA data to get evolutionarily related variants of the target RNA, basically giving us more data and highlighting which nucleotides are more important.

The outupt of the model is a list of 3D coordinates for each nucleotide in the input sequence:w.


# What does the data look like?

The input data is a sequence of the 4 RNA nucleotide bases (A, U, C, G). We also get MSA files.

MSA files are evolutionarily related variants of the target RNA structure, this can be from different species, isoforms, etc. Here, the nucleotides that stay the same across these different samples, are clearly important to maintain its foundational structure. Any nucleotides that have changed, are less important or have modified the RNA's structure. If two nucleotides have changed together, it could indicate that they have co-evolved and thus if nucleotide evolves, to maintain the same structure, the other one must as well.

FASTA files are just basic file formats used to store these sequences, along with some basic metadata about the sequences, nothing too complex here.

## Current datasets

- [Stanford RNA 3D Folding](https://www.kaggle.com/competitions/stanford-rna-3d-folding/data)
- [RFDiffusion - uw_synthetic_rna_structures](https://www.kaggle.com/datasets/andrewfavor/uw-synthetic-rna-structures)
- [trRosettaRNA Training Datasets](https://yanglab.qd.sdu.edu.cn/trRosettaRNA/benchmark/)


# [paper] How to think about RNA structure

1. RNA, in its normal environement, is very social and interacts with a lot of other molecules
Unlike with protein folding, RNA bases can interact with every other base, whereas in protein folding, amino acids favour interacting with other certain amino acids.

2. RNA bases are tightly stacked and have little space between them, the helical structure of RNA is not due to Watson-Crick pairing, but by stacking-induced helical arrangments.

3. RNA structure can change over time due to environmental variables. This strcuture is dictated by a thermodynamic landscape that depends on the sequence of RNA and the conditions. Can think of it like an energy landscape, where the valleys are thermostable folds, however, the bottom of these deep valleys can have small indentations, which allow the RNA structure to wiggle and flex around this main low-energy state.

4. RNA is a compact molecule, this tight packing causes the RNA strand to adopt a seld-associating state. 

5. Watson-crick pairing isn't as important as is made out, in most cases, non-watson-crick pairs are critical for creating the teriary interactions that stabilize the confomation.

6. Watson-crick pairing is mostly important for transfering information, but less important for 3D structure. Non-watson-crick pairs can cause unstable structures initially, but are vital for overall stable tertiary structures.
