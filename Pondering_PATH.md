
# 1. The PATH variable

This challenge prompted me to manipulate the `PATH` variable to prevent a program from finding a command.

## My Solve

**Flag:** `pwn.college{8Im3HfR_jiAZKlNc_9GhNO1er6t.QX2cDM1wCM2EDNzEzW}`

The goal was to stop the `/challenge/run` program from using the `rm` command. I did this by clearing the `PATH` variable by setting it to an empty string, and then exporting it. When I ran `/challenge/run`, it inherited the empty `PATH` and couldn't find `rm`, so it failed to delete the flag.

```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ export PATH
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{8Im3HfR_jiAZKlNc_9GhNO1er6t.QX2cDM1wCM2EDNzEzW}
```

## What I Learned

I learnt that the `PATH` environment variable contains a list of directories the shell searches for commands. By clearing and exporting it, I can prevent child processes from finding and executing standard programs.

## References

The problem statement provided was the reference used.

```
There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.
...
In this level, you will disrupt the operation of the /challenge/run program.
This program will DELETE the flag file using the rm command.
However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you!
...
/challenge/run will be a child process of your shell, so you must apply the concepts you learned in Shell Variables to mess with its PATH variable!
```

# 2. Setting PATH

This challenge prompted me to set the `PATH` variable to a specific directory.

## My Solve

**Flag:** `pwn.college{ENsIY6M9fhQN_Np6krv3nYr6Ta5.QX1cjM1wCM2EDNzEzW}`

The `/challenge/run` program needed to find the `win` command, which was in `/challenge/more_commands`. I set the `PATH` variable to just that directory. When I ran `/challenge/run`, it was able to find and execute `win`, giving me the flag.

```
hacker@path~setting-path:~$ PATH="/challenge/more_commands"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{ENsIY6M9fhQN_Np6krv3nYr6Ta5.QX1cjM1wCM2EDNzEzW}
```

## What I Learned

I learnt that you can change the `PATH` to point to a new directory, which makes the shell look there for commands. This lets you run programs in that directory without typing their full path.

## References

The problem statement provided was the reference used.

```
...by adding directories to or replacing directories in this list,
 you can expose these programs to be launched using their bare name!
For example:

hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!

This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH.
...you can just overwrite PATH with that one directory.
```

# 3. Finding Commands

This challenge prompted me to find the location of a command and read a file which was in the same directory.

## My Solve

**Flag:** `pwn.college{s3Zhss0Xtod2mffe7MGEpvBy_dh.01NzEzNxwCM2EDNzEzW}`

I used `which win` to find the full path of the `win` executable. Once I had the directory path, I listed its contents with `ls` and found a `flag` file, which I then read using `cat`.

```
hacker@path~finding-commands:~$ which win
/challenge/paths/7710/win
hacker@path~finding-commands:~$ ls /challenge/paths/7710
flag  win
hacker@path~finding-commands:~$ cat /challenge/paths/7710/flag
pwn.college{s3Zhss0Xtod2mffe7MGEpvBy_dh.01NzEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `which` command searches the directories in the `$PATH` variable to show the full path of an executable.

## References

The problem statement provided was the reference used.

```
When you type the name of a command, something inside one of the many directories listed in your $PATH variable is what actually gets executed...
But which file, precisely?
You can find out with the aptly-named which command:

hacker@dojo:~$ which cat
/bin/cat

In this challenge, we added a win command somewhere in your $PATH...
You must find win (with the which command), and cat the flag out of that directory!
```

# 4. Adding Commands

This challenge prompted me to create a custom command and modify the `PATH` so another program could use it.

## My Solve

**Flag:** `pwn.college{s9UOlWlAyTHc4nTIXgnl8wKgny6.QX2cjM1wCM2EDNzEzW}`

The `/challenge/run` program needed a `win` command, so I created a shell script named `win` in my home directory that would `cat` the flag. I then set my `PATH` to include both the standard binary directory and my home directory. This allowed `/challenge/run` to find my `win` script, and my script to find the `cat` command.

Content of `win`:

```
#!/bin/bash
cat /flag
```

```
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ PATH="/run/dojo/bin:/home/hacker"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{s9UOlWlAyTHc4nTIXgnl8wKgny6.QX2cjM1wCM2EDNzEzW}
```

## What I Learned

I learnt how to create my own commands by writing a script and adding its directory to the `PATH`. I also learnt that the `PATH` needs to include directories for all the commands that will be used, including those used by my script.

## References

The problem statement provided was the reference used.

```
...make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!
Hint: /challenge/run runs as root and will call win. Thus, win can simply cat the flag file.
Again, the win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory.
But remember, if you do that, your win command won't be able to find cat.
```

# 5. Hijacking Commands

This challenge prompted me to hijack a command by creating a fake program and manipulating the `PATH`.

## My Solve

**Flag:** `pwn.college{Au664dOlsRLQFTHeEzvq2cZ20Bk.QX3cjM1wCM2EDNzEzW}`

To stop `/challenge/run` from deleting the flag, I created my own script named `rm` that would `cat /flag` instead. I made it executable with `chmod +x`, then prepended the current directory (`.`) to my `PATH`. This made the shell find my `rm` script before the real one, so when `/challenge/run` tried to delete the flag, it printed it instead.

Content of my `rm` script:

```
#!/bin/bash

cat /flag
```

```
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod +x rm
hacker@path~hijacking-commands:~$ PATH=".:$PATH"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{Au664dOlsRLQFTHeEzvq2cZ20Bk.QX3cjM1wCM2EDNzEzW}
```

## What I Learned

I learnt about PATH hijacking. By creating a script with the same name as a system command and placing its directory at the beginning of the `PATH`, you can make the shell execute your script instead of the real command.

## References

The problem statement provided was the reference used.

```
This challenge is almost the same as the first challenge in this module.
Again, this challenge will delete the flag using the rm command.
But unlike before, it will not print anything out for you.
How can you solve this?
You know that rm is searched for in the directories listed in the PATH variable.
You have experience creating the win command when the previous challenge needed it.
What else can you create?
```
