---
title: Transformer notes
permalink: /transformer/
sitemap: false
---

### March 29, 2023
* Tutorials to consider going through
	* [Whisper.cpp](https://github.com/ggerganov/whisper.cpp) by George Gerganov. Speech to text on Apple Silicon.
	* Andrej Karpathy's build GPT from scratch [2-hour video](https://www.youtube.com/watch?v=kCc8FmEb1nY&t=13s)
		* Description: 'We build a Generatively Pretrained Transformer (GPT), following the paper "Attention is All You Need" and OpenAI's GPT-2 / GPT-3. We talk about connections to ChatGPT, which has taken the world by storm. We watch GitHub Copilot, itself a GPT, help us write a GPT (meta :D!) . I recommend people watch the earlier makemore videos to get comfortable with the autoregressive language modeling framework and basics of tensors and PyTorch nn, which we take for granted in this video.'
	* Prior videos on makemore

### March 30, 2023
* See also [page on python setup](/python)

## September 2023
### Thoughts on Transformer article
* Wikipedia article
* Original 2017 Attention is All You Need paper

### Thoughts on Llama and Llama 2 
* [Wikipedia article](https://en.wikipedia.org/wiki/LLaMA)
* [Anyscale article from August 2023](https://www.anyscale.com/blog/llama-2-is-about-as-factually-accurate-as-gpt-4-for-summaries-and-is-30x-cheaper)
* [QLora paper](https://arxiv.org/abs/2305.14314) also discusses Guanaco. Simon Willison's [HN comment](https://news.ycombinator.com/item?id=36064845): 'I'm very impressed at the quality of Guanaco 33B, the model that accompanies this paper.  You can try it out here at HuggingFace.'
* August 11, 2023 [blog-post by anyscale](https://www.anyscale.com/blog/fine-tuning-llama-2-a-comprehensive-case-study-for-tailoring-models-to-unique-applications) about 'Fine-tuning Llama-2: A comprehensive case study for tailoring models to unique applications'
	* [HN thread](https://news.ycombinator.com/item?id=37090632)
	* [top hn comment](https://news.ycombinator.com/item?id=37091097) has links to YouTube live-coding stremas where he builds a single Colab. Videos for fine-tuning Llama and qlora fine-tuning. Comment by [Jared Wright](https://news.ycombinator.com/user?id=jawerty) and his Youtube Channel: https://www.youtube.com/@jaredthecoder
	* [HN comment](https://news.ycombinator.com/item?id=37091602): 'Fine tuning for training the model to perform a new task, RAG for adding knowledge. e.g., one could fine tune the model to train it to code in a language it hasn't seen before, RAG will not really help with that.' 
	* [HN comment](https://news.ycombinator.com/item?id=37092802) talks about the Anyscale 'Fine tuning = form, not facts' blogpost.
		* Leads to this commentary
		* This 7/17/2023 [substack rant](https://zzbbyy.substack.com/p/why-you-need-rag-not-finetuning)
	* [HN comment](https://news.ycombinator.com/item?id=37091586): You can easily train Llama 2-7B on an RTX 3060 (12GB VRAM) for qlora / 4bit / GPTQ finetuning.

### Some Llama 2 links from comp-notes Sept 20
* 7/27 [article by Lucas Pauker](https://lucaspauker.com/articles/llms-unleashed-the-power-of-fine-tuning) Some explanations on how to fine-tune a model and performance of pre-training vs fine-tuning.
	* Comment by [Jeremy Howard}(https://news.ycombinator.com/item?id=36900969) and progress of what GPT and BERT did in terms of simplifying fine-tuning. From this [HN thread](https://news.ycombinator.com/item?id=36896710)
* 8/01 [article by Ollama](https://ollama.ai/blog/run-llama2-uncensored-locally) about how an uncensored locally running version of Llama-2 compares. [HN thread](https://news.ycombinator.com/item?id=36973584) with relevant [top comment](https://news.ycombinator.com/item?id=36975031)

### Glossary
* [PEFT](https://www.leewayhertz.com/parameter-efficient-fine-tuning/) = Parameter-Efficient Fine-Tuning.
* [RAG](https://research.ibm.com/blog/retrieval-augmented-generation-RAG) = Retrieval-Augmented Generation. From IBM: 'RAG is an AI framework for retrieving facts from an external knowledge base to ground large language models (LLMs) on the most accurate, up-to-date information and to give users insight into LLMs' generative process.'

### List of chatbots available
* ChatGPT
* Google BARD
* Microsoft Bing Chat
* Phind.com - for developers
* Pi by Inflection AI
* Sizzle (math) see [TC article](https://techcrunch.com/2023/09/20/former-meta-ai-vp-debuts-sizzle-an-ai-powered-learning-app-and-chatbot/)
* Claude by Anthropic
* Poe by Quora
* ['Chinese users can finally try their homegrown ChatGPT equivalents'](https://techcrunch.com/2023/08/31/chinese-users-can-finally-try-their-homegrown-chatgpt-equivalents/)
	* Ernie Bot by Baidu
	* Doubao by ByteDance
	* Baichuan by the founder of Sougou

### 9/30 notes
* Straightforward and simple on fine-tuning and LLMs overall[IBM video](https://www.youtube.com/watch?v=T-D1OfcDW1M)
	1. Critical point. RAG is a small data store that is quick and easy to update with new information without having to retrain the whole foundation model. 
	1. It can also be clearer about what source it is using for a given fact. and if there are no good sources to back it up, the LLM is instructed to not be as confident or simply say i don't know or that there are not good sources about this.
* more general [IBM video](https://www.youtube.com/watch?v=hfIUstzHs9A) explaining relationship between Foundation Models vs. LLMs vs. other types of models. Outline this 9 minute video

### Video: [How are LLMs trained?](https://www.youtube.com/watch?v=VPRSBzXzavo) by Ari Seff
1. 45 seconds in, InstructGPT was a forerunner to ChatGPT. See this [March 2022 paper](https://arxiv.org/abs/2203.02155) by Ouyang, Wu et al "Training language models to follow instructions with human feedback"
1. Three steps in building in LLM that sequentially improve aka 'fine-tune' the model.
	1. Generative pretraining with a large corpus of unsupervised data
	1. Fine-tuning with instruction, ground-truth labelled q+a pairs
	1. RLHF 
1. What is a language model? (1:49)
	* "A language model is just a special case of an autoregressive sequence model. Aka, given some history of observed variables, where history is specified by variables *x<sub>1</sub>,... x<sub>t</sub>*, what is the value of the next element *x<sub>t+1</sub>*?
	* During training, we adjust the value of the parameters for next element *X<sub>t+1</sub>* such that it more accurately models the 'ground truth' value of *x<sub>t+1</sub>*.
	* This sequence prediction technique has been used in many domains such as audio waveforms, chemical structure prediction (e.g., structures of organic molecules)
	* In the specific example of language models, each of the variables *x<sub>1</sub>,... x<sub>t</sub>* is referred to as a *token*. A token can represent a whole word or just a portion of a word.  
	* Uses the example of the sentence "Alice painted her house `X`". Given history *h*, `X` may taken on any of these values = ['brown', 'beige', 'red', 'because', 'with',...]. Each of these options has its own probability.
	* Language models are agnostic to model architecture. But since the 2017 "Attention is all you need" paper, most language models are huge transformer models with billions of parameters
1. Transformer models since 2017
	* Example models include GPT3 (2020), PaLM (2022) from Google.
	* History that is used to condition the next token prediction only has a limited window, aka context length. For example, the underlying LLM for GPT-3 can attend to a history of about 3000 words. Long enough for short conversations but not long enough for generating a novel.
1. Why is this not enough? Why do we need fine-tuning?
	* Answer: misalignment. Based solely on pre-training, the model is actually trained a mix of many types of tasks. For example, let's say the user asks: 'Explain how the bubble sort algorithm works?'
	* Because there is some large set of examinations in the training corpus, it's likely that the model will reply with something like 'Explain how the merge sort algorithm works?' because that sort of question is one of many that might appear with the bubble question.
	* in order to guide the LLM to the smaller subset of data/training within its model taht is appopriate, we can do a few things to constrain it to a specific subset/task. This can be done by prompt engineering for exampe.
	* One challenge of prompt engineering is that it might be tiresome for the end-user.
1. Thus, part two of building the LLM is supervised fine-tuning 
	* Before the advent of creation of synthetic datasets, people paid pairs of humans to have dialogues. These dialogues have been captured in to a supervised dataset that can be used for fine-tuning.
	* This can be called a typical imitation learning setup, specifically 'behavior cloning' where we try to mimic an expert's `action distribution` conditioned on an `input state`.
	* At (7:15) of the video, good chart showing how the fine-tuned supervised model outperforms prompted GPT which outperforms vanilla GPT with no adjustment at all. Even better b/c it has less need for prompting from an end-user.
		* This chart is from the [March 2022 paper](https://arxiv.org/abs/2203.02155) by Ouyang, Wu et al "Training language models to follow instructions with human feedback"
1. But even fine-tuning still has limitations. 
	* For a variety of reasons, the model may poorly learn the true probability distribution of a human expert. See "Efficient Reductions for Imitation Learning" (2010) by Ross & Bagnell. 
	* As novel states are encountered, the model may compound error after error.
	* It can be shown mathematically that the error rate grows quadratically (x<sup>2</sup>!) if x = length of history.
	* In the case of a LLM, early mistakes during generation can cause it to make overconfident assertions.	
	* In other words, an LLM can't just passively observe an expert during training. It needs to *act* or *interact*
1. RLHF
	* One way to further fine-tune through this interaction is by Reinforcement Learning through Human Feedback


"t = *x<sub>t+1</sub>*
"l = *x<sub>1</sub>,... x<sub>t</sub>*


Next video is "What are Transformer Neural Networks?" by Ari Seff. [Link](https://www.youtube.com/watch?v=XSSTuhyAmnI) from May, 2021.
