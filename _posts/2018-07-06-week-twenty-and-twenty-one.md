---
layout: post
title: Week Twenty and Twenty-One in Review
tags:
  - weekly review
  - ci/cd
  - books
  - security
---

It's been a somewhat long two weeks, with a lot to learn from my new crew. I think that I'm settling in well though :smile:

## Goals

#### Settle into my new crew

I think I've settled in quite well. Everyone is friendly and happy to answer questions, which helps a lot :blush:

---

## Tasks

#### Moving to a new crew

I've spent most of these two weeks pairing with other members of the crew on their work. That's been very useful for learning how more experienced developers work, and also the crew's code base etc. There's been a lot to learn about the services they work with! Since it's towards the start of a new project one of the things I paired on was the ci/cd pipeline (e.g. adding environment variables to the deployment); since I'd just been working on our meaningful project's pipeline, it was nice to spend a bit of timing working on something I was more familiar with. I also got to see some of the security review process, which was very interesting. Towards the end of the week I was given a task to work on by myself; I still had a lot of questions, but it was nice to take a break from pairing occasionally. So far I'm enjoying working with the crew.

#### _Clean Code_ chapters 15, 16 and 17

Chapter 15 was a case-study of tidying up a JUnit class. There were a few points to come out of this. Refactoring is an iterative process; you may well undo a refactoring you've just done. You should write your code so that temporal coupling are explicit (e.g. have the second method take the output of the first). Choose whether to have variables be 0- or 1-based depending on where the +/-1s are the most readable. Refactoring can help expose useless statements. Group functions together based on their purpose (e.g. analysis vs formatting). 

Chapter 16 was a case-study of refactoring the `SerialDate` class. This was far more extensive than the chapter 15 case-study. The first thing to do before refactoring is to ensure that there is sufficient test coverage, and that all the tests pass.Then you can being the refactoring process, running the tests after each step. Comments should not include the change history, or html formatting, and should provide additional information; delete any unnecessary comments. `Enums` are usually better than constants, especially since they can include functions (e.g. for parsing). The same goes for things like switch statements. Variables and methods should be kept in the class that actually uses them; things which are only used in derivatives should not be in the base class, and things which need no knowledge of the derivatives should be in the base class. Base classes should not know anything about their derivatives. E.g. abstract factories can be used to maintain this. Things should be `private` by default, and only `protected` or `public` where necessary. It's better to have two separate functions than to pass flags, especially if it's just for formatting. Good naming and temporary, intermediate variables help to explain methods. Methods which are only used by the test suite can probably be deleted. Make logical dependencies clear through the structure of the code. `Enums`, and `static` variables and methods, can usually be moved into seperate utility classes. Abstract methods should be at the top of the class. 

Chapter 17 contained a long list of smells and heuristics:  
**Comments** should only hold information which is necessary and cannot be found elsewhere, and should be short and well-written. Code should not be commented out; it is better to delete it and use the source control system if you ever need it back.  
The **environment** should be a single step to build, and a single step to test.  
**Functions** should have as few arguments as possible, should not use output arguments, and not use flag arguments. They should do one thing, and use one level of abstraction. Uncalled functions should be deleted.  
**Names** should be clear and meaningful, and use the right level of abstraction. They should be unambiguous, and follow any standards or existing nomenclature. They should indicate any side-effects. Names should not encode type or scope. All things should do what they say on the tin.  
**Tests** should cover all conditions and validate all calculations. Coverage tools are useful for indicating where more tests are needed. Trivial tests are still worth writing for documentation. You should still write tests where there are ambiguities; you can `@Ignore` them or comment them out, but they will help document where clarification is needed. Always test boundaries, and write extra tests in code close to where you've found a bug; these areas are prone to error. Patterns of failure are useful for finding bugs; design or structure your tests with this in mind. Finally, tests must be as fast as possible to run.  
**Java** should import packages in preference to classes. Classes should not inherit just to access constants, and should use enums in preference to constants anyway.  
In **general** should try to only use one language per source file as much as possible. Implement obvious behaviour, which your users will expect. Avoid overriding safeties. Don't duplicate code or functionality. Group levels of abstraction. Don't couple base classes to their derivatives, or anything that doesn't need to be coupled. Keep interfaces and methods small. Delete code which is never called, and remove clutter. Order variables and private functions near to where they are first used, and be consistent. Functions should not be overly interested in the internals of other classes. Don't obscure intent, and put responsibilities where they are most expected. Err towards non-static functions, and carefully check that all static functions do need to be static. Use intermediate variables to explain calculations and functions. Make sure you fully understand your algorithm, and can verify its correctness. Make logical or temporal dependencies physical through code design. Use polymorphism over selectors; you should only need one selector of each type (to set up the polymorphism). Follow common conventions, especially within the team, and enforce these using code structure where possible. Use constants over magic numbers. Deal with edge cases and eliminate any possible imprecisions. Encapsulate condition checks, especially boundary conditions, and express these as positives where possible. Make sure that your structural choices are deliberate, and that your reasoning is expressed in the structure. Keep all configuration in one place at a high level, even if you expect it to never change, so that it is clear where these defaults are coming from. Only call methods on your variables, not your variables' variables; you shouldn't need to transverse project structure.  
Despite all the above rules however, this chapter makes the point that the values behind them are more important than the rules themselves.

That just about brings me to the end of the _Clean Code_ book (there is still one appendix which I think will be worth summarising, and an epilogue, but I won't bother with the other two appendices since they're a code listing and a cross-reference). _Clean Code_ has been an interesting read. As it stated, I think that the values are far more important than the rules it expounds. We should all strive for well-designed, easily understandable, and provably correct code. A lot of this book however is either Java-centric or personal preference. For example, many of the design principles are simply not applicable (or will make your code far **less** clean) outside of the object-oriented world. And I don't agree with everything in it (e.g. some of the **lengthy** method names I find far less clear than a shorter, less precise one). On the whole though, I think that is a useful window into **one** method of working towards good code, and its core values should be taken to heart.

---

## Takeaways

* Learning a new group of services and code base takes some time
* I joined the crew at a good time: just as coding was starting on a new project
* It's interesting to get different perspectives on things
* It's going to take a while before I get up to speed with things, but I should focus more on learning for now

---

## Next Week's Goals

* Continue learning from other members of the crew
