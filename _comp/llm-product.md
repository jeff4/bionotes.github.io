---
title: LLM Product Notes
permalink: /llm-product/
sitemap: false
---

## Products to use
* ChatGPT
* BingChat
* From this [HN thread](https://news.ycombinator.com/item?id=35545019), discovered [phind.com](www.phind.com) on 12 April 2023

### 2023 Log

## 05 April 2023
### Prompt 1: "Assuming I understand the fundamentals of data structures and algorithms and am comfortable writing basic programs in other languages like C, Java, and Javascript, what are the core concepts that would get me productive as a developer new to Python?"

* GPT: "If you're already familiar with programming concepts and have experience in other languages, transitioning to Python should be relatively straightforward. Here are some core concepts to focus on that will help you get productive as a developer new to Python:
	1. Python's syntax and basic data types: Python has a clean, readable syntax, and it's important to familiarize yourself with the language's basic data types (such as strings, numbers, lists, and dictionaries) and their operations.
	1. Python's built-in functions and libraries: Python has a rich set of built-in functions and libraries that can help you write efficient and readable code quickly. Some commonly used libraries include NumPy, Pandas, and Matplotlib for data analysis and visualization, and Flask and Django for web development.
	1. Control flow and functions: Understanding how to use control flow statements like if-else, for loops, and while loops, as well as how to define and call functions, is essential for writing effective Python code.
	1. File input/output and exception handling: Python provides easy-to-use tools for reading from and writing to files, as well as for handling exceptions and errors that may arise during program execution.
	1. Object-oriented programming: Python supports object-oriented programming (OOP), which can help you write modular, reusable code. It's important to understand how to create classes and objects, and how to use inheritance and polymorphism effectively.
	1. Python's community and ecosystem: Python has a large and active community, with many resources available online, including documentation, tutorials, and forums. It's also important to be familiar with package managers like pip and conda, which make it easy to install and manage third-party libraries and packages.
* By focusing on these core concepts, you'll be well on your way to becoming a productive Python developer. Good luck!"

### Prompt : "Thank you. What books or courses would you recommend for an experience programmer who is new to Python?

* GPT: 'There are many great books and courses for experienced programmers who are new to Python. Here are some recommendations:
	* Books:
		1. "Python Crash Course" by Eric Matthes: This book is a great introduction to Python for programmers who are already familiar with other languages. It covers the basics of Python syntax, data structures, control flow, and functions, as well as more advanced topics like file I/O, testing, and web development.
		1. "Effective Python" by Brett Slatkin: This book provides 59 specific ways to write better Python code. It covers a wide range of topics, including Python's data model, functions, classes, concurrency, and debugging.
		1. "Fluent Python" by Luciano Ramalho: This book is for programmers who want to become fluent in Python. It covers advanced topics like decorators, metaclasses, and concurrency, and provides real-world examples and best practices for writing idiomatic Python code.
	* Courses:
		1. "Python for Data Science and Machine Learning Bootcamp" by Jose Portilla: This course covers the basics of Python programming, as well as data science and machine learning topics like NumPy, Pandas, Matplotlib, and Scikit-Learn. It's a great choice for programmers who want to learn Python for data analysis and machine learning.
		1. "Python Beyond the Basics - Object-Oriented Programming" by David Blaikie: This course focuses on object-oriented programming (OOP) in Python. It covers topics like classes, inheritance, polymorphism, and exception handling, and provides real-world examples of how to use OOP to write modular, reusable code.
		1. "Python Web Development with Flask" by Jose Portilla: This course teaches you how to build web applications using the Flask web framework. It covers topics like routing, templates, forms, and databases, and provides hands-on experience building a full-stack web application.
	* These are just a few examples of the many great books and courses available for experienced programmers who are new to Python. I hope you find them helpful!'

### Prompt (second attempt): "Thank you. What books or courses would you recommend for an experience programmer who is new to Python?

* GPT regenerated response: 'There are many great resources for experienced programmers who are new to Python. Here are some books and courses that I would recommend:
	* Books:
		1. "Python Crash Course" by Eric Matthes: This book is an excellent resource for programmers who are new to Python. It covers the basics of Python programming, as well as more advanced topics like web development, data visualization, and machine learning.
		1. "Fluent Python" by Luciano Ramalho: This book is geared towards experienced programmers who are already familiar with Python's syntax and basic data types. It covers advanced topics like metaclasses, decorators, and concurrency.
		1. "Effective Python" by Brett Slatkin: This book offers 59 specific ways to improve your Python code. It's a great resource for programmers who want to write more Pythonic code that is easier to read, write, and maintain.
	* Courses:
		1. "Python for Everybody" by Dr. Charles Severance: This is a free online course offered by the University of Michigan on Coursera. It covers the basics of Python programming, as well as web scraping, databases, and data visualization.
		1. "Python Bootcamp" by Colt Steele: This is a comprehensive Python course that covers the basics of programming, as well as advanced topics like web development, data analysis, and machine learning.
		1. "Python for Data Science and Machine Learning Bootcamp" by Jose Portilla: This course focuses on using Python for data analysis and machine learning. It covers topics like NumPy, Pandas, Matplotlib, and Scikit-learn.
	* These resources should give you a solid foundation in Python programming, and help you apply your existing programming knowledge to Python. Good luck!'


## 07 April 2023

### Prompt: Please provide detailed explanation of what this code does:

* GPT: This code performs the following tasks:
    1. Imports the PyTorch library, a popular machine learning library for building neural networks and performing tensor computations.
    1. Reads in a list of words from a file named "names.txt" and stores them as a list of strings in the variable **words**.
    1. Creates a 158x158 matrix filled with zeros of data type int32 using PyTorch, and stores it in the variable N. This matrix will be used to count the number of times each pair of characters appears in the words in the list words.
    1. Extracts all unique characters from the list of words, converts the resulting set into a sorted list, and stores it in the variable chars.
    1. Creates a dictionary stoi (string to integer) where each character is a key and the value is the corresponding index of that character in the chars list. The dictionary also contains two special tokens S and E \[*JH edit: needed to remove surrounding angle brackets so strikethrough problems are not caused in Markdown*] with indices 156 and 157 respectively.
    1. Iterates over each word in the words list, and for each word, the code adds start and end tokens S and E \[*JH edit: needed to remove surrounding angle brackets so strikethrough problems are not caused in Markdown*] respectively to the beginning and end of the word, creating a new list chs that contains all characters of the word plus the start and end tokens.
    1. The code then iterates over each pair of adjacent characters in the chs list using the zip() function, and for each pair, the code increments the value in the corresponding element of the N matrix by 1. This effectively counts the number of times each pair of characters appears in the list of words.
    1. Finally, the code prints out the N matrix, which contains the counts of pairs of characters in the words.
* Overall, this code is performing some data preprocessing to count the number of times each pair of characters appears in a list of words. This type of data processing is often used as a first step in training language models or in other natural language processing tasks.


## 12 April 2023

### Prompt: What is the difference between a torch tensor and a regular multidimensional array

* GPT: A torch tensor and a regular multidimensional array are both data structures used to store and manipulate multi-dimensional data. However, there are a few key differences between the two:
	1. Automatic differentiation: One of the main differences is that a torch tensor is capable of automatic differentiation. This means that when you perform operations on a tensor, it can keep track of the gradient of those operations with respect to the tensor's inputs. This is useful in machine learning applications, where you often need to calculate gradients for optimization algorithms.
	1. GPU acceleration: Torch tensors can be run on GPUs for accelerated computation, while regular arrays are typically only run on CPUs.
	1. Compatibility: Torch tensors are optimized for use with the PyTorch framework, while regular arrays can be used with any programming language or framework that supports them.
	1. Extra functionalities: Torch tensors provide a variety of extra functionalities such as broadcasting, slicing, and concatenation, which can be helpful for machine learning tasks.
	1. Data type consistency: Torch tensors require a consistent data type for all elements in the tensor, whereas regular arrays can be mixed data types.
* Overall, while regular multidimensional arrays can be useful in many applications, torch tensors are specifically designed for use in machine learning and deep learning tasks, providing extra functionalities and optimization for these types of applications.

### Prompt: from a programming perspective, is a tensor just a multidimensional array?

* GPT: From a programming perspective, a tensor can be thought of as a generalization of a multidimensional array.
	* Like a multidimensional array, a tensor is a data structure that can store values organized in multiple dimensions. However, a tensor can have a variable number of dimensions (also called axes), whereas a multidimensional array has a fixed number of dimensions.
	* In addition, as mentioned earlier, tensors can be used for automatic differentiation and can be run on GPUs for faster computation. These additional features make tensors particularly useful for machine learning applications.
	* From a programming perspective, tensors are typically implemented as classes with associated methods and attributes. In the case of PyTorch, a popular deep learning library, the torch.Tensor class is used to represent tensors, and it provides a wide range of methods and functionalities for manipulating and operating on tensors.
	* So while a tensor can be thought of as a generalized version of a multidimensional array, its additional features and implementation as a class make it a distinct data structure in its own right.

#### answers from Bing (see Apple Photos)

### Prompt: from a programming perspective, is a tensor just a multidimensional array?

* Phind.com (non-expert, non-concise, non-creative): Yes, from a programming perspective, a torch tensor is just a multidimensional array in Python. As explained in machinelearningmastery.com, a tensor is a generalization of a matrix that can be indexed in more than two dimensions. Thus, a one-dimensional tensor is simply a one-dimensional array, or a vector. We can create tensors using the torch.tensor() function which takes in Python lists as input. For example, if we have a list of integers, we can convert it to a tensor using torch.tensor([10, 11, 12, 13]). Similarly, if we have a list of floating-point numbers, we can convert it to a tensor using torch.tensor([10.0, 11.0, 12.0, 13.0]).
	* As mentioned in geeksforgeeks.org, there are various methods to create a tensor in PyTorch. A tensor can contain elements of a single data type. The different ways of defining a tensor are:
		1. torch.Tensor(): It copies the data and creates its tensor. It is an alias for torch.FloatTensor.
		1. torch.tensor(): It also copies the data to create a tensor; however, it infers the data type automatically.
		1. torch.as_tensor(): The data is shared and not copied in this case while creating the data and accepts any type of array for tensor creation.
		1. torch.from_numpy(): It is similar to tensor.as_tensor() however it accepts only numpy array.
	* We can use these methods to create tensors of different data types, shapes, and sizes in PyTorch.
	* It's important to note that when the term "tensor" is used in PyTorch, it refers to any torch.Tensor object. Matrices and vectors are special cases of torch.Tensors, where their dimension is 2 and 1 respectively. When we talk about 3D tensors, we explicitly use the term “3D tensor” as mentioned in pytorch.org.
	* As explained in math.stackexchange.com, tensors and multidimensional arrays are different types of objects. In mathematics, a "tensor" is usually defined to be a multilinear function, which is a function of several vector variables that maps to a scalar. However, in programming and computer science, tensors are generally considered to be multidimensional arrays.
	* In conclusion, while tensors and multidimensional arrays have different mathematical definitions, from a programming perspective, a torch tensor is just a multidimensional array in Python.

* Phind.com (Expert, non-concise, non-creative): Yes, from a programming perspective, a Torch tensor can be considered as a multidimensional array in Python. However, there are some differences and additional features that make tensors more suitable for specific tasks, such as deep learning and GPU computation.
	* Tensors can be created from Python lists or NumPy arrays using the torch.tensor() function [0]. They can have various data types like integers or floats, and can be converted between these types [1]. PyTorch also provides GPU and CPU variants of tensors, as well as utility functions for tensor manipulation [3].
	* But what sets tensors apart from simple multidimensional arrays is their transformation properties. Tensors are a generalization of matrices that can be indexed in more than 2 dimensions, and they have specific transformation rules when applying linear operations [4]. In other words, tensors are multidimensional arrays with certain transformation properties that make them suitable for representing linear transformations.
	* For example, in the context of deep learning, tensors are used to represent data and weight parameters, and can be efficiently processed on GPUs for faster computation. The transformation properties of tensors are crucial when dealing with operations like backpropagation or gradient computation.
	* In summary, while you can think of a Torch tensor as a multidimensional array in Python, it is important to remember that tensors have additional features and transformation properties that make them more suitable for specific tasks like deep learning and GPU computation. 


## 24 May 2023

* Prompt: what are the Mandarin characters used for the show title of the HBO TV show "Succession"?
	* Bing Chat: 'I’m sorry, but I couldn’t find any information about the Mandarin characters used for the show title of the HBO TV show “Succession”. Is there anything else you would like to know?'
	* Chat-GPT: 'The HBO TV show "Succession" is not commonly translated or officially titled in Mandarin. However, it is possible to transliterate the English title into Mandarin characters. The Mandarin characters commonly used to represent "Succession" are:
		* 继承之路 (Jì4 Chéng2 Zhī Lù4)
	* 'Please note that this is a transliteration and not an official translation.'

## 28 June 2023

* Prompt: when i ask gpt-4 to write an article based on my input and ask it to produce a 1500-2000 word article, gpt-4 creates an article that is consistently only 500 words or so. Do you have any tips that can nudge gpt-4 to produce a longer article?

### GPT-4 via api

While GPT-4 isn't released yet and I can't speak specifically to its capabilities, I can share general tips on how you might encourage GPT-3, or any similar AI, to produce a longer response:

1. **Breakdown the Task**: Instead of asking the AI to write the entire article in one go, you could break the task down into smaller sections. For example, you could ask the AI to draft an introduction, then the main points, and finally the conclusion. This will allow you to control the length of each section and ensure that the overall article meets your word count requirement.

2. **Ask for More Detail**: If the AI's response is too short, you could ask it to elaborate on certain points. For example, you could say, "Can you provide more detail on X?" or "Can you expand on Y?" This should prompt the AI to write more.

3. **Use an Iterative Approach**: You can also use an iterative approach, where you provide feedback on the AI's response and ask it to improve on it. For example, if the AI writes a short paragraph, you could say, "That's a good start, but can you add more information on X, Y, and Z?"

4. **Set Clear Expectations**: When giving the AI a task, make your expectations clear. If you want a 1500-word article, you could say, "Please write a 1500-word article on X."

5. **Rephrase your Request**: If the AI is not generating a long enough output, you might need to rephrase or clarify your request. For example, instead of saying, "Write an article," you could say, "Write a detailed analysis" or "Write a comprehensive report".

Remember, the AI's ability to generate long responses may also be limited by the platform you're using, as some platforms impose a maximum limit on the length of the AI's responses.

### Bing Chat via MS Edge (medium temperature)

Here are some tips that might help you nudge GPT-4 to produce a longer article:

1. Try to provide more detailed prompts or input to GPT-4. The more information you give it, the more it will have to work with and the longer the output may be.
1. You can also try increasing the length of the output by specifying a higher max_length parameter when calling GPT-4. This will tell GPT-4 to generate a longer output.
1. Another option is to fine-tune GPT-4 on your specific task or domain. This can help it better understand the context of your input and generate more relevant and detailed output.

I hope these tips help you get the results you’re looking for. Good luck! 😊

### Bing Chat via MS Edge (creative temperature)

I’m sorry to hear that you are having trouble with GPT-4. I don’t have any direct tips for using GPT-4, but I can offer some general advice for generating longer articles based on your input.

Some possible strategies are:

* Use more specific and detailed input. The more information you provide, the more GPT-4 has to work with and expand on. For example, instead of “write an article about climate change”, you could say “write an article about the effects of climate change on polar bears and their habitat”.
* Use prompts or questions to guide the article. You can include some questions or subheadings in your input that you want GPT-4 to answer or elaborate on. For example, you could say “write an article about the history of chocolate. Include the following sections: 1) How chocolate was discovered and used by ancient civilizations. 2) How chocolate spread around the world and became popular. 3) How chocolate is made today and what are the different types and varieties. 4) What are the health benefits and risks of chocolate consumption.”
* Use feedback or editing to improve the article. You can review the article that GPT-4 generates and provide some feedback or suggestions for improvement. For example, you could say “This is a good start, but I would like you to add more details and examples to each section. Also, please check the spelling and grammar and fix any errors.”

### phind.com

Prompt: When I ask GPT-4 to write a 1500-2000 word article, it consistently produces an article that's about 500 words. This happens regardless of what max_tokens and temperature I set it at. What suggestions do you have to engineer the prompt to write an article that is the correct length?

Answer:

It seems that you're experiencing issues with GPT-4 generating shorter articles than the desired length, even with the max_tokens and temperature settings. Here are some suggestions to help you achieve the desired output length:

1. Specify the desired length in the prompt: Make sure to mention the desired length of the article in the prompt itself. For example, you can include something like "Write a 1500-2000 word article about the impact of climate change." This will provide GPT-4 with a clear expectation of the output length pcguide.com.
1. Check token limits: Ensure that the total number of tokens (both prompt and completion) does not exceed the model's token limit. For GPT-3.5-turbo, the limit is 4096 tokens learn.microsoft.com. Make sure your prompt and completion stay within this limit.
1. Adjust max_tokens: You may need to set max_tokens to a slightly higher value than normal, such as 300 or 500, to ensure the model doesn't stop generating text before it reaches the end of the message learn.microsoft.com.
1. Use temperature: Adjust the temperature parameter to control the randomness of the generated text. Lower values (e.g., 0.5) will result in more focused and deterministic outputs, while higher values (e.g., 1.0) will produce more diverse and creative outputs. Experiment with different temperature values to find the best balance between randomness and coherence learn.microsoft.com.
1. Iterate and refine: If GPT-4 still produces shorter articles than desired, you can use a two-step approach. First, generate an article with a lower max_tokens value (e.g., 1000) to get a shorter summary of the desired topic. Then, use the summary as a new prompt to generate a longer article with a higher max_tokens value (e.g., 2000) zapier.com.

Remember that GPT-4 might not always produce the exact output length you desire, but by providing clear instructions, adjusting parameters, and iterating on the generated content, you can get closer to the desired length.


## 31 August 2023
 * Prompt: Please recommend one or a combination of tools that accepts as input a text transcript and outputs a video of a human character speaking this text in an appealing way

### phind.com
* Based on GPT-4 Model
* Based on the search results, there are several tools that can convert text transcripts into videos with human-like characters speaking the text. These tools use advanced artificial intelligence (AI) technologies to generate realistic speech and movements. Here are some of the most recommended tools:
	1. Synthesia IO: Synthesia is an AI-powered video creation platform that can generate realistic talking head avatars to deliver messages in multiple languages. You can create custom talking head videos by uploading a script and selecting an avatar. The platform will then animate the avatar to speak the script, allowing you to create high-quality video content without needing a professional actor or videographer. Additionally, Synthesia also offers the ability to create personalized videos using a digital twin of a natural person, adding an extra layer of authenticity to your content. [Synthesia.io](https://www.synthesia.io/tools/digital-human) and [vaslou.com](https://www.vaslou.com/ai-talking-head-generator)
	1. DeepBrain AI: This innovative tool uses human-focused AI technology to generate video content. You can input text and generate an AI-powered video with over 100 avatars that speak your text. DeepBrain AI also offers a wide range of customization options, allowing you to tailor the appearance and speech patterns of the avatar to your specific needs. Answer from [vaslou.com](https://www.vaslou.com/best-ai-video-generators-text-to-video)
	1. Yepic AI: Yepic is a professional AI text-to-video creator that allows you to generate AI videos with human avatars. You can customize the video by changing backgrounds, language, voice, and design elements. Yepic supports over 60 languages and 480 different voices, and you can also upload your own voice-over. Answer from [vaslou.com](https://www.vaslou.com/best-ai-video-generators-text-to-video)
	1. HeyGen: HeyGen is an AI video generation tool that facilitates the conversion of text into high-quality videos. The tool boasts an impressive collection of over 80 talking human avatars complete with authentic voices and perfect text lip-syncing. You may also create custom avatars through several pricing plans. Answer from [vaslou.com](https://www.vaslou.com/best-ai-video-generators-text-to-video) 
	1. Kapwing's Text to Video AI: This tool can transform documents, essays, scripts, and blog posts into short, compelling video summaries with AI. Afterward, you can edit your AI-generated video directly in your browser with Kapwing's video editor. Trim and cut your video, add an AI voice over, apply filters and effects, or even translate it to over 70+ available languages. [Kapwing.com](https://www.kapwing.com/ai/text-to-video)
* Each of these tools offers unique features and capabilities, so the best choice will depend on your specific needs and preferences. For instance, Synthesia IO might be the best choice if you need a wide range of languages and avatar options, while Kapwing's Text to Video AI might be more suitable if you're looking for a tool that also provides comprehensive video editing capabilities.

## 05 September 2023
### Video research
* Sythesia.io. $30/month, no free trial. ($270/year if paid upfront)
* Deepbrain.io. created acct with atljeffh@gmail.com before being able to see pricing page
	* $30/month for every 10 minutes per month. i.e., $60, $120, $180 per month for 20, 40, 60 minutes, respectively.
* HeyGen.com seems to have a free credit program with 1 minute video creation. But costs $29/month just like with the others. 
* www.yepic.ai -- has a 3-day free trial. After that, it's £29 per user per month when billed monthly. Started free trial.

### summary
* created atljeffh account at HeyGen. Created jeffh@sloan.mit.edu account at Yepic.AI and added credit card. Yepic website is a bit buggy.
* successfully generated a video at HeyGen.
* Signed up with atljeffh at Runway ML. Those tools are more generative, less focused on the video creation.

## 06 September 2023=
* Cleaned out all old accounts. Synthesia is clear winner over yepic.ai. Only downside is that they only have 1 doctor. :(
