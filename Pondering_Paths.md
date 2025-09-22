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


# 4. Position Elsewhere
Like the last challenge, this challenge also required me to run the `/challenge/run` command and invoke `run` from a specific directory.

## My Solve
**Flag:** `pwn.college{QDqAZ6_9fS1OeWP0YXt0Mvybir2.QX3QTN0wCM2EDNzEzW}`

In the problem statement, it was provided that using `/challenge/run` from a specific directory, the program would be initialized, and thus would provide the flag.

1. First I ran the `/challenge/run` command to invoke the `run` program.
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
```

2. Then I used `cd` to change my directory to `/usr/share/doc/fontconfig` and re-ran the `run` program
```
hacker@paths~position-elsewhere:~$ cd /usr/share/doc/fontconfig
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QDqAZ6_9fS1OeWP0YXt0Mvybir2.QX3QTN0wCM2EDNzEzW}
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$
```

## What I learned
It was similar to the last challenge `Position thy self`.

## References
The problem statement was the reference used

```
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the `cd` (`c`hange `d`irectory) command and passing a path to it as an argument, as so:

console
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$


This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the `~` was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the `/challenge/run` program from a specific path (which it will tell you). You'll need to `cd` to that directory before rerunning the challenge program. Good luck!
```

# 5. Position yet elsewhere

Similar to problems `3` and `4`, invoke the `run` program from a specific path.

## My Solve
**Flag:** `pwn.college{8TZvvaiVFdmvsDtPcb9HNH8dNO9.QX4QTN0wCM2EDNzEzW}`

<p>In the problem statement, it was provided that using `/challenge/run` from a specific directory, the program would be initialized, and thus would provide the flag.</p>

1.  First I ran the `/challenge/run` command to invoke the `run` program.
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/131 directory.
Please use the `cd` utility to change directory appropriately.
```
2.  Then I used `cd` to change my directory to `/proc/131` and re-ran the `run` program
```
hacker@paths~position-yet-elsewhere:~$ cd /proc/131
hacker@paths~position-yet-elsewhere:/proc/131$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8TZvvaiVFdmvsDtPcb9HNH8dNO9.QX4QTN0wCM2EDNzEzW}
```

## What I learned
It was similar to the last challenge `3.Position thy self`.and `4.Position elsewhere`

## References
The problem statement was the reference used
```
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the `cd` (`c`hange `d`irectory) command and passing a path to it as an argument, as so:

console
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$


This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the `~` was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the `/challenge/run` program from a specific path (which it will tell you). You'll need to `cd` to that directory before rerunning the challenge program. Good luck!
```

# 6. Implicit relative paths, from /

The challenge prompted me to run `/challenge/run` from a relative path by setting my current working directory to `/`

## My Solve
**Flag:** `pwn.college{4DZUwdwA3atIyvN7lYKM0NcJJ9Z.QX5QTN0wCM2EDNzEzW}`

First I changed my `cwd` to `/`, then invoked the `run` program in the `challenge` directory.
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ ^C
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4DZUwdwA3atIyvN7lYKM0NcJJ9Z.QX5QTN0wCM2EDNzEzW}
```

## What I learnt
I learnt the usage of relative paths (any path that does not start at root), and my current working directory or `cwd` is where the prompt locates the relative path for

## References
The problem statement was the reference used
```
However, the current working directory does matter for **relative** paths.

- A relative path is any path that does not start at root (i.e., it does not start with `/`).
- A relative path is interpreted **relative** to your **c**urrent **w**orking **d**irectory (`cwd`).
- Your `cwd` is the directory that your prompt is currently located at.

This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at `/tmp/a/b/my_file`.

- If my `cwd` is `/`, then a relative path to the file is `tmp/a/b/my_file`.
- If my `cwd` is `/tmp`, then a relative path to the file is `a/b/my_file`.
- If my `cwd` is `/tmp/a/b/c`, then a relative path to the file is `../my_file`. The `..` refers to the parent directory.

Let's try it here! You'll need to run `/challenge/run` using a relative path while having a current working directory of `/`. For this level, I'll give you a hint. Your relative path starts with the letter `c` 😊
```

# 7. Explicit relative paths, from /

This challenge is similar to last challenge, I am required to invoke the `run` program from `/` directory, with the addition of `./` in the path

## My Solve
**Flag:** `pwn.college{MBDheQwY7D2ggT811CAOFKQPDeQ.QXwUTN0wCM2EDNzEzW}`

First I changed my `cwd` to root directory `/`, then I invoked the program using the path `./challenge/run`, This is identical to the path `challenge/run`. Here the `./` references to the `cwd` only
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{MBDheQwY7D2ggT811CAOFKQPDeQ.QXwUTN0wCM2EDNzEzW}
```

## What I learned
I learnt where and how `./` is used while defining relative paths

## References
The problem statement was the referenced used
```
Of course, if your current working directory is `/`, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using `.` in your relative paths. Get ready!
```

# 8. Implicit relative paths

The challenge prompted to invoke the `run` program from the `cwd` of `/challenge`

## My Solve
**Flag:** `pwn.college{0OtEfn4-4l6xuS-6UowTaMyFNNu.QXxUTN0wCM2EDNzEzW}`

First I changed my `cwd` to the `/challenge` and then invoked the program by using the path `./run`
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0OtEfn4-4l6xuS-6UowTaMyFNNu.QXxUTN0wCM2EDNzEzW}
```

## What I learned
I learned why directly mentioning the name of the program while having your `cwd` in that executable's directory would not invoke the executable.
`This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities!`

## References
The problem statement was the reference used
```
In this level, we'll practice referring to paths using `.` a bit more. This challenge will need you to run it from the `/challenge` directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

console
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run


This will _not_ invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:


bash: run: command not found

We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use relative paths to launch `run` in this scenario. The way to do this is to _tell_ Linux that you explicitly want to execute a program in the current directory, using `.` like in the previous levels. Give it a try now!
```

# 9. home sweet home
I was prompted to use the `/challenge/run` with an argument that was an absolute path, which must be inside the `~` (home) directory and is three characters or less

## My Solve
**Flag:** `pwn.college{8Aby-MNVpvl9LJLsPwWPvy1KpMO.QXzMDO0wCM2EDNzEzW}`

The argument I provided  `/challenge/run` was `~/C`. This wrote the flag to a file in `/home/hacker/C`.

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/C
Writing the file to /home/hacker/C!
... and reading it back to you:
pwn.college{8Aby-MNVpvl9LJLsPwWPvy1KpMO.QXzMDO0wCM2EDNzEzW}
```

## What I learned
The path `~` is a short-hand for `/home/user` directory. The expansion of `~` will always be a absolute path

## References
The problem statement was the reference used.
```
Now it's your turn to play! In this challenge, `/challenge/run` will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

1. Your argument must be an absolute path.
2. The path must be inside your home directory.
3. Before expansion, your argument must be three characters or less.

Again, you must specify your path as an _argument_ to `/challenge/run` as so:

hacker@dojo:~$ /challenge/run YOUR_PATH_HERE

```

