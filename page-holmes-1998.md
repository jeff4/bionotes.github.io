---
title: Page and Holmes 1998
permalink: /page-and-holmes/
---

# [Molecular Evolution: A Phylogenetic Approach](https://books.google.com/books?id=p2lWhjuK8m8C&printsec=frontcover&source=gbs_book_other_versions_r&cad=2#v=onepage&q&f=false)
* Authors: [Roderic D. M. Page](https://en.wikipedia.org/wiki/Roderic_D._M._Page) and [Edward C. Holmes](https://en.wikipedia.org/wiki/Edward_C._Holmes)
* Blackwell Science, 1998

## Chapter 1: The Archaeology of the Genome p. 1
* Examples include Woese and Fox's work on rRNA SSU16 from 1977 etc.

## Chapter 2: Trees
#### 2.1.1 Tree terminology p 11-13
* "A **tree** is mathematical structure which is used to model the actual evolutionary history of a group of sequences or organisms. the actual pattern of historical relationships is the **phylogeny** or **evolutionary tree**" [aka *pedigree* for humans/domesticated animals or *family tree*].
* A tree consists of **nodes** connected by **branches** aka **edges**.
	* **Terminal nodes** represent sequences or organisms for which we have data; they may be either currently existing or extinct. Terminal nodes are also called **leaves**, **leaf nodes**, or **OTUs** (Operational Taxonomic Units).
	* **Internal nodes** represent hypothetical ancestors; the ancestor of all sequences that comprise the tree is called the **root** of the tree.
* A **weighted tree** is a tree whose branches are drawn such that branch length (aka edge length) imply the amount of time that has passed.
* The number of branches connected to a node indicate the **degree of the node**. For the most part, this book seems to use tree (mostly) in the computer science sense of a [rooted directional tree data structure](https://en.wikipedia.org/wiki/Tree_(data_structure)). 
* Polytomies
	* If a node has a degree greater than three (i.e., the node is connected to one ancestor node and more than 2 immediate descendant nodes), then this node is referred to as a [**polytomy**](https://en.wikipedia.org/wiki/Polytomy).
	* If a tree has no polytomies, it is referred to as **fully resolved**. 
	* Polytomies can represent two rather different situations: (1) First they may represent simlutaneous divergence–all the descendants evolved at the same time, aka a *hard polytomy*. (2) Secondly, they may represent uncertainty about phylogenetic relationships; the lineages did not necessarily all diverge at once, but we are unsure as to the actual order of divergence; this is called a *soft polytomy*.
	* Typically, polytomies are treated as soft.

#### 2.1.2 A shorthand for trees
* Uses parentheses. See JH notes, Bio #3, 1/28/2021.

#### 2.1.3 Cladograms, additive trees, and ultrametric trees
* Different kinds of tree can be used to depict different aspects of evolutonary history.
* The most basic tree is the **cladogram** aka **n-tree** which simply shows relative recency of common ancestry. For example, given three sequences A, B, and C, a cladogram shows when each sequence diverged from the other. (See Figure 2.5 on p. 14)
* **Additive trees** (aka **metric trees** aka **phylograms**)contain additional information, namely branch length or edge length. The number associated with each branch (aka edge) correspond to some attribute of the sequences, such as the amount of evolutionary change. In the example shown in Figure 2.5, sequence A has acquired four substitutions since it shared a common ancestro with sequence B. 
* **Ultrametric trees** aka **dendrograms** are a special subset of additive tree. Here, all the tips of the trees are quidistant from the root of the tree. This kind of tree can be used to depict evolutionary time, expressed directly as years or indirectly as the amount of sequence divergence using the molecular clock.

#### 2.1.4 Rooted and unrooted trees p. 16
* Cladograms and additive trees can be either rooted or unrooted.
* A **rooted tree** has one particular node identified as the root from which ultimately all the other nodes descend, hence a rooted tree has a direction. This direction corresponds to evolutionary time; the closer a node is to the root of the tree, the older it is in time.
* An **unrooted tree** does not have an explicitly named root node. However, this does not mean no root exists "in reality"; we simply don't know where to place it on the diagram. As such, there is a set of *possible* rooted variants all represented by this single unrooted tree. See Figures 2.6 and 2.7 for more detail (p. 17).
* Many methods of reconstructing phylogenies generate unrooted trees as output. In other words, the output implies many different rooted trees are possible. In order to root an unrooted tree (i.e., to decide which of the seven trees from Fig 2.7 is the correct interpretation of the unrooted tree shown in Fig. 2.6), we need some other source of information.
* Note that ultrametric trees are rooted by definition.
* See Chapter 6 for more on how to root unrooted trees.
* See Table 2.1 (p. 18) to see how many unrooted and rooted trees are possible given x number of OTUs, sequences, species, or organisms are leaf nodes.

#### 2.1.5 Tree Shape p. 18-19
* Figure 2.8 (p. 19) shows three possible **shapes** aka **topologies** for a rooted tree of five OTUs. These 5 topologies account for all 105 possible trees listed in Table 2.1.

#### 2.1.6 Splits
* Trees can be represented in a variety of ways other than as graphs. One useful representation is as a set of sets, aka **splits** aka **partitions**. Each split takes a set of OTUs and partions them into two mutually exclusive (and collectively exhaustive) sets. 
* One can think of a split as two sets of OTUs obtained by chopping ('splitting') the tree at a given branch. 
* See Figure 2.9 (p. 19) for an example.
* Only the splits that result form chopping the original tree within internal branches (*not* terminal branches) provide useful partitions.
* Chapter 6 provides some methods for reconstructing phylogenies after a split where each partition was arbitrarily assigned letters representing nucleotides.

### 2.2 Reconstructing the history of character change
* The tree relating a set of sequences tells us only part of hwat we wnat to know. The tree alone does *not* tell us when a particular evolutionary change took place or whether the occurrence of the same amino acid in two sequences is: (a) the result of inheritance from a common ancestor or (b) the result of independent evolution.
* To address these questions, we need to be able to reconstruct the history of character change. Chapter 5 delves more deeply into this topic; here is just a taste.
* Given a tree, we can distinguish between **ancestral** (aka primitive) versus **derived** character states. If an OTU has the same base as the common ancestor of all the sequences under study, then we say that OTU is in the primitive or **plesiomorphic state**. Such an ancestral character seen in an OTU is called a **plesiomorphy**. 
* If it is *not* in the ancestral state, then we say that the OTU is in the derived or **apomorphic state**. A derived character is called an **apomorphy**.
	* If an OTU has is apomorphic and it is a unique derived character state (aka a sequence that we do not see in any of ther other OTUs), then we call this unique apomorphy an [**autapomorphy**](https://en.wikipedia.org/wiki/Autapomorphy).
	* Alternately, if a derived character state is seen in multiple OTUs, then this apomorphy

## Chapter 3: Genes: Organization, Functions, and Evolution p. 37
## Chapter 4: Genes in Populations p. 89
## Chapter 5: Measuring Genetic Change p. 135
## Chapter 6: Inferring Molecular Phylogeny p. 172
## Chapter 7: Models of Molecular Evolution p. 228
## Chapter 8: Applications of Molecular Phylogenetics p. 280
