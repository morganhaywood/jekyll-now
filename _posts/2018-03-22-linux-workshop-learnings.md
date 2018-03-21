---
layout: post
title: Linux Workshop Learnings
---

Two weeks ago I attended a workshop on Linux. What follows is a brief summary of what I learnt from it, mostly for my own reference. As usual this comes with the caveart that I may misremember or misinterpret details, so while I'll try to be as accurate as possible this post may contain errors.

---

## How Linux Works

#### OS architecture

An operating system is a thin layer of abstraction on top of the hardware. The kernel is its core component, which directly accesses the hardware, and abstracts it for the rest of the system. It is loaded first and allows the rest of the system to function. The next level up is the userland, which consists of all non-kernel programs, and in particular all non-GUI user programs. Finally there is the GUI, which abstracts the other layer for the user.

#### The kernel

The kernel is responsible for memory management, driving the hardware, and program execution. Programs do not acutally run concurrently; the kernel must handle process execution and resource management such that it appears to the user that everything is happening simultaneously.  
The kernel generally has a constant stream of work to do; new requests will therefore get scheduled for execition. The hardware (e.g. keypresses) is required to be highly responsive, so it cirumvents the kernel's schedulling by sending inturrupts. When it receives such an inturrupt, the kernel will stop what it is doing, handle the inturrupt, and then continue with what it was doing. 

#### Userland



#### Standard practices



#### Shell scripting



---

## Useful Commands


---

[outro]
