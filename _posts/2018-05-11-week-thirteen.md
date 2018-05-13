---
layout: post
title: Week Thirteen in Review
tags:
  - weekly review
  - meaningful project
  - ctf
  - books
---

This week was a bit shorter for me, because I was sick Tuesday :mask: But it was good to get started on the project!

## Goals

#### Decide on a tech stack for the group project, and high-level design.

We made progress towards this, but haven't finalised everything yet (well, to the extent that anything is ever finalised in agile :stuck_out_tongue: ). So we'll have a bit more work to do on it on Monday.

#### Set up a good workflow for the project team.

We've made good progress towards this. Establishing team dynamics and workflow takes a while, but I'm happy with how we're progressing.

---

## Tasks

#### _Clean Code_ chapter 11

Chapter 11 examined systems. It explained the importance of having a globally consistent strategy for set up and instantiation. E.g. put all setup into main, use abstract factories, or use dependency injection. This is in contrast to e.g. using lazy initiation, where new objects are created on the fly when they become necessary. Separating these concerns allows for better incremental growth and easier testing. One way to get around many of these issues is to use a minimally-invasive aspect-oriented framework, which as the name suggests will handle certain concerns by aspect (e.g. instantiation). On a slightly different tack, this chapter also advocated doing **some** up-front design, but only the minimum necessary. In general decisions should be postponed until the last possible moment, so that they are made with the most possible information. Finally, architecture should not be invasive; it should help your code be clean, not take it over.

#### Database options and schema suggestions

I spent a lot of this week investigating possible data structures for storing our project's data, depending on what type of database we use. It was quite interesting modelling the same data using different paradigms, and seeing which fit best. This was mostly paper-and-pencil scratch work; none of it is really well thought-out enough to use as the final schema for our project, but all of them are good enough to show how well-suited the paradigm is for our dataset. I did put some into an actual database though (the type we feel is most suitable), so we could demonstrate searching etc. in our end-of-sprint review.

#### Solution options

We ended up inadvertently going through the project process completely out of order :sweat_smile: So it was only at the end of this week that we wrote up the solution options document. But we're trying! And this project is primarily meant to be a learning experience, so we're definitely getting that!

#### CTF workshop

The security team ran a CTF workshop, which was really fun :yum: The one we went through was a little different to the others I've done; it was a single-page application with several challenges listed (e.g. "leave a zero-star review"). It was interesting to see a different type of CTF though, and work with more people on one. I certainly learnt a lot from it, although it wasn't nearly as difficult as what I have been doing (just a little fiddly in places to get it to recognise that you had succeeded in doing the thing). I hope the security team runs more of these :blush:

#### Retrospective and review

Since we're doing weekly sprints, on Friday we had our first retro and review sessions. I probably won't discuss these in every weekly review, but suffice to say that the retro was useful (and we happily have no major problems), and it was good to show our product owner et al what we've done so far (it certainly helps keep us focused on having something deliverable at the end of the sprint).

---

## Takeaways

* Knowing the project process before you start helps!  
* It's good to look at things from different perspectives.  
* Our team seems to be coming together well.  
* I still really like CTFs :laughing: And I feel that I learn a lot from them.

---

## Next Week's Goals
 
 * Start writing some actual code for the project (even if it's just spikes).
 
 That's all! next week is very short, since I'll be on leave Thursday and Friday.
