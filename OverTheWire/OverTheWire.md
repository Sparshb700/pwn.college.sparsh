
# Level 0
In this level of the wargame, we need to use the `ssh` command to connect to the host. We are given the hostname, the username, and the password.

## My solve

**password:** `bandit0`

I solved this challenge as under:

1. I first read through the challenge statement given on the website. On reading through the challenge, I understood that we need to connect to the challenge using the `ssh` command and connect to a specific port. I also learned that every time we switch from one level to another, we will need to reconnect by utilizing a new username each time.
    
2. I did not know the argument we needed to add a port number to the `ssh` command, so I first used the `man` command to understand how to add the port number.
    
    ```
    sparsh@LAPTOP-F80QI4V2:~$ man ssh
    
    SSH(1)                                       General Commands Manual                                               SSH(1)
    NAME
           ssh — OpenSSH remote login client
    SYNOPSIS
           ssh ... [-p port] ... destination [command [argument ...]]
    ...
    ```
    
3. In the SYNOPSIS of the `ssh` command, I saw that we can use the `-p` argument to add the port number. Using this newfound knowledge, I crafted the command as below to log in. The password for `bandit0` was `bandit0`.
    
    ```
    sparsh@LAPTOP-F80QI4V2:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
    ...
    Welcome to OverTheWire!
    ...
    bandit0@bandit:~$
    ```
    

## What I learned

From this challenge, I learned how we can add a custom port to the `ssh` command using the `-p` argument.

## References

- `https://overthewire.org/wargames/bandit/bandit0.html`
    
- Guidance from mentor
    

---

# Level 0 → Level 1

In this level, we need to find the password for the next level, which is stored in a `readme` file in the home directory.

## My solve

**password:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

To solve the level, I followed these steps:

1. I first listed the contents of the `bandit0` home directory.
2. Finding the `readme` file, I used the `cat` command to read its content and get the password.

```
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
The password for the next level is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

## What I learned

From this challenge, I got more comfortable navigating the file system and reading files.

## References

- `https://overthewire.org/wargames/bandit/bandit1.html`
    
- Guidance from mentor
    

---

# Level 1 → Level 2

In this level, we need to find the password hidden in a file named `-` in the home directory.

## My solve

**password:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

To find this password, I followed these steps:

1. I knew the file was in the `/home/bandit1` directory and named `-`.
    
2. Because the filename is a special character, I used the full path `./-` to specify to the `cat` command that it's a file in the current directory.
    
    ```
    bandit1@bandit:~$ ls
    -
    bandit1@bandit:~$ cat ./-
    263JGJPfgU6LtdEvgfWU1XP5yac29mFx
    ```
    

## What I learned

From this challenge, I learned that to access files that start with a special character like `-`, you should prefix the path with `./` to prevent the shell from interpreting it as an option.

## References

- `https://overthewire.org/wargames/bandit/bandit2.html`
    

---

# Level 2 → Level 3

In this level, we need to find a file which has spaces in its file name.

## My solve

**password:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

To solve this level, I followed these steps:

1. I first listed the files in the home directory and found one named `spaces in this filename`.
    
2. I knew that when there are spaces in a file name, we should enclose the file name in double quotes (`""`) or escape the spaces with a backslash (`\` ).
    
3. Using quotes, I was able to `cat` the file and find the password.
    
    ```
    bandit2@bandit:~$ ls
    spaces in this filename
    bandit2@bandit:~$ cat "spaces in this filename"
    MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
    ```
    

## What I learned

From this level, I learned how to handle filenames with spaces by either enclosing them in quotes or escaping each space.

## References

- `https://overthewire.org/wargames/bandit/bandit3.html`
    

---

# Level 3 → Level 4

In this level, we need to find a hidden file in the `inhere` directory.

## My solve

**password:** `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

To solve this challenge, I followed these steps:

1. I changed my directory to `inhere`.
    
2. Hidden files start with a `.` and are not shown by a normal `ls`. I used the `ls -a` command to list all files, including hidden ones.
    
3. I found the hidden file `.hidden` and used `cat` to read its content.
    
    ```
    bandit3@bandit:~$ ls
    inhere
    bandit3@bandit:~$ cd inhere
    bandit3@bandit:~/inhere$ ls -a
    .  ..  .hidden
    bandit3@bandit:~/inhere$ cat .hidden
    2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
    ```
    

## What I learned

This level was a practice for the `ls -a` command to find hidden files, which are common in Linux for configuration.

## References

- `https://overthewire.org/wargames/bandit/bandit4.html`
    

---

# Level 4 → Level 5

In this level, we need to find the only human-readable file in the `inhere` directory.

## My solve

**password:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

To solve this challenge, I followed these steps:

1. I moved into the `inhere` directory and listed the files.
    
2. I used the `file` command to inspect each file's type. The `file` command is great for determining what a file contains.
    
3. I found that only `-file07` was identified as "ASCII text", meaning it was human-readable. All others were "data". I then used `cat` to read it.
    
    ```
    bandit4@bandit:~$ cd inhere/
    bandit4@bandit:~/inhere$ file ./*
    ./-file00: data
    ./-file01: data
    ./-file02: data
    ./-file03: data
    ./-file04: data
    ./-file05: data
    ./-file06: data
    ./-file07: ASCII text
    ./-file08: data
    ./-file09: data
    bandit4@bandit:~/inhere$ cat ./-file07
    4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
    ```
    

## What I learned

This challenge served as practice for the `file` command, which is very useful for identifying file types without relying on extensions.

## References

- `https://overthewire.org/wargames/bandit/bandit5.html`

---
# Level 5 → Level 6

In this level, we need to find a file somewhere in the `inhere` directory which is human-readable, 1033 bytes in size, and not executable.

## My solve

**password:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

To solve this challenge, I followed these steps:

1. I suspected the `find` command could search by file size. I confirmed this by reading its manual page with `man find` and found the `-size` argument, using the `c` suffix for bytes.
    
2. I used this knowledge to craft a command to find the specific file: `find . -size 1033c`. The `.` tells `find` to start searching from the current directory.
    
3. The command returned a single file path. I then used `cat` to read this file and get the password.
    

Bash

```
bandit5@bandit:~$ find . -size 1033c
./inhere/maybehere07/.file2
bandit5@bandit:~$ cat ./inhere/maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

## What I learned

From this level, I learned how to use the `-size` argument with the `find` command to locate files based on their exact size in bytes.

## References

- Manpage of `find` command.
    

---

# Level 6 → Level 7

In this challenge, we need to find a file hidden somewhere on the server which has the following properties: owned by user `bandit7`, owned by group `bandit6`, and is 33 bytes in size.

## My solve

**password:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

To solve this challenge, I followed these steps:

1. I again read the `man` page for the `find` command to find arguments for searching by owner and group. I found `-user` and `-group`.
    
2. I crafted a command combining all three conditions: `find / -user bandit7 -group bandit6 -size 33c`. I started the search from the root directory (`/`).
    
3. The command produced a lot of "Permission denied" errors, but it found one accessible file: `/var/lib/dpkg/info/bandit7.password`. I used `cat` to read it and find the password.
    

Bash

```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c
find: ‘/sys/kernel/tracing/osnoise’: Permission denied
...
/var/lib/dpkg/info/bandit7.password
...
find: ‘/home/drifter8/chroot’: Permission denied
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## What I learned

From this challenge, I learned how to combine the `-user`, `-group`, and `-size` arguments with the `find` command to search for files with very specific metadata.

## References

- Manpage of `find` command.
    

---

# Level 7 → Level 8

In this challenge, we need to find the password for the next level, which is located in the file `data.txt` next to the word "millionth".

## My solve

**password:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

To solve this challenge, I followed these steps:

1. I read the contents of the `data.txt` file.
    
2. Since the file was large, I piped the output of `cat` to the `grep` command, searching for the unique word "millionth" to isolate the line containing the password.
    

Bash

```
bandit7@bandit:~$ cat data.txt | grep millionth
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## What I learned

This challenge served as good practice for basic piping and using the `grep` command to filter text.

## References

- `https://overthewire.org/wargames/bandit/bandit8.html`
    

---

# Level 8 → Level 9

In this challenge, we need to find the single unique line within the file `data.txt`, which contains many repeated lines.

## My solve

**password:** `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

To solve this challenge, I followed these steps:

1. I first tried using `uniq -u data.txt` to find the unique line, but it didn't work because `uniq` only detects adjacent duplicate lines.
    
2. I realized I needed to sort the file first so that all identical lines would be grouped together.
    
3. I created a pipeline that first sorted the file with `sort`, and then piped the sorted output to `uniq -u`. This successfully filtered out all duplicate lines and revealed the single unique one.
    

Bash

```
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

## What I learned

From this challenge, I learned that `uniq` requires sorted input to work on a whole file. The common pattern to find truly unique lines is `sort <file> | uniq -u`.

## References

- `https://stackoverflow.com/questions/13778273/find-unique-lines`
    

---

# Level 9 → Level 10

In this challenge, we need to find a human-readable password hidden within a binary data file.

## My solve

**password:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

To solve this challenge, I followed these steps:

1. I understood that the file contained mostly non-printable characters. The `strings` command is designed to extract printable character sequences from such files.
    
2. I ran `strings data.txt` and looked through the output. I found several lines that started with `==========` and one of them contained the password.
    

Bash

```
bandit9@bandit:~$ strings data.txt
...
========== the
...
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
...
```

## What I learned

From this challenge, I was introduced to the `strings` command and learned how to use it to find readable text inside binary files.

## References

- `https://overthewire.org/wargames/bandit/bandit10.html`
    

---

# Level 10 → Level 11

In this challenge, we need to decode a password that is stored in Base64 format.

## My solve

**password:** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

To solve this challenge, I followed these steps:

1. The challenge hint pointed towards Base64 encoding. I knew the `base64` command could be used for this.
    
2. I read the `man` page for `base64` and found the `-d` option for decoding.
    
3. I used the command `base64 -d data.txt` to decode the file and reveal the password.
    

Bash

```
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## What I learned

From this challenge, I learned about the `base64` command and how to use its `-d` password to decode Base64-encoded data.

## References

- `https://overthewire.org/wargames/bandit/bandit11.html`
    

---

# Level 11 → Level 12

In this challenge, we need to decode data which has been rotated by 13 positions (ROT13 cipher).

## My solve

**password:** `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

To solve this challenge, I followed these steps:

1. I first used `cat` to view the encoded string in the `data.txt` file.
    
2. I recognized this as a ROT13 cipher. While this can be done on the command line, I copied the string and used an online tool (CyberChef) to quickly decode it. An alternative on the command line is to use `tr`.
    
    Bash
    
    ```
    bandit11@bandit:~$ cat data.txt
    Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
    
    # Using tr command for command-line solution
    bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
    The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
    ```
    

## What I learned

From this challenge, I learned about the ROT13 cipher and how it can be reversed using tools like CyberChef or the `tr` command to shift characters.

## References

- `https://overthewire.org/wargames/bandit/bandit12.html`
