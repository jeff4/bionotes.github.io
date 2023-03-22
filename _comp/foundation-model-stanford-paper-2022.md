---
title: Foundation Model - Opportunities and Risks
permalink: /foundation-model-stanford-paper-2022/
---
# [On the Opportunities and Risks of Foundation Models](https://arxiv.org/abs/2108.07258) 
* Authors: Bommasani, Hudson, Adeli, Altman, Arora, von Arx, Bernstein, Bohg, Bosselut, et al.
* First published: August 2021
* Revised version: July 2022

## Table of Contents
* Introduction p. 3
* Capabilities p. 21
* 4.0 Technology p. 73
	* 4.1 Modeling p. 74
	* 4.2 Training p. 81
	* 4.3 Adaptation p. 85
	* 4.4 Evaluation p. 91
	* 4.5 Systems p. 97
	* 4.6 Data p. 101
	* 4.7 Security and privacy p. 105
	* 4.8 Robustness to distribution shifts p. 109
	* 4.9 AI safety and alignment 114
	* 4.10 Theory p. 118
	* 4.11 Interpretability p. 123
* 5.0 Society p. 129
	* 5.5 Economics p. 149
		* 5.5.1 Productivity p. 149
		* 5.5.2 Wage inequality p. 150
		* 5.5.3 Centralization p. 151
	* 5.6 Ethics of scale p. 152
		* 5.6.1 Homogenization and scale p. 152
		* 5.6.2 Surveillance, exclusion, and power  p. 153
		* 5.6.3 Norms p. 155
		* 5.6.4 Release and Auditing p. 157
		* 5.6.5 When not to build p. 158

## 4.0 Technology
### 4.1 Modeling p. 74
* Five key properties of a foundation model:
	1. Expressivity
	1. Scalability
	1. Multimodality
	1. Memory capacity
	1. Compositionality

#### 4.1.1 Expressivity
* Theoretical and practical capacity of a network to model the distributiuon it is trained over and ability represent it in a fleixble manner.
* **Inductive biases**
	* "Great depths" or what i would say many deep layers allow these models to form powerful *hierarchical* and *distributed* representations that generalize from training data to unseen examples.
	* From [Lu Lu, Pengzhan Jin, et al "DeepONet" 2019 paper](https://arxiv.org/abs/1910.03193), the universal approximation theorem states that even "multilayer perceptrons (MLP's) can represent a broad set of functions."
		* RNNs and CNNs have distinct inductive biases as subtypes of MLPs so they have optimized capacity to learn various kinds of information. 
* **Transformer Networks & Attention** [Vaswani, Shzeer, Parmar et al "Attention is all you need" 2017](https://arxiv.org/abs/1706.03762) showed that transformer networks are more powerful b/c they build on the self-attention mechanism (see [Bahdanau, Cho, Bengio "Neural machine translation by jointly learning to align and translate"](https://arxiv.org/abs/1409.0473) as well as the 2017 Vaswani Shazeer attention paper for more). Self-attention allows better capture of long-range dependencies, higher-order interactions between elements, all while enabling shorter computation paths and "provides direct means to compare elements far-across gthe input data--e.g., a pronoun and its antecedent in a sentence, or two sentences that refer to the same topic."
* From another perspective, the *multiplicative interaction* embodied in attention and gating structures (see LSTMs from Hocreiter and Schmidhuber 1997) or Mixture-of-Experts (see [Shazeer, Azalia Mirhoseini, K. Maziarz, Davis, Quoc Le, Geoffrey Hinton, and Jeff Dean "Outrageously large neural networks: The sparsely-gated mixture-of-experts layer" 2017](https://arxiv.org/abs/1701.06538)) offer a more flexible option than the more traditional, rigid, fixed-weight computation of MLPs and CNNs. 
	* In other words, attention and gating structures allow dynamic adaptation of the computation at hand.
	* See the example of a sentece like 'She ate the ice-cream with the X'. Should X = 'spoon' or 'strawberry'? Humans can figure this out based on context. 
		* An older feed-forward network would always process the above sentence in the very same manner, an attention-based modle could adapt it's computation to the input; updating the contextual representation of the word 'ate' if the prepositional phrase attachment X is 'spoon', or instead link it to the 'ice cream' if the X refers to 'strawberries.'
* **General Purpose Computation**. A final notable advantage of attention over prior architectures stems from its stronger *generality* where it is not strongly tied to a particular task or domain as is the case fot he local receptive field of convultion or the sequential assumption of an RNN.
	* We hypothesize that the general-purpose nature of attention and transformers contributes to their broad applicability to a wide range of research problems and applications.
	* Tradeoff between task-specialization and expressivity. 
		* Models with stronger structural priors can leverage them to improve sample efficiency on the particular tasks that benefit from these assumptions.
		* Conversely, models that interate weaker inductive biases learn more slowly--BUT can scale to higher volumes of data and adapt to a more diverse set of domains
		* JH observation: tradeoff between specialization/speed of learning *versus* breadth/diversity of domains/BUT longer to train, requires more data and more diverse data
		* "As data and compute become more accessible, we observe that the exploratin of models with a minimal set of inductive biases that can 'let the data speak for itself', seems to serve as a more promising approach for progress."	
	* Expansion of foundation models beyond language domain to modalities like structural, perceptual, and reasoning.



#### 4.1.2 Scalability
* Scalability across models' depth, width, as well as their training time, number of parameters, and amount of data they can process.


#### 4.1.3 Multimodality



#### 4.1.4 Memory



#### 4.1.5 Compositionality



#### 4.1.6 Summary


### 4.2 Training


#### 4.2.1 Goals of training objectives


#### 4.2.2 Design trade-offs in current SSL methods
* Current self-supervised learning (SSL)


#### 4.2.3 Paths forward


### Adaptation

#### 4.3.1 Methods for foundation model adaptation
* Factor 1: Compute budget
* Factor 2: Data availability
* Factor 3: Access to foundation model gradients


#### 4.3.2 Use cases for adaptation

#### 4.3.3 A long-term goal for foundation model adaptation research

### 4.4 Evaluation

#### 4.4.1 Introduction

#### 4.4.2 Intrinsic evaluation

#### 4.4.3 Extrinsic evaluation and adaptation

#### 4.4.4 Evaluation design

#### 4.4.5 Takeaways

### 4.5 Systems

#### 4.5.1 Improving performance through co-design

#### 4.5.2 Automated optimization

#### 4.5.3 Execution and programming models

#### 4.5.4 Productionization of foundation models

### 4.6 Data

#### 4.6.1 Data management desiderata

#### 4.6.2 Data Hub Solution

### 4.7 Security and privacy

#### 4.7.1 Risks

#### 4.7.2 Opportunities

### 4.8 Robustness to distribution shifts

#### 4.8.1 Advantages

#### 4.8.2 Persistent challenges

#### 4.8.3 Opportunities

### 4.9 AI Safety and Alignment

### 4.10 Theory

#### 4.10.1 Theoretical formulations and modularizations

#### 4.10.2 Why is the pretraining-adaptation interface interesting?

#### 4.10.3 Challenge: analysis of in-context learning and other emergent behavior

#### 4.10.4 Challenge: appropriate data assumptions and mathematical tools

### 4.11 Interpretability

#### 4.11.1 Characterizing behavior

#### 4.11.2 Explaining behavior

#### 4.11.3 Characterizing model mechanisms

#### 4.11.4 Impacts of non-interpretability and interpretability

### 5.5 Economics
* *General-purpose technology* (Bresnahan and Trajtenberg, 1995) is a term use by economists to refer to things like the steam engine, electricity. JH: 'stacking technology', like the microprocessor, the web, printing press.

#### 5.5.1 Productivity and innovation

#### 5.5.2 Wage inequality

#### 5.5.3 Centralization

#### 5.5.4 Other considerations

#### 5.6.5 When not to build
