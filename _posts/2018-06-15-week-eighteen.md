---
layout: post
title: Week Eighteen in Review
tags:
  - weekly review
  - meaningful project
  - ci/cd
---

This was the second-last week of the project, since we got a one-week extension of the original deadline due to public holidays etc. We've made very good progress, in that our project is now useable! It's missing a **lot** of features, but it feels good to have something actually up and running.

## Goals

#### Get the project deployable, with CI/CD set up

Done! It wasn't finished until last thing on Friday, but we now have the project up and running with a build pipeline, and deploying such that others can access it :grin: This should have been done much earlier in the project so that it was useable sooner, but still, we got there in the end.

---

## Tasks

#### Mobbing

We continued to mob on most of the feature additions for the project. We're still not entirely there with the process, but we've come leaps and bounds since we started. I think that if we were going to working on this project long-term, we'd become a very solid mob.

#### Pipeline and deployment

We got a lot of help on these, since we all had very limited experience. I learnt a lot though, and I think I could (mostly) set it up myself now if I had to do it again. Deployment ended up taking a long time to get working though, since there were a few minor bugs we had trouble tracing down, but we got there in the end and I think that I learnt a lot more than I would have if things had gone smoothly (since I volunteered to help our experts debug everything). Since the deployment script came from a different source I also spent some time by myself to bring it in line with the other pipeline scripts (it wasn't passing linting, and had to be in a certain directory originally, with didn't work well with our project structure). I really enjoyed getting to work with bash scripts etc :blush:

#### Readme

I wrote a first draft of a readme for our project. It still needs some work, but at least we have **any** documentation now. I found it somewhat difficult to write, since the _how to_ section needed to be readable by non-technical people, but explain technical concepts (since I couldn't assume they'd know what JSON is etc). It was an interesting exercise though, and will hopefully help our project get used.

---

## Takeaways

* Pipelines and deployment is fun to work on! Frustrating at times, but very interesting.  
* I'd like to learn more about how our deployment infrastructure works, and how to use it.  
* We're improving at mobbing, but an always get better.  
* Non-technical things are often harder to write than technical ones, but are still important.

---

## Next Week's Goals
* Wrap up the project!
