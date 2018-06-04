---
layout: post
title: Week Fifteen in Review
tags:
  - weekly review
  - meaningful project
  - books
---

This week has been very productive. We now have a good workflow going, and have made a lot of progress on getting something useable made.

## Goals

#### Get something useable working for the meaningful project

It's not particularly pretty yet, but we have functional code which is a solid foundation for moving forward.

---

## Tasks

#### Mobbing

We spent most of the week mobbing on both the front and back end of the project. We made a lot of progress, especially after we pulled an experienced Go programmer into the mob for a couple of hours to give us a good path to more forwards on. We're getting better at the whole mobbing thing, although we need have a ways to go before it's really smooth. That said, I definitely prefer when we had 3-4 people, rather than when many others joined us and we had 5-7.

#### Idiomatic Go

The other thing I spent a lot of time on this week was trying to figure out what **idiomatic** Go looks like; I feel like I often fall back to writing Java in Go, but they're very different paradigms. We had a good chat with Mel about it, as well as a couple of others, and I did some of my own research. I'm still no there yet, but I've definitely improved.

#### Story slicing workshop: hamburger method

We had a workshop on using the hamburger method to slice up stories and plan sprints. I don't feel like it entirely clicked with me, but it was really useful to see one method for planning. It certainly would have been useful to know this method at the start of the project :joy:

#### _Clean Code_ chapter 14

Chapter 14 is a case study showing how successive refinement can lead from a first draft of a program to a cleanly-written program. Rough drafts are necessary, but once you have enough information to understand what the design **should** be, but before your program gets too big to fix, you should stop adding features and take the time to clean what you have done. To do this you need to make incremental changes that move towards a better structure, but don't break the code. Having a test suite helps with this, since you can ensure that the program still works by checking that the tests pass. In general this sort of refactoring is a long process of splitting out one thing at a time (e.g. a new class, then gradually turning that new class into an interface and sub-class structure). Sometimes there is no **perfect** solution though, and you have to compromise.

#### Concurrency vs parallelism talk

I watched a video of a talk on the difference between concurrency and parallelism. It basically came down to concurrency being how many things can run **independently**, and parallelism being how many things can happen at the same time. Thus you need concurrency to make any good use of parallelism, but not vice versa.

#### Meeting crew

I had lunch with the crew I'm going to be moving into after the project. It was good to meet everyone, and I'm looking forward to joining them! :blush:

---

## Takeaways

* learning a new work style takes time
* learning a new programming paradigm takes time
* it's encouraging to be making progress

---

## Next Week's Goals

* Get better at mobbing
