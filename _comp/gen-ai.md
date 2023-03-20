---
title: Generative AI
permalink: /gen-ai/
---

## 2023 Log
* 2/09 - Got stable diffusion working on the Mac Studio and documented all the steps.
* 2/12 - Review Goodfellow, Bengio, and Courville on history of autoencoders
* 2/13 - more GBC on autoencoders, refers to GOFAI/symbolic approach as "knowledge base" approach. But I think KB was really an 80s subset of symbolic overall approach.
* 2/21 - read [Stephen Wolfram](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/) and [Murray Shanhan](https://arxiv.org/abs/2212.03551) Feb 2023 articles on LLM
* 2/23 - more articles on history of BERT, transformers, MUM, etc.
	* This 18 minute [YouTube video](https://youtu.be/wi0M2J4uE5I) by Mean Gene Hacks compares 3 LLMs that all have about 175 B parameters: OpenAI's GPT-3, BigScience's BLOOM, and Facebook's OPT-175 
* 2/24 - Today, [FB released LLaMA](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/) (Large Langauge Model Meta AI) in 4 sizes 7 billion parameters, 13 billion parameters, 33B parameters, and 65B parameters. Yann LeCun claims that LLaMa-13B outperforms GPT-3 (even though the latter has 175B). And LLaMA-65B is competitive with the best models like Chinchilla70B and PaLM-540B.
* 2/26 - Mt. AI / volcanic island / infiinite skycraper. Elevators vs. Staircases
* 3/01 - Links on BERT and AI
	* From Weights and Biases. [An Introduction to BERT and How to Use It](https://wandb.ai/mukilan/BERT_Sentiment_Analysis/reports/An-Introduction-to-BERT-And-How-To-Use-It--VmlldzoyNTIyOTA1) by Mukilan Krishnakumar.  Good simple diagrams here.
	* [Transformers Explained, Understanding the Model Behind GPT-3, BERT, and T5](https://daleonai.com/transformers-explained) from May 2021. Gets quite detailed with the math etc.
	* Towards Data Science article. A little simple but still useful intro from July 2022. Evolution of Large Language Models–BERT, GPT3, MUM and PaML. Unfortunately uses up a member-only medium article. Here is the [Box link](https://app.box.com/s/icufqddckrr9o2x3hrpyogah6ekaz513).
	* Good diagrams at intermediate level going pretty in-depth into how transformers work. [The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/) by Jay Alammar.

* 3/03 - Adam Gopnik [New Yorker](https://www.newyorker.com/culture/cultural-comment/what-can-ai-art-teach-us-about-the-real-thing) article on DALL-E
* 3/05 - Walter Benjamin [1936 essay](https://en.wikipedia.org/wiki/The_Work_of_Art_in_the_Age_of_Mechanical_Reproduction) "The Work of Art in the Age of Mechanical Reproduction" ([pdf link](https://web.mit.edu/allanmc/www/benjamin.pdf))
* 3/06 - Werner Schweibenz 2018 essay ["The Work of Art in the Age of Digital Reproduction"](https://www.researchgate.net/publication/329941032_The_Work_of_Art_in_the_Age_of_Digital_Reproduction?enrichId=rgreq-1a7b17a5c17c75f568d1cac896f5c87b-XXX&enrichSource=Y292ZXJQYWdlOzMyOTk0MTAzMjtBUzoxMDU4ODEzNjYyNzQ0NTgxQDE2Mjk0NTIyNTcyNzU%3D&el=1_x_2&_esc=publicationCoverPdf) in *Museum International* 
* 3/06 William J. Mitchell [*The Reconfigured Eye: Visual Truth in the Post-Photographic Era*](https://mitpress.mit.edu/9780262132862/the-reconfigured-eye/) 1992
* 3/07 links to commentary on papers related to Episode 5. I wrote some notes and created specific webpages for each of the following papers:
	* Adam Gopnik 2023 [article](/gopnik-2023-dalle/)
	* Walter Benjamin [1936](/benjamin-1936/) 
	* Werner Schweibenz [2018](/schweibenz-2018/)
* 3/11 Exciting! See this [Hacker News thread](https://news.ycombinator.com/item?id=35100086) about running FB's latest LLaMA locally on Apple Silicon 
	* This is the [github repo](https://github.com/ggerganov/llama.cpp) with relevant stuff by ggerganov
	* Super useful [notes by Simon Willison](https://til.simonwillison.net/llms/llama-7b-m2) who got the 7B version running on a M2 MacBook Pro with 64GB of RAM. From this [comment](https://news.ycombinator.com/item?id=35105321) in the same HN thread. 
	* applied to allowed to download the 250GB collection of all 4 models.
* 3/12 Success! dali etc
* 3/15 From this [HN comment](https://news.ycombinator.com/item?id=35173577) in this [submission about LLVM](https://news.ycombinator.com/item?id=35169750), I thought about buy Transformers for NLP: Build, train, and fine-tune deep neural networm architectures with Python, PyTorch, TensorFlow, BERT and GPT-3, 2nd edition. [Amazon link](https://www.amazon.com/Transformers-Natural-Language-Processing-architectures-ebook/dp/B09T34LVRM/ref=tmm_kin_swatch_0?_encoding=UTF8&qid=&sr=)
    * important to get the second edition!
    * as of 3/15, kindle edition is $19.59. Paperback is $37.79. Both come with free PDF.
    * 2nd edition published March 25, 2022
* [Good guide](https://sebastianraschka.com/blog/2023/llm-reading-list.html) to all the relevant papers over the last 9 years on transformers, LLMs etc. by Sebastian Raschka. Published February, 2023.
* 3/16 Read a bit about [Noam Shazeer](https://www.linkedin.com/in/noam-shazeer-3b27288/), co-author of the first Transformer paper, worked on Google's LaMDAsystem with project leader Daniel De Freitas who is now Noam's cofounder at [Character.ai](www.character.ai)
* 3/17 [Runway](https://runwayml.com) cofounded by [Cristobal Valenzuela](https://cvalenzuelab.com) has launched a video gen product named Gen-1 using Stable Diffusion .
    * see also this [Decoder article](https://the-decoder.com/ai-startup-runway-integrates-stable-diffusion-for-text-to-video-editor/) and this [MIT Tech Review piece](https://www.technologyreview.com/2023/02/06/1067897/runway-stable-diffusion-gen-1-generative-ai-for-video/)


### Stanford paper
* Published July 2022
* [On the Opportunities and Risks of Foundation Models](https://arxiv.org/abs/2108.07258)
* Authors: Rishi Bommasani, Drew A. Hudson, Ehsan Adeli, Russ Altman, et al.
* Originally published summer 2021, updated July 2022.
* Table of Contents
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
