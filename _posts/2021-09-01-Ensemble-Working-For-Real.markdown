---
layout: post
title:  "Getting to Ensemble on Real Code"
date:   2021-09-01 06:54:00 -0600
categories: mob programming
---

A few days ago, I was talking to a developer I really respect about the challenges he faced introducing the idea of coding as an ensemble in his workplace. Having multiple developers working on the same problem at the same time is a tough sell to a manager or director who's only ever worked or seen work done asynchronously. Aside from convincing his leadership team of the value, he was concerned about gaining traction among the developers he works with.
> Individual devs might actually be the toughest sell. Most people are pretty introverted and pretty anxious about people watching them type at all.

He's right. An ensemble can be an incredibly intimidating idea the first time you encounter it, and it can easily be seen as a waste of time. Because of how easy it is to misunderstand, it is extremely important to be conscious of how the idea is presented and propagated at your organization. It's easiest to start ensemble working if your organization sees it as a supportive environment for rapid problem solving. 

In order to help me remember how to do this, and potentially help others who might be uncertain of where to start, I've compiled a list of things that I did, along with tips and ideas from other experts in the industry. These items and ideas have worked in at least one context, so they may work for you in yours. Feel free to adapt and adjust them to your needs.

**Before you start.** Go to a few ensembles, and ensure you understand the basic mechanics of the different roles and rotation times. Take time to [read a book](http://www.mobprogrammingguidebook.com/) or watch some episodes of a [podcast](https://www.youtube.com/channel/UCgt1lVMrdwlZKBaerxxp2iQ) about how and why ensemble working is effective. A new mob behaves entirely differently from one that’s well established. The rigid structure of the roles and timer allows team members to figure out how to make space for each other and fosters dynamics that are simply not possible with solo work. You are going to need to explain the process to your team, so you want a solid basis on how and why mobs work the way they do.

**Socialize the idea of ensemble working.** Look for opportunities to raise awareness about the concept of an ensemble, and how it might benefit your team. Have discussions where you happily listen to other people's opinions on the topic, even if they disagree. If developers and managers have previously been exposed to the idea, and they know you are not dogmatic about it. They’ll be more likely to be curious, and willing to investigate further.

How to do this:
* Share your favourite mobbing articles in your office slack channel ([here's one of my favourites](https://jessitron.com/2021/03/27/those-pesky-pull-request-reviews/))
* Watch for problems that mobbing could help solve and mention that mobbing might be helpful.
* Start a book club reading a book that happens to talk about the benefits of collaborative coding. ([Team Topologies](https://www.amazon.ca/Team-Topologies-Organizing-Business-Technology/dp/1942788819/ref=sr_1_1?dchild=1&gclid=CjwKCAjwybyJBhBwEiwAvz4G7w8ddo_BaXAKV9K43CSwzQxRG8lJhMuUk2cp7lJDXiIL5naTCLe9MxoCY-EQAvD_BwE&hvadid=357275073039&hvdev=c&hvlocphy=9001335&hvnetw=g&hvqmt=e&hvrand=18116534911720749592&hvtargid=kwd-723035983914&hydadcr=26027_9772381&keywords=team+topologies&qid=1630503542&sr=8-1) and [The Pragmatic Programmer](https://www.amazon.ca/Pragmatic-Programmer-journey-mastery-Anniversary/dp/0135957052/ref=sr_1_1?crid=3BY7BSFC0LBFU&dchild=1&keywords=pragmatic+programmer&qid=1630503608&sprefix=Pragma%2Caps%2C224&sr=8-1) both discuss the benefits of ensemble working.)
* Share meetups that give their members an opportunity to try out working as an ensemble ([like mine!](https://www.meetup.com/Calgary-Software-Crafters/)) and invite your team members to join you
* Repeat the above and any other soft introductory steps as you see fit

**Baby Mobs.**  Start facilitating small, low stakes ensembles. This isn’t always easy to do at work, but it's incredibly valuable for socializing mobs further if you can. In order to do this, you need to find something your leadership will find valuable, that is also simple enough that it creates a safe environment for anyone who joins. As these will likely be the first ensembles you’re facilitating, it’s a good idea to keep them small, and only involve people who self-select into the process. I found it took me about 10-15 of these sessions before I was actually comfortable running mobs on production tasks.

Tasks I’ve picked: 
* Simple refactoring of a piece of code (leadership was on board as this was a KT activity about an area with a deep knowledge silo)
* Doing a kata (This was picked by the team as they wanted to learn how TDD worked. Management was on board because this let me teach 4-5 developers the skill at once)
* Running a mob in other areas of the company, or with other departments as a networking event.

**Preparation for the real thing.** Once the idea of ensemble work is well-socialized at your company, and you have a few people who might be willing to try it on real code, it’s time to figure out details to make sure that your first experiment is a success.  If you’re remote, you’ll need to figure out details about how you’ll share the code to enable quick rotations. [Emily Bache’s Samman book](https://leanpub.com/techagilecoach) has some excellent suggestions on remote mobbing setups. If you’re co-located, you’ll need to find a space in a conference room with a large enough screen that everyone can see what’s happening at the same time. You should also consider any setup you may need to do in order to run experiments and prove effectiveness.

**Do the real thing.** This is the tricky bit. You need to find an opportunity where developers are willing to work with you, and leadership will see the value of using this new way of working on real code. For this reason, I would probably repeat the steps above until a team _invites me to help them_ by facilitating a mob or look for opportunities where an ensemble will really shine. Situations like onboarding large groups of developers, exploring a new problem space, or working with a group of new programmers are all tasks that highlight the benefits of working this way.

**Proof.** Not only is it important for your ensembles to _be_ effective, you need to be able to prove their effectiveness in a way leadership and developers will understand. Proof can take many forms, and the best format will depend on who you’re trying to convince. Here are some options you might want to try:

* Testimonials - If your mob had a good time, ask them to share their experience. This can be really powerful, as you aren’t the only voice pushing for mobbing anymore
* Daily log book - Keep a journal of the 3-5 most significant things that happened in the mob that day, including things that blocked the mob. Share them with whoever asks. 
* [The Puckett Experiment](https://www.youtube.com/watch?v=h-baijxbBYs) - Divide sprint work into two categories, one set to be done as an ensemble, and another to be done asynchronously. Work on the ensemble work 2 hours a day for a month. Measure the cycle time (time from start to delivery) and velocity (number of story points done in a sprint) of each type of work. Compare the two values at the end of a month.

That's all I've discovered so far. I may add to or adjust this article as I learn more. Please let me know what you find helpful and what works for you.
