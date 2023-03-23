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
* 3/15 From this [HN comment](https://news.ycombinator.com/item?id=35173577) in this [submission about LLVM](https://news.ycombinator.com/item?id=35169750), I thought about buying *Transformers for NLP: Build, train, and fine-tune deep neural network architectures with Python, PyTorch, TensorFlow, BERT and GPT-3*, 2nd edition. [Amazon link](https://www.amazon.com/Transformers-Natural-Language-Processing-architectures-ebook/dp/B09T34LVRM/ref=tmm_kin_swatch_0?_encoding=UTF8&qid=&sr=)
	* important to get the second edition!
	* as of 3/15, kindle edition is $19.59. Paperback is $37.79. Both come with free PDF.
	* 2nd edition published March 25, 2022
* [Good guide](https://sebastianraschka.com/blog/2023/llm-reading-list.html) to all the relevant papers over the last 9 years on transformers, LLMs etc. by Sebastian Raschka. Published February, 2023.
### Created [this page](/startups-v-incumbents-2023a) for business notes on Generative AI (March 15, 2023)
* Yann LeCun reposted this March 2, 2023 lecture by Professor Pascale Fung on [ChatGPT: What it can and cannot do](https://youtube.com/watch?v=ORoTJZcLXek&si=EnSIkaIECMiOmarE)
	* Watched up to 3:30 where Prof Fung describes history and mapping Shannon's model of communication to Speech Recognition and Machine Translation.
	* Source --> Transmitter/Encoder --> Channel/SpeechRecog/MachineTranslator --> Receiver/Decoder --> Destination/Output
* 3/16 Read a bit about [Noam Shazeer](https://www.linkedin.com/in/noam-shazeer-3b27288/), co-author of the first Transformer paper, worked on Google's LaMDAsystem with project leader Daniel De Freitas who is now Noam's cofounder at [Character.ai](www.character.ai)
* 3/17 [Runway](https://runwayml.com) cofounded by [Cristobal Valenzuela](https://cvalenzuelab.com) has launched a video gen product named Gen-1 using Stable Diffusion .
	* see also this [Decoder article](https://the-decoder.com/ai-startup-runway-integrates-stable-diffusion-for-text-to-video-editor/) and this [MIT Tech Review piece](https://www.technologyreview.com/2023/02/06/1067897/runway-stable-diffusion-gen-1-generative-ai-for-video/)
* 3/20 Created [new page](/foundation-model-stanford-paper-2022/) on Stanford paper "On the Opportunities and Risks of Foundation Models".
* 3/20 Found two useful articles from Lilian Weng's [blog](https://lilianweng.github.io):
	* [Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/)
	* [Updated version of Transformer Family](https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/) v2
* 3/20 Found a bunch of interesting resources re: Foundation models
	* [2023 MAD landscape](https://mattturck.com/mad2023/) posted by Matt Turck. [web version here](https://mad.firstmarkcap.com). 404's occasionally. Scroll to bottom right of blue ML+AI section to see box on Closed Source Models"
	* [Snorkel.ai intro guide](https://snorkel.ai/foundation-models/) dated March 1, 2023. 
	* Alan Thompson's Life Architect post [Inside language models](https://lifearchitect.ai/models/#summary-models) which is updated recently enough to include GPT-4 and to note that LLaMA has been leaked.
* [HN thread](https://news.ycombinator.com/item?id=35258553) about an alpaca tuned llama-7b chatbot. llama-30b coming soon. 
