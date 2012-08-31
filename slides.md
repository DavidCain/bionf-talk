% Bioinformatics: An Introduction
% David Cain
% 2012-08-30

<!--
# What to expect?

Over the next hour or so, I'm going to deliver a survey of trending
research topics and the applications of computer science within these
fields. I'm a computer scientist by education, not a biologist, and what
I cover should reflect that. Rather than an in-depth exploration of
the biology, I'll focus on problems within these fields, and how C.S.
can produce solutions. -->

# Background

## About me
- Education
    - Colby College, 2013
    - Majors:
        * computer science 
        * economics
- Work history
    - [Sasisekharan Lab][sasisekharan-lab]: 2010 - present


# About the [Sasisekharan Lab][sasisekharan-lab]

\begin{center}
\includegraphics[width=9cm]{images/sasisekharan.png}
\end{center}

## [Discoveries][sasisekharan-news]
- [Important mutation point discovered in H1N1][H1N1-mutation]
- [Heparin contamination][heparin]

## Research
- Specializes in glycobiology
- Focus extends into multiple fields
- Multidisciplinary approach to research

## Affiliations
- Harvard-MIT Division of HST
- SMART


# What _is_ bioinformatics?

## Definition
 > "A branch of biological science which deals with the study of methods for
 > storing, retrieving and analyzing biological data."

\begin{center}
\includegraphics[width=6cm]{images/bioinformatics.jpg}
\end{center}


# Systems biology

## What is it?
 - Seeks to understand how units in a system _interact_.
 - Dynamic systems as a whole
 - Build hypotheses and construct computational models
 - Doesn't entirely fall under the classification of bioinformatics;
   it's quite multidisciplinary.


# Systems biology

\begin{center}
\includegraphics[width=7cm]{images/systemscycle.png}
\end{center}

<!-- Graphic comes from:
Systems Biology: A Brief Overview
Hiroaki Kitano, et al.
Science 295, 1662 (2002);
DOI: 10.1126/science.1069492
-->

# Systems biology

\begin{center}
\includegraphics[width=10cm]{images/fish.jpg}
\end{center}


# Systems biology

\begin{center}
\includegraphics[width=10cm]{images/ants.jpg}
\end{center}


# Systems biology

\begin{center}
\includegraphics[height=10cm]{images/fish2.jpg}
\end{center}


# Systems biology

\begin{center}
\includegraphics[width=10cm]{images/birds.jpg}
\end{center}


# Systems biology

\begin{center}
\includegraphics[width=10cm]{images/fish3.jpg}
\end{center}


# Systems biology

\begin{center}
\includegraphics[width=10cm]{images/birds2.jpg}
\end{center}


# Systems biology

## Common theme?
- [Swarm behavior][swarm-behavior]
- Swarm intelligence


# Systems biology

\begin{center}
\includegraphics[width=10cm]{images/models.png}
\end{center}


# Systems biology

## Simulators
> - [Boids][boids] -- [Craig Reynolds][craigr], 1986

## Example #2
> - Circadian rhythm

## Other applications:
> - genetic algorithms
> - simulating evolution
> - cellular subsystems

# Bioinformatics tools

\begin{center}
\includegraphics[width=10cm]{images/biopython.jpg}
\end{center}

## About Biopython

- "A set of libraries to provide the ability to deal with
  'things' of interest to biologists working on the computer."
- Package modules to address many areas within bioinformatics
- Open source, completely free/libre


# Working with Sequences

## Sequences

- A biological sequence is the result of reading a biological object (e.g. a
  protein or a string of DNA) end to end.
- Represented as a string of characters
- Characters belong to a pre alphabet
    * Protein alphabet
    * DNA/RNA alphabet


# Working with Sequences: Simple Example #1

- DNA is double-stranded
- Each side of a double helix is the complement of the other

Using Biopython:

    >>> from Bio.Seq import Seq
    >>> from Bio.Alphabet import IUPAC
    >>> dna_seq = Seq("CGATATAGGATCG", IUPAC.unambiguous_dna)
    >>> dna_seq
    Seq('CGATATAGGATAA', IUPACUnambiguousDNA())
    >>> print dna_seq.complement()
    Seq('GCTATATCCTATT', IUPACUnambiguousDNA())


# Working with Sequences: Simple Example #2

If we assume this DNA sequence to be a template strand, we can easily
find the mRNA sequence that would create the fragment:

    >>> dna_seq
    Seq('CGATATAGGATAA', IUPACUnambiguousDNA())
    >>> dna_seq.reverse_complement().transcribe()
    Seq('UUAUAUAGGAUCG', IUPACUnambiguousRNA())


# Sequence alignment

## Sequence mutation
- DNA mutation -> protein mutation
- redundancy in codon to amino acid translation
- radical changes are selected against

\begin{center}
\includegraphics[height=4cm]{images/codons.png}
\end{center}


# Sequence alignment

## Probability of mutation
- Given amino acids are more likely to transform to certain amino acids
  than they are to others.
    * Properties of codon -> amino acid code
    * Evolutionary pressures
- Substitution matrices
    * Store probability that one amino acid will mutate to another
    * Metric of evolutionary similarity


# Sequence alignment

## BLOSUM substitution matrices
- **BLO**ck **SU**bstitution **M**atrix
- Constructed with local alignments of evolutionarily divergent proteins
- Observed conserved sequence blocks to build probabilities
- Accounts for the bias given by very similar sequences
    * Threshold percent identity
    * BLOSUM62 is very good at aligning distant sequences

## Alignment
- Indels
- Gap penalties

# Sequence alignment

\begin{center}
\includegraphics[width=10cm]{images/BLOSUM62.png}
\end{center}


# Sequence alignment

## Alignment example
- Input: various H1N1 strains
- Tool: [Clustalx][clustal]

\begin{center}
\includegraphics[width=3cm]{images/clustalw.png}
\end{center}


# Finding similar sequences

## [BLAST][ncbi-blast]

- **B**asic **L**ocal **A**lignment **T**ool
- A similarity search against all known sequences
- Web services to handle BLAST queries

\begin{center}
\includegraphics[width=3cm]{images/ncbi.png}
\end{center}

- Can be run locally
- [Explanation of BLAST algorithm][blast-overview]


# Finding similar sequences: example

## Example BLAST query

- BLAST tool: [protein blast][pblast]
- Input: a subsequence of the H1N1 virus, found in 1935
- Output: evolutionarily similar sequences?


# Finding similar sequences: example

[Influenza A virus (A/Puerto Rico/8/**1934**(H1N1))]    
[Influenza A virus (A/Puerto Rico/8-JV1/**1934**(H1N1))]    
[Influenza A virus (A/Puerto Rico/8-KV7/**1934**(H1N1))]    
[Influenza A virus (A/Puerto Rico/8-KV3/**1934**(H1N1))]    
[Influenza A virus (A/Puerto Rico/8-CV6/**1934**(H1N1))]    
[Influenza A virus (A/Puerto Rico/8-JV3/**1934**(H1N1))]    
[Influenza A virus (A/Puerto Rico/8-CV10/**1934**(H1N1))]    
[Influenza A virus (A/lvPR8/**34**(H1N1))]    
[Influenza A virus (A/Alaska/**1935**(H1N1))]    
[Influenza A virus (A/Mongolia/153/88(H1N1))]     
[Influenza A virus (A/Puerto Rico/8-KV1/**1934**(H1N1))]   
[Influenza A virus (A/Puerto Rico/8-KV8/**1934**(H1N1))]   
[Influenza A virus (A/Puerto Rico/8-KV6/**1934**(H1N1))]   
[Influenza A virus (A/Puerto Rico/8-KV5/**1934**(H1N1))]   


# Secondary structure

## Structures
- Alpha helixes
    * Most common, easily predictable
    * N-H group to C=O group 4 residues earlier
- Beta sheets
    * Parallel/antiparallel
    * N-H to C=O bond

<!--Explain alpha helixes and beta sheets with PyMOL structures-->

## Obtaining secondary structure
> - `dssp`: secondary structure from a PDB file


# Mutation analysis

## Mutations
> - A few are beneficial
> - Most are benign
> - Some are *deadly*.
> - **What makes a mutation dangerous?**


# Mutations

\begin{center}
\includegraphics[width=5cm]{images/h1n1_masks.jpg}
\end{center}

## H1N1: a case study
- WHO feared a large-scale pandemic with a high death toll.
- Far fewer people died than expected.
- That might not be the case next time.
- [Important mutation point discovered in H1N1][H1N1-mutation]


# Mutation analysis

## Other major fields
- Understanding cancerous mutations

# Tertiary structure

\begin{center}
\includegraphics[width=10cm]{images/protein_structure.png}
\end{center}


# Homology modelling

## Why it's done
- Absence of structural data
- Difficulties of crystallography
- Structures conserve better among homologues

## How it's done
- Target to template
- Primary -> tertiary structure


# Homology modelling

\begin{center}
\includegraphics[width=8cm]{images/homology_backbone.jpg}
\end{center}


# Protein Docking

\begin{center}
\includegraphics[width=5cm]{images/patch_mols.png}
\end{center}

## What is docking?
- Seeks to predict strongest interactions
- Structures are fixed, conformations variable
- Parameters to customize the process:
    * active site
    * distance constraints

## Fast-evolving field
- Computationally expensive operation
- Hardware advances are changing the field
- Increasing algorithm complexity, rising success rates

# Protein Docking

## Popular algorithms:
- [PatchDock][patchdock]
- [ZDOCK][zdock]
- [HADDOCK][haddock]


# Protein Docking

## Scoring conformations
- Geometric fit
- Strength of interactions

## Measuring success
- Take real complex, split up receptor & ligand
- Feed receptor and ligand to docking software
- See how closely results match actual complex

## Example
- PDB structure [1ktr][1ktr]
- Antibody-antigen complex


# Folds

\begin{center}
\includegraphics[width=8cm]{images/fold.png}
\end{center}

## Fold prediction
- Modifying a sequence can introduce radical fold changes
- Field seeks to learn about how folds form, how to predict them


# Folds

## Crowd-sourcing, distributed computing
- Distributed computing: [SETI@home][seti-home]
    * 3 million computers run SETI@home
    * Together, they analyze radio telescope data

\begin{center}
\includegraphics[width=5cm]{images/sah_logo.jpg}
\end{center}


# Folds

\begin{center}
\includegraphics[width=11cm]{images/fah_ps3.jpg}
\end{center}


# Folds

## [Folding@Home][folding-home]
- "Help unlock the mysteries of disease"
- Advance Alzheimer's, Huntington's, and cancer research
- Gives visual feedback to current job
- Launched in 2000, has produced 100 papers
- Makes a competition out of "who can donate the most computing power"

\begin{center}
\includegraphics[width=8cm]{images/fah_logo.jpg}
\end{center}


# Folds

\includegraphics[width=10cm]{images/fah_gpu.jpg}


# Engineering, drug design

## Engineering proteins
- artifical antibodies to combat viruses
- modified viruses to actually help the body

## Relation to study of protein folding
- Fold contains the function
- Produce a drug to bind with the functional site, while maintaining a fold
  that holds its shape.


# Engineering, drug design

## Gene therapy
- Modified viruses deliver genes to human cells

\begin{center}
\includegraphics[height=5cm]{images/genetherapy.jpg}
\end{center}

<!-- Section: technical explanation -->

# Hardware

- Powerful, RAM-laden machines
- Impact of distributed computing & super computers

## GPU computing
- Folding
- Systems biology

## GPU Performance
- Cost per calculation
- Multithreading
- Overclocking
- low-level: C & assembly


# Open source

## Free vs. libre
- FOSS
- Free "as in beer" and free "as in freedom"
- copyright vs. copyleft
- [Free Software Foundation][fsf]

## Well-known libre licenses
- [GPL][gnu]
- MIT
- BSD


# Open source

## Benefits
- Facilitates collaboration in the community
- Faster rate of scientific progress
- Many eyeballs make for better code
    * Secure, transparent code
    * The Cathedral and the Bazaar

## Personal experience
- [Biopython][biopython]
    * Responsive developer community
    * Code affecting your work? Existing code flawed? Patch it.
    * Open source benefits everyone
- Why open source is important to me


# My program

## Basic properties
- All Python, interacting with third party utilities
- Medium in size and scope (approx. 6,000 lines)
- Only runs on GNU/Linux (limitation of third party tools)
- All components are free, most are libre

## Project management
 - Version controlled on Git
 - Automated testing with `unittest` framework
 - Written in Vim


# Bioinformatics tools

## Common programming languages
- Perl
- Python
- Java
- C, C++, Fortran, & Pascal (to a lesser extent)

## Open source tools:
- OBF: [Biopython][biopython], BioPerl, BioJava, BioSQL
- [PyMOL][pymol]

## Commercial tools:
- MATLAB bioinformatics toolkit
- Discovery Studio


# Online resources
- Large effort to create standalone servers, databases, etc.
- Massive, large-scale sharing of data, in the hopes of collaborative progress
- Databases of mutations, crystal structures, sequences, etc.

## Well-known databases, servers
- [BLAST][ncbi-blast]
- [SWISS-MODEL][swiss-model]
- [COSMIC][cosmic]


# Closing notes

## Importance of data structures & good design
- Time complexity is very, very important
- Big O notation- minutes vs. days
- The right data structure often makes all the difference

## Getting involved
- Low barriers to entry
- Many aspects of CS have direct applications
    * machine learning
    * database theory
    * etc.
- Many open source projects need contributors
    * [Biopython][biopython-contribute]


# Contact information

- \includegraphics[width=4.5cm]{images/email.png}
- github.com/davidcain


  [smart]: http://smart.mit.edu
  [sasisekharan-lab]: http://web.mit.edu/tox/sasisekharan/index.html
  [sasisekharan-news]: http://web.mit.edu/tox/sasisekharan/news/index.html
  [H1N1-mutation]: http://web.mit.edu/newsoffice/2011/h1n1-mutation-0309.html
  [heparin]: http://web.mit.edu/newsoffice/2008/heparin-0423.html
  
  [clustal]: http://www.clustal.org/
  [ncbi-blast]: http://blast.ncbi.nlm.nih.gov/
  [blast-overview]: http://www.ncbi.nlm.nih.gov/books/NBK1734/
  [pblast]: http://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastp&BLAST_PROGRAMS=blastp&PAGE_TYPE=BlastSearch&SHOW_DEFAULTS=on&LINK_LOC=blasthome
  
  [patchdock]: http://bioinfo3d.cs.tau.ac.il/PatchDock/
  [zdock]: http://zdock.umassmed.edu/
  [haddock]: http://TODO
  
  [muscle]: http://www.drive5.com/muscle/
  [mustang]: http://www.csse.monash.edu.au/~karun/Site/mustang.html
  
  [dssp-2]: http://swift.cmbi.ru.nl/gv/dssp/DSSP_3.html
  
  [pymol]: http://pymol.org/
  [biopython]: http://biopython.org
  [biopython-contribute]: http://biopython.org/wiki/Contributing
  
  [1ktr]: http://www.rcsb.org/pdb/explore.do?structureId=1KTR
  
  [folding-home]: http://folding.stanford.edu/
  [seti-home]: http://setiathome.ssl.berkeley.edu/
  [swiss-model]: http://swissmodel.expasy.org/
  [cosmic]: http://www.sanger.ac.uk/perl/genetics/CGP/cosmic
  
  [fsf]: http://fsf.org
  [gnu]: http://gnu.org
  
  [boids]: http://www.red3d.com/cwr/boids/
  [craigr]: http://www.red3d.com/cwr/index.html
  [swarm-behavior]: http://en.wikipedia.org/wiki/Swarm_behaviour)
