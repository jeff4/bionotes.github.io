---
title: Notes on git
permalink: /git-notes/
---

## 2023 Log

## 9/14/2023
* Created a git-aware local directory and then pushed it to github. Not optimal, but I used the web UI to create a new repo at github.com.
* Next, I used my terminal to navigate to the local a2-astro directory. I followed [these instructions](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git):
	* `git remote add origin git@github.com:jeff4/a2-astro.git`
	* Then I verified that fetch/pull has the correct URLs (aka authenticated by SSH rather than HTTPS) with the command `git remote -v`
* Then, I used the usual sequence of `git add .`; `git commit -m "this is first comment etc"`; `git push origin`
* However, I got the error that 'fatal: The current branch master has no upstream branch. To push the current branch and set the remote as upstream, use `git push --set-upstream origin master`"
* this worked! However, now I have two branches: `main` and `master`. So I had to set `master` as the default branch and delete the old empty `main` branch. Note that `main` branch was created when I used the web ui to create the GH.com repo originally.  
* OK, deployed successfully to Netlify, and site is live!



## 9/22 Friday
* Next edit `.gitignore` and add `*.swp *.swo` so that git does not track temporary vim files

### commands to use github webui
* Used web app at github.com to create a new repo called `a3`
* Local commandline used these 3 commands in succession
	1. `git remote add origin git@github.com:jeff4/a3.git` This uses SSH to specify what "origin" refers to...in this case, the repo that lives at github.
	1. `git push --set-upstream origin master` This names the main branch master.
	1. `git push origin`  If you try to execute this command before the `git push --set-upstream origin master` command, git has a helpful error which tells you to execute --set-upstream first before git push origin.

## 9/23 Saturday
* succeeded in transferring domains to Netlify and provisioning ssl certs for domain names.


## 9/25 Monday
* In this case, I created the desired `a4` directory first, navigated to there, and within the astro installer, chose `./` as root directory. In previous installs, I went to `proj-n`, ran `npm create astro` command there, and then inside installer, I defined the root directory = `./a4/`.
* Edited `.gitignore` file to ignore vim temp files.
* Followed steps from 9/22 to make sure local and remote branches synch via git. Actually, here are updated instructions. It's four steps:    
	1. `git remote add origin git@github.com:jeff4/a3.git` This uses SSH to specify what "origin" refers to...in this case, the repo that lives at github.
	1. Now, you have to go through usual sequence of: (a) `git add .`; (b) `git commit -m "this is my first commit"`. *Then* you have staged changes on local that allows steps 3 and 4.
	1. `git push --set-upstream origin master` This names the main branch master.
	1. `git push origin`  If you try to execute this command before the `git push --set-upstream origin master` command, git has a helpful error which tells you to execute --set-upstream first before git push origin.
* In the future, I will rewrite the instructions to default naming the origin branch **main** rather than 'master'. 

### Instructions
* [How to manage git branches](https://www.freecodecamp.org/news/git-branching-commands-explained/) by Deborah Kurata at Free Code Camp
