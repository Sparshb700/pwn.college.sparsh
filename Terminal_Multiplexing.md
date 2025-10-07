
# 1. Launching Screen

This challenge prompted me to start a new `screen` session.

## My Solve

**Flag:** `pwn.college{coSfsKingIy9t-ZULw99O8ePDu0.0VN4IDOxwCM2EDNzEzW}`

To get the flag, I just had to run the `screen` command, which launched a new virtual terminal session and printed the flag upon entry.

```
hacker@terminal-multiplexing~launching-screen:~$ screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{coSfsKingIy9t-ZULw99O8ePDu0.0VN4IDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `screen` command is used to start a new terminal multiplexer session.

## References

The problem statement provided was the reference used.

```
Let's dive right in!
screen is a program that creates virtual terminals inside your terminal.
It's somewhat like having multiple browser tabs, but for your command line!
Starting screen is super simple:

hacker@dojo:~$ screen

That's it!
...
For this challenge, we've hooked things up so that just launching screen will get you the flag.
```

# 2. Detaching and Attaching

This challenge prompted me to detach from and reattach to `screen` session.

## My Solve

**Flag:** `pwn.college{YzdKXNxHIEvSJm-jRCNivJoWY6X.0lN4IDOxwCM2EDNzEzW}`

I started a new session with `screen`, then detached from it by pressing `Ctrl-A` followed by `d`. After detaching, I ran `/challenge/run`, which sent the flag to the background session. I then used `screen -r` to reattach and find the flag.

```
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 176.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 176.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
```

Inside screen:

```
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{YzdKXNxHIEvSJm-jRCNivJoWY6X.0lN4IDOxwCM2EDNzEzW}
Yes! Flag is: pwn.college{YzdKXNxHIEvSJm-jRCNivJoWY6X.0lN4IDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that you can detach from a `screen` session using `Ctrl-A` then `d`, which leaves it running in the background. You can then reattach to the session with `screen -r`.

## References

The problem statement provided was the reference used.

```
Now we'll start digging in with the magic of detaching!
...
You detach by pressing Ctrl-A, followed by d (for detach).
This leaves your session running in the background while you return to your normal terminal.
...
To reattach, you can use the -r argument to screen:

hacker@dojo:~$ screen -r

For this challenge, you'll need to:

Launch screen
Detach from it.
Run /challenge/run (this will secretly send the flag to your detached session!)
Reattach to see your prize
```
# 3. Finding sessions

This challenge prompted me to find and attach to a specific `screen` session among several decoys.

## My Solve

**Flag:** `pwn.college{caQtSVK5Zmod2QpgvyFkt7dLrxp.01N4IDOxwCM2EDNzEzW}`

I used `screen -ls` to list all the active sessions. Then, I attached to the first one on the list, `session_c4bb1652c0e413d1`, using the `screen -r` command, which turned out to be the correct one containing the flag.

```
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        170.pts-0.practice~terminal-multiplexing~launching-screen       (Remote or dead)
        144.session_c4bb1652c0e413d1    (Detached)
        147.session_80ff2ffc40ec2348    (Detached)
        150.session_f9fe18bf810e3fb3    (Detached)
4 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_c4bb1652c0e413d1
```

Inside screen:

```
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{caQtSVK5Zmod2QpgvyFkt7dLrxp.01N4IDOxwCM2EDNzEzW}
pwn.college{caQtSVK5Zmod2QpgvyFkt7dLrxp.01N4IDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that `screen -ls` lists all running screen sessions, and you can attach to a specific one by its name or PID using `screen -r <name>`.

## References

The problem statement provided was the reference used.

```
If you become an avid screen user, you will inevitably end up with multiple sessions running.
How do you find the right one to reattach to?
Well, we can list them:

hacker@dojo:~$ screen -ls
...
To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.

hacker@dojo:~$ screen -r goodwork

In this challenge, we've created three screen sessions for you.
One of them contains the flag.
The other two are decoys!
You'll need to check each one until you find it.
```

# 4. Switching windows

This challenge prompted me to switch between windows within a `screen` session.

## My Solve

**Flag:** `pwn.college{o2FpezETCqPAxIbcLhbhN3yg0On.0FO4IDOxwCM2EDNzEzW}`

I attached to the screen session with `screen -r`, which put me in window 1. The message there told me the flag was in window 0. I then pressed `Ctrl-A` followed by `0` to switch to window 0, where the flag was waiting.

In window 1:

```
hacker@terminal-multiplexing~switching-windows:~$ 
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
```

In window 0 (after pressing `Ctrl-A 0`):

```
hacker@terminal-multiplexing~switching-windows:~$ 
Excellent work! You found window 0!
Here is your flag: pwn.college{o2FpezETCqPAxIbcLhbhN3yg0On.0FO4IDOxwCM2EDNzEzW}
```

## What I Learned

I learnt how to manage multiple windows in `screen`. `Ctrl-A c` creates a new window, and you can switch between them with shortcuts like `Ctrl-A n` for next, `Ctrl-A p` for previous, or `Ctrl-A <number>` to jump to a specific window.

## References

The problem statement provided was the reference used.

```
Inside a single screen session, you can have multiple windows, like your browser has multiple tabs.
...
These windows are handled with different keyboard shortcuts, all starting with Ctrl-A:

Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
...
Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1.
```

# 5. Detaching and Attaching (tmux)

This challenge prompted me to detach from and reattach to a `tmux` session.

## My Solve

**Flag:** `pwn.college{AWVyXmDwKC1vo-cZbMwnfdqyh6j.0VO4IDOxwCM2EDNzEzW}`

I started a new session with `tmux`, then immediately detached by pressing `Ctrl-B` followed by `d`. After detaching, I ran `/challenge/run`, which sent the flag to the background session. I then reattached with `tmux a` to find the flag.

```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
```

Inside tmux:

```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{AWVyXmDwKC1vo-cZbMwnfdqyh6j.0VO4IDOxwCM2EDNzEzW}
Congratulations, here is your flag: pwn.college{AWVyXmDwKC1vo-cZbMwnfdqyh6j.0VO4IDOxwCM2EDNzEzW}
```

## What I Learned

I learnt the basics of `tmux` as an alternative to `screen`. The command prefix is `Ctrl-B`, detaching is `Ctrl-B` then `d`, and reattaching is done with `tmux attach` or `tmux a`.

## References

The problem statement provided was the reference used.

```
Let's try the same thing with tmux!
tmux (terminal multiplexer) is screen's younger, more modern cousin.
...
Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.
So to detach from tmux, you press Ctrl-B followed by d.
...
The commands also differ:

tmux ls - List sessions
tmux attach or tmux a - Reattach to session

For this challenge:

Launch tmux
Detach from it.
Run /challenge/run (this will send the flag to your detached session!)
Reattach to see your prize
```

# 6. Switching Windows (tmux)

This challenge prompted me to switch between windows within a `tmux` session.

## My Solve

**Flag:** `pwn.college{IbMsT0wJeBLPHabuJaKj-7bp8zv.0FM5IDOxwCM2EDNzEzW}`

I attached to the `tmux` session with `tmux a`. I found myself in window 1, but the flag was in window 0. I pressed `Ctrl-B` then `w` to open the window picker, selected window 0, and found the flag.

```
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
```

Inside tmux, after switching to window 0:

```
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{IbMsT0wJeBLPHabuJaKj-7bp8zv.0FM5IDOxwCM2EDNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{IbMsT0wJeBLPHabuJaKj-7bp8zv.0FM5IDOxwCM2EDNzEzW}
```

## What I Learned

I learnt the key combinations for managing windows in `tmux`, all prefixed by `Ctrl-B`. `c` creates a new window, `n` goes to the next and `p` to the previous, `0-9` jumps to a specific window, and `w` shows a window picker.

## References

The problem statement provided was the reference used.

```
Let's learn to navigate windows in tmux!
Just like screen, tmux has windows.
The key combos are different, but the concept is the same:

Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker
...
We've created a tmux session with two windows:

Window 0 has the flag!
Window 1 has your warm welcome.
Go get that flag!
```
