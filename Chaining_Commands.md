# 1. Chaining with Semicolons

This challenge prompted me to run two commands in sequence on a single line.

## My Solve

**Flag:** `pwn.college{gmgRiCGmChDwOqrI9jTj70qOHns.QX1UDO0wCM2EDNzEzW}`

I needed to run `/challenge/pwn` followed by `/challenge/college`. I did this on one line by separating the two commands with a semicolon.

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{gmgRiCGmChDwOqrI9jTj70qOHns.QX1UDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that a semicolon (`;`) can be used to separate multiple commands on the same line, and they will be executed in order.

## References

The problem statement provided was the reference used.

```
The easiest way to chain commands is ;.
In most contexts, ; separates commands in a similar way to how Enter separates lines.
...
Basically, when you hit Enter, your shell executes your typed command
 and, after that command terminates, gives you the prompt to input 
another command.
The semicolon is analogous, just without the prompt and with you 
entering both commands before anything is executed.
Give it a try now! In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.
```

# 2. Building on Success

This challenge prompted me to chain two commands so that the second runs only if the first succeeds.

## My Solve

**Flag:** `pwn.college{0gCiUib_Q6uA25DCAuyl6tJOJrQ.0lM0MDOxwCM2EDNzEzW}`

I needed to run `/challenge/second` only after `/challenge/first-success` completed successfully. I used the `&&` operator to chain them together on one line, which provided the flag.

```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{0gCiUib_Q6uA25DCAuyl6tJOJrQ.0lM0MDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `&&` operator can be used to run a second command only if the first command executes successfully, meaning it exits with code 0.

## References

The problem statement provided was the reference used.

```
You learned about exit codes in the Processes module.
Now let's use them to chain commands together!
The && operator allows you to run a second 
command only if the first command succeeds (in Linux convention, this 
means it exited with code 0).
...
Here's the syntax:

hacker@dojo:~$ command1 && command2
This means: "Run command1, and IF it succeeds, then run command2."
...
In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the && operator.
```

# 3. Handling Failure

This challenge prompted me to chain two commands so that the second runs only if the first fails.
## My Solve

**Flag:** `pwn.college{8fg3KQRSCpnc7xf43V07aiMz2w2.01M0MDOxwCM2EDNzEzW}`

The goal was to run `/challenge/second` only after `/challenge/first-failure` failed. I used the `||` operator to chain the two commands, which executed the second program after the first one exited with an error.

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{8fg3KQRSCpnc7xf43V07aiMz2w2.01M0MDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `||` operator can be used to run a second command only if the first command fails, meaning it exits with a non-zero code.

## References

The problem statement provided was the reference used.

```
You just learned about the && operator, which runs the second command only if the first succeeds.
Now let's learn about its opposite: the || operator allows you to run a second command only if the first command fails (exits with a non-zero code).
...
Here's the syntax:

hacker@dojo:~$ command1 || command2
This means: "Run command1, and IF it fails, then run command2."
...
In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator.
```

# 4. First Shell Script

This challenge prompted me to create and execute a simple shell script.

## My Solve

**Flag:** `pwn.college{Qaf9cbPuZRF61EmQQk_euk8T3Y6.QXxcDO0wCM2EDNzEzW}`

I created a file named `x.sh` and put the two required commands inside it, each on a new line. Then I executed the script by running `bash x.sh` to get the flag.

Content of `x.sh`:

```
/challenge/pwn
/challenge/college
```

Execution:

```
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{Qaf9cbPuZRF61EmQQk_euk8T3Y6.QXxcDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that you can put a sequence of shell commands into a file (a shell script) and then run them all by executing the script with an interpreter like `bash`.

## References

The problem statement provided was the reference used.

```
When this happens, you can put these commands in a file, called a shell script, and run them by executing the file!
...
And then we can execute by passing it as an argument to a new instance of our shell (bash)!
...
Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!
```

# 5. Redirecting Script output

This challenge prompted me to pipe the output of an entire shell script into another program.

## My Solve

**Flag:** `pwn.college{oBr8WHYnyUdN68U0UkhjFYflOAW.QX4ETO0wCM2EDNzEzW}`

I created a script named `x.sh` that ran two challenge programs in sequence. Then, I executed the script with `bash` and piped its combined output into the `/challenge/solve` program to get the flag.

Content of `x.sh`:
```
/challenge/pwn
/challenge/college
```

```
hacker@chaining~redirecting-script-output:~$ nano x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{oBr8WHYnyUdN68U0UkhjFYflOAW.QX4ETO0wCM2EDNzEzW}
```

## What I Learned

I learnt that a shell script can be treated like a single command, and its entire standard output can be redirected or piped into other commands.

## References

The problem statement provided was the reference used.

```
As far as the shell is concerned, your script is just another command.
That means you can redirect its input and output just like you did for commands in the Piping module!
...
All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors, and | for piping to another command.
In this level, we will practice piping (|) from your script to another program.
...you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command!
```

# 6. Executable shell scripts

This challenge prompted me to make a shell script executable and run it directly.

## My Solve

**Flag:** `pwn.college{YOroAsemjL8eRJQ-g6ZsBmeIcM0.QX0cjM1wCM2EDNzEzW}`

I created a script named `script.sh` containing the path to the solve binary. I then used `chmod +x` to make the script executable and ran it with `./script.sh` to get the flag.

```
hacker@chaining~executable-shell-scripts:~$ nano script.sh
hacker@chaining~executable-shell-scripts:~$ cat script.sh
/challenge/solve
hacker@chaining~executable-shell-scripts:~$ chmod +x script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{YOroAsemjL8eRJQ-g6ZsBmeIcM0.QX0cjM1wCM2EDNzEzW}
```

## What I Learned

I learnt that if a script file has execute permissions (`+x`), it can be run directly using its path (like `./script.sh`) without needing to pass it to an interpreter like `bash`.

## References

The problem statement provided was the reference used.

```
You have written your first shell script, but calling it via bash script.sh is a pain.
...
It turns out that you can avoid the need to manually invoke bash.
If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path!
...
Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!
```

# 8. Scripting with arguments

This challenge prompted me to write a script that processes command-line arguments.

## My Solve

**Flag:** `pwn.college{I0vq2B8AQyDR2X-fxw1_rc1gP3E.0VNzMDOxwCM2EDNzEzW}`

I created a script named `solve.sh` that takes two arguments and prints them in reverse order. The script used the special variables `$2` and `$1` to access the arguments. I made it executable and ran the verifier to get the flag.

Content of `solve.sh`:

Bash

```
#!/bin/bash

echo "$2 $1"
```

Execution:

Bash

```
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod +x solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{I0vq2B8AQyDR2X-fxw1_rc1gP3E.0VNzMDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that shell scripts can access command-line arguments using special positional variables like `$1` for the first argument, `$2` for the second, and so on.

## References

The problem statement provided was the reference used.

```
Scripts become much more powerful when they can accept arguments!
...
The script can access these arguments using special variables:

$1 contains the first argument ("hello")
$2 contains the second argument ("world")
...
For this challenge, you need to write a script at /home/hacker/solve.sh that:

Takes two arguments
Outputs them in REVERSE order (second argument first, then the first argument)
```

# 9. Scripting with Conditionals

This challenge prompted me to write a script that uses an `if` statement to check an argument.

## My Solve

**Flag:** `pwn.college{IQ8KU57Aw3YsZGNRLF51WtbWvEn.0lNzMDOxwCM2EDNzEzW}`

I created a script named `solve.sh` that contained an `if` statement. The script checks if the first argument (`$1`) is equal to the string "pwn", and if it is, it prints "college". After creating the script, I ran the verifier to get the flag.

Content of `solve.sh`:
```
#!/bin/bash

if [ "$1" == "pwn" ]
then
      echo "college"
fi
```

```
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{IQ8KU57Aw3YsZGNRLF51WtbWvEn.0lNzMDOxwCM2EDNzEzW}
```

## What I Learned

I learnt the basic syntax of an `if` statement in bash to perform conditional checks, using `[ ... ]` for the condition and `then ... fi` for the body.

## References

The problem statement provided was the reference used.

```
Now that you can use arguments in scripts, let's make them smarter with conditional logic!
In bash, you can use if statements to make decisions:

if [ "$1" == "ping" ]
then
    echo "pong"
fi
...
For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "pwn", output "college"
For any other input, output nothing
```

# 10. Scripting with default cases

This challenge prompted me to write a script with an `if/else` conditional statement.

## My Solve

**Flag:** `pwn.college{g3ja_4lzXebYvBT30AesZFVwDje.01NzMDOxwCM2EDNzEzW}`

I created a script `solve.sh` with an `if/else` block. It checks if the first argument is "pwn" and prints "college" if it matches, or "nope" for any other input. After writing the script, I ran the verifier to get the flag.

Content of `solve.sh`:

```
#!/bin/bash

if [ "$1" == "pwn" ]
then
      echo "college"
else
      echo "nope"
fi
```

```
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{g3ja_4lzXebYvBT30AesZFVwDje.01NzMDOxwCM2EDNzEzW}
```

## What I Learned

I learnt how to use an `else` clause with an `if` statement to create a default case that runs when the `if` condition is false.

## References

The problem statement provided was the reference used.

```
Your if statements so far have handled specific cases, but what about everything else?
That's where else comes in!
The else clause executes when the if condition is false:

if [ "$1" == "hello" ]
then
    echo "Hi there!"
else
    echo "I don't understand"
fi
...
For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "pwn", output "college"
For any other input, output "nope"
```

# 11. Scripting with multiple conditions

This challenge prompted me to write a script that handles multiple conditions using `if/elif/else`.

## My Solve

**Flag:** `pwn.college{0DQSJznsYRdLjj3A7NScrKVEPTq.0FOzMDOxwCM2EDNzEzW}`

I created a script `solve.sh` that used an `if/elif/else` structure to check the first argument against several strings. It printed a different output for "pwn", "hack", and "learn", and a default "unknown" for anything else. After writing the script, I ran the verifier.

Content of `solve.sh`:

```
#!/bin/bash

if [ "$1" == "pwn" ]
then
      echo "college"
elif [ "$1" == "hack" ]
then
      echo "the planet"
elif [ "$1" == "learn" ]
then
      echo "linux"
else
      echo "unknown"
fi
```

```
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{0DQSJznsYRdLjj3A7NScrKVEPTq.0FOzMDOxwCM2EDNzEzW}
```

## What I Learned

I learnt how to use `elif` to check for multiple, different conditions in a sequence within a single `if` block.

## References

The problem statement provided was the reference used.

```
You've learned how to use a single if statement to check a condition.
But what if you need to check multiple conditions?
You can use elif (short for else if):

if [ "$1" == "one" ]
then
    echo "1"
elif [ "$1" == "two" ]
then
    echo "2"
...
else
    echo "unknown"
fi
...
For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "hack", output "the planet"
If the argument is "pwn", output "college"
If the argument is "learn", output "linux"
For any other input, output "unknown"
```

# 12. Reading Shell Scripts

This challenge prompted me to read the source code of a shell script to find a password.

## My Solve

**Flag:** `pwn.college{4Jifp8i3pBNLEQkPnpVUPJEuC5F.0lMwgDOxwCM2EDNzEzW}`

I used `cat /challenge/run` to read the script's source code. I saw in the `if` statement that it was checking for the password "hack the PLANET". I then ran the script and entered that password to get the flag.

```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{4Jifp8i3pBNLEQkPnpVUPJEuC5F.0lMwgDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that you can understand a program's logic by reading its source code if it's a script.

## References

The problem statement provided was the reference used.

```
In this level, we will learn to read shell scripts.
/challenge/run is a shell script that requires you to put in a secret password, but that password is hardcoded into the script iself!
Read the script (using, say, cat), figure out the password, and get the flag!
```
