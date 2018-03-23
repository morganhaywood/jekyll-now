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

The kernel is responsible for memory management, driving the hardware, program execution, security, etc. Programs do not acutally run concurrently; the kernel must handle process execution and resource management such that it appears to the user that everything is happening simultaneously.  
The kernel generally has a constant stream of work to do; new requests will therefore get scheduled for execition. The hardware (e.g. keypresses) is required to be highly responsive, so it cirumvents the kernel's schedulling by sending inturrupts. When it receives such an inturrupt, the kernel will stop what it is doing, handle the inturrupt, and then continue with what it was doing.  
The kernel may report incorrect information about the state of the system. For example, althought the kernel may **say** that it has allocated memory, it will not acutally do this until that memory is used by the program. While this can cause some odd behaviour and errors, in general it improves performance (e.g. a rogue program cannot take up all the avaliable memory simply by continously asking for it to be allocated).

#### System calls

System calls are what userlands uses to communicate with the kernel; they are the application binary interface (ABI). Some examples are: clone, exec, chdir, open, create, connect, accept, read, write, unlink, rename, select, and kill.  
The shell is a userinterface to the kernel, which uses these sys calls (although it generally comes with built-ins which make use of them). It is just another program, which runs in userland. It is not really a language.  
GNU (the standard userland on Linux) is only mostly POSIX compliant.  

#### Standard practices

When working with the shell, you should write programs which do only one thing, and do it well. You should use throwaway prototypes as necessary.  
You should write programs which work together. That is, any programs you write should expect to take input from, and give output to, an as-yet unknown program. This means avoiding unnecessary output (e.g. headers), and not expecting interactive input. It should accept input from stdin and write output to stdout, and write diagnostic output to stderr. Additionally, it should use text streams for this, since these function as a universal interface. In effect, the program's output should be its API, and as such should be simple to parse and compose. Omit needless diagnostics, and signal failure with an exit status.  
Standard in, out and error are files created by the shell fo the process. Input and output can be riedirect, e.g. by using pipes. Blocks of code have their own standard in, out and error.  
Variables are reffered to as parameters. Environement parameters are always use all uppercase and underscores; **only** environment parameters should use this formatting. New processes inherit their envrionment from the caller. Most control structures act as standard. '[' is an alias of test on POSIX compliant systems.  

---

## Useful Commands


---

[outro]
