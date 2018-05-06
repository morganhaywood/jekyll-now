---
layout: post
title: Week Twelve in Review
tags:
  - weekly review
  - meaningful project
  - ctf
  - books
  - katas
  - agile
  - networking
---

This week has been once again filled with workshops and meetings. I did get some other work done though, and they were necessary in order to be able to start the group project next week (which I'm looking forward to :blush:).

## Goals

#### Document what I've learnt from doing ctfs.

Done :star2: The blog post can be found [here]({{site.url}}{ % post_url 2018-05-01-ctf-learnings %}).

#### Do enough planning that we can start working on the group project.

Also done :smiley: Well, next week will be a lot of investigating technology and design choices, but the project will officially start!

#### Do at least one more natas level.

And finally, also also done! So three for three :star: I did a few more levels since there was a run of quite easy ones. I think it may be a while before I do more now though, since the group project is starting.

---

## Tasks

#### _Clean Code_ chapter 10

Chapter 10 discussed how classes should be organised. Variables should generally be public-static, then private-static, then private (since there is generally no reason to have public variables). Functions should follow a similar scheme: public first, but private methods should follow the public method that calls them rather than all being grouped at the end. Protected should generally only be used if absolutely necessary for testing.  
Classes should be as small as possible, and have only a single responsibility. Tied to this, they should also be cohesive, in that all the methods use most (if not all) of the same variables. When a class loses these properties, it should be split into two (or more) classes. Having many seperate, small classes means that each class will only have **one** reason to change. Thus changes won't break existing code (or as little exiting code as possible). This conforms to the open-closed principle: classes should be open for extension but closed for modification. In general, you should therefore be dependent upon interfaces rather than concrete classes (i.e. use the dependency inversion principle).

#### Scrum workshop

This workshop took us through some basics of scrum. I used scrum at my previous work (or at least, a lose interpretation of it) so I don't feel like I got as much out of the workshop as I would have if I had no experience in scrum. While it was good to get a refresher in some of the details, I learn faster from reading so I would have preferred to be given a book to read in two or three hours rather than a full day workshop :stuck_out_tongue: I think it was useful from a team-building perspective though.

#### Natas and Krypton

As mentioned above I did a few more levels of Natas, which introduced more concepts around sessions and code injection. I also got half way through Krypton (which admittedly is only seven levels, unlike Natas' 33). I found Krypton an interesting refresher on some basic cryptographic concepts.

#### Project planning

We had a couple of meetings to bring our mentors up to speed on the project, and do offical kick-off. The latter of these two was really useful, with Terry and Justin taking us through some basic first steps to defining the problem and planning the solution. We also had a quick sprint planning session with just the three of us. So we're ready to start working on the actual project on Monday! :grin:

#### Learning Go

While we haven't decided on a language for the project yet, we will most likely be using Go since that what the team who will have to maintain it prefers. We therefore asked Dede to give us a quick overview of the language, which was very useful :blush:

#### Dynamic scaling and self-healing instances workshop

JC and Prateek explained how auto-scaling and load balancing works, with reference to AWS. The load balancer routes traffic to equalise the load across servers. It needs to be able to perform health checks on all severs, so that it knows they're able to serve traffic before it routes any there. Auto-scaling uses cloud formation to provision additional servers when load increases beyond a given point, or if a server dies etc. (or conversely decommission servers during low load).

#### Code review with Jon

Jon was generally happy with my Tic Tac Toe kata (and it was definitely an improvement on my Game of Life kata, which he previously code reviewed) which I was very pleased about :satisfied: Of course there were still improvements which I could make: my tic tac toe class needs to be split into two classes, I should make my game rules class into an interface so I can use it to drive my tests (instead of using i/o), my test doubles should be more dumb and specific, I need to make sure my unit tests properly test **all** business logic, and I should more any switched into my builder classes. I am glad that I have improved since his last code review though!

---

## Takeaways

* Projects take a lot of planning to get started, especially when you haven't really done one before.  
* Pay attention to class structure and single responsibility.  
* The cloud makes server management much easier.  
* It's useful to have the same person code review your (corrected) work again.

---

## Next Week's Goals

* Decide on a tech stack for the group project, and high-level design.  
* Set up a good workflow for the project team.  
