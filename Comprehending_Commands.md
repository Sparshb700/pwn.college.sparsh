# 1. cat: not the pet, but the command!
The challenge introduced me to the `cat` command, which is used to read the content of a file

## My Solve

**Flag:** `pwn.college{8Oqa92lbIw_T-WPmH4FGV7hVguW.QXxcTN0wCM2EDNzEzW}`

I ran the `cat` command on the `flag` file while being in the home directory
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{8Oqa92lbIw_T-WPmH4FGV7hVguW.QXxcTN0wCM2EDNzEzW}
```

## What I learned
I learned how to use the `cat` command, and thus being able to read any file located inside the storage. Also `cat` will concatenate multiple files if provided.

## References
The problem statement was the reference used
```
One of the most critical Linux commands is `cat`. `cat` is most often used for reading out files, like so:

console
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:


`cat` will con**cat**enate (hence the name) multiple files if provided multiple arguments. For example:

console
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!

Finally, if you give no arguments at all, `cat` will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the `flag` file in your home directory (where your shell starts). Go read it with `cat`!
```

# 2. catting absolute paths
The challenge prompted to `cat` to an absolute path where the flag was located

## My Solve
**Flag:** `pwn.college{AhviXTf5eNvZ-RXyvPsf7NAIem-.QX5ETO0wCM2EDNzEzW}`

I ran the `cat` command from the `~` directory by providing the absolute path `/flag` to it
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{AhviXTf5eNvZ-RXyvPsf7NAIem-.QX5ETO0wCM2EDNzEzW}
```
## What I learned
`cat` can be used with absolute paths.

## References
The problem statement was the reference used
```
In the last level, you did `cat flag` to read the flag out of your home directory! You can, of course, specify `cat`'s arguments as absolute paths:

console
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:


In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with `cat` at its absolute path: `/flag`.
```

# 3. More catting practice
The challenge required me to `cat` the `flag` using an absolute path.

## My Solve
**Flag:** `pwn.college{UZGAlQZmuVfQTs5K5ePG2x62qre.QXwITO0wCM2EDNzEzW}`

1. When I logged into the terminal, I was shown this message:
```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /bin/flag. Go cat it out **without** cding into that directory!
```
2. So I used `cat /bin/flag` to get the required flag
```
hacker@commands~more-catting-practice:~$ cat /bin/flag
pwn.college{UZGAlQZmuVfQTs5K5ePG2x62qre.QXwITO0wCM2EDNzEzW}
```

## What I learned
Same learnings as Challenges `1` and `2` .

## References
The problem statement was the reference used
```
You can specify all sorts of paths as arguments to commands, and we'll practice some more with `cat`. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with `cd`, so no `cat flag` for you. You must retrieve the flag by absolute path, wherever it is.
```

# 4. grepping for a needle in a haystack

The challenge introduced me to the `grep` command. Asked me find the flag in a large file using `grep`.
## My Solve
**Flag:** `pwn.college{oofZfce8J7YMd2d2r_NlewhLUGT.QX3EDO0wCM2EDNzEzW}`

I used the grep command to search for the string `pwn` in the file provided at `/challenge/data`, found the flag amidst the strings provided

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep "pwn" /challenge/data.txt
pwning
pwn.college{oofZfce8J7YMd2d2r_NlewhLUGT.QX3EDO0wCM2EDNzEzW}
pwns
pwn
pwned
```

## What I learned
I learnt how to use the `grep` command, how it can be used to find specific strings in any file

## References
The problem statement was the reference used
```
Sometimes, the files that you might `cat` out are too big. Luckily, we have the `grep` command to search for the contents we need! We'll learn it in this challenge.

There are many ways to `grep`, and we'll learn one way here:

console
hacker@dojo:~$ grep SEARCH_STRING /path/to/file

Invoked like this, `grep` will search the file for lines of text containing `SEARCH_STRING` and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the `/challenge/data.txt` file. `grep` it for the flag!

HINT: The flag always starts with the text `pwn.college`.
```

# 5. Comparing files
