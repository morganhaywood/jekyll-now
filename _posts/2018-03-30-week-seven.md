---
layout: post
title: Week Seven in Review
---

This week was fairly short due to Easter, plus several meetings and workshops. I still got a reasonable amount done though. I suspect next week will be similar since it will also be only four days.

## Goals

#### Remember how to write C

I am still very rusty at C. I did enough to remember how to get something working in it, but I feel like I'm writing C as if it was Java. I think a good next step would be to read a book on it to understand the idioms of the language.

#### Finish the blog posts in my backlog

I got one or two done, but added another, so this was a bit of a wash :persevere:

#### Get Docker working

This proved surprisingly easy :satisfied: The hardest parts were finding an image with gcc (turns out it's conveniently called _gcc_ :sweat_smile:) and copying files into it (`docker ps` to find the container id and `docker cp <source_path> <container_id>:<destination_path>` to copy it turned out to work pretty well :yum:). 

#### Figure out my roadmap for the next few weeks with my mentors

I had a good chat with my mentors, and we decided that I should do the advanced katas. Depending on how I go with them I can then look at moving on to the projects in the next few weeks.

---

## Tasks

#### Programming with Pedro in C

Pedro and I completed the fizz buzz and mastermind katas in C. It took a while to get the basics working since I was very rusty and Pedro had not used C before, but we got there in the end :sweat_smile: As mentioned above, although we got the katas working I feel like I need to look at some idiomatic C to further improve.

#### Minefield kata with Sina

This was a relatively simple and quick exercise, although we could definitely refactor our solution to improve upon it. Regardless, the point was more about pair programming with more people than actually solving the problem, and I feel like I got a lot out of it in that regard.

#### _Clean Code_ chapters 3 and 4

Chapter 3 covered functions. Functions should be small, doing only one thing, use only one level of abstraction, have a descriptive name, have no side effects, and have as few arguments as possible. Long switch or if/else statements should generally be replaced by polymorphism (with the one remaining buried in a factory). It is better to have explicit outputs than output arguments, and exceptions should be used in preference to error codes. The contents of each part of a try/catch block should generally be their own method.  
Chapter 4 covered comments. The main thrust was that comments should be avoided as much as possible, since they easily become out of date or misleading. It is generally better to write self-documenting code, and use comments only as a last resort (eg. to clarify working around code you cannot alter, TODOs, Javadocs for public APIs, warning of non-obvious consequences,  etc).

#### zsh workshop

This was a really useful and interesting workshop. I learnt a little too much to document here, but I want to update my Linux workshop post to include the new things I learnt. Since I've been using bash so far, I also need to figure out which things working in bash too, and wether I want to switch to zsh if not everything does.

---

## Takeaways

* Everyone has different pairing and coding styles. It's important to work with your partner to find a pairing workflow which works for both of you.  
* Learning how to write _idiomatically_ in a new language is harder than learning to write in a new language.
* During refactoring, make sure to pay attention to function size, naming, abstraction level, etc.
* There are a **lot** of shortcuts and tricks to learn to make CLI more efficient to use.

---

## Next Week's Goals

* Finish the Game of Life kata, with good design.
* Get something useful done despite the short week.
