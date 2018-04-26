---
layout: post
title: Books Roundup
tags:
  - learnings
  - books
  - roundup
---

This is a summary of the books I've read, and what I thought of them :innocent: It's largely pulled from my weekly reviews, and will be updated as appropriate.

## _Apprentiship Patterns_

I found this book a very quick, interesting read and well worth the time. It posits that the first step on the long road to mastering the craft of software development is becoming an apprentice. 
It also advocates enjoying this stage, where you can focus on learning rather than other obligations. Finally, it tries to instill a commitment to developing good, life-long learning habits. 
I think that I should keep in mind the attitude promoted in this book.

## _New Programmer's Survival Manual_

Chapter one of this book focused on writing good code. 
It advocated paying attention to writing correct, clean, modular and readable code; writing tests, and testing early and often; and making use of frequent code reviews. 

Chapter 2 discussed the importance of choosing your language and platform to suit the task, and working idiomatically in them rather than trying to force them to be something they’re not. 
It also taked about choosing your tools carefully, and updating them as appropriate.

Chapter 3 discussed the need to find a mentor, and be aware of your personal image. It talked about performance reviews, why they’re important, and how to make them as pain-free as possbile. 
It also included suggestions for how to manage your stress levels and ergonomics.

Chapter 4 covered working with other people, who will likely have different personality types. You need to learn to work effectively with people with different perspectives. 
You need to be aware that influence is not always connected to the formal organisation chart; personal connections play a large role. 
Knowing who to get on side before pitching ideas, or who will know the person to ask about a topic, is very valuable. Finally, meetings should have a clear purpose and be constructive.

Chapter 5 talked about different roles with the engineering department and the wider company. 
It suggested how to begin a conversation with people in various roles, and emphasised the value in getting to know people from a wide variety of backgrounds.

Chapter 6 discussed project and product life cycles, and how your role changes depending on where your product is at. It also suggested taking time to consider your role from the company’s perspective. 
Finally, it discussed some red-flags when it comes to business practices.

Chapter 7 focused on self-improvement, how to keep a positive outlook and continue learning, and future career goals.
I think that the main takeaways from this book are to focus on writing solid, maintainable code which improves the product rather than quick fixes. 
You should also make sure that you get recognised for your work, and work as best you can within your team and company. 
You should have both a deep understanding of and high skill at your job, as well as a wide breadth of knowledge of the company as a whole and the various roles within it. 
Effective team work is also important; be a positive influence within the team.
 
I found this book useful, but a bit more dry than Apprentiship Patterns. I think that has a lot to do with it dealing with the wider corporate structure, rather than just programming though :joy: 
It’s still very useful advice though, and worth reading.

On the final point the book raised about future career goals, I think that this is something I should keep in mind during the grad program. 
The program is my best chance at experiencing a wide variety of areas within the engineering department (although obviously in low-level roles), and thus learning which I love or hate. 
I really want to have as much variety as possible in my crew rotations, so that I can be exposed to as many areas as possible and hopefully get a feel for where I want to aim long-term.

## _Clean Code_

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
