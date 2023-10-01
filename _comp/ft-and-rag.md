---
title: Notes on Fine-Tuning and RAG
permalink: /ft-and-rag/
---

## 2023 Log

## 9/20/2023
### Fine-Tuning links
* 7/05/2023 ['Fine tuning is for form, not facts'](https://www.anyscale.com/blog/fine-tuning-is-for-form-not-facts) by Anyscale.

### Overview of fine-tuning
* Single slide summarizing the entire production process. Foundation model construction, self-supervised trainingin, then the fine-tuning at the end. 

### 9/29/2023
* Read [Nous-Hermes thread](https://twitter.com/Teknium1/status/1682459395853279232?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1682459395853279232%7Ctwgr%5Ee2e857234d07d452699f1396d249e307c856468b%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fwww.redditmedia.com%2Fmediaembed%2F155wwrj%2F%3Fresponsive%3Dtrueis_nightmode%3Dtrue)
* The Bloke at [HF](https://huggingface.co/TheBloke/Nous-Hermes-13B-GGML)
* [YouTube video](https://www.youtube.com/watch?v=iOJD1hw2xaw) by Fahd Mirza. Three ways of final adjustments to a foundation model:
	1. Prompt Engineering. Zero-shot vs. Few-Shot Learning
	1. Fine-Tuning. Instruction-based vs. Domain-based
	1. RAG. Process includes:
		1. Gathering data from data sources and extracting data
		1. Transforming data into appropriate format  
		1. Embedding this data in vector format and loading into a vector DB
* Straightforward and simple [IBM video](https://www.youtube.com/watch?v=T-D1OfcDW1M)
	1. Critical point. RAG is a small data store that is quick and easy to update with new information without having to retrain the whole foundation model. 
	1. It can also be clearer about what source it is using for a given fact. and if there are no good sources to back it up, the LLM is instructed to not be as confident or simply say i don't know or that there are not good sources about this.

### 9/30
* Hardware Corner has a [link to all versions of nous-hermes](https://www.hardware-corner.net/llm-database/Nous-Hermes/)















