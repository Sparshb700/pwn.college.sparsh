# 1. The Root
The question prompted me to invoke a program called `pwn` by giving its absolute path, using the terminal.
## My Solve
**Flag:** `pwn.college{Q7GpIbTTkavylc2SnBJCdcTm-TS.QX4cTO0wCM2EDNzEzW}`

In the problem statement, it was provided that using `/pwn`, the program would be initialized, and thus would provide the flag

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{Q7GpIbTTkavylc2SnBJCdcTm-TS.QX4cTO0wCM2EDNzEzW}
```

## What I learned
I learnt to run programs using the bash script, and I learnt what are absolute paths.
By pointing to the absolute path of an executable, the program can be executed. `/` points to the root directory.

## References
The problem statement was the reference used
```
Alright, so the filesystem starts at `/`. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, _flags_. In this level, we've added a program right in `/`, called `pwn`, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from `/`, so the path would be `/pwn`. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the `pwn` program using its absolute path, and Capture that Flag! Good luck!
```


# 2. Program and absolute paths
The question prompted me to invoke a program called `run` by pointing to its absolute path in the directory `challenge`, using the terminal.

## My Solve
**Flag:** `pwn.college{QfXr1ZDK-vXtHRPqA-_P0j64ggD.QX1QTN0wCM2EDNzEzW}`

In the problem statement, it was provided that using `/challenge/run`, the program would be initialized, and thus would provide the flag
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{QfXr1ZDK-vXtHRPqA-_P0j64ggD.QX1QTN0wCM2EDNzEzW}
```

## What I learned
I learnt how to run programs by pointing to the absolute path. If they are in a directory, the directory needs to be mentioned in the absolute path.

## References
The problem statement was the reference used.
```
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the `challenge` directory and the `challenge` directory is, in turn, right in the root directory (`/`). The path to the challenge directory is, thus, `/challenge`. The name of the challenge program in this level is `run`, and it lives in the `/challenge` directory. Thus, the path to the `run` challenge program is `/challenge/run`.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the `run` file that is in the `challenge` directory that is, in turn, in the `/` directory. If you invoke the challenge correctly, it will give you the flag. Good luck!
```

# 3. Position thy self
The question prompted me to invoke a program called `run` by pointing to its absolute path in the directory `challenge` and by changing my current working directory to a specific directory.

## My Solve
**Flag:** `pwn.college{AwYWq4bCAVNAJYY4v5Lbtk2oF2O.QX2QTN0wCM2EDNzEzW}`

In the problem statement, it was provided that using `/challenge/run` from a specific directory, the program would be initialized, and thus would provide the flag.
1. Firstly Invoking the `/challenge/run` command, I was prompted with this

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
```

2. Then I switched to the `etc` directory and invoked `run` again and was prompted with the flag
```
hacker@paths~position-thy-self:~$ cd /etc
hacker@paths~position-thy-self:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AwYWq4bCAVNAJYY4v5Lbtk2oF2O.QX2QTN0wCM2EDNzEzW}
```

## What I learned
I learnt the use of `cd` command, I learned what current working directory is.

## References
The problem statement was the reference used.
```
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the `~` was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the `/challenge/run` program from a specific path (which it will tell you). You'll need to `cd` to that directory before rerunning the challenge program. Good luck!
```


