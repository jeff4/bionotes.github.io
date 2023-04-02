---
title: Python Notes
permalink: /python/
---

## 30 March 2023
### Articles on setting up python environment
* First, install mamba as a lighter weight and faster alternative to conda
* Next, install jupyter notebook server which relies on mamba + python
* Also read this article on [Managing Python Environment in 2022](https://aseifert.com/p/python-environments/)
* Less necessary, but read [this section](https://realpython.com/python-virtual-environments-a-primer/#what-other-popular-options-exist-aside-from-venv) of this longer, more comprehensive [article](https://realpython.com/python-virtual-environments-a-primer/) on understanding venv in particular. But it also has comments on virtualenv, conda, etc.
* Ross Dobson's January 2022 tutorial on [setting up Python environments with Mambaforge](https://ross-dobson.github.io/posts/2021/01/setting-up-python-virtual-environments-with-mambaforge/)
* This 2020 update to an older 2018 version of a post explains why ["Pip is here to stay!"](https://chriswarrick.com/blog/2018/07/17/pipenv-promises-a-lot-delivers-very-little/#pip-is-here-to-stay)
* Older 2018 piece on ["Why You Need Python Environments and How to Manage Them with Conda"](https://www.freecodecamp.org/news/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c/)
* Cached version of this older Coiled blog post on ["Use Mambaforge to Conda Install PyData Stack on your Apple M1 Silicon Machine"](https://webcache.googleusercontent.com/search?q=cache:AmxeEUnBp84J:https://www.coiled.io/blog/apple-arm64-mambaforge&cd=6&hl=en&ct=clnk&gl=us&client=safari)

### Andrej Karpathy videos to watch on Transformers
* Makemore series
	* [Makemore 1](https://www.youtube.com/watch?v=PaCmpygFfXo&t=198s)
	* [Makemore 2](https://www.youtube.com/watch?v=TCH_1BHY58I)
	* [Makemore 3](https://www.youtube.com/watch?v=P6sfmUTpUmc)
	* [Makemore 4](https://www.youtube.com/watch?v=q8SA3rM6ckI)
	* [Makemore 5](https://www.youtube.com/watch?v=t3YJ5hKiMQ0)
* Main [Transformer video](https://www.youtube.com/watch?v=kCc8FmEb1nY&t=13s)

## 01 April 2023
* Quote from aseifert's [article](https://aseifert.com/p/python-environments/): "Pip, venv, virtualenv, pyenv, pipenv, micropipenv, pip-tools, conda, miniconda, mamba, micromamba, poetry, hatch, pdm, pyflow 🤯 These days even the most senior Python developer is confused about all the options to manage environments."
* After successful install of mambaforge from github (see ON notes), i verified that both conda info and mamba info work. Eventually, I should read [this page](https://mamba.readthedocs.io/en/latest/user_guide/mamba.html) from the mamba docs site.
* Took multiple steps, but using [this YouTube video](https://www.youtube.com/watch?v=Qq8gPwRpbp0)I was able to: (1) install mamba, (2) install python 3.10 within mamba, (3) install jupyter lab, (4) activate the jupyter mamba 'space' or whatever it's called, and (5) launch the jupyter server and connect to it from my local web client.
* Out of curiosity, I wondered how well PyTorch works with Apple Silicon and was led by this [reddit comment](https://www.reddit.com/r/pytorch/comments/10g7jw8/state_of_mps_apple_m1m2_support_in_pytorch/) to this PyTorch [GitHub issue](https://github.com/pytorch/pytorch/issues/77764)
* Should go through the basic [PyTorch tutorial](https://pytorch.org/tutorials/beginner/basics/quickstart_tutorial.html) and download the Jupyter notebook to run locally or can run through Google Colab.

## 02 April 2023


# Jupyter Notes
* Mamba + Jupyter setup video [How to install JupyterLab using Mamba](https://www.youtube.com/watch?v=Qq8gPwRpbp0)


# PyTorch Notes

# Mamba / Conda Notes