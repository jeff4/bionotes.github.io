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


### Read in names.txt and populate words object
		words = open('names.txt','r').read().splitlines()

### View first 10 entries
		words[:10]

### See how many records are in name.txt
		len(words)

### See the shortest and longest words available in words.txt
#### returns 2 which means t the shortest word in names.txt has 2 letters
		min(len(w) for w in words) 
#### returns 15 which means t the shortest word in names.txt has 15 letters
		max(len(w) for w in words) 


### Bigram model
* judge 2 characters at a time.
* sample python code to just grab 2 characters at a time (8:05)
 
		for w in words[:3]:
			for ch1, ch2 in zip(w, w[1:]):
				print(ch1,ch2)

* Got to PyTorch and created zero tensor at 13:53
* 15:27 Next, learning how to manipulate errors using torch.tensor object. torch.tensor is zero-indexed in both dimensions so to access the last (aka bottom right-most) cell in a 5x5 array named A, you would enter 'A.(4,4)'.
* Create a new square array. 26 letters in the alphabet plus 2 more for start character 'S', and end character 'E'. so 28x28 array
* In theory, we can just copy the code that generated the bi-gram values before. But remember, we are creating a 28x28 int array. So we need a lookup table that converts characters into integers.
* completed populating the tensor with statistics. See ~/demo_files/makemore/1mm.py



