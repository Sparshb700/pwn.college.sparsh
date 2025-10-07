
# 1. Listing Processes

This challenge prompted me to find and then execute a hidden process.

## My Solve

**Flag:** `pwn.college{U72JCWNvzV-r-Hmy8zHNYBhh3pJ.QX4MDO0wCM2EDNzEzW}`

The location of the `run` binary was hidden. I used `ps aux` to list all the running processes and found the full path to the executable, then I ran the program found and got the flag.

```
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   20:17   0:00 /sbin/docker-init -- /nix/var/nix/profiles/
root           6  0.1  0.0 231708  2560 ?        S    20:17   0:00 /run/dojo/bin/sleep 6h
root         131  0.0  0.0   4132  2560 ?        S    20:17   0:00 /challenge/2413-run-26592
...
hacker@processes~listing-processes:~$ /challenge/2413-run-26592
Yahaha, you found me! Here is your flag:
pwn.college{U72JCWNvzV-r-Hmy8zHNYBhh3pJ.QX4MDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that `ps aux` or `ps -ef` can be used for listing all the running processes on system.

## References

The problem statement provided was the reference used.

```
First, we will learn to list running processes using the ps command.
...
To make it useful, we need to pass a few arguments.
"Standard" Syntax: ... ps -ef
"BSD" Syntax: ... ps aux
...
In this level, I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory!
But I also launched it, so you can find it in the running process list, figure out the filename, and relaunch it directly for the flag!
```

# 2. Killing Processes

This challenge prompted me to find and terminate a specified running process.

## My Solve

**Flag:** `pwn.college{kmmhPa1xYHNBnW1noTG7UU8MXfg.QXyQDO0wCM2EDNzEzW}`

I couldn't run the challenge binary because another process was blocking it. I used `ps aux | grep "dont"` to find the Process ID (PID) of the `/challenge/dont_run` process, which was 136. Then I used `kill 136` to terminate it and ran `/challenge/run` to get the flag.

```
hacker@processes~killing-processes:~$ ps aux | grep "dont"
hacker        136  0.0  0.0 231576  3520 ?        Ss   20:25   0:00 /challenge/dont_run
hacker        156  0.0  0.0 230524  1920 pts/0    R+   20:26   0:00 grep --color=auto dont
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{kmmhPa1xYHNBnW1noTG7UU8MXfg.QXyQDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that you can terminate a process using the `kill` command followed by its Process ID (PID). You can find the PID using `ps` and `grep`.

## References

The problem statement provided was the reference used.

```
You've launched processes, you've viewed processes, now you will learn to terminate processes!
In Linux, this is done using the aggressively-named kill command.
...
You use kill to terminate it by passing the process identifier (the PID from ps) as an argument...
...
In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running!
You must find the dont_run process and kill it.
```

# 3. Interrupting Processes

This challenge prompted me to terminate a foreground process using a keyboard shortcut.

## My Solve

**Flag:** `pwn.college{0a0jMKVal3oSKHhzjtTHjz5ibJa.QXzQDO0wCM2EDNzEzW}`

I ran the `/challenge/run` program, and it paused without exiting. As instructed, I pressed `Ctrl-C` to send an interrupt signal, which terminated the program and revealed the flag.

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{0a0jMKVal3oSKHhzjtTHjz5ibJa.QXzQDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that `Ctrl-C` is a keyboard shortcut used to send an interrupt signal to the current foreground process, which usually causes it to exit.

## References

The problem statement provided was the reference used.

```
You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal!
Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C)
 sends an "interrupt" to whatever application is waiting on input from 
the terminal and, typically, this causes the application to cleanly 
exit.
Try it here! /challenge/run will refuse to give you the flag until you interrupt it.
```

# 4. Killing misbehaving Processes

This challenge prompted me to find and kill a decoy process that was interfering with the challenge.

## My Solve

**Flag:** `pwn.college{sOni0Itzpq-3q3YXWwWKCsT7yIu.0FNzMDOxwCM2EDNzEzW}`

A decoy process was writing to a named pipe that the challenge needed. I used `ps aux` to find the decoy process and its PID, which was 142. I then used `kill 142` to stop it, ran `/challenge/run` to write the real flag to the pipe, and then used `cat` to read the flag from the pipe.

```
hacker@processes~killing-misbehaving-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
...
hacker       142  0.7  0.0  13516  9280 ?        Ss   20:34   0:00 /usr/bin/python /challenge/decoy
...
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{sOni0Itzpq-3q3YXWwWKCsT7yIu.0FNzMDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that sometimes you need to kill interfering processes before a program can run correctly. `ps` helps you find the process, and `kill` helps you stop it.

## References

The problem statement provided was the reference used.

```
Sometimes, misbehaving processes can interfere with your work.
These processes might need to be killed...
In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo ...
You need to kill this process.
Your general workflow should be:

Check what processes are running.
Find /challenge/decoy in the list and figure out its process ID.
kill it.
Run /challenge/run to get the flag...
```

# 5. Suspending processes

This challenge prompted me to suspend a process and run a second instance of it.

## My Solve

**Flag:** `pwn.college{gcYhJSnt6ihyoazjo7wLYTwfEVt.QX1QDO0wCM2EDNzEzW}`

The program required another copy of itself to be running. I launched the first instance of `/challenge/run`, then pressed `Ctrl-Z` to suspend it and get my terminal back. After that, I launched a second instance which then found the first one and gave me the flag.

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!
...
I don't see a second me!
...
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!
...
Yay, I found another version of me! Here is your flag:
pwn.college{gcYhJSnt6ihyoazjo7wLYTwfEVt.QX1QDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that `Ctrl-Z` can be used to suspend the current foreground process. This stops the process but doesn't terminate it, allowing you to resume it later.

## References

The problem statement provided was the reference used.

```
You can suspend processes to the background with Ctrl-Z.
...
This level's run wants to see another copy of itself running and using the same terminal.
How?
Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!
```
# 6. Resuming Processes

This challenge prompted me to suspend a process and then resume it in the foreground.

## My Solve

**Flag:** `pwn.college{YnE5O-rxRgSsX0lEpZ8v6ikYasH.QX2QDO0wCM2EDNzEzW}`

I launched the `/challenge/run` program, suspended it by pressing `Ctrl-Z`, and then used the `fg` command to bring it back to the foreground, which printed the flag.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{YnE5O-rxRgSsX0lEpZ8v6ikYasH.QX2QDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that the `fg` command is used to resume a suspended job and bring it back to the foreground.

## References

The problem statement provided was the reference used.

```
Usually, when you suspend processes, you'll want to resume them at some point.
...
To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.
Go try it out!
This challenge's run needs you to suspend it, then resume it.
```


# 7. Backgrounding Processes

This challenge prompted me to run a process in the background and then launch a second instance.

## My Solve

**Flag:** `pwn.college{USeopjyAzI17Q6BVn91zfY5_AtE.QX3QDO0wCM2EDNzEzW}`

The challenge required a second copy of the program to be actively running. I started the first instance of `/challenge/run`, suspended it with `Ctrl-Z`, and then used `bg` to resume it in the background. With the first instance running in the background, I launched the second one, which found the first and printed the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!
...
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!
...
Yay, I found another version of me running in the background! Here is your flag:
pwn.college{USeopjyAzI17Q6BVn91zfY5_AtE.QX3QDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that the `bg` command is used to resume a suspended job and run it in the background, which lets it continue executing while keeping the terminal free.

## References

The problem statement provided was the reference used.

```
You can also resume processes in the background with the bg command!
This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.
This level's run wants to see another copy of itself running, not suspended, and using the same terminal.
How?
Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background!
```

# 8. Foregrounding Processes

This challenge prompted me to move a process from the background to the foreground.

## My Solve

**Flag:** `pwn.college{UJd3UfIkguNweFp-AmHVKh2o5Fc.QX4QDO0wCM2EDNzEzW}`

This was a multi-step task. I first ran `/challenge/run` and suspended it with `Ctrl-Z`. Then I used `bg` to let it run in the background. Finally, I used `fg` to bring the background process back to the foreground to get the flag.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{UJd3UfIkguNweFp-AmHVKh2o5Fc.QX4QDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that the `fg` command works not only on suspended processes, but also on processes that are actively running in the background.

## References

The problem statement provided was the reference used.

```
Imagine that you have a backgrounded process, and you want to mess with it some more.
What do you do?
Well, you can foreground a backgrounded process with fg just like you foreground a suspended process!
This level will walk you through that!
```

# 9. Starting Backgrounded Processes

This challenge prompted me to launch a process directly into the background.

## My Solve

**Flag:** `pwn.college{4KVgsrOElK-i_EWSmcVvzHP52Wn.QX5QDO0wCM2EDNzEzW}`

I launched the `/challenge/run` program and appended an ampersand (`&`) to the end of the command. This started the process in the background immediately and printed the flag.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 138
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{4KVgsrOElK-i_EWSmcVvzHP52Wn.QX5QDO0wCM2EDNzEzW}

Connected!
```

## What I Learned

I learnt that you can start a process directly in the background by adding an ampersand (`&`) to the end of the command line.

## References

The problem statement provided was the reference used.

```
Of course, you don't have to suspend processes to background them: you can start them backgrounded right off the bat!
It's easy; all you have to do is append a & to the command, like so:

hacker@dojo:~$ sleep 1337 &
[1] 1771
hacker@dojo:~$
Here, sleep is actively running in the background, not suspended.
Now it's your turn to practice!
Launch /challenge/run backgrounded for the flag!
```
# 10. Process Exit Codes

This challenge prompted me to capture the exit code of one program and use it as an argument for another.

## My Solve

**Flag:** `pwn.college{4IiHD99yQxBsIPwgwgPxHkqd2Hu.QX5YDO1wCM2EDNzEzW}`

First, I ran `/challenge/get-code`. Then I used `echo $?` to get the exit code of that last command, which was 28. Then I passed that code as an argument to `/challenge/submit-code` to get the flag.

```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
28
hacker@processes~process-exit-codes:~$ /challenge/submit-code 28
CORRECT! Here is your flag:
pwn.college{4IiHD99yQxBsIPwgwgPxHkqd2Hu.QX5YDO1wCM2EDNzEzW}
```

## What I Learned

I learnt that every command returns an exit code, and I can access the code of the last command using the special variable `$?`.

## References

The problem statement provided was the reference used.

```
Every shell command, including every program and every builtin, exits with an exit code
 when it finishes running and terminates.
...
You can access the exit code of the most recently-terminated command using the special ? variable...
...
In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument.
```


