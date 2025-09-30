
# 1. Printing Variables

This challenge prompted me to print the value of a shell variable to the terminal.

## My Solve

**Flag:** `pwn.college{I5ku2TOSC6lgSJkEyMr7ViR8NQf.QX3UTN0wCM2EDNzEzW}`

The flag was stored in a variable named `FLAG`. I used `echo` to read the content of the variable.

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{I5ku2TOSC6lgSJkEyMr7ViR8NQf.QX3UTN0wCM2EDNzEzW}
```

## What I Learned

I learned that to access the value of a shell variable, the prefix of its name starts with a dollar sign `$`

## References

The problem statement provided was the reference used.

```
The /challenge/run program will not, and cannot, give you 
the flag, but that's okay, because the flag has been put into the 
variable called "FLAG"!
Just have your shell print it out!
...
You can also print out variables with echo, by prepending the variable name with a $.
...
Have your shell print out the FLAG variable and solve this challenge!
```

# 2. Setting Variables

This challenge prompted me to assign a string value to shell variable.

## My Solve

**Flag:** `pwn.college{YFuFPH1h-547jX_ldJCoYJzoGfC.QX5UTN0wCM2EDNzEzW}`

I just set the variable `PWN` to the value `COLLEGE`, and was prompted with the flag. 

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is your flag:
pwn.college{YFuFPH1h-547jX_ldJCoYJzoGfC.QX5UTN0wCM2EDNzEzW}
```

## What I Learned

I learned the syntax for **setting a variable** is `VAR=value`. You should not provide any spaces while defining a shell variable, otherwise the shell will misinterpret it for a command.

## References

The problem statement provided was the reference used.

```
Naturally, as well as reading values stored in variables, you can write values to variables.
This is done, as with many other languages, using =.
To set variable VAR to value 1337, you would use:

hacker@dojo:~$ VAR=1337
Note that there are no spaces around the =!
...
To solve this level, you must set the PWN variable to the value COLLEGE.
```


# 3. Multi word variables

This challenge prompted me to set a variable to a value containing spaces.

## My Solve

**Flag:** `pwn.college{UoSGc_jlqmdWiZXv8JqkhyWzxCU.QXwYTN0wCM2EDNzEzW}`

I set the variable `PWN` to the value `COLLEGE YEAH` by putting the multi word string in double quotes.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is your flag:
pwn.college{UoSGc_jlqmdWiZXv8JqkhyWzxCU.QXwYTN0wCM2EDNzEzW}
```

## What I Learned

I learned that to assign a value with spaces to a variable, you have to enclose it in **quotes** (`"`) to treat it as single string.

## References

The problem statement provided was the reference used.

```
Spaces have special significance in the shell, and there are places where you can't use them spuriously.
...
To set VAR to 1337 SAUCE, you need to quote it:

hacker@dojo:~$ VAR="1337 SAUCE"
Here, the shell reads 1337 SAUCE as a single token, and happily sets that value to VAR.
In this level, you'll need to set the variable PWN to COLLEGE YEAH.
```

# 4. Exporting Variables

This challenge prompted me to pass one variable to a program while keeping another one local.

## My Solve

**Flag:** `pwn.college{cssVXfoSUih--XKMd8XkSt7cRLn.QXyYTN0wCM2EDNzEzW}`

I used `export` on `PWN` and set its value to `COLLEGE` and created another variable `COLLEGE` and set its value to `PWN` and then ran the program. Thus I was prompted with the flag.

```
hacker@variables~exporting-variables:~$ export PWN
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{cssVXfoSUih--XKMd8XkSt7cRLn.QXyYTN0wCM2EDNzEzW}
```

## What I Learned

I learned that if you want a program you're running to see one of your shell's variables then you have to **`export`** it. If you don't then the variable just stays local to your current shell.

## References

The problem statement provided was the reference used.

```
By default, variables that you set in a shell session are local to that shell process.
...
When you export your variables, they are passed into the environment variables of child processes.
...
In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported...
```

# 5. Printing Exported Variables

This challenge prompted me to find the flag by listing all the exported environment variables.

## My Solve

**Flag:** `pwn.college{47JTW7_A1ZvY7TmrsT2gnbZ2Cpp.QX4UTN0wCM2EDNzEzW}`

I ran `env` to list all environment variables and was prompted with the flag with `FLAG` variable. 

```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=b765b7c5ec20f3c539263bda59180c8e32fe2c7d6fc5c6e5b40cc7f97ef0eb64
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{47JTW7_A1ZvY7TmrsT2gnbZ2Cpp.QX4UTN0wCM2EDNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
```

## What I Learned

I learned that `env` can be used to list all the environment variables on the system.

## References

The problem statement provided was the reference used.

```
There are multiple ways to access variables in bash. `echo` was just one of them, and we'll now learn at least one more in this challenge.

Try the `env` command: it'll print out every _exported_ variable set in your shell, and you can look through that output to find the `FLAG` variable!e!
```

# 6. Storing Command Output

This challenge prompted me to store the output of a command to a variable and read it.

## My Solve

**Flag:** `pwn.college{E3WSd28pkrZaKhzBavDrCl9dmb5.QX1cDN1wCM2EDNzEzW}`

I used command substitution to store the output of the `run` binary, then just used `echo` to print the variable and see the flag.

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{E3WSd28pkrZaKhzBavDrCl9dmb5.QX1cDN1wCM2EDNzEzW}
```

## What I Learned

I learnt that command substitution can be used to store values on shell variables.

## References

The problem statement provided was the reference used.

```
In the course of working with the shell, you will often want to store the output of some command into a variable.
Luckily, the shell makes this quite easy using something called Command Substitution!
Observe:

hacker@dojo:~$ FLAG=$(cat /flag)
hacker@dojo:~$ echo "$FLAG"
pwn.college{blahblahblah}

Now, you practice.
Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!
```

# 7. Reading Input

This challenge prompted me to use the `read` command to store user input into a variable.

## My Solve

**Flag:** `pwn.college{06csIGFvt_osPCsVRRcT3WMJuE3.QX4cTN0wCM2EDNzEzW}`

I used the `read` command with a prompt to capture my input. When prompted, I typed `COLLEGE`, which was then stored in the `PWN` variable and solved the challenge.

```
hacker@variables~reading-input:~$ read -p "Input: " PWN
Input: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{06csIGFvt_osPCsVRRcT3WMJuE3.QX4cTN0wCM2EDNzEzW}
```

## What I Learned

I learnt that the `read` command is used to get input from the user and save it to a shell variable.

## References

The problem statement provided was the reference used.

```
We'll start with reading input from the user (you).
That's done using the aptly named read builtin, which reads input into a variable!
Here is an example using the -p argument, which lets you
 specify a prompt...

hacker@dojo:~$ read -p "INPUT: " MY_VARIABLE
INPUT: Hello!
hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
You entered: Hello!

In this challenge, your job is to use read to set the PWN variable to the value COLLEGE.
```

# 8. Reading Files

This challenge prompted me to read the content of a file directly into a shell variable.
## My Solve

**Flag:** `pwn.college{gsplZcAaJguntLGFfhJWwn0DyKZ.QXwIDO0wCM2EDNzEzW}`

I used the `read` command and input redirection to read the contents of the `/challenge/read_me` file directly into the `PWN` variable.

```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gsplZcAaJguntLGFfhJWwn0DyKZ.QXwIDO0wCM2EDNzEzW}
```

## What I Learned

I learnt that you can read a file into a variable by redirecting the file as standard input to the `read` command.

## References

The problem statement provided was the reference used.

```
Often, when shell users want to read a file into an environment variable, they do something like:

hacker@dojo:~$ VAR=$(cat some_file)

This works, but it represents what grouchy hackers call a "Useless Use of Cat".
...
It turns out that you can just use the powers of the shell!
...
hacker@dojo:~$ read VAR < some_file
hacker@dojo:~$ echo $VAR
test

Now, use that to read /challenge/read_me into the PWN environment variable, and we'll give you the flag!
```
