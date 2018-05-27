---
layout: post
title: Week Fifteen in Review
tags:
  - weekly review
  - meaningful project
  - ctf
  - books
---

This week was a bit strange for me, since I was only in the office for two days (I was working from home for two and a half, and on leave for half a day). I feel like we made a lot of progress on the meaningful project though.

## Goals

####  Get some real data into a database

This has been achieved!

#### Get that database accessible

This was mostly done, and then we changed some things... It should be working again by Monday though.

---

## Tasks

#### Data import

The spreadsheet data we have had a lot of inconsistencies in it, so I spent some time cleaning it to prepare for import. I also wrote some queries to import the data into our database (and got them testing and verified as working), but since we decided to change to a different one that won't end up being used. Oh well, such is agile (and our lack of understanding the project planning steps initially :stuck_out_tongue:). Finally, I also got some of the less-structured data into a spreadsheet so we can start working on importing it as well.

#### Bandit

In the interest of continuing to devote some time to learning specifically (despite working on the meaningful project), I redid Bandit. It didn't take me long at all, but it was good to both refresh my memory on some commands I haven't used much, and to see how much better I've gotten at the command line over the last few weeks.

#### Front end mobbing

I spent a bit of time mobbing with Sol, Ryan and Tony on the front end. I was working from home at the time which wasn't ideal, but it was good to see how to set up a new project. I have done a bit of front end work before, but it was all making changes to a well-established project.

#### _Clean Code_ chapters 12 and 13

Chapter 12 discusses how simple, well-written code tends to be clean naturally. Specifically, if you follow the four rules of simple design then it almost unavoidable to end up with clean code. Rule 1 is to run all the tests, and easily testable code tends to be clean. A good test suite also makes refactoring easier, which leads to cleaner code. Rule 2 is to have no (or minimal) duplication, which removes work, risk and complexity. Template methods are a good way to do this; you implement all the common parts (sub-methods), and leave the variable section (sub-method) abstract, then sub-class it with concrete implementations. Rule 3 (express the intent of the programmer) naturally leads to meaningful names, small classes and standard nomenclature. Finally there is rule 4: minimise the number of classes and methods. It must be kept in mind that the rules are ordered, and therefore this is the lowest priority. It is bad to have too many tiny classes, but at the same time it is worse to have one huge one.  
Chapter 13 covers (some of) concurrency. It is a very long chapter, and expected from the complexity of the subject. Concurrency decouples the **what** from the **when**. This can improve structure and throughput, but also introduces complexity which can do more harm than good. There are four basic principles to keep in mind when working with concurrency: the single responsibility principle (concurrency is one responsibility); to limit the scope of data; to use copies of data; and that threads should be as independent as possible. Other things to keep in mind include: understand your language's standard library an work with it; learn common execution models and how to solve the problems inherent in them (e.g. producer-consumer, readers-writers, dining philosophers); only have one synchronised method per class (use a client-based lock, server-based lock, or adapted server to achieve this if necessary); keep synchronised sections as small as possible, since these are bottlenecks; shutting down is very difficult, so if it's necessary then plan early; treat any unusual bugs or failures (especially sporadic ones) as threading issues; run your tests with many threads, on many OS and in many configurations (e.g. using jiggling); and keep your threaded and non-threaded code seperate and pluggable so that each can be tested independently of the other.

#### Solution options and architecture

We finally completed the solution options document, got it distributed to stakeholders, and had a meeting to decide on which to go with. It is good to have made a decision and be able to move forward with it! We then started working on a basic outline of the architecture, which needs a bit more work.

---

## Takeaways

* Upfront planning is best done up-front  
* You still learn a lot from spikes though, even if you end up using a different option  
* I have made a lot of progress in the time I've been here  

---

## Next Week's Goals
 
* Get something useable working for the meaningful project
