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
* 3/05 - Walter Benjamin [1936 essay](https://en.wikipedia.org/wiki/The_Work_of_Art_in_the_Age_of_Mechanical_Reproduction) *The Work of Art in the Age of Mechanical Reproduction* ([pdf link](https://web.mit.edu/allanmc/www/benjamin.pdf))

### 3/05 Notes on Gopnik 
* Quote from Gopnik's [NYer piece](https://www.newyorker.com/culture/cultural-comment/what-can-ai-art-teach-us-about-the-real-thing). "Instead, it proposes a recombinant approach to popular imagery as a means of making art. (The dialogue of popular imagery and modern art was, as it happens, the topic of that abandoned Ph.D. thesis.)"
* "In effect, it exploits, and has installed in it as a premise, an idea specific to a particular heritage of image-making, the heritage of Symbolism, and then of the Surrealism that Symbolism engendered. Appropriately enough, the system takes its punning name from a Surrealist painter, since DALL-E 2 is ideally trimmed to make soft watches and derby hats on dogs and trains racing out of fireplaces."
* "The reason that DALL-E 2 is a machine for making Surrealist images is that the essence of such art is to be a dialogue between the prompter and the prompted. That’s why so much of the best Surrealist art is not terribly accomplished in itself as optical painting. Instead, it approximates and appropriates the slick styles of illustration, or subjects popular imagery to sudden dislocations. Max Ernst collages are the type of this kind, made from many common sources—cheap advertisements in the back of the newspaper or department-store catalogue—scissored together into a new appearance of meaning. "
* "So, lava lamp or electric light? Surely a lava lamp, for now—a diversion of the moment. But then there is something to be said for the idea that art should always be more lava lamp than electric light. The light bulb, after all, is a supreme specimen of imitative technology, a mechanized candle. The lava lamp is a combination of things never before seen, curious and worth looking at for its own sweet sake."
* "The new visual A.I. is really a pictorial collider, the image-making equivalent of a particle accelerator that hurls subatomic bits together at high speeds to see what they will reveal as they slam into and fracture each other. In making images collide, we reveal the traces of our table of artistic elements."

### 3/05 Notes on Benjamin
* "First, process reproduction is more independent of the original than manual reproduction.
	* "For example, in photography, process reproduction can bring out those aspects of the original that are unattainable to the naked eye yet accessible to the lens, which is adjustable and chooses its angle at will. And photographic reproduction, with the aid of certain processes, such as enlargement or slow motion, can capture images which escape natural vision.
* "Secondly, technical reproduction can put the copy of the original into situations which would be out of reach for the original itself. Above all, it enables the original to meet the beholder halfway, be it in the form of a photograph or a phonograph record. The cathedral leaves its locale to be received in the studio of a lover of art; the choral production, performed in an auditorium or in the open air, resounds in the drawing room.
* "The situations into which the product of mechanical reproduction can be brought may not touch the actual work of art, yet the quality of its presence is always depreciated. This holds not only for the art work but also, for instance, for a landscape which passes in review before the spectator in a movie.
* "...that which withers in the age of mechanical reproduction is the aura of the work of art.
* "These two processes lead to a tremendous shattering of tradition which is the obverse of the contemporary crisis and renewal of mankind.
* "The uniqueness of a work of art is inseparable from its being imbedded in the fabric of tradition. This tradition itself is thoroughly alive and extremely changeable. An ancient statue of Venus, for example, stood in a different traditional context with the Greeks, who made it an object of veneration, than with the clerics of the Middle Ages, who viewed it as an ominous idol.
* "
