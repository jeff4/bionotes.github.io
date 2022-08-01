---
title: None
permalink: /si/
sitemap: false
---

*Last updated: 8/01/2022*

per my Wednesday 7/27 phone call with Helena the recruiter, this is what I can expect from each of my 30 minute sessions

* CTO and Co-founder Julianna will want to learn more about my background, my interests, what have I done. JH interjection: probably *why am i interested in Stytch*??
	* perhaps introduce the idea of Start with Why marketing, and how this evolves over time??
* CEO and co-founder Reed: will ask me about my previous PMM experience and future GTM plans. Prep a lot for this.
* Product mgr, former backened security/identity engineer at Slack and Fast Lydia: will ask about cross-team collaboration
* Growth lead, former Partnerships/BD Spyri will ask about cross team collaboration. I may need to ask her about both current growth challenges/opportunities and what she's seen in the past in terms of Partnership challenges/opportunities.


## Initial thoughts

* First, what is the value to the customer? To the various stakeholders? end users, shop owners, and developers?
* Second, how is Stytch's value prop's *differentiated* from all the alternatives that are available to their customer? We have to be objective and honest with ourselves about what is special about us. Empathize with the customer and understand them.
* Next, how do we encapsulate that positioning? And then how do we test those messages??

## Problems Stytch Solves
* Security for site owners
* Improved conversion rates for retailers, anyone with a authentication / authorization flow
* Better user experience for end users and better security / peace of mind

## Questions
* What are the biggest challenges for growth?
* Who is responsible for advertising/measurment? How is this balanced between the Marketing team and the Growth team?
* For Partnerships/BD, what has been most effective as a method of outreach, initial approach, and endgame? What have been the bigggest challenges?
* Also for Partnership/BD, what is the ICP that have been most attractive? 

## Ideas
* Managing transition from direct sales, to partners, to channel
* All about finding the right primitives that are composable.
	* Example obviously of when Amazon first architected AWS.
	* What ECL is trying to build. What are the elements of equipment? What are the parts that are supposed to be automated? What are the right software objects???
* From Moore, p. 149: "When most people think of positioning, they are thinking about how to *make their products easier to sell*. But the correct goal is to *make the product easier to buy*.

## Verticals to attack
* Obviously e-commerce and adjacent territories. Research dev shops that focus on this eg. upwork, fiverr. See updated Google Doc for more on this.
* Regarding attacking finance and healthcare. I'd tread somewhat carefully becaus this is big reward, potentially big risk. Costs in terms of making this bullet proof and making sure it meets whatever regulatory requirements there are. Plus different regulatory regimes around the world. That said, may be critical learning experience here that helps us build competitive advantage.

## Interviews with Reed McGinley-Stempel
* [November, 2021 interview](https://www.youtube.com/watch?v=Ay3NV_UjAIg) with Isaiah Bollinger and Tim Peterson. Episode 60 of The Hard Truth

## Interviews with Julianna Lamb
* Opening sponsorship [video](https://www.youtube.com/watch?v=Y67QW9HKrWA) for SolidJS / SolidHack
	* Open source is super important
	* Open source is core to our ethos
	* Ecosystem is super important. supporting builders everywhere
* LogRocket [video](https://www.youtube.com/watch?v=0LxbIKyMP10). PodRocket. published February 2022. Interview with Julianna
	* Reed and Julianna met at Plaid. Both worked on authentication.
	* Saw downsides of passwords first hand
	* Developer-first approach. To help navigate that transition.
	* Q: Most sites have a social or SSO option. What are the advantages of social or SSO logins.
		* A: We support FB, Apple, all the major social sign ins. We offer other options like magic links side by side. Another advantage: we offer so many other options: SMS one time code, WebAuthn. Concept of step-up auth.
		* A: out of the box, Stytch offers a wider suite of options.
	* **2:54** Magic link. A one time-use token that is appended to a link available as URL or text. 
	* **4:41** Q: What is credential stuffing?
		* A: Matching a lot of passwords from a comproimised list of breached passwords into a webform 
	* **5:28** Q: SMS passcode
		* A: SMS is still reasonable because it's a time-consuming attack for SIM swap attack. Need to convince customer support
	* **7:51** Q: Integration process
		* A: Two main integration options. 
			1. Client side SDK which you can use with a just a few lines of code.
			2. Direct API integration. Backend API integration is better for a better brand experience. Step-up authentication for a more sensitive action. Maximum flexibility.
	* Q:  Brand experience
		* Email magic links accessible through pull-down menu showing email providers where you don't even have to go to  your inbox.
	* **10:41** Q: Step Up Auth
		* Different kinds of access within application
		* Stripe uses this concept a lot. GitHub also uses this.
	* **12:29** Benefits of session management in Stytch
		* A: Session mgt. Know whether the original user who authenticated at the beginning of an engagement is still in the same session. Do they need to recheck session mgt? Introduced concept of step-up auth within the same session. can set more granular session time-outs based on level of step-up.
	* **14:32** Q: What is WebAuthn?
		* A: Great option for 2-factor. B/c you have YubiKey, biometrics, etc. Most sites are still not using this. Stripe and GitHub are early to this.
			* Another advantage: works really well on mobile
	* **15:41** developer experience
		* SDK integration. some config. Select which products you want to show
		* API integration, need to do more heavy lifting. Deciding which auth methods you want to surface.
	* **16:43** Future of password managers
		* A: It's going to take quite a while before we get to the passwordless nirvana. so for now and the foreseeable future, password mgrs will be useful
		* Also
	* **19:23** Long term goal for user experience at Stytch

## Simon Sinek
* Original 2011 TED Talk video [here](https://youtu.be/u4ZoJKF_VuA)
	* Section on Apple begins at 4:15
	* Here's how Apple *acutally* communicates: 
	* **Why** "Everything we do, we believe in challenging the status quo. We believe in thinking differently. 
	* **How** "The way we challenge the status quo is by making our products beautifully designed, simple to use, and user-friendly."
	* **What** "We just happen to make great computers. Wanna buy one?"
* Goal is shared values. We buy from people who believe what we believe
* Sales objection: "It just doesn't feel right" comes from the inner limbic system.
* If you hire someone just to do a job, they will work for the money. But if you hire people who believe what you believe, they will work with blood, tears, passion.
