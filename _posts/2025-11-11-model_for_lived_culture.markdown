---
layout: post
title: "My Model of Lived Culture"
date: 2025-11-11
categories: [culture, engineering, leadership]
description: "A developer's perspective on how lived culture emerges from tools, practices, and behaviours."
---

# My Model of Lived Culture

I am not a manager. 

I like to write code. I love complex systems. If I have to sit in a meeting for more than an hour or two a day, I go crazy.

That’s why it always feels strange when I hear people talk about organizational "culture" and "mindsets". They're words that usually live with managers, HR, or leadership decks. Culture statements get written in handbooks, not code.

This is a blog post about organizational culture — but not the culture your organization and leadership _say_ they have. This is a blog post about **lived culture**, the one that you're immersed in, all day every day.

---

## Culture as a System

Like a fish trying to understand water, it can be hard to describe what makes a company’s culture work. A fish might notice changes in temperature, pressure, or salinity without understanding why one part of the ocean feels different from another.

Developers working at any organization experience something similar. We can describe the visible patterns of behaviour: scrum ceremonies, pull requests, performance reviews, alignment meetings, and technical practices.  

As much as people love software delivery frameworks, it’s important to acknowledge that two companies with identical processes can have completely different cultures.

That’s because culture is more than just a set of practices or stated values. It’s a **system of interconnected layers** where each one influences, and is influenced by, the others.

- **Practices** — observable patterns of behaviour that show up in daily work.  
- **Tools** — the things that make those practices possible or impossible.
- **Principles** — guidelines for how to uphold your values  
- **Values** — what people believe in and reward.  



![Diagram of the culture system model]({{ 'assets/lived_culture_model.png' | relative_url }})

It’s tempting to think culture flows in one direction: values lead to principles, which lead to tools that enable desired practices.  
But reality is a bit messier. Tools reshape practices. Practices reinforce or challenge principles. And, over time, all of that changes what people truly value.

---

### A Brief Segue on Stated vs. Lived Values

You might notice something odd about my definition of “values.”  

When you look at proper leadership materials that talk about organizational culture, values are described along the lines of *“What the Company Stands For”* or *“Your Core Beliefs and Principles.”*  
Those are **stated values** — the values leadership wants your company to have.

**Lived values** are different. They show up in what people actually believe, what they have time and support to learn, and which behaviours are rewarded.

You can’t claim to have a lived value of *collaboration* if the solo firefighter who ships fast but leaves chaos behind gets the raise, while the engineer who quietly unblocks others and pairs or asks questions is told they’re not delivering enough new features.

---

## The Unique Role of Platform and Data Engineers in Maintaining Culture

Platform and data engineers work directly in the **tools layer** of this model.  
By enabling other teams, reducing their cognitive load, and providing the systems and tools they need to do their jobs, we shape how those teams behave.

A good observability stack can make teams more comfortable with risk.  
A dashboard can make transparency feel normal.  
A brittle deployment process can make caution a cultural value.

Every default, guardrail, and piece of documentation carries an implicit message about what matters.  
Are we optimizing for safety? Autonomy? Transparency? Collaboration?  

The tools we build and the data we make available answer those questions — whether we mean to or not.

---

## Culture is Co-Created

The fact that lived values influence culture should be self-evident.  
If a manager praises independence but discourages visible collaboration, the lived value becomes self-reliance, not teamwork — and the team’s principles, practices, and tools shift as a result.

A company’s culture isn’t just the responsibility of leadership. It’s the **product of the behaviours of every individual** in that company.  

One of the strongest leverage points for influencing that behaviour is building tools that make *“the right thing”* the easy thing.  

That’s the domain of platform and data engineers.  
And I think that’s pretty awesome.

---

## References and Further Reading

As I built this model of lived culture, I drew on some wonderful, thought-provoking articles.  
The core ideas are my own, but they are heavily influenced by the following:

- [OKR Quick Start – The Difference Between Values, Principles and Behaviours](https://okrquickstart.com/post/difference-between-values-principles-behaviours)  
- [Platform Engineering: It’s About Culture, Not Tools — Brian Ross, Field CTO at GitLab](https://about.gitlab.com/the-source/platform/platform-engineering-its-about-culture-not-tool)  
- [Gilbert’s Behaviour Engineering Model](https://sites.google.com/view/hpt-manual/models/gilberts-behaviour-engineering-model)  
- [Updating the Behaviour Engineering Model — Roger Chevalier](https://www.researchgate.net/publication/229651267_Updating_the_behaviour_engineering_model)
- [Arlo Belshee on Gilbert’s Behaviour Engineering Model
 – Arlo’s reinterpretation focuses less on management performance and more on how these dynamics shape lived culture.](https://www.youtube.com/watch?v=H6z2bj5uiYM)

