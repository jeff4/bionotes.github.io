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
* Technology p. 73
	* Modeling p. 74
	* Training p. 81
	* Adaptation p. 85
	* Evaluation p. 91
	* Systems p. 97
	* Data p. 101
	* Security and privacy p. 105
	* Robustness to distribution shifts p. 109
	* AI safety and alignment 114
	* Theory p. 118
	* Interpretability p. 123


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
* "Great depths" or what i would say many deep layers allow these models to form powerful *hierarchical* and *distributed* representations that generalize from training data to unseen examples.
* From [Lu Lu, Pengzhan Jin, et al "DeepONet" 2019 paper](https://arxiv.org/abs/1910.03193), the universal approximation theorem states that even "multilayer perceptrons (MLP's) can represent a broad set of functions."
	* RNNs and CNNs have distinct inductive biases as subtypes of MLPs so they have optimized capacity to learn various kinds of information. 
* **Transformer Networks & Attention** [Vaswani, Shzeer, Parmar et al "Attention is all you need" 2017](https://arxiv.org/abs/1706.03762) showed that transformer networks are more powerful b/c they build on the self-attention mechanism (see [Bahdanau, Cho, Bengio "Neural machine translation by jointly learning to align and translate"](https://arxiv.org/abs/1409.0473) as well as the 2017 Vaswani Shazeer attention paper for more). Self-attention allows better capture of long-range dependencies, higher-order interactions between elements, all while enabling shorter computation paths and "provides direct means to compare elements far-across gthe input data--e.g., a pronoun and its antecedent in a sentence, or two sentences that refer to the same topic."
* From another perspective, the *multiplicative interaction* embodied in attention and gating structures (see LSTMs from Hocreiter and Schmidhuber 1997) or Mixture-of-Experts (see [Shazeer, Azalia Mirhoseini, K. Maziarz, Davis, Quoc Le, Geoffrey Hinton, and Jeff Dean "Outrageously large neural networks: The sparsely-gated mixture-of-experts layer" 2017](https://arxiv.org/abs/1701.06538)) offer a more flexible option than the more traditional, rigid, fixed-weight computation of MLPs and CNNs. 
	* In other words, attention and gating structures allow dynamic adaptation of the computation at hand.
	* See the example of a sentece like 'She ate the ice-cream with the X'. Should X = 'spoon' or 'strawberry'? Humans can figure this out based on context. 
		* An older feed-forward network would always process the above sentence in the very same manner, an attention-based modle could adapt it's computation to the input; updating the contextual representation of the word 'ate' if the prepositional phrase attachment X is 'spoon', or instead link it to the 'ice cream' if the X refers to 'strawberries.'
* **Genera-Purpose Computation**. A final notable advantage of attention over prior architectures stems from its stronger *generality* where it is not strongly tied to a particular task or domain as is the case fot he local receptive field of convultion or the sequential assumption of an RNN.
	* We hypothesize that the general-purpose nature of attention and transformers contributes to their broad applicability to a wide range of research problems and applications.
