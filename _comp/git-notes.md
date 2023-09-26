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

### Deborah Kurata articles at Free Code Camp, from 2023
1. Conceptual introduction to branching in Git (Feb 2023). [Link](https://www.freecodecamp.org/news/how-to-work-with-branches-in-git/) 
1. [How to manage git branches](https://www.freecodecamp.org/news/git-branching-commands-explained/) (March 2023)
	* Remember, when you type `git add .`, you are adding files to the Git staging area. You can think of staging like a shopping cart before you check out.
	* When you type `git commit -m "comment"`, that is when you actually check out and hit buy. Remember, this only commits things to your local repo; *not* your remote origin repo (i.e. at GitHub.com)






### Conceptual introduction to branching in Git 
* [Atlassian article](https://www.atlassian.com/git/tutorials/using-branches) and associated [YouTube video](https://www.youtube.com/watch?v=S2TUommS3O0)

* Possibly best article? -- [git branches article by Noble Desktop](https://www.nobledesktop.com/learn/git/git-branches) including diagrams and commands

### Git-Tower articles from circa 2015
1. [An introduction to Branches](https://www.git-tower.com/help/videos/learning-git-with-tower/introduction-branches) by git-tower.
	* Associated [video](https://www.youtube.com/watch?v=Ao1beK2rEIY)
	* HEAD and 'checked out' branch are synonymous.
	* There can only be one active or 'checked out' branch at a single time.
	* The checkout command moves the HEAD pointer to a different branch. It makes the other branch the currently active branch now.
1. Next article [Creating and Checking Out Branches](https://www.git-tower.com/help/videos/learning-git-with-tower/creating-branches)
	* [Associated video](https://www.youtube.com/watch?v=8jLJHCcu7r4)
	* video uses git-tower gui.
1. [Merging Branches](https://www.git-tower.com/help/videos/learning-git-with-tower/merging-branches)
	* [Associated video](https://www.youtube.com/watch?v=hGmPhhdBAHE)
	* Note: when merging branches, remember that you first have to change the HEAD to the *receiving branch* (aka where the new commits will merge *into*). Merges always have to be received, they are never pushed from the originating branch. So always checkout the receiving branch, probably 'main' or 'master'
1. [Dealing with Merge Conflicts](https://www.git-tower.com/help/videos/learning-git-with-tower/merge-conflicts)
1. [Undoing Things](https://www.git-tower.com/help/videos/learning-git-with-tower/merge-conflicts)
	* "Git allows you to undo almost anything. Knowing this should let you sleep a bit easier at night." 


### Operations/experimentation with a2-astro
* First, rename local branch from 'master' --> 'main'. Let's use [this stack overflow answer](https://stackoverflow.com/a/30590238). I got it working but it was a bit complicated, involving going to the github web UI to manually changed default branch from 'master' to 'main' before `git push` worked. Probably not worth it for now. Also, there was no auto-deploy on the netlify side until I did some config to make sure Netlify was responding to the new default branch 'main' rather than the older 'master'.
#### Experimenting with `footer-edits` branch
* Instructions adapted from [2nd Deborah Kurata article](https://www.freecodecamp.org/news/git-branching-commands-explained/).
1. Verify that you are on main branch with `git checkout main`. (alternately, `git branch` will show a star next to `main`).
1. Next, create a new branch with the command: `git branch <NEW-BRANCH-NAME>`. In this case, i typed `git branch footer-edits`.
1. Then switch to the newly created branch: `git checkout footer-edits`.

* Next, let's try creating a little mini branch 


### Consolidated list of git commands
* to see local branches only, `git branch`
* to see remote branches only, `git branch -r`
* to see all local and remote branches, `git branch -a`


* Good summary of [git branches](https://www.nobledesktop.com/learn/git/git-branches) including diagrams and commands







