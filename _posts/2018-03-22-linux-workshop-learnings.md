---
layout: post
title: Linux Workshop Learnings
tags:
  - learnings
  - cli
---

Two weeks ago I attended a workshop on Linux. What follows is a brief summary of what I learnt from it, mostly for my own reference. As usual this comes with the caveat that I may misremember or misinterpret details, so while I'll try to be as accurate as possible this post may contain errors.

---

## How Linux Works

#### OS architecture

An operating system is a thin layer of abstraction on top of the hardware. The kernel is its core component, which directly accesses the hardware, and abstracts it for the rest of the system. It is loaded first and allows the rest of the system to function. The next level up is the userland, which consists of all non-kernel programs, and in particular all non-GUI user programs. Finally there is the GUI, which abstracts the other layer for the user.  

#### The kernel

The kernel is responsible for memory management, driving the hardware, program execution, security, etc. Programs do not actually run concurrently; the kernel must handle process execution and resource management such that it appears to the user that everything is happening simultaneously.  
The kernel generally has a constant stream of work to do; new requests will therefore get scheduled for execution. The hardware (e.g. keypresses) is required to be highly responsive, so it circumvents the kernel's scheduling by sending interrupts. When it receives such an interrupt, the kernel will stop what it is doing, handle the interrupt, and then continue with what it was doing.  
The kernel may report incorrect information about the state of the system. For example, although the kernel may **say** that it has allocated memory, it will not actually do this until that memory is used by the program. While this can cause some odd behaviour and errors, in general it improves performance (e.g. a rogue program cannot take up all the available memory simply by continuously asking for it to be allocated).

#### System calls

System calls are what userland uses to communicate with the kernel; they are the application binary interface (ABI). Some examples are: clone, exec, chdir, open, create, connect, accept, read, write, unlink, rename, select, and kill.  
The shell is a user interface to the kernel, which uses these sys calls (although it generally comes with built-ins which make use of them). It is just another program, which runs in userland. It is not really a language.  
GNU (the standard userland on Linux) is only mostly POSIX compliant.  

#### Standard practices

When working with the shell, you should write programs which do only one thing, and do it well. You should use throwaway prototypes as necessary.  
You should write programs which work together. That is, any programs you write should expect to take input from, and give output to, an as-yet unknown program. This means avoiding unnecessary output (e.g. headers), and not expecting interactive input. It should accept input from stdin and write output to stdout, and write diagnostic output to stderr. Additionally, it should use text streams for this, since these function as a universal interface. In effect, the program's output should be its API, and as such should be simple to parse and compose. Omit needless diagnostics, and signal failure with an exit status.  
Standard in, out and error are files created by the shell fo the process. Input and output can be redirect, e.g. by using pipes. Blocks of code have their own standard in, out and error.  
Variables are referred to as parameters. Environment parameters are always use all uppercase and underscores; **only** environment parameters should use this formatting. New processes inherit their environment from the caller. Most control structures act as standard. '[' is an alias of test on POSIX compliant systems.  

---

## Useful Commands

The following is a list of commands I have come across generally, and also by doing the Over The Wire Bandit game.

`^c` to cancel running command.  
`^d` to destroy running command.
`^r` will back-search your previous commands.  
`^u` will clear the current line.  
`<` at the end of a command sends the RHS to the stdin of the LHS. `>` sends the stdout of the LHS to the RHS. `>>` appends the stdout of the LHS to the RHS. The RHS of all of these is typically a file.  
`/dev/null` is a sink for output; it deletes everything it gets given.  
`/dev/random` gives random output. `/dev/urandom` also gives random output (but will not block if it runs out of randomness, and is typically preferred).  
`2>/dev/null` redirects stderr to dev/null  
`2>&1` redirects stderr to stdout  
`yes` just gives you a constant stream of "yes".  
`pwd` to print working directory.  
`mkdir -p <directory structure>` will make any intermediary directories necessary in the given structure.  
`ls -a` shows **all** (including hidden directories. `-A` shows all except `.` and `..`. `-l` displays the output in a list format (with some extra information). `-lh` is list but with human-readable sizes. `list -hal` is common catch-all.  
`file <file>` describes the file contents.  
`which` shows the alias or location.  
`sort | uniq` or `sort -u` will pull out unique lines  
`tr` is the transform utility  
`grep <options> <file>` to parse a file. `-f` will get the patterns from a file. `-v` will invert the match (i.e. return unmatched lines).  
`jq <flags> "<commands>"` is god if working with JSON. Useful commands are: `setpath(<key>;<value>)` to add value at key; `@csv` to convert a values-only structure to a csv; `|` to chain commands; `-M` for monochrome output; `-c` for concise output (one line per object); `keys` and `keys_unsorted` to get the keys; `map()` to get only values; and `<field> = <value>` to update values.  
localhost is 127.0.0.1  
`nc` is netcat: arbitrary TCP and UDP connections. It writes to stderr by default. `-zv` will scan ports. `-l` will listen on a port (e.g. to serve files or run as a chat server).  
`nmap -p <port range> <host>` scans ports. `-Pn` will scan without sending a ping first. `-p-` will scan all ports. It may need to be installed, depending on the system.  
`openssl s_client -connect <host>:<port>` will connect via ssl to a host. Use `-ign-eof` for non-interactive mode.  
`ssh -p <port> -i <id file>` (e.g. public key) to ssh to a remote  
`&` at the end of a line will send the process to the background. `jobs` will show all running processes. `fg` will bring the last used process to the foreground (indicated by a `+` in the jobs list). `fg %<number>` will bring the process with the given number to the foreground.  
`set -e` will exit a script immediately if a simple command returns with a non-zero status.  
`set -x` will show what commands are running and their output (esp. useful in a script). `set +x` will turn this off again.  
`shellcheck` is a non-standard utility for checking scripts (e.g. for syntax errors) with helpful suggested fixes included. `-x` will follow external sources. `$0` will check the running script (the running command is always parameter zero).  
`cat` consumes input! You'll need to store input in a variable if you want to use the same input twice in a script.  
`trap <command> <signal>` will run a command when a signal is received (e.g. cleanup on exit).
`command -v <command> >/dev/null` can be used to check if a command exists (although care if running it without arguments will do something).  
`while <statement>; do ... done` is a bash while loop, and `if [<statement>]; then ... elif [<statement>]; then ... else ... if` if an if statement.  

---

I will hopefully make a cheat-sheet for the commands at some point (and update this this post when that happens). I learnt a lot from the workshop and Bandit, and will hopefully get the chance to do more of the Over The Wire exercises to learn more about bash!
