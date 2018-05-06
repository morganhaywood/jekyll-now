---
layout: post
title: CTF Learnings
tags:
  - learnings
  - ctf
  - security
  - cli
---

Over the past few weeks I've completed two capture the flag (CTF) exercises from Over The Wire, and got partway through two more. Three (Bandit, Leviathan and Krypton) were command line based, and one (Natas) was web based. Here's what I've learnt from these exercises (with as few spoilers as possible, for anyone intending to do them themselves :innocent:).

First off, my command line literacy has definitely improved. I've been exposed to a range of tools I either hadn't used before, or had forgotten about. Since I had to figure out how to use them myself, I've also become a lot better at looking up man pages and searching online for the right tool(s) for what I want to do. In general, I've simply become much better at thinking in the bash paradigm. Examples of this can be found in [this]({{site.url}}{% post_url 2018-03-22-linux-workshop-learnings %}) blog post, and [this]({{site.url}}/cheatsheets/cli_cheatsheet.pdf) cheatsheet.

Connected to this, I've become a lot better at shell scripting. I had done some of this before, but not for several years. Both Bandit and Natas required me to write scripts, and as a result I've re-learnt a lot of the syntax for this. I'm glad I got the chance to do this, since I quite enjoy writing shell scripts and I was **very** rusty. I now feel confident that I can write a basic shell script without trouble.

Since Natas is web-based, it taught me a lot about the basics of working with the web. For example, I learnt about how session IDs are used to store user data, how characters are encoded in URLs, and some potentially undesirable defaults (e.g. being able to access file indices).  It also gave me a lot of exposure to php, which I haven't worked with before. I have learnt about how php handles many edge-cases (e.g. `strcmp` on an array, `string > integer`), for which I found the interactive shell (`php -a`) quite handy.

Of course, much of the point of CTFs is learning about security. I have gained an understanding of the importance of very carefully sanitising user input, since incorrectly doing this leaves your website open to a wide range of vulnerabilities (e.g. cross-site scripting or SQL injection). You also need to very careful about how you store, retrieve and verify user secrets. Sessions are also vulnerable if IDs are insufficiently difficult to guess, which is partly why it's important to expire old session IDs. They can also be vulnerable if user input is used to directly edit session data.

Natas also briefly touched on encryption, and Krypton is entirely based around it. For example, Natas proved that XOR is very insecure if used with short keys, since it's commutative; if you can guess some of the plain text you can crack the key very easily. I have yet to finish Krypton, but the levels which I have done so far have examined simple substitution and vigenere ciphers. While I have seen these previously, that was quite some time ago so it was useful to get a refresher on the basics of a few different types of simple attacks. These include basic frequency analysis, and chosen-plaintext and known-plaintext attacks.

I think that everything I've learnt from the CTFs will be very useful no matter what I end up working on. Pretty much everything I could do would involve using the command line at minimum (e.g. for git) and most things require some for of user input, sessions and passwords. And of course, security is **important** not matter what you're doing :smiling_imp:
