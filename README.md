# rna-folding

Can we understand RNA-folding and start to figure out how to solve it?

Background
--
 - what is RNA folding?
 - how is it different to protein folding?
 - what is its purpose?

Problem
--
 - how do we model the problem?
 - what do the inputs look like?
 - what do the outputs look like?

Data
--
 - what does the data look like?
 - what datasets are currently available?

Current
--
 - what is the current state of the art in this domain?
 - are there similar domains (protein folding?) that can be applied here?


# Papers

- [Thoughts on how to think (and talk) about RNA structure](https://www.pnas.org/doi/epub/10.1073/pnas.2112677119)
- [Geometric nomenclature and classification of RNA base pairs](https://pmc.ncbi.nlm.nih.gov/articles/PMC1370104/pdf/11345429.pdf)



# Background


RNA folding is where a strand of RNA folds into a low energy state. RNA shape can help determine the RNA's function, for example:
- tRNA folding allows it to bring amino acids to the ribosome
- Ribozymes need precice folding to act like enzymes
- mRNA folding affects translation and stability

RNA has 3 primary structures:
1. Primary structure - the initial linear sequence of nucleotides (our input?)
2. Secondary structure - local structures in the RNA (hairpin loops, stems, bulges, internal loop, etc)
3. Tertiary structure - the full 3D shape of the RNA


## RNA structure

RNA is made up of two fundamental components

 - ribose-phosphate chain (negatively charged) (makes up 2/3 the necleotides mass)
 - bases: adenine (A), uracil (U), cytosine (C), guanine (G)


# [paper] How to think about RNA structure

1. RNA, in its normal environement, is very social and interacts with a lot of other molecules
Unlike with protein folding, RNA bases can interact with every other base, whereas in protein folding, amino acids favour interacting with other certain amino acids.

2. RNA bases are tightly stacked and have little space between them, the helical structure of RNA is not due to Watson-Crick pairing, but by stacking-induced helical arrangments.

3. RNA structure can change over time due to environmental variables. This strcuture is dictated by a thermodynamic landscape that depends on the sequence of RNA and the conditions. Can think of it like an energy landscape, where the valleys are thermostable folds, however, the bottom of these deep valleys can have small indentations, which allow the RNA structure to wiggle and flex around this main low-energy state.

4. RNA is a compact molecule, this tight packing causes the RNA strand to adopt a seld-associating state. 

5. Watson-crick pairing isn't as important as is made out, in most cases, non-watson-crick pairs are critical for creating the teriary interactions that stabilize the confomation.

6. Watson-crick pairing is mostly important for transfering information, but less important for 3D structure. Non-watson-crick pairs can cause unstable structures initially, but are vital for overall stable tertiary structures.
