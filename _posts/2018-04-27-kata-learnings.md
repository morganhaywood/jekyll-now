---
layout: post
title: Kata Learnings
tags:
  - learnings
  - katas
  - tdd
---

During acceleration I have done many katas. In the interest of record keeping, here's a summary of what I've learnt from those exercises.

First off, dependency injection and the usefulness of interfaces in general. In short, this involves making dependencies on interfaces rather than implementations, and passing in the instantiated objects via an injector class. This leads to loose coupling, more extensible and maintainable code, and much easier testing.

Shortly after learning about dependency injection, I did some research into test doubles and mocks (since using dependency injection assists with using doubles and mocks for testing). I found that test doubles are essentially a bare-bones implementation of an interface, which generally return static data (e.g. `getHeight(){return 3;}`). Mocks on the other hand test the internal workings of your implementation (e.g. how many times `getHeight)` is called). Thus mocks are generally frowned upon (implementations should be able to be changed without breaking your tests), but test doubles are very useful for isolating tests, or testing when you haven't written the other class yet, etc.

I have also become much more confident with JUnit. I have learnt how to set up, perform and check the results of each test. I have also had demonstrated the importance of examining only one concept per test, with as few assert statements as possible.

I also did some research and found how to use rules in JUnit to create a temporary folder. This is very useful for testing with IO, since you don't need to worry about old files being left around; they are automatically destroyed when the test finishes running.

During his code review, Jon discussed with me the importance of identifying which parts of my application should be able to be swapped out for another, similar class. This helped clarify the purpose and advantages of loose coupling for me, and which parts of applications should be in this category.

Jon also explained to me how package organisation and naming can help reveal your intent. For example, if a `page` is only ever exists as part of a `book`, then it should be part of (or a sub-package in) in the `book` package. This helps tell others how your classes should be used.

Short, clearly named methods are also something of which I have come to learn the importance. This makes code much easier to understand, and therefore debug. Clear names also help identify where one method should be broken up; if you're naming something `createBookWithTableOfContentsAndIntroductionAndSnazzyCoverBasedOnIntendedAudience` then it's probably trying to do too many things! Crucially, each method should do _one_ thing.

I have also learnt to think about layers of abstraction. Functions which deal with a high level of abstraction (e.g. `createBook`) should not also deal with lower levels of abstraction (e.g. `addNewline`). Keeping to one level of abstraction makes the code much more readable, since you do not need to switch between conceptual levels, and helps keep methods short (since lower levels of abstraction must be pushed to separate methods).

To support all of this, I've learnt a lot about test driven development (TDD). TDD helps you design your way towards an end goal, and ensure that it stays loosely coupled etc etc along the way. Yu should start with the highest-level test you can, which will look very similar to your eventual main method. You then work your way down, avoiding creating any concrete implementation for as long as possible. Throughout this process, you should write tests **just** before the code which they test. You should ensure that your new test fails, then make it pass as quickly as possible, and then refactor your code to make the code as clean as possible.

This brings up two key points: only the public interface is ever tested, and refactoring does not change the public interface. This means that you **never** test implementation, only behaviour. Additionally, refactoring will not break your tests.

Finally, the katas on which I have paired have taught me that everyone has different styles of working. When pairing with someone, it's important to reach a style which you are both ok with (even if it's neither of your ideals). Compromise and communication are key! That said, it's always much easier when your preferred styles are compatible :wink:

While I'm sure there's a lot more, less concrete things I have learnt form the various katas which I have done, I think that sums up the highlights! :innocent:
