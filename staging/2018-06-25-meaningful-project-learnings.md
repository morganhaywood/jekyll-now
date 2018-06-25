---
layout: post
title: Meaningful Project Learnings
tags:
  - meaningful project
  - learnings
  - ci/cd
  - networking
  - language paradigms
---

This has been a very educational project. While it's had its ups and downs, I learnt a lot from it and I'm glad I did it. I'm especially glad that we got something working and useable, and could hand it over to a team who will keep maintaining it. However the main point of the project was to learn. I don't think that this blog post **can** cover everything; a lot of what I've learnt has been less tangible or possible to put into words, or is of a fairly bland and factual nature (which can therefore be looked up in e.g. the Go language documentation). But here I'll reflect and document as much as can, and I feel is worth writing down.

## Project Process

I learnt a lot about the process of starting a new project. Going into this project I had very little idea about what documents needed to be produced in order to communicate with stakeholders and set expectations. The whole process ended up taking longer than it perhaps should have, but we got there in the end :joy: 

We produced three documents: a high-level overview of the current state (the problem) and the goal state; an investigation of possible solutions, with pros and cons of each; and an architecture diagram for the proposed solution. These documents helped us discuss the problem with stakeholders and the wider organisation, weigh up the possible solutions and decide upon one, and make sure that our solution was well-designed. Since we didn't really know anything about this process going in, we ended up working through this process entirely out of order :persevere: While this was definitely a detriment to the project deliverables, I think that in a way it was beneficial for our learning in the end; **not** having the documents when we needed them drove home their value very effectively.

I also learnt the importance of communicating with stakeholders and managing their expectations. The documents help with this, but you still need to make an effort to ensure that you are meeting their needs, and that they know what they are getting.

## Working in a Team

I really enjoyed the team I was working with for this project, and we worked well together. I think that this was largely due to good communication. If there was a problem then we all felt that we could, and were willing to discuss it frankly at the first possible opportunity, rather than letting things get worse. And on the flip side, everyone was willing to listen to others' concerns without getting defensive, and work together to find a solution. This made for a much more functional team.

## Mobbing

Once we started coding we spent a lot of time mobbing, either as trio or with others - experts who we pulled in to help, mentors, or other proteges who wanted to see what we were up to. None of us had much mobbing experience at the start, so it was a bit of learning curve. Our strong communication helped a lot with this though. One of the most beneficial things we did all project was to ask Mark to spend time with us mobbing though. We learnt a lot very quickly from him, and our mobbing drastically improved.

Some key points I've learnt from this:

* At the start of a mobbing session, very briefly discuss what you want to work on and make a list somewhere everyone can see (e.g. on a whiteboard). This helps to align everyone, and keep focus.  
* If you don't have context, or aren't following what's happening, it's best to drive. This is difficult (and newer mob members may need encouragement to pick up the keyboard), but will get you up to speed quickly. Other options are to ask questions, or make a note to look something up by yourself later, depending on _why_ you're not understanding.  
* If someone doesn't know enough to contribute to navigating at all, get them to take extra turns at driving (e.g. when we had a protege in the mob who had no idea what was going on, we got him to take every second turn at driving so he could keep contributing and learning).  
* If someone wants to navigate, don't let them drive. It's better to skip them in the driving rotation than to have them trying to do both(which tends to end in them losing the rest of the mob). Equally though everyone should take a turn at driving; if you skip someone because they're in the middle of navigating, make sure they take the next turn.  
* Having an expert in the mob helps **enormously** if that knowledge is lacking (in our case, none of us were familiar with Go, so having someone in the mob for 2-3 hours to explain how Go does things really helped).  
* Experts shouldn't be driving (as an exception to the _everyone should drive_ rule); the rest of the mob will learn much better if the expert has to **explain** what they're doing, and the best way to force that is to have someone else type it. If they feel that they **have** to, get them to type out an example and then delete it (so that others can re-type it with the expert's guidance).  
* If you have a blocker, or otherwise feel the need for individual investigation, time box separation (e.g. half an hour) but stay within earshot of each other. Come back together as soon as someone finds a solution, or the time ends to share what you've learnt. Even if no one has found the whole solution, together you may have learnt enough to work it out.  
* If you need a longer discussion on something, move to the whiteboard. Write down facts and opinions separately, and work towards alignment. Then lay out your attack plan to ensure that everyone's on the same page.  
* Communication is key.  
* Setting a timer for switching drivers is very important. However, sometime it's useful to ignore it in order to complete a logical piece of work (depending on the amount of extra time relative to the driving-turn time).  
* Remember to commit regularly! Before switching drivers is a useful way to remember if the mob struggles with this.  

## Go

I found it very interesting to learn Go. I came to really like it as a language, although it has its quirks and annoyances (e.g. error handling :expressionless: ). It is **very** different to Java in paradigm though, so it took me a while to get used to it. I still don't think that I'm writing entirely idiomatic Go, but I'm definitely a lot closer than at the start of the project. Some short points:

* Functions don't need to be part of a struct in the same way that methods need to be part of an object.  
* Something should only be a struct if it **has** to (e.g. needs data members).  
* You can pass functions around!  
* Keep interfaces as short as possible (i.e. one function where possible). It's better to have a struct implement many small interfaces than one big one.  
* Only export a function, struct or interface if you have to.  
* Embedded structs have quirks.

I've also come to realise that what constitutes _clean code_ varies wildly between language paradigms. What I've learnt so far in this program about architecture, code design and coding practices has been very object-oriented centred, taken from the perspective of Java. Design is not transferrable between paradigms for obvious reasons. Even some things like naming, which you'd assume would be the same regardless, have different standards in different languages for a **reason**. It's important to learn good practices for the language in which you are working, and keep to that standards for that language as much as possible; you communicate better by working with your audience's background knowledge than by forcing them to learn yours.

In the end, it's not really about one paradigm being better or worse, it's about choosing the right one for the job; they each have their strengths and weaknesses.

## Pipelines and Deployment

I spent a lot of time trying to track down bugs in our pipeline, but as a result I learnt a lot about how it works. While I won't go into an explanation of our particular pipeline or deployment applications (although I do understand them a lot better now), I do have some general lessons:

* The basic steps are lint -> test -> stand up instances -> build and push images -> deploy. This generally goes from least time / risk to most.  
* It's better to have the bulk of your code in scripts; that way you can easily test locally, or transfer to a new build tool if need be. It also lets you use the same code to build all branches, but only push the images for some branches (or push them to different places).  
* Test locally! It's faster and easier.  
* Pay attention to which agents are doing what, and which permissions they need.  
* Have a clear structure to your scripts, templates, etc. both internally and in how they're stored.  
* Consider carefully where to put waits (i.e. which steps can run in parallel and which can't).  
* Make sure your application has basic logging (even if it's just a welcome message) and can describe itself (even if it just logs a build number). This helps a lot with debugging if you don't know whether things are deploying correctly, or where your pipeline is breaking.  
* Docker is your friend, but choose the lightest-weight (base) image you can (`from scratch` if possible).

---

Overall this has been a good experience. Having a good team helped a lot; I will miss working with them. I liked mobbing far more than I expected to, having been somewhat dubious about it to begin with. I found Go quite difficult at the start, but I came to quite like it. In retrospect that's not really surprising, since it's lightweight and script-like (somewhat similar to bash in concept if not concretely), and it borrows heavily from C which I really liked when I used it previously. And I'm definitely not surprised that I thoroughly enjoyed working on the pipeline :yum: It was frustrating, but I still liked it. Hopefully I can do more similar work in the future.
