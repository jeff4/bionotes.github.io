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
## Created [this page](/startups-v-incumbents-2023a) for business notes on Generative AI (March 15, 2023)
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
* Rodney Brooks [What Will Transformers Transform](https://rodneybrooks.com/what-will-transformers-transform/)
	* 'Generative Pre-trained Transformer' models (GPT) are now the rage and have inspired Kissinger and Noam Chomsky. That sure is some hype level
	* References Wolfram's excellent explainer
	* "By the way, even since the earliest days of AI, the 1955 proposal for the 1956 workshop on AI, the document in which the term AI first appears anywhere, the goal of the researchers was to produce general intelligence. That AGI is a different term than AI now is due to a bunch of researchers a dozen or so years ago deciding to launch a marketing campaign for themselves by using a new buzz acronym. 'AGI' is just 'AI' as it was known for the first 50+ years of its existence. Hype produced the term 'AGI' with which we are now saddled."
	* Quotes unconfirmed reports that GPT-4 has 1 trillion parameters, but that has been specifically debunked by Sam Altman and others. (compared with GPT-3 with 175-billion parameters)
	* All successful systems need to have a person in the loop. 
		* "This is true of language translation systems where a person is reading the output and, just as they do with children, the elderly, and foreigners, adapts quickly to the mistakes the person or system makes, and fill in around the edges to get the meaning, not the literal interpretation."
		* "This is true of speech understanding systems where we talk to Alexa or Google Home, or our TV remote, or our car. We talk to each of them slightly differently, as we humans quickly learn how to adapt to their idiosyncracies and the forms they can understand and not understand.
		* "This is true of our search engines, where we have learned how to form good queries that will get us the information we actually want, the quickest.
		* "This is true of mobile robots in hospitals, taking the dirty sheets and dishes to be cleaned, or bringing up prescriptions from the hospital pharmacy, where there is a remote network operations center that some unseen user is waiting to take over control when the robot gets confused."
	* Amara's Law, overestimate the effect of the tech in the short run and underestimate it in the long run.
		* John McCarthy’s estimate that the computers of the 1960’s were powerful enough to support AGI 
		* Minsky and Michie and Nilsson each believing that search algorithms were the key to intelligence, 
		* Neural networks (volume 3, perceptrons) [[I wasn’t around for the first two volumes; McCulloch and Pitts in 1943, Minsky in 1953]], 
		* First order logic, Resolution theorem proving, MacHack (chess 1), fuzzy logic, STRIPS, 
		* Knowledge-based systems (and revolutionizing medicine), 
		* Neural networks (volume 4, back propagation), the primal sketch, self driving cars (Dickmanns, 1987),
		* Reinforcement learning (rounds 2 and 3), SOAR, 
		* Support vector machines, self driving cars (Kanade et al, 1997), 
		* Deep Blue (chess 2), self driving cars (Thrun, 2007), Bayesian inference, Watson (Jeopardy, and revolutionizing medicine), 
		*  Neural networks (volume 5, deep learning), Alpha GO, reinforcement learning (round 4), generative images, and now large language models. 

	* All have heralded the imminence of human level intelligence in machines. All were hyped up to the limit, but mostly in the days when very few people were even aware of AI, so very few people remember the levels of hype. I’m old. I do remember all these, but have probably forgotten quite a few…
		* "None of these things have lived up to that early hype.

## 27 March 2023
* Downloaded recent Yann LeCun slides and summer 2022 paper summarizing his proposal to approach more human/animal like learning/intelligence for machines

* Articles by [Erich Grunewald](https://www.erichgrunewald.com) from this [HN thread](https://news.ycombinator.com/item?id=35332537):
	* [Prospect for an AI Winter](https://www.erichgrunewald.com/posts/the-prospect-of-an-ai-winter/)
	* [Against LLM Reductionism](https://www.erichgrunewald.com/posts/against-llm-reductionism/)


## Created [this page](/transformer-1) dedicated to Transformers papers and tutorials
## Created [this page](/python) dedicated to setting up Python environments

## 31 March 2023
* [vicuna 13B](https://news.ycombinator.com/item?id=35378683) is an online competitor based on LLaMA 13B but with different training

## 3 April 2023
* Interesting way of explaining uncanny confidence of LLMs by Devin Coldeway 4/03 in TechCrunch article ["The Great Pretender"](https://techcrunch.com/2023/04/03/the-great-pretender/)

## 10 April 2023
*  "On Efficient Training of Large-Scale Deep Learning Models: A Literature Review" by Li Shen, Yan Sun, Zhiyuan Yu, Liang Ding, Xinmei Tian, Dacheng Tao. [arXiv link](https://arxiv.org/abs/2304.03589) and [HN thread](https://news.ycombinator.com/item?id=35513510)
* Out of curiosity, I began probing ChatGPT, Bing, and Google on how they describe the difference between 'ordinary training', pre-training, and fine tuning. See archive of my chat histories at ChatGPT to see more.
	* see also [this stackexchange answer](https://stats.stackexchange.com/questions/193082/what-is-pre-training-a-neural-network/193451#193451) which draws on this [ML glossary](https://martin-thoma.com/ml-glossary/) -- look at answers for pre-training and fine-tuning.

## 11 April 2023
* [Listing of decentralized and open-source LLMs](https://github.com/imaurer/awesome-decentralized-llm#edge-llms) from this [HN comment](https://news.ycombinator.com/item?id=35527675)
* Found on [HN thread](https://news.ycombinator.com/item?id=35527907), this open-source orchestrator and performance evaluator of multiple LLMs [PhaseLLM](https://github.com/wgryc/phasellm) and related [collaborative data community](https://phaseai.com)


## 13 April 2023
* From Seymour in Slack, George Ho's survey from a few years ago (May 2020) of using [Transformers in NLP](https://www.georgeho.org/transformers-in-nlp/)
* from [HN](https://news.ycombinator.com/item?id=35565212), [productizing mature LLM eng pipelines](https://huyenchip.com/2023/04/11/llm-engineering.html)

## 14 April 2023
* From 3/28, [Cerebras-GPT](https://www.cerebras.net/blog/cerebras-gpt-a-family-of-open-compute-efficient-large-language-models/) is a family of open, compute-efficient, LLMs, ranging from 0.11B to 13B parameters. Trained using Chinchilla formula
* A nice concise, mathematically formal description of Transformers by Mary Phuong and Marcus Hutter at DeepMind, published 7/19/2022: [*Formal Algorithms for Transformers*](https://arxiv.org/abs/2207.09238). from this [HN comment](https://news.ycombinator.com/item?id=35506069) which also had this [HN comment](https://news.ycombinator.com/item?id=35507378) about Hopf algebras, including Adam Nemecek's 2/03/2023 paper [*Coinductive guide to inductive transformer heads*](https://arxiv.org/abs/2302.01834) and the older 2012 paper [*Hopf algebras and Markov chains: Two examples and a theory*](https://arxiv.org/abs/1206.3620) and a recommendation to check out [this website](https://bivector.net) about Geometric Algebra aka Clifford Algebra. Recommend watching this 44-minut intro [YouTube video](https://www.youtube.com/watch?v=60z_hpEAtD8&t=120s)
* Dan Fu, Michael Poli, Chris Re 3/28/2023 ["From Deep to Long Learning?"](https://hazyresearch.stanford.edu/blog/2023-03-27-long-learning)
* From this [HN thread](https://news.ycombinator.com/item?id=35544851), found this article by Eugene Yan at Amazon ["Experimenting with LLMs to Research, Reflect, and Plan"](https://eugeneyan.com/writing/llm-experiments/)

## 15 April 2023
* Found another reference to this good intermediate level discussion how transformers work. [The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/) by Jay Alammar. Originally noted on 3/01.
	* See also this previous post by Jay about [Attention](https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/)
* Researchers at Allen Institute find a way to 6x the toxicity of ChatGPT. [Allen Institute blog post](https://blog.allenai.org/toxicity-in-chatgpt-ccdcf9265ae4) and [TC article](https://techcrunch.com/2023/04/12/researchers-discover-a-way-to-make-chatgpt-consistently-toxic/)
* Quote from Betaworks CEO John Borthwick: "This is the biggest change in technology in my lifetime. We’ve been building, accelerating and investing in and around machine learning for the last decade, and in the last 12 months, everything’s changed — the launch of generative visual models like [OpenAI’s] DALL-E 2 last year, the open and affordable access to these models with the availability of stability and GPT. AI has the potential to affect every sector, and every part of how we live, work, play and even die." Part of [Betaworks AI camp announcement](https://techcrunch.com/2023/04/13/betaworks-new-camp-aims-to-fund-transformative-early-stage-ai-startups/)

## 16 April 2023
* [Batch computing and AI](https://hazyresearch.stanford.edu/blog/2023-04-12-batch) and associated [HN thread](https://news.ycombinator.com/item?id=35589027) 
* New 'Consistency Models' are an upgrade over previous diffusion models for image generation and related visual tasks. [Paper](https://arxiv.org/abs/2303.01469) and [TC article](https://techcrunch.com/2023/04/12/openai-looks-beyond-diffusion-with-consistency-based-image-generator/)

## 17 April 2023
* Excellent compilation of various LLM resources by Sebastian Raschka. [Blog post](https://magazine.sebastianraschka.com/p/understanding-large-language-models) and associated [HN thread](https://news.ycombinator.com/item?id=35589756) with more resources
* Review article on ChatGPT related papers by [Zhang, Zhang, et al](https://arxiv.org/abs/2304.06488). From abstract: 'According to Google scholar, there are more than 500 articles with ChatGPT in their titles or mentioning it in their abstracts. Considering this, a review is urgently needed, and our work fills this gap. Overall, this work is the first to survey ChatGPT with a comprehensive review of its underlying technology, applications, and challenges. Moreover, we present an outlook on how ChatGPT might evolve to realize general-purpose AIGC (a.k.a. AI-generated content), which will be a significant milestone for the development of AGI.'
* [Together](https://www.together.xyz) released [RedPajama](https://www.together.xyz/blog/redpajama), a project to create 'reproducible, fully-open, leading language model. RedPajama is a collaboration between Together, Ontocord.ai, ETH DS3Lab, Stanford CRFM, Hazy Research, and MILA Québec AI Institute.'. 
	* three components: (1) Pre-training data, (2) Base models trained at scale with data from (1), and (3) Instruction tuning data and models for usability and safety
	* Released LLaMA training dataset of 1.2 trillion tokens

## 22 April 2023
* New [article by Sebastian Raschka](https://magazine.sebastianraschka.com/p/finetuning-large-language-models) with a comprehensive introduction to 'Finetuning LLMs'. Associated [HN thread](https://news.ycombinator.com/item?id=35666201)
	* Review again Jay's 2020 [Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) and his preceding [article on Attention](https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/)

## 24 April 2023
* [New paper](https://arxiv.org/abs/2304.11062) increases context window from 32k tokens for GPT-4 to 1M tokens using the Recurring Memory Transformer architecture (aka RMT). [HN thread](https://news.ycombinator.com/item?id=35682424) Point from this [HN comment]: 
	* 'For LLMs there are at least three different ways of "learning":
		1. *Pre-training* for text prediction, using unsupervised learning
		2. *Fine-tuning* e.g. to follow instructions or to reject certain queries, using supervised and/or reinforcement learning (optional)
		3. *In-context learning* using "few-shot prompts" as examples
	* 'Now the last two can have similar effects. For example, you might fine-tune a foundation (only pre-trained) model to follow instructions, or you don't and instead just modify your prompt such that it looks like a dialogue between a human and a helpful chat assistant.  But neither can replace the extensive pre-training phase, which is what gives the model all its intelligence.'
	* 'One other disanalogy between fine-tuning and in-context learning appears to be that the model can't exactly remember the data it was fine-tuned with, while it "knows" exactly everything in its context window. That is its working memory, so to speak.'

## 27 April 2023
* e2eml school's [Transformers from scratch](https://e2eml.school/transformers.html#markov_chain) nice diagrams on seq2seq etc
* Harvard SEAS Jupyter notebook [annotated version](http://nlp.seas.harvard.edu/annotated-transformer/) of original Transformer / attention-is-all-you-need paper
* arXiv paper from 3/22/2023 ['Sparks of AGI: Early experiments from GPT-4](https://arxiv.org/abs/2303.12712)
* A Cookbook of Self-Supervised Learning [paper](https://arxiv.org/abs/2304.12210) and [HN thread](https://news.ycombinator.com/item?id=35702490)

## 28 April 2023
* Shared by Yann LeCun on FB -- ['A Practical Guide for LLMs'](https://github.com/Mooler0410/LLMsPracticalGuide) with a history of taxonomic relationships between the various LLMs. Comments on FB from Yann: 
	* ‘A survey of LLMs with a practical guide and evolutionary tree.
	* ‘Number of LLMs from Meta = 7
	* ‘Number of open source LLMs from Meta = 7
	* ‘The architecture nomenclature for LLMs is somewhat confusing and unfortunate.
	* 'What's called "encoder only" actually has an encoder and a decoder (just not an auto-regressive decoder).
	* 'What's called "encoder-decoder" really means "encoder with auto-regressive decoder"
	* 'What's called "decoder only" really means "auto-regressive encoder-decoder"’
* GPT4Free - allows various projects without an OpenAI API key. Very empty [HN thread](https://news.ycombinator.com/item?id=35685512) and [project home](https://github.com/xtekky/gpt4free)
* Arxiv paper from Feb, 2023 ['Hyena Hierarchy: Towards Larger Convolutional Language Models'](https://arxiv.org/abs/2302.10866) and fragmentary [HN comment](https://news.ycombinator.com/item?id=35514579)
* ['Choose Your Weapon: Survival Strategies for Depressed AI Academics'](https://arxiv.org/abs/2304.06035) from March, 2023

## 30 April
* [A Brief History of LLaMA](https://agi-sphere.com/llama-models/) and [HN thread](https://news.ycombinator.com/item?id=35736872)
    * [this comment](https://news.ycombinator.com/item?id=35757925) indicates that [this GH repo](https://github.com/jankais3r/LLaMA_MPS) runs unquantized 7b and 13b models on an M2 GPU which means it's a little slower but much much more energy efficient.

## 01 May 2023
* [Mojo](https://www.modular.com/mojo)--a new programming language from [Chris Lattner's](https://en.wikipedia.org/wiki/Chris_Lattner), [new company Modular AI](https://www.modular.com). [HN thread](https://news.ycombinator.com/item?id=35790367)
* [Project](https://github.com/mlc-ai/mlc-llm/blob/main/README.md) to run LLMs on mobile devices and diverse hardware. 'Everything runs locally with no server support and accelerated with local GPUs on your phone and laptops. Supported platforms include: iphone/ipad, Metal GPUs and Intel/ARM MacBooks, AMD and NVIDIA GPUs via Vulkan on Windows and Linux, NVIDIA GPUs via CUDA, WebGPU on browsers through [WebLLM](https://github.com/mlc-ai/web-llm/blob/main/README.md).'
	* [HN thread](https://news.ycombinator.com/item?id=35763483) 

## 03 May 2023
* Recommended to read this nice article explaning RLHF -- ['Illustrating Reinforcement Learning from Human Feedback (RLHF)'](https://huggingface.co/blog/rlhf)

## 04 May 2023
* Two good intro articles by [Assembly AI](https://www.assemblyai.com/about):
	* [The Full Story of LLMs and RLHF](https://www.assemblyai.com/blog/the-full-story-of-large-language-models-and-rlhf/) and associated [HN thread](https://news.ycombinator.com/item?id=35803522)
	* [Intro to Generative AI](https://www.assemblyai.com/blog/introduction-generative-ai/)

## 05 May 2023
* Introductory 2021 blog post by Pinecone ['What is a Vector Database?'](https://www.pinecone.io/learn/vector-database/) and [HN thread](https://news.ycombinator.com/item?id=35826929)
* Deepgram blogpost ['Augmenting LLMs Beyond Basic Text Completion and Transformation'](https://blog.deepgram.com/augmenting-llms-beyond-basic-text-completion-and-transformation/) and [HN thread](https://news.ycombinator.com/item?id=35819613)

## 08 May 2023
* Lastest on which consumer hardware (including Apple Silicon) is effective for home training in [this comment thread](https://news.ycombinator.com/item?id=35861272) as part of this [HN post](https://news.ycombinator.com/item?id=35859344) about [RasaGPT](https://github.com/paulpierre/RasaGPT) which simplifies integration of multiple NLP, NLU, machine translation, etc using tools like Rasa, FastAPI, LangChain etc.
* Explanation of current landscape of diffusion models and why [Reflected Diffusion Models might be the next step](https://aaronlou.com/blog/2023/reflected-diffusion/) plus [HN thread](https://news.ycombinator.com/item?id=35863309)

## 15 May 2023
* [StarCoder and StarCoderBase](https://arxiv.org/abs/2305.06161) Foundation model StarCoderBase and finetuned tool called StarCoder. [HN thread](https://news.ycombinator.com/item?id=35954481)
* [Ash Vardanian](https://ashvardanian.com) implemented a 1000-line C++ vector database as announced in this short [HN thread](https://news.ycombinator.com/item?id=35803649). [Main blogpost here](https://ashvardanian.com/posts/abusing-vector-search/) and [main HN thread](https://news.ycombinator.com/item?id=35887983)

## 18 May 2023
* ACM article on [Cargo Cult AI](https://queue.acm.org/detail.cfm?ref=rss&id=3595860) and [HN thread](https://news.ycombinator.com/item?id=35991362)

## 20 May 2023
* Dialogue between [Don Knuth and Stephen Wolfram](https://cs.stanford.edu/~knuth/chatGPT20.txt) regarding Knuth's test questions to ChatGPT. [HN thread](https://news.ycombinator.com/item?id=36012360)
* Rodney Brooks says to 'calm down about GPT-4' in [IEEE](https://spectrum.ieee.org/gpt-4-calm-down) and [HN thread](https://news.ycombinator.com/item?id=36017309)
* Rich Sutton of Reinforcement Learning textbook fame and his [The Bitter Lesson](http://incompleteideas.net/IncIdeas/BitterLesson.html) reappeared on [HN](https://news.ycombinator.com/item?id=36017857)


## 22 May 2023
* New paper by Meta about how fine-tuning is much less important than pre-training ['LIMA: Less is More for Alignment'](https://arxiv.org/abs/2305.11206) -- Minimal finetuning is still effective suggesting that bulk of work is done during pre-training. Uses 65-B version of LLaMA

## 23 May 2023
* [RWKV: Reinventing RNNs in the Transformers Era](https://arxiv.org/abs/2305.13048) New paper thaT tries to rebuild RNNs to get the benefits of Transformer attention while scaling more efficiently. [PDF](https://news.ycombinator.com/item?id=36038868)
* Meta launches mutltilingual model from the prior SOTA 100 languages to [1100+ languages](https://ai.facebook.com/blog/multilingual-model-speech-recognition/)
* Sebastian Raschka has [another post up](https://magazine.sebastianraschka.com/p/why-the-original-transformer-figure) about 'Why the original transformer drawing is wrong and some other historical tidbits about LLMs'. [HN thread](https://news.ycombinator.com/item?id=36057183)

## 26 May 2023
* [HN thread](https://news.ycombinator.com/item?id=35994037) about building CLI tools to work with ChatGPT and LLMs by [Simon Willison](https://simonwillison.net/2023/May/18/cli-tools-for-llms/)
* Stanford paper on [AlpacaFarm](https://crfm.stanford.edu/2023/05/22/alpaca-farm.html) which has been RHLFed to 'beat ChatGPT-3.5'. [HN thread](https://news.ycombinator.com/item?id=36052411)
* Paper written by several AI/ML PhD students about how to do [NLP research in the age of LLMs](https://arxiv.org/abs/2305.12544) and [HN thread](https://news.ycombinator.com/item?id=36080886)

## 27 May 2023
* New paper ['QLoRA: Efficient Finetuning of Quantized LLMs'](https://arxiv.org/abs/2305.14314) and [HN thread](https://news.ycombinator.com/item?id=36064568) 

## 28 May 2023
* Good PDF ['The Little Book of Deep Learning'](https://www.fleuret.org/public/lbdl.pdf) and related [HN thread](https://news.ycombinator.com/item?id=35767789)
* FB publishes paper ['MEGABYTE: Predicting Million-byte Sequences with Multiscale Transformers'](https://arxiv.org/abs/2305.07185) with [effusive commentary](https://www.artisana.ai/articles/meta-ai-unleashes-megabyte-a-revolutionary-scalable-model-architecture) and [HN thread](https://news.ycombinator.com/item?id=36053662)
* 5/27/2023 casual [listing of AI chips](https://news.ycombinator.com/item?id=36095965) from this [HN thread 'Ask HN: What is an AI chip and how does it work?](https://news.ycombinator.com/item?id=36092831)
* a16z collects together various deep learning resources in [The AI Canon](https://a16z.com/2023/05/25/ai-canon/) and [HN thread](https://news.ycombinator.com/item?id=36072268)
* Xorvoid criticism of LLMs called ['ChatGPT: A Mental Model'](https://xorvoid.com/chatgpt_a_mental_model.html) and critical back and forth at [HN](https://news.ycombinator.com/item?id=36099822)

## 06 June 2023
* Need to investigate running LLMs locally with [ggml.ai](http://ggml.ai) which works with llama.cpp whisper, etc. Optimized for Apple Silicon. [HN thread](https://news.ycombinator.com/item?id=36215651)

## 20 June 2023
* SimpleAIchat on [GitHub](https://github.com/minimaxir/simpleaichat) -- a new and concise Python package for easily interacing with chat apps like GPT-4 with robust features and minimal code complexity. [HN thread](https://news.ycombinator.com/item?id=36393782) 

## 27 June 2023
* Lilian Weng has another detailed overview post up on her excellent blog about ['Autonomous Agents'](https://lilianweng.github.io/posts/2023-06-23-agent/). [HN thread](https://news.ycombinator.com/item?id=36488871)


## 01 July 2023
* 


