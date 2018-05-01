---
layout: post
title: CTF Learnings
tags:
  - learnings
  - ctf
  - security
  - cli
---

Over the past few weeks I've done three capture the flag (CTF) exercises from Over The Wire. Two (Bandit and Leviathan) were command line based, and one (Natas) was web based. Here's what I've learnt from these exercises (with as few spoilers as possible, for anyone intending to do them themselves :innocent:).

First off, my command line literacy has definitely improved. I've been exposed to a range of tools I either hadn't used before, or had forgotten about. Since I had to figure out how to use them myself, I've also become a lot better at looking up man pages and searching online for the right tool(s) for what I want to do. In general, I've simply become much better at thinking in the bash paradigm.

Connected to this, I've become a lot better at shell scripting. I had done some of this before, but not for several years. Both Bandit and Natas required me to write scripts, and as a result I've re-learnt a lot of the syntax for this. I'm glad I got the chance to do this, since I quite enjoy writing shell scripts and I was **very** rusty.

Since Natas is web-based, it taught me a lot about the basics of working with the web: how sessions and session IDs work, how characters are encoded in URLs, how to access file indexes on websites, etc.  It also gave me a lot of exposure to php, which I haven't worked with before. I have learnt about how php handles many edge-cases (e.g. strcmp on an array, [string] > [integer]), for which I found the interactive shell (`php -a`) quite handy.

Of course, much of the point of CTFs is learning about security. I have gained an understanding of the importance of very carefully sanitising user input, since incorrectly doing this leaves your website open to a wide range of vulnerabilities (e.g. cross-site scripting or SQL injection). You also need to very careful about how you store, retrieve and verify user secrets. Sessions are also vulnerable if IDs are insufficiently difficult to guess (or old sessions are not closed), or if user input allows editing or adding session data.

Natas also briefly touched on encryption, such as XOR (which is very insecure if used with short keys, since it's commutative; if you can guess some of the plain text you can crack the key). Hopefully after finishing the last few levels of Natas I will be able to do Krypton as well, which will expand my knowledge in this area.

I think that everything I've learnt from the CTFs will be very useful no matter what I end up working on. Pretty much everything I could do would involve using the command line at minimum (e.g. for git) and most things require some for of user input, sessions and passwords. And of course, security is **important** not matter what you're doing :smiling_imp:
