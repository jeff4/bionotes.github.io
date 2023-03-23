---
title: Startups v Incumbents 2023 
permalink: /startups-v-incumbents-2023a/
sitemap: false
---

## Earlier posts
* Elad Gil #1: [Startups v Incumbents: who will capture value?](https://blog.eladgil.com/p/ai-startup-vs-incumbent-value) published 10/25/2022

* Elad Gil #2: Difference between [LLM, image gen and between platforms/markets/open-source](https://blog.eladgil.com/p/ai-platforms-markets-and-open-source) published 2/15/2023
finished reading

* Elad Gil #3: [Transformers and LLMs](https://blog.eladgil.com/p/ai-revolution-transformers-and-large) published 8/30/2022

* a16z on [who owns the generative AI platform](https://a16z.com/2023/01/19/who-owns-the-generative-ai-platform/) published 1/19/2023
	* We’re starting to see the very early stages of a tech stack emerge in generative artificial intelligence (AI). Hundreds of new startups are rushing into the market to develop foundation models, build AI-native apps, and stand up infrastructure/tooling.
	* In other words, the companies creating the most value — i.e. training generative AI models and applying them in new apps — haven’t captured most of it. Predicting what will happen next is much harder. But we think the key thing to understand is which parts of the stack are truly differentiated and defensible. This will have a major impact on market structure (i.e. horizontal vs. vertical company development) and the drivers of long-term value (e.g. margins and retention). So far, we’ve had a hard time finding structural defensibility anywhere in the stack, outside of traditional moats for incumbents.
	* The stack can be divided into three layers:
		* Applications that integrate generative AI models into a user-facing product, either running their own model pipelines (“end-to-end apps”) or relying on a third-party API
		* Models that power AI products, made available either as proprietary APIs or as open-source checkpoints (which, in turn, require a hosting solution)
		* Infrastructure vendors (i.e. cloud platforms and hardware manufacturers) that run training and inference workloads for generative AI models




## Developments from this past weekend
* Simon Willison's timeline of LLaMA developments as of 3/13/2023
	* [HN thread](https://news.ycombinator.com/item?id=35140369)
	* [blog post 1](https://simonwillison.net/2023/Mar/11/llama/) from 3/11/2023 - LLMs are having their Stable Diffusion moment
	* [blog post 2](https://simonwillison.net/2023/Mar/13/alpaca/) from 3/13/2023 - Stanford Alpaca

## Developments from Tuesday 3/14/2023
* Announcements from OpenAI today
	* [GPT-4 is announced](https://techcrunch.com/2023/03/14/openai-releases-gpt-4-ai-that-it-claims-is-state-of-the-art/)
	* it can ingest images as well as text to output text
	* can now pass the bar
	* partnership with Khan Academy for customized tutors
	* Announcement of $20/month paid consumer plan to ChatGPT
* Techcrunch articles
	* [Interview with Greg Brockman](https://techcrunch.com/2023/03/15/interview-with-openais-greg-brockman-gpt-4-isnt-perfect-but-neither-are-you/) CEO of OpenAI
	* [Together aka OpenChatKit](https://techcrunch.com/2023/03/14/meet-the-team-developing-an-open-source-chatgpt-alternative/) building open-source API replacement for ChatGPT
	* [Google Cloud gives dev access to Foundation Model](https://techcrunch.com/2023/03/14/google-cloud-gives-developers-access-to-its-foundation-models/)
		* API access to PaLM model
		* MakerSuite
		* Vertex AI now supports generative AI and launching Generative AI App Builder
		* Google brings a lot [more AI to Workspace](https://techcrunch.com/2023/03/14/google-goes-all-in-on-bringing-ai-to-workspace/) aka Google Docs
	* [New framework](https://techcrunch.com/2023/03/14/the-ai-revolution-has-outgrown-the-turing-test-introducing-a-new-framework/) to replace Turing Test
	* [Nabla](https://techcrunch.com/2023/03/14/nabla-a-french-digital-health-startup-launches-copilot-using-gpt-3-to-turn-patient-conversations-into-actionable-items/) uses GPT-3 to turn patient conversations into action
		* also named Copilot
	* [Anthropic launches Claude](https://techcrunch.com/2023/03/14/anthropic-launches-claude-a-chatbot-to-rival-openais-chatgpt/), an LLM competitor to ChatGPT
	* [Bing has been using GPT-4](https://techcrunch.com/2023/03/14/microsofts-new-bing-was-using-gpt-4-all-along/) for a while now
	* [Duolingo launches AI tutor powered by GPT-4](https://techcrunch.com/2023/03/14/duolingo-launches-new-subscription-tier-with-access-to-ai-tutor-powered-by-gpt-4/)
	* [5 ways GPT-4 outsmarts ChatGPT](https://techcrunch.com/2023/03/14/5-ways-gpt-4-outsmarts-chatgpt/)
	* [Quora launches Poe based on GPT-4](https://techcrunch.com/2023/03/15/quoras-poe-is-launching-subscriptions-to-let-you-chat-with-gpt-4-powered-bot/) with subscriptions

## Developments Tuesday 3/21/2023
* Adobe launches [Firefly](https://techcrunch.com/2023/03/21/adobe-firefly-generative-ai/)
* Nvidia GTC Conference [announcements](https://www.engadget.com/nvidia-and-medtronic-are-building-an-ai-enhanced-endoscopy-tool-161532723.html)
* Google BARD announcements
	* Verge on [Google says Bard is not a search engine](https://www.theverge.com/23649897/google-bard-chatbot-search-engine)
	* [YouTube](https://www.youtube.com/watch?v=9ll_pth4Sss) video reviewing Bard v. Bing aka LaMDA v. GPT-4 from this [HN submission](https://news.ycombinator.com/item?id=35250831)
	* [BBC article](https://www.bbc.com/news/technology-65018107) on the Bard launch 
	* [Main HN thread](https://news.ycombinator.com/item?id=35246260)
	* [NYT main article](https://www.nytimes.com/2023/03/21/technology/google-bard-chatbot.html)
	* [NYT evaluation of Bard](https://www.nytimes.com/2023/03/21/technology/google-bard-guide-test.html) compared to other LLMs
	* Interesting observation. There is a "Google It" cta at the bottom of each Bard answer. Is it a convenience, an acknowledgement that Bard is not complete, or an attempt to still maintain search revenue over time?
	* Note: Bard is the overall chat product but it is powered in the back by the LLM / foundation model LaMDA
	* [LaMDA](https://en.wikipedia.org/wiki/LaMDA) was originally announced as Meena in 2020. First generation LaMDA (aka Langugage Model for Dialogue Applications) was then introduced in October 2021. 
	* More history of LaMDA, formerly named Meena
		* Developed by Google Brain over many years, Meena was introduced in January 2020 with 2.6B parameters.
		* Two of the lead developers Daniel De Freitas and Noam Shazeer (2nd author on Attention is all you need paper Dec 2017), left Google in frustration b/c senior Google execs would not let Meena/LaMDA be released to public. They left and cofounded [Character.ai](https://beta.character.ai/help?). See additional info in this [HN comment](https://news.ycombinator.com/item?id=33025237)
		* First generation of LaMDA announced during Google I/O May 2021.
		* Second generation of LaMDA announced during Google I/O May 2022.
		* Summer of 2022 -- Google engineering Blake Lemione [claimed](https://en.wikipedia.org/wiki/LaMDA#Sentience_claims) that LaMDA was sentient giving an interview with *WIRED* and hiring a lawyer for LaMDA claiming alien intelligence rights under the 13th Amendment of the US Constitution. Wiki article has a summary of objections by Gary Marcus, Yann LeCun, etc. I would claim this is a human hallucinating, rather than an LLM hallucinating.
		* November, 2022, OpenAI launched ChatGPT. The capability, ease-of-use, and popularity of ChatGPT led to a code red within Google HQ.
		* Early february, Google had a series of announcements and demos of Bard which is based on LaMDA and these did not go well. Led to $100B loss of market cap within hours.
		* This week on Tuesday March 21, 2023, Google released Bard to a small number of users in the US and UK with a waiting list for more ppl over time.
	* [The NYT](https://www.nytimes.com/2023/03/21/technology/google-bard-chatbot.html) reported 3/21 that "more than 20 A.I. products and features" will be launched, including "a feature called Shopping Try-on and the ability to create custom background images for YouTube videos and Pixel phones."
	* 
