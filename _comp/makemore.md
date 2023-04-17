---
title: Makemore Notes
permalink: /makemore/
---

# Andrej Karpathy videos to watch on Transformers
* Makemore series
	* [Makemore 1](https://www.youtube.com/watch?v=PaCmpygFfXo&)
	* [Makemore 2](https://www.youtube.com/watch?v=TCH_1BHY58I)
	* [Makemore 3](https://www.youtube.com/watch?v=P6sfmUTpUmc)
	* [Makemore 4](https://www.youtube.com/watch?v=q8SA3rM6ckI)
	* [Makemore 5](https://www.youtube.com/watch?v=t3YJ5hKiMQ0)
* Main [Transformer video](https://www.youtube.com/watch?v=kCc8FmEb1nY&)

# Makemore video 1 Notes

### As of 43:00 

	import torch
	import matplotlib.pyplot as plt
	
	words = open('names.txt','r').read().splitlines()
	
	N = torch.zeros((27,27), dtype=torch.int32)
	
	chars = sorted(list(set(''.join(words))))
	
	## create dictionary that maps strings to integers for easier manipulation
	## the i+1 means a = 1, b = 2, c =3, ... z = 26. Meanwhile, command below will
	## map index number 0 = delimiter '.'
	stoi = {s:i+1 for i,s in enumerate(chars)}
	
	## specify a single delimiter char '.' that will take index position = 0
	## '.' replaces '<S>' and '<E>' in previous version.
	stoi['.'] = 0
	
	## create reverse mapping dictionary called 'itos' to turn integers back into strings
	itos = {i:s for s,i in stoi.items()}
	
	
	for w in words:
		chs = ['.'] + list(w) + ['.']
		for ch1, ch2, in zip(chs, chs[1:]):
			ix1 = stoi[ch1]
			ix2 = stoi[ch2]
			N[ix1, ix2] += 1
	
	plt.figure(figsize=(16,16))
	# plt.imshow(N, cmap='Blues')	# commented out printing of dataplot
	for i in range(27):
		for j in range(27):
			chstr = itos[i] + itos[j]
			plt.text(j, i, chstr, ha="center", va="bottom", color='gray')
			plt.text(j, i, N[i, j].item(), ha="center", va="top", color='gray')
	plt.axis('off');
	
	##########
	
	g = torch.Generator().manual_seed(2147483647)
	
	for i in range(50):
		out = []
		ix = 0
		while True:
			p = N[ix].float()
			p = p / p.sum()
			ix = torch.multinomial(p, num_samples=1, replacement=True, generator=g).item()
			out.append(itos[ix])
			if ix == 0:
				break
		print(''.join(out))
	
### Bigram model
* Got to PyTorch and created zero tensor at 13:53
* 15:27 Next, learning how to manipulate errors using torch.tensor object. torch.tensor is zero-indexed in both dimensions so to access the last (aka bottom right-most) cell in a 5x5 array named A, you would enter 'A.(4,4)'.
* Create a new square array. 26 letters in the alphabet plus 2 more for start character 'S', and end character 'E'. so 28x28 array
* In theory, we can just copy the code that generated the bi-gram values before. But remember, we are creating a 28x28 int array. So we need a lookup table that converts characters into integers.
* completed populating the tensor with statistics. See ~/demo_files/makemore/1mm.py
* next, rewriting code to have the output of matplotlib look nicer and properly labelled
* got to (36:03), generating names. still dissatisified b/c not starting with 'mor.' the way Andrej is. Instead, my first name generated is 'cexze.'
* Learned a little more about broadcasting semantics which PyTorch borrows from numpy. When performing array by array manipulations, each dimension needs to be exactly the same size, or, exactly 1 or exactly 0. At 43:00 of makemore 1 video. See also [PyTorch docs](https://pytorch.org/docs/stable/notes/broadcasting.html) and [numpy docs and example](https://numpy.org/doc/stable/user/basics.broadcasting.html)
* Completed more efficient version 3c-mm.py as of 44:23. And also can skip to evaluation part later
	* Discussion of very dangerous and subtle bugs that are introduced if you do not respect 'keepdim=True' and Broadcast semantics for both numpy and PyTorch.
* Begin next at 50:19 loss function to evaluate how good/bad this bi-gram model is
* Up to 52:01
* OK, the problem is P.sum(1, keepdim=True) = 0. So when we execute:

	P /= P.sum(1, keepdim=True)

* We are dividing by 0 so output is NaN 

## 15 April 2023 - timestamped notes on video 1
* 52:00 to 1:05:00 explains how to evaluate the "effectiveness" of the model, by first explaining maximum likelihood estimate. 
	* Because these values are between 0 and 1 and the product of all 27 MLEs becomes a small number, better to view as the log(maximum likelihood estimate). This means that the closer that MLE gets to 1 (better), the closer log(MLE) gets to zero. And the worse MLE is (closer to zero it gets), the closer log(MLE) gets to negative infinity.
	* Finally, the standard is to miniminze the loss function which is why we invert the log(MLE) by putting a negative sign in front of it. This aligns log(MLE) with the usual loss function Objective function.
* 1:08:00 - Explains difference between torch.tensor and torch.Tensor. generally best to use only the lower-case version. PyTorch offical docs don't explain very well, but a StackExchange thread does do a good job.
* 1:12:00 - Explains the simplifications that come with One-Hot encoding. All that means is that it represents every letter (a-z) as a 27-dimension vector, where each dimension represents one of the letters of the alphabet plus position zero represents the delimiter '.'
	* Exactly 1 dimension has a non-zero value, initialized at 1 to represent a particular letter.
	* e.g., \[1,0,0,0,...] = '.'
	* e.g., \[0,1,0,0,...] = 'a'
	* e.g., \[0,0,1,0,...] = 'b'
	* e.g., \[0,0,0,1,...] = 'c'
	*  ....
	* e.g., \[0,0,0,0,...1] = 'z' is the final encoding for the 27th dimension
* 1:23:00. Logits are just a nickname for "log counts". We are normalizing the former randomly drawn values between -3 to +3 (roughly drawn from a normal distribution of untrained weights. Turning this series of positive and negative numbers into a consistent bunch of positive numbers by exponentiating them against Euler's number e^x. 
	* Andrej reminds us that for when x is anywhwere from -infinity to 0, output of function y=e^x is a float between y=0 (at x=negative infinty) and y=1 (at x=0).
	* Similarly, for all postive x values input into the y=e^x function, the output is always a postive number from y=1 (when x=0) to y=positive infinity as x approaches postive infinity.
* 1:24:30 - 1:25:58 Andrej summarizes again everything he's done over the last 15 minutes or so. Going from one-hot encoding, entry of first 5-letter example, etc..
* 1:32:00 summarizes that all the operations are differentiable. And as such, you can calculate the gradient for it and use SGD to optimize the weight and backprop 
* 1:38:45 at this point, Andrej has done everything including pushed through a forward pass. 
* 1:38:48 Andrej begins the first backward pass
* 1:41:35 Andrej does first weight adjustment based on (i think this is backprop at this point). similar to what he did in micrograd. It's after the extra 'h' term a few seconds earlier
* 1:42:10 Andrej recalculates and readjusts the weights about 2-3 times while measuring the loss function output, which is a postive float that slowly gets smaller. Optimally, we should get to loss function = 0
	* Values of loss function over time: 3.76. Rerun forward pass, new loss function output is 3.74. Based on new weight values, backward pass means we update the weights again. Rerun forward pass again, new loss function output is 3.72
	* At 1:42:44, Andrej says "see, we are now doing gradient descent!"
* Up to 1:43:50, all 10 iterations of forward pass, update weights, backward pass, etc. improved result of loss function using only the likelihood of letter "x" being the next letter in the sequence  based on the values of 'emma.' i.e., 
	1. '.e'
	1. 'em'
	1. 'mm'
	1. 'ma'
	1. 'a.
* From this point on, Andrej will start training with all ~228,000 bigrams, not just the 5 bigrams derived from 'emma.'
* 1:44:27, goes from 10 iterations to 100 iterations and get a final loss value of about 2.47.
	* 1:44:20, also, andrej changed the learning rate from 0.1 to 1.0 to 10.0 to 50.0
* From 1:45:00 to 1:46:00, Andrej explains that the best (aka lowest) loss value we can achieve through gradient descent-based learning is about 2.45. which is the same value we got from the explicit counting based approach in the first 30 minutes of this video! But that's because the representation is not that complicated. SGD is nice because it's a flexible system that can be used to fit much more complicated representations. 

## 16 April 2023
* Was able to implement everything needed up until In[164..]

		g = torch.Generator().manual_seed(...)
		for i in range(5):
			out = []

* Finished everyting before In[487...]. i.e., xs and ys provided the correct output for emma
* Got a few lines more to [490... BUT tensor shape is wrong for In [493...



