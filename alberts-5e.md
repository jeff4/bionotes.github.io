---
title: MBOC Alberts 5th Edition
permalink: /alberts-5e/
---


# Molecular Biology of the Cell
* MBOC, Fifth Edition (2008)
* Authors: Bruce Alberts, Alexander Johnson, Julian Lewis, Martin Raff, Keith Roberts, and Peter Walter

## Chapter 1: Cells and Genomes
* p. 20 - defintion of **homologs**: All related genes that result from duplication 
	* Duplicate genes that are conserved in two branches after speciation are called **orthologs**
	* Duplicate genes within a single genome are **paralogs**
	* Orthologs and paralogs are subsets of the larger containing set of homologs
* **Dehydration Synthesis** (aka Condensation Synthesis) vs. **Hydrolysis**. See Alberts 5e Fig. 2-64 and 2-65 on p. 85, Alberts 5e Fig. 2-19 on p. 57, and JH handwritten notes (8/22/2020)

## Chapter 2: Cell Chemistry and Biosynthesis
### 10 Steps of Glycolysis
* Glycolysis converts glucose to pyruvate in 10 steps. 
* For more details, see JH handwritten notes August 7-13, 2020,  Alberts p. 120-121 (Panel 2-8), and [this page](/glycolysis). 

## Chapter 3: Proteins
* See p. 127-129 to see tables and panels of categories of polar vs. nonpolar sidechain/amino acids, acidic vs. basic sidechains, etc.

## Chapter 4: Chromosome Structure and Genomes
* Avg. size of a human gene is ~27,000 bp including both introns and exons. However, avg size of genes is only 1300 bp when all the introns are thrown out.  (p. 206) 
* See other interesting stats on human genes in Table 4-1 on p. 206.
* [Shared synteny](https://en.wikipedia.org/wiki/Synteny#Shared_synteny) aka conserved synteny = not only are DNA sequences / genes conserved, but the exact order of these genes are conserved across species (p. 207). 
* Three specialized DNA sequences are special on the chromosome: (1) [origin of replication](https://en.wikipedia.org/wiki/Origin_of_replication); prokaryotes have 1 origin per chromosome while eukaryotes have multiple ori's; (2) [centromere](https://en.wikipedia.org/wiki/Centromere); (3) [telomere](https://en.wikipedia.org/wiki/Telomere).


## Chapter 5: DNA Replication and Repair
*  DNA structure on Panel 2-6 Alberts p. 116-17 and Figure 4-4 and 4-5 on p. 198-199. See also JH handwritten notes August 25-29, 2020.
* Mutation rates in DNA are surprisingly low across multiple genera. It is about 1 mutation in 10<sup>9</sup> in both *E. coli* and *C. elegans* aka 1 base pair change per 1 billion bp. In addition, more indirect methods in humans using fibrinopeptides, fibrinogen, and fibrin formation during blood clotting have also produced a similar 1 in a billion figure (p. 264-265).
* See Table 5-1 on p. 271 to see how the 3 different error correcting mechanisms of 5'&#8594; 3' polymerization, 3'&#8594; 5' exonuclease proofreading, and strand-directed mismatch repair together combine to provide a 1 error per 10<sup>9</sup> bp during DNA replication.
* [DNA Polymerase I](https://en.wikipedia.org/wiki/DNA_polymerase_I) was discovered by Arthur Kornberg in 1956 ( p. 266)
* [Okazaki fragments](https://en.wikipedia.org/wiki/Okazaki_fragments) discovered in mid- to late-1960s in Japan. This along with other evidence disproved earlier hypothesis that DNA polymerases could act in both 5'&#8594; 3' and in the 3'&#8594; 5' direction.

### Proofreading mechanisms during and post replication
1.  ***Delay* between initial base pair hydrogen bonding and permanent phosophodiester covalent bonding**. First, a free nucleotide base pairs with the template DNA strand via hydrogen bonding. Obviously, the correct nucleotide is energetically more favorable. However, DNA polymerase is like a right hand whose fingers must tighten for the next step: covalently creating the phosphodiester bond on the backbone. It's hard to do that with the wrong nucleotide. So even if the wrong nucleotide slips in for step 1a, it's hard to "permanently" lock it in with the "finger-closing step". (p. 269 and Fig 5-4b)
1. [**Exonucleolytic proof-reading**](https://en.wikipedia.org/wiki/Exonuclease) that excise nucleotides dNMP (aka 2'-**d**eoxyribose **N**ucleotide **M**ono **P**hosphates) one at a time from the new daughter strand. The exonuclease is actually a separate catalytic site on DNA polymerase. DNA Poly "absolutely requires a previously formed base-paired 3'-OH end of the primer strand." If the wrong dNMP is at the end of the daughter strand, the exonuclease is engaged and excised in the opposite 3'&#8594; 5' direction from the Poly's regular growing 5'&#8594; 3' direction.  (See Fig. 5-8 and 5-9 on p. 270.)
1. **Strand-Directed Mismatch Repair System** which is a post-replication complex that catches errors missed in the initial multi-enzyme replication machine. This system finds mismatched base-pairs between a template and daughter strand. How does it know which is the template and which is the new strand? 
	* In prokaryotes like E.coli, by looking for unmethlyated A's. In bacteria, new strands eventually get all the A's in the sequence *GATC* methylated. Fresh new daughter strands have not gotten their A's methylated so that is the strand that is corrected. (p. 276-277)
	* Eukaryotes rarely (never?) have their A's methylated. Fresh, new daughter strands are identified because they have frequent ss nicks where ligase has not performed it's function.

### Why is DNA growth only in the 5'&#8594; 3' direction?
For answer, see Fig. 5-10 p. 271

### Multi-enzyme Replication Complex per Alberts Fig. 5-19
* See p. 276 **Fig 5-19**...
* **DNA helicase** to cut / unwind DNA template strands at the beginning of the replication fork
* **Primase** to put down RNA primers. Used in leading strand once but used over and over again in the lagging strand.
* **DNA Polymerase** that both adds new nucleotides and has an exonuclease catalyic site to remove mismatches
* **Sliding clamp** and **clamp loader** to keep DNA Poly machinery attached to template strand
* [**Single-Stranded DNA Binding Protein**](https://en.wikipedia.org/wiki/Single-strand_DNA-binding_protein) (aka SSB) used only on the lagging strand 
* **Ligase** used on lagging strand to stitch together the various Okazaki fragments and to replace RNA primers with proper DNA segments.
* Also two other items:
	* topo I and topo II to relieve DNA helix torsion ahead of the replication fork.
	* strand-directed mismatch repair, keyed to unmethylated A nucleotides in GATC sequences.
* [A more technical anatomy of the replisome](https://en.wikipedia.org/wiki/DNA_polymerase_III_holoenzyme#Components) can be found on the Wikipedia entry for *E. coli* [Pol III](https://en.wikipedia.org/wiki/DNA_polymerase_III_holoenzyme)

### Major enzymes involved in DNA Replication per Lander lecture
* Helicase to make the initial cut to start the replication fork
* Primase to add short RNA primers as a starting point for DNA Polymerase
* DNA Polymerase and associated Exonuclease catalytic sites
* Ligase to join together short Okazaki fragments on the lagging strand
* Topoisomerase I and II that moves ahead of the replication fork and relieving the coil tension created by unwinding the double helix. [Topo I](https://en.wikipedia.org/wiki/Type_I_topoisomerase) creates a single strand nick while [Topo II](https://en.wikipedia.org/wiki/Type_II_topoisomerase) is a  gate-folded enzyme that moves strands past each other with a controlled cut and rejoin of one strand. See also p. 278-280.

### Right-handed structure of Polymerase
* Per [this link](https://microbenotes.com/dna-polymerase/), all DNA polymerases have  three domains:
	1. The "thumb" binds to the DNA substrate
	2. The "fingers" recognize specific nucleotides and performs the base-pair hydrogen bonding
	3. The "palm" contains the catalytic sites. (I think this means the "P" catalytic site for the phosphodiester covalent bond extending the DNA backbone and the "E" catalytic site for proofreading and exonuclease for incorrect nucleotides that have been accidentally attached.)

### Different types of DNA Polymerase
#### Prokaryotic DNA Polymerase
* [Pol I](https://en.wikipedia.org/wiki/DNA_polymerase_I) - first polymerase discovered by Arthur Kornberg in 1956. ["Pol I accounts for 95% of the polymerase activity in *E. coli*"](https://en.wikipedia.org/wiki/DNA_polymerase#Pol_I) but not primarily in replication. Removes RNA primers on the lagging strand and replaces them with DNA to connect Okazaki fragments. [According to Wikipedia](https://en.wikipedia.org/wiki/DNA_polymerase_I#Function), Pol I has 4 functions:
	1. Most important replication function: forward 5'&#8594; 3' replacement of RNA with proper DNA daughter sequences. This all takes place on the lagging strand and  connects Okazaki fragments, waiting only for ligase to seal everything up to finish the job.
	2. Proofreading in the reverse 3'&#8594; 5' direction using exonuclease site.
	3. Forward exonuclease 5'&#8594; 3' to mediate nick translation during DNA repair. 
	4. Very low usage forward 5'&#8594; 3' RNA-dependent polymerase activity.
* [Pol II](https://en.wikipedia.org/wiki/DNA_polymerase#Pol_II) was discovered in 1970 by Thomas Kornberg and there is 5x more abundant in E. coli cells as compared to Pol III. 
	* The activity of Pol II is still under debate but it seems to be a backup molecule for replication when Pol III stalls out. 
	* Pol II seems to preferentially work on the lagging strand. 
	* Pol II important to the *E. coli* [SOS induction](https://en.wikipedia.org/wiki/SOS_response) cellular repair system. 
	* Part of Famiy B like eukaryotic polymerases like Pol B, Pol alpha(&#945;), Pol delta (&#948;), Pol epsilon (&#949;).  
* [Pol III](https://en.wikipedia.org/wiki/DNA_polymerase#Pol_III)
	* Although lowest in apparent concentration and activity, Pol III is by far the most important polymerase used in bacterial DNA replication. 
	* Because of the action of it's associated sliding camp, this polymerase works incredibly, fast, moving through nucleotides at a 1000x rate compared to other polymerases.
	* Like Pol II, discovered in 1970 by Thomas Kornberg.
	* Member of Family C. Moves in the usual  5'&#8594;  3' direction for replication and moves backwards in the 3'&#8594;  5' direction for exonuclease action.
	* Has 3 components: (1) the pol III core, (2) the [beta sliding clamp](https://en.wikipedia.org/wiki/DNA_clamp) processivity factor, and (3) the sliding clamp loader. The clamp loader is responsible for both attaching the clamp to the DNA strand and removing the clamp. A sliding camp molecule can only be attached to *either* a clamp loader complex *or* a polymerase molecule, but *not both* at the same time.  
* [Pol IV](https://en.wikipedia.org/wiki/DNA_polymerase#Pol_IV) –involved in *E. coli* [SOS response](https://en.wikipedia.org/wiki/SOS_response) cellular repair system
* [Pol V](https://en.wikipedia.org/wiki/DNA_polymerase#Pol_V) –involved in *E. coli* [SOS response](https://en.wikipedia.org/wiki/SOS_response) cellular repair system
* [Family D](https://en.wikipedia.org/wiki/DNA_polymerase#Family_D)

#### Eukaryotic DNA Polymerase
* Polymerases alpha (&#945;), delta (&#948;), and epsilon (&#949;) - part of Family B
	* [Polymerase delta (&#948;)](https://en.wikipedia.org/wiki/DNA_polymerase_delta) is probably the eukaryotic equivalent of Pol III in bacteria because polymerase delta (&#948;) also has an associated sliding clamp called [PCNA](https://en.wikipedia.org/wiki/Proliferating_cell_nuclear_antigen). Per the [DNA Clamp Wikipedia article](https://en.wikipedia.org/wiki/DNA_clamp), [PCNA is highly conserved](https://en.wikipedia.org/wiki/DNA_clamp#Eukaryote) across the animal, fungi, and plant kingdoms. 
* Polymerase beta (&#946;) used in DNA repair
* Polymerase lambda (&#955;), sigma (&#963;), and mu (&#956;) and TdT
* Polymerases eta (&#951;), iota (&#953;), and kappa (&#954;)
* Polymerases Rev1 and zeta (&#950;)
* Polymerases gamma (&#947;) is used in mitochondria. theta (&#952;), and nu (&#957;)
* Reverse Transcriptase
* Telomerase

#### 7 families of DNA polymerase
* **Family A** - **Pol I** and has 2 exonuclease domains (goes in both directions 5'&#8594; 3' and 3'&#8594; 5')
* **Family B** - **Pol II** for proofreading
* **Family C** - Prokaryotic only, e.g. **Pol III** Standard workhorse for primary *E. coli* transcription
* Family D ([Archaea](https://en.wikipedia.org/wiki/Archaea))
* Family X - Eukaryotic only
* Family Y 
* Family RT - viruses, retroviruses, and Eukaryotes, e.g., telomerase
