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
