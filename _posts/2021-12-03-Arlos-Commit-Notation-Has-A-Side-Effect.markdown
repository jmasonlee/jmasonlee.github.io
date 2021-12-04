---
layout: post
title:  "Arlo's Commit Notation Has a Side Effect"
date:   2021-12-03 06:54:00 -0600
categories: TDD
---
I love TDD.

I struggle with the red-green-refactor cycle of TDD.

I understand why each phase is important, but I also have a brain that is easily distracted, and doesn't like to think too far ahead. Keeping each step separate and "small" is a struggle, because I usually figure out what would make my change easier about halfway through the (not-so-easy) change. In my mind, this is part of the cost of implementing the new feature, and it usually means that I'm refactoring at the same time as I try to make a failing test pass.

One of the things that should make TDD easier is that I can focus on one failing test at a time. Doing the simplest thing that could possibly work (and only that) lets me solve problems in small steps, without worrying about a lot of mental overhead. This makes me go faster. At least, it should. In theory. 

In practice, doing refactorings with feature changes makes TDD an impossible slog. When I tried TDD in my work code, I would definitely get the benefits of unit testing and a testable design by writing my tests first, but I couldn't seem to go faster. In fact, because I couldn't understand how to separate the refactorings from the actual feature implementation, most of my focus would be on solving the next failing test. This meant I'd need to think about the feature I was implementing, as well as how it should be designed. I was holding a lot in my brain, and this slowed me down. 

Eventually I'd go back to my old method of coding - design a feature upfront, code the whole thing, write tests. Although I'd wind up with a few tricky bugs at the end, this let me separate my design-thinking from my code-thinking, so I could deliver faster than when I did TDD.

At this point, I'd been running the Calgary Software Crafters for a few years, and I understood the theory behind how TDD enabled faster delivery. I'd also seen enough videos on it to guess the reason I was going so slowly was because I needed to get better at the refactor step, and make adding features easier. I just couldn't see _how_.

## A Side Effect of Arlo's Commit Notation

I was stuck. I still believed in practising and learning my tools, I still wanted to write quality code, but without the increase in speed, I didn't understand how TDD was better than testing last for doing that.

It was at this point that I attended a course by Llewellyn Falco and Jay Bazuzi where they talked about cleaning code safely without tests. One of the tools they presented in the course was a new way of marking commits called [Arlo's Commit Notation](https://github.com/RefactoringCombos/ArlosCommitNotation). The intent is to make the commit history more scannable for the relative risk and type of each change, in order to help with code review and finding bugs.

I decided to apply the new tools I'd learned to my regular practice sessions. After a few katas working in this way, I started to notice a side effect of Arlo's Commit Notation that didn't really match it's original intent at all. When I used it, disciplined, high-order TDD became easier. Without it, I was back to the same old refactor-and-add-feature slog.

It took me a while to figure out what was going on. By asking me to identify type of change I was making on each commit, Arlo's Commit Notation forces me to pay attention to what I'm doing in each step. Because I mark each commit based on it's level of risk, I am constantly assessing the impact of my changes, and whether or not I could make those changes in a less risky way.

The new feature label is what really changed how I worked. In Arlo's Commit Notation, the least risky feature changes are labeled with an "F  ", while the more risky ones are labelled "F!!" or "F**". In order to achieve that coveted "F  ", I need to add a new feature in 8 lines of code or less. This means that the feature needs to be really easy to add, which usually means I need to refactor to make the change simple. 

At first this was difficult, and it took a long time to achieve, but as I continued writing code using this notation, I began to notice my code becoming easier to change. Because I'm always changing my code in order to add features more easily, I'm constantly optimizing for changeability in the right places, and it's more likely that new features will be easier to add. I have to think about design less and less. This allows me to TDD more quickly, and better than before.

I'm still not perfect at TDD. Figuring out a series of small steps that would make adding a feature achievable in 8 lines or less is hard, it takes time, and sometimes I still can't do it, but sometimes I can, sometimes I can do it quickly, and sometimes I can do it so quickly that it feels effortless. This side effect of Arlo's Commit Notation is a big part of why that's possible.