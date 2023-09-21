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

### Glossary
* [PEFT](https://www.leewayhertz.com/parameter-efficient-fine-tuning/) = Parameter-Efficient Fine-Tuning.
* [RAG](https://research.ibm.com/blog/retrieval-augmented-generation-RAG) = Retrieval-Augmented Generation. From IBM: 'RAG is an AI framework for retrieving facts from an external knowledge base to ground large language models (LLMs) on the most accurate, up-to-date information and to give users insight into LLMs' generative process.'

### Fine-Tuning links
* 7/05/2023 ['Fine tuning is for form, not facts'](https://www.anyscale.com/blog/fine-tuning-is-for-form-not-facts) by Anyscale.


### Overview of fine-tuning
* Single slide summarizing the entire production process. Foundation model construction, self-supervised trainingin, then the fine-tuning at the end. 
