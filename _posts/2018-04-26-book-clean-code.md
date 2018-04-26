---
layout: post
title: Book&#58; Clean Code
tags:
  - learnings
  - books
---

This is a collation of my thoughts on the _Clean Code_ book. It is aggregated from my weekly reviews.

The forward to this book discussed the 5S principles (seiri (整理), seiton (整頓), seiso (清楚), seiketsu (清潔) and shitsuke (躾)) which made a lot of sense to me as principles for writing good code (although I found the explanation in the Japanese wikipedia was better than the one in the book :joy: 
I think Japanese concepts just make more sense in Japanese).

The first chapter discussed different definitions of “clean code”. The key points I took out of this were: bad code always slows you down, and begets more bad code; you can, should and have to fight to implement good code despite deadlines; 
clean code does one thing well; it is clear, easy to maintain and testable; we should aim to reduce duplication and use simple abstractions; work with your language, rather than forcing into something it’s not; write readable code; 
and always leave the code base cleaner than when you found it.

Chapter two discussed choosing names. The core of this was to make them as clear, intention-revealing and easy to use as possible. It also talked about avoiding encoding (including the implementation type in names), being consistent in name conventions, and giving context via classes etc in preference to prefixes. 
In short, your names should help make your code as easy to read, work with and refactor as possible.

Chapter 3 covered functions. Functions should be small, doing only one thing, use only one level of abstraction, have a descriptive name, have no side effects, and have as few arguments as possible. Long switch or if/else statements should generally be replaced by polymorphism (with the one remaining buried in a factory). It is better to have explicit outputs than output arguments, and exceptions should be used in preference to error codes. The contents of each part of a try/catch block should generally be their own method.

Chapter 4 covered comments. The main thrust was that comments should be avoided as much as possible, since they easily become out of date or misleading. It is generally better to write self-documenting code, and use comments only as a last resort (eg. to clarify working around code you cannot alter, TODOs, Javadocs for public APIs, warning of non-obvious consequences, etc).

Chapter 5 discussed formatting. It emphasised readability and consistency, especially when working as part of a team (since the whole team needs to use the same standards). I think the most interesting point it made was that code should be organised like a newspaper article, with the broad overview at the top and the nitty-gritty details at the bottom and a logical flow of information in between.

Chapter 6 talked about objects and data structures. I haven’t really thought about this topic before, so it was quite interesting. The main argument was that the two are opposites - objects expose functions which act on their data (but hide the data itself) while data structures expose their data but have no meaningful methods. This means that objects let you add new classes easily but make it difficult to add functions, and vice versa for data structures. Hybrids tend to have the worst of both worlds, so you should carefully and deliberately choose which you are going to use for each class.

Chapter 7 discussed how exceptions are preferable to returning error codes, since they allow more flexibility for when and how they are handled. It also talked about the importance of ensuring that your exceptions provide enough context, without having too many different types (which must be handled separately). It suggested encapsulating exceptional, but correct behaviour in special case objects rather than using exceptions, and why to avoid nulls where possible.

Chapter 8 discussed the use of boundaries, in particular between your system and 3rd party code. It recommended wrapping calls to 3rd party APIs (or even built-in, which may change) in your own class, so that if or when these change you only need to modify that single adapter class. This also makes testing easier, since you can easily create a test double for the adapter class which does not use the 3rd party code. Finally, it suggested testing the 3rd party API in much the same way you would your own code. This allows you to learn the new API, but later will also assist in verifying that a new version of the API is compatible with your application (or what you need to change).

Chapter 9 advocated that tests need to be maintained as well as the rest of your code. However, since efficiency is less of a concern, you should prioritise readability over efficiency (within reason, since your tests still need to run fast enough to be usable in a pipeline etc). It suggested writing functions within the test code on top your API when tests need to do extensive setup or other repeated calls, to make them more readable (e.g. makePages(1,2,3,4,5) to replace book.addPage(1, whitePaper); book.addPage(2, whitePaper); etc). Each test should deal with only one concept, and minimise the number of asserts needed to test that concept. Finally, it discussed the need for tests to be F.I.R.S.T (fast, independent, repeatable, self-validating, and timely).  
When I looked at my tests for the tic tac toe kata, I felt that I had done fairly well with the recommendations for testing discussed above, except for the repeated calls during setup. I therefore went through and made changes based on the suggestions in Clean Code. I think that this was a good exercise, and definitely demonstrated how it can improved readability.
