# 1. Redirecting Output

The challenge required using the output redirection character (`>`) to write a specific string into a file.
## My Solve

**Flag:** `pwn.college{0sVbP5jUMu-g_r_ARyjZOHHlBRv.QX0YTN0wCM2EDNzEzW}`

I used the `echo` command to output the string "PWN" and then used the `>` operator to redirect that output directly into file named "COLLEGE". This command created the file and I was prompted with the flag.

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{0sVbP5jUMu-g_r_ARyjZOHHlBRv.QX0YTN0wCM2EDNzEzW}
```

## What I Learned

I learnt the usage of the `>` operator for redirecting standard output (stdout). This is a core shell concept for saving command results, creating files, and controlling data flow. 

## References

The problem statement provided was the reference used.

```
First, let's look at redirecting stdout to files.
You can accomplish this with the > character, as so:

hacker@dojo:~$ echo hi > asdf
This will redirect the output of echo hi (which will be hi) to the file asdf.
You can then use a program such as cat to output this file:

hacker@dojo:~$ cat asdf
hi
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).
```


# 2. Redirecting More Output

The challenge asked me to redirect the standard output (stdout) of a binary to a file, while observing messages on standard error (stderr).
## My Solve

**Flag:** `pwn.college{ImUSscKuDFKQTi78yC2phY1CBzJ.QX1YTN0wCM2EDNzEzW}`

First, I executed the `/challenge/run` binary using `>` operator to redirect its  output to a file named `myflag`. By which the `stderr` text was printed to my terminal. Then I used the `cat` on `myflag`, which prompted me the flag.

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ImUSscKuDFKQTi78yC2phY1CBzJ.QX1YTN0wCM2EDNzEzW}
```

## What I Learned

I learnt that programs have one standard output (stdout) for normal output and one standard error (stderr) for errors.

## References

The problem statement provided was the reference used.

```
Aside from redirecting the output of echo, you can, of course, redirect the output of any command.
In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag.
Your flag will, of course, end up in the myflag file!
You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout.
That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!
```

Roger that. Here's the updated write-up for challenge #3, revised to be more concise and direct.

---

# 3. Appending Output

The challenge required using append-mode redirection (`>>`) to combine two parts of a flag into a single file.

## My Solve

**Flag:** `pwn.college{Yz2t1Zd9WTTyQqLN6jFpeZ89z1j.QX3ATO0wCM2EDNzEzW}`

The program wrote the flag in two parts. To prevent the second part from overwriting the first, I redirected the program's output using the append operator (`>>`) into the file `the-flag`. Then I read the file to get the complete flag.

```
hacker@piping~appending-output:~$ /challenge/run >> the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!

hacker@piping~appending-output:~$ /challenge/run >> the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
...
hacker@piping~appending-output:~$ cat the-flag
 |
\|/ This is the first half:
 v
pwn.college{Yz2t1Zd9WTTyQqLN6jFpeZ89z1j.QX3ATO0wCM2EDNzEzW}
                              ^
     that is the second half /|\
                              |
```

## What I Learned

I learned to use the `>>` operator to **append** output to a file. Unlike `>`, which overwrites a file's contents, `>>` adds the new output to the end.
## References

The problem statement provided was the reference used.

```
A common use-case of output redirection is to save off some command results for later analysis.
...
You can redirect input in append mode using >> instead of >, as so:

hacker@dojo:~$ echo pwn > outfile
hacker@dojo:~$ echo college >> outfile
hacker@dojo:~$ cat outfile
pwn
college

To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag.
...
```

# 4. Redirecting Errors

The challenge was to redirect a program's standard output and standard error to two different files.

## My Solve

**Flag:** `pwn.college{8GwZcXvPU35DGAg1Icbmo1Kfc6R.QX3YTN0wCM2EDNzEzW}`

The task was to save the program's normal output and its error messages into separate files. I redirected standard output (FD 1) to `myflag` and standard error (FD 2) to `instructions`. After running the command, the flag was found in the `myflag` file.

```
hacker@piping~redirecting-errors:~$ /challenge/run 1> myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{8GwZcXvPU35DGAg1Icbmo1Kfc6R.QX3YTN0wCM2EDNzEzW}
```

## What I Learned

I learned about **File Descriptors** (FDs) and how the shell uses them: **`0`** for standard input, **`1`** for standard output, and **`2`** for standard error. This allows for redirecting specific streams, like using `2>` to capture only error messages.

## References

The problem statement provided was the reference used.

```
Just like standard output, you can also redirect the error channel of commands.
Here, we'll learn about File Descriptor numbers.
A File Descriptor (FD) is a number that describes a communication channel in Linux.
...
FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
...
In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions.
```

# 5. Redirecting Input

This challenge required creating a file with specific content and then redirecting that file as standard input to a program.
## My Solve

**Flag:** `pwn.college{ohGLn4FwrzuFh2Jstn6H7DONEVN.QXwcTN0wCM2EDNzEzW}`

The challenge was a two-step process. First, I created a file named `PWN` containing the word 'COLLEGE' using output redirection. Second, I used the input redirection operator (`<`) to feed the contents of the `PWN` file into the `/challenge/run` program, which then printed the flag.

```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{ohGLn4FwrzuFh2Jstn6H7DONEVN.QXwcTN0wCM2EDNzEzW}
```

## What I Learned

I learned how to use the `<` operator to redirect a file's content as **standard input (stdin)** to a command. This is a powerful way to provide input to programs non-interactively.
## References

The problem statement provided was the reference used.

```
Just like you can redirect output from programs, you can redirect input to programs!
This is done using <, as so:

hacker@dojo:~$ echo yo > message
hacker@dojo:~$ rev < message
oy

In this level, we will practice using /challenge/run, which will require you to redirect t
```

# 6. Grepping Stored Results

This challenge involved redirecting a large amount of output to a file and then using `grep` to find the flag within it.

## My Solve

**Flag:** `pwn.college{U6PzeWM1X2K_M8ljsQ2t2qS3W3I.QX4EDO0wCM2EDNzEzW}`

First, I redirected the output of `/challenge/run` into the file `/tmp/data.txt`. To find the flag in the large file, I then piped the file's contents to `grep` and searched for the known flag format `pwn.college{`, which isolated the correct line.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ cat /tmp/data.txt | grep "pwn.college{"
pwn.college{U6PzeWM1X2K_M8ljsQ2t2qS3W3I.QX4EDO0wCM2EDNzEzW}
```

## What I Learned

I learned to combine **output redirection** with `grep` to efficiently search for specific patterns in large datasets. This is a common and powerful workflow for analyzing log files or the output of noisy commands. 

## References

The problem statement provided was the reference used.

```
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep).
Let's put this together!
In preparation for more complex levels, we want you to:

Redirect the output of /challenge/run to /tmp/data.txt.
This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
grep that for the flag!
```

# 7. Grepping live output

This challenge involved using the pipe (`|`) operator to search a command's live output with `grep` without saving it to a file.

## My Solve

**Flag:** `pwn.college{0Ndjzoz740wKtKmlpSPqaXqvcxs.QX5EDO0wCM2EDNzEzW}`

Instead of saving the output to a file first, I piped the standard output of `/challenge/run` directly into the standard input of `grep`. This allowed me to search for the flag pattern `pwn.college{`

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep "pwn.college{"

[INFO] WELCOME! This challenge makes the following asks of you:

[INFO] - the challenge checks for a specific process at the other end of stdout : grep

[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.

[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...

[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.

[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).

[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!

[PASS] Success! You have satisfied all execution requirements.

pwn.college{0Ndjzoz740wKtKmlpSPqaXqvcxs.QX5EDO0wCM2EDNzEzW}
```

## What I Learned

I learned that the **pipe (`|`) operator** is used to chain commands together. It connects the stdout of the command on the left to the stdin of the command on the right, which is an efficient way to process data without intermediate files.

## References

The problem statement provided was the reference used.

```
It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level.
You can do this by using the | (pipe) operator.
...
Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe.
...
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. grep for the flag!
```

# 8. Grepping errors

This challenge was about filtering a program's standard error stream by first redirecting it to standard output and then piping it to `grep`.

## My Solve

**Flag:** `pwn.college{AdlPUa8Ykz7VFZ1koLoRravqx3k.QX1ATO0wCM2EDNzEzW}`

The goal was to `grep` the error output of a program. Since the pipe (`|`) only works on standard output, I first redirected the standard error stream (FD 2) to the standard output stream (FD 1) using `2>&1`. Then, I piped this combined stream to `grep` to find the flag.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep "pwn.college{"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{AdlPUa8Ykz7VFZ1koLoRravqx3k.QX1ATO0wCM2EDNzEzW}
```

## What I Learned

I learned how to pipe **standard error**. The pipe operator `|` only sends stdout, so to filter stderr, you must first merge it into stdout using the special redirection `2>&1`. 

## References

The problem statement provided was the reference used.

```
You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep.
But what if you wanted to grep through errors directly?
...
The | operator redirects only standard output to another program... It can only redirect standard output (file descriptor 1).
Luckily, where there's a shell, there's a way!
The shell has a >& operator, which redirects a file descriptor to another file descriptor.
... first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!
```

# 9. Filter with grep -v

The challenge was to find a real flag amongst many decoys by using `grep -v` to filter out the unwanted lines.
## My Solve

**Flag:** `pwn.college{ATq8pCp_VCTw4HL8kEbCUKlECAk.0FOxEzNxwCM2EDNzEzW}`

The program's output contained many decoy flags marked with the word "DECOY". I piped the output to `grep -v "DECOY"` to invert the search and display only the line that did not contain the decoy keyword, revealing the true flag.

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v "DECOY"
pwn.college{ATq8pCp_VCTw4HL8kEbCUKlECAk.0FOxEzNxwCM2EDNzEzW}
```
## What I Learned

I learned about the **`-v`** option for `grep`, which inverts the match. It's a useful tool for filtering out noise or unwanted data to isolate the specific information you need. 
## References

The problem statement provided was the reference used.

```
The grep command has a very useful option: -v (invert match).
While normal grep shows lines that MATCH a pattern, grep -v shows lines that do NOT match a pattern:

hacker@dojo:~$ cat data.txt | grep -v world
hello hackers!

In this challenge, /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags...
Use grep -v to filter out all the lines containing "DECOY" and reveal the real flag!
```

# 10. Duplicating piped data with tee

This challenge required using the `tee` command to intercept and inspect the data in a pipe to debug a command pipeline.
## My Solve

**Flag:** `pwn.college{M40oKIq29FYAjrpjelvi1iGkFur.QXxITO0wCM2EDNzEzW}`

1. I first piped `/challenge/pwn` to `/challenge/college` and used `tee pwn.txt` to save the intermediate output. This initial attempt failed but captured the necessary debug info.
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn.txt | /challenge/college
    Processing...
    The input to 'college' does not contain the correct secret code! This code
    should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
    output of 'pwn' and figure out what the code needs to be.
```

2.  I then examined the saved output with `cat pwn.txt` and discovered that the `pwn` command required a secret argument: `--secret M40oKIq2`.
```
    hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn.txt
    Usage: /challenge/pwn --secret [SECRET_ARG]
    
    SECRET_ARG should be "M40oKIq2"
    ```
```

3. Finally, I ran the command again with the correct secret argument. This successfully piped the required data to `/challenge/college` and printed the flag.
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret M40oKIq2 | tee pwn.txt | /challenge/college
    Processing...
    WARNING: you are overwriting file pwn.txt with tee's output...
    Correct! Passing secret value to /challenge/college...
    Great job! Here is your flag:
    pwn.college{M40oKIq29FYAjrpjelvi1iGkFur.QXxITO0wCM2EDNzEzW}
```

## What I Learned

I learned how the **`tee`** command works like a T-splitter, duplicating a data stream. It passes data through to the next command in a pipe while also saving a copy to a file, which is extremely useful for debugging pipelines. 

## References

The problem statement provided was the reference used.

```
When you pipe data from one command to another, you of course no 
longer see it on your screen.
...
The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line.
...
This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!
```


# 11. Process substitution for input

The challenge was to use **process substitution** to compare the output of two different programs directly with the `diff` command.

## My Solve

**Flag:** `pwn.college{kAHZYSFTRhxIhfiwQySH2SGJf7_.0lNwMDOxwCM2EDNzEzW}`

I needed to find the difference between two programs output. I used process substitution with `diff` to compare them without making files. `diff` showed the extra line, which were the flag.

```
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
48a49
> pwn.college{kAHZYSFTRhxIhfiwQySH2SGJf7_.0lNwMDOxwCM2EDNzEzW}
```

## What I Learned

I learned about **process substitution** `(<command>)`. Its a way to use a command output like a file. This is useful for commands like `diff` that need file inputs.

## References

The problem statement provided was the reference used.

```
Sometimes you need to compare the output of two commands rather than two files.
...
For reading from a command (input process substitution), use <(command).
When you write <(command), bash will run the command and hook up its output to a temporary file that it will create.
...
Now, you'll diff two sets of command outputs: /challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag.
```


# 12. Writing to multiple programs

The challenge was to pipe the output from one command into two other commands at the same time using **`tee`** and **process substitution**.
## My Solve

**Flag:** `pwn.college{kMMPu-5P3ogKmxgWjysSoOXwXIW.QXwgDN1wCM2EDNzEzW}`

I had to send the output of `/challenge/hack` to two other programs. I piped the output to `tee`, and then used output process substitution `>(command)` for both `/challenge/the` and `/challenge/planet`. This made them look like files to `tee`, so it send the data to both.

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
15769162712324010880
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{kMMPu-5P3ogKmxgWjysSoOXwXIW.QXwgDN1wCM2EDNzEzW}
```

## What I Learned

I learned how to use **output process substitution** `>(command)` to make a program's input look like a file. You can use it with `tee` to send one output to many command's inputs at once. Its a cool trick. 

## References

The problem statement provided was the reference used.

```
Now you've learned that process substitution can make command output appear as files for reading with <(command).
But you can also use process substitution for writing to commands!
...
For writing to a command (output process substitution), use >(command).
...
Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!
```

# 13. Split-piping stderr and stdout

This challenge was to take one program's output and send its **stdout** to one program and its **stderr** to another, at the same time.

## My Solve

**Flag:** `pwn.college{E_SpQ0sRyIAIS4sKJiJeROefP3F.QXxQDM2wCM2EDNzEzW}`

To solve this, I split `/challenge/hack`'s output. then I used process substitution to create input streams for `/challenge/the` and `/challenge/planet`. Then I redirected **stderr** (`2>`) to one and **stdout** (`1>`) to the other in a single command.

```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) 1> >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{E_SpQ0sRyIAIS4sKJiJeROefP3F.QXxQDM2wCM2EDNzEzW}
```

## What I Learned

I learned how to split **stdout** and **stderr** to different program inputs. The key is using **output process substitution** (`>(command)`) to create a writeable "file" for each destination program, then redirecting the specific file descriptors (`1>` and `2>`) accordingly.
## References

The problem statement provided was the reference used.

```
Now, let's put your knowledge together.
You must master the ultimate piping task: redirect stdout to one program and stderr to another.
...
In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program
```
# 14. Named Pipes

This challenge involved creating a **named pipe** (FIFO) and managing its blocking behavior to redirect a program's output into it.
## My Solve

**Flag:** `pwn.college{YMttzTdk7FofRwu7xAZhJ-FfeCy.01MzMDOxwCM2EDNzEzW}`

1. First, I created a persistent named pipe on the filesystem using the `mkfifo` command.
```
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
```

2.  FIFOs require both a reader and a writer to be connected before data can flow. To manage this, I started the reader (`cat`) as a background job with `&`, which made it wait. Then, in the same line, I started the writer (`/challenge/run`), which unblocked the pipe and allowed the flag to be written and read.

```
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo & /challenge/run > /tmp/flag_fifo
[1] 226
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{YMttzTdk7FofRwu7xAZhJ-FfeCy.01MzMDOxwCM2EDNzEzW}
[1]+  Done                    cat /tmp/flag_fifo
```

## What I Learned

I learned how to create and use **named pipes** (also called **FIFOs**) with `mkfifo`. Their key feature is the blocking behavior that synchronizes processes: a writer waits for a reader, and vice-versa. This makes them a powerful tool for passing data between processes in memory without using temporary disk files. 

## References

The problem statement provided was the reference used.

```
You can also create your own persistent named pipes that stick around on the filesystem!
These are called FIFOs, which stands for First (byte) In, First (byte) Out.
You create a FIFO using the mkfifo command...
...
One problem with FIFOs is that they'll "block" any operations on them
 until both the read side of the pipe and the write side of the pipe are
 ready.
...
You'll need to create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it.
```
