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
