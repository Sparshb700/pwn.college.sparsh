# 1. Learning from Documentation  
The challenge provided the documentation for the `/challenge/challenge` and prompted me to use it to read the flag.  
  
## My Solve  
**Flag:** `pwn.college{UuqboXWau8-IIN2_dI1aC90fQwC.QX0ITO0wCM2EDNzEzW}`  
  
Using the documentation of `/challenge/challenge`, I used the `--giveflag` argument to read the flag.  
```  
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag  
Correct argument! Here is your flag:  
pwn.college{UuqboXWau8-IIN2_dI1aC90fQwC.QX0ITO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the use of documentations, and how they can be used.  
  
## References  
The problem statement and the manual given was the reference used.  
```  
The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:  
  
    Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!  
  
Given that knowledge, go get the flag!  
```

# 2. Learning Complex Usage  
The challenge provided the documentation of binary `challenge` and using that to read the `flag` file.  
  
## My Solve  
**Flag:** `pwn.college{UKjriIIj7tTMf3lVib1smB_JCzS.QX1ITO0wCM2EDNzEzW}`  
  
I first located the `flag` which was in the `/` directory. then using the documentation, I gave the argument `--printfile /flag` to the `/challenge/challenge` binary to get the flag.  
```  
hacker@man~learning-complex-usage:~$ ls /  
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr  
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var  
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag  
Correct argument! Here is the /flag file:  
pwn.college{UKjriIIj7tTMf3lVib1smB_JCzS.QX1ITO0wCM2EDNzEzW}  
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile ~/not-the-flag  
Correct argument! Here is the /home/hacker/not-the-flag file:  
pwn.college{UKjriIIj7tTMf3lVib1smB_JCzS.QX1ITO0wCM2EDNzEzW}  
```  
  
## What I Learned  
Same as challenge `1.`, already used complex arguments before with `find`.  
  
## References  
The problem statement was the reference used.  
```  
Here is this level's documentation for /challenge/challenge:  
  
    Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!  
  
Given that documentation, go get the flag!  
```

# 3. Reading Manuals  
The challenge prompted to read the manual of `challenge`, and using that to read the flag.  
  
## My Solve  
**Flag:** `pwn.college{QPpgSIJ8WSw3dhCITj4WfCPZLK5.QX0EDO0wCM2EDNzEzW}`  
  
1. I first read the manual of `challenge` by using `man challenge` and  located the argument which returns the flag.
```
hacker@man~reading-manuals:~$ man challenge
```
```
Manual File  
       --pgwdhj NUM  
              print the flag if NUM is 834  
```  
2. Then I used this argument with `/challenge/challenge` to read out the flag.  
```  
hacker@man~reading-manuals:~$ /challenge/challenge --pgwdhj 834  
Correct usage! Your flag: pwn.college{QPpgSIJ8WSw3dhCITj4WfCPZLK5.QX0EDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the usage of `man` command and how it can be used to read the manuals. To quit the manual page, press `q` and scroll through `up` and `down` keys.  
  
## References  
The problem statement was the reference used  
```  
Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).  
  
The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!  
```

# 4. Searching Manuals  
The challenge prompted me to find the correct argument to print the flag from the binary `/challenge/challenge` from its manual.  
  
## My Solve  
**Flag:** `pwn.college{k9tTFCOcU465sOV-IEl4413pug9.QX1EDO0wCM2EDNzEzW}`  
  
Opening the manual of `challenge`, I searched for the term `flag` using `/flag` in the `man` window, After looking at the instances of `flag`, I found the correct argument to use, and printed the flag.  

  ```
  --itigr  
              This argument will give you the flag!  
  ```

```  
hacker@man~searching-manuals:~$ man challenge  
hacker@man~searching-manuals:~$ /challenge/challenge --itigr  
Initializing...  
Correct usage! Your flag: pwn.college{k9tTFCOcU465sOV-IEl4413pug9.QX1EDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt how you can use `/` to search in manuals and using `n` and `N` to look at different instances of the searched word.  
  
## References  
The problem statement was the reference used  
```  
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!  
  
Find the option that will give you the flag by reading the challenge man page.  
```

# 5. Searching Manuals  
The challenge prompted to read the hidden manual page of the `challenge` executable and using that to print the flag.  
  
## My Solve  
**Flag:** `pwn.college{06SlAZk0i-R8brgS_haJ40jKt6E.QX2EDO0wCM2EDNzEzW}`  
  
1. I first opened the manpage of `man using `man man`, and read through the different options in which I found the -K option   
```  
-K, --global-apropos  
              Search  for  text  in  all manual pages.  This is a brute-force search, and is likely to take  
              some time; if you can, you should specify a section to reduce the number of pages  that  need  
              to  be searched.  Search terms may be simple strings (the default), or regular expressions if  
              the --regex option is used.  
  
              Note that this searches the sources of the manual pages, not the rendered text,  and  so  may  
              include  false  positives due to things like comments in source files, or false negatives due  
              to things like hyphens being written as "\-" in source files.  Searching  the  rendered  text  
              would be much slower.  
```  
2. Through this I could search through all the man pages for a specific keyword, so I searched for `/challenge/challenge`, that prompted me this man page  
```  
DESCRIPTION  
       Output the flag when called with the right arguments.  
  
       --fortune  
              read a fortune  
  
       --version  
              output version information and exit  
  
       --lkibrg NUM  
              print the flag if NUM is 060  
```  
3. Founding the argument to print that flag, I finally got the flag using the `challenge` executable.  
```  
hacker@man~searching-for-manuals:~$ man man  
hacker@man~searching-for-manuals:~$ man -K /challenge/challenge  
hacker@man~searching-for-manuals:~$ /challenge/challenge --lkibrg 060  
Correct usage! Your flag: pwn.college{06SlAZk0i-R8brgS_haJ40jKt6E.QX2EDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt that I can search through all the man pages using `-K` which can be useful when manpages are randomly named.  
There is a man page for `man` command as well.  
  
## References  
The problem statement was the reference used.  
```  
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!  
  
HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge  
  
HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!  
```

# 6. Helpful Programs  
The challenge prompted to read the documentation of `challenge` binary using `--help` and find the argument which provides the flag.  
  
## My Solve  
**Flag:** `pwn.college{wafOMwajO6zoxzYa_0M-3zVizYd.QX3IDO0wCM2EDNzEzW}`  
  
1. Using `--help` with the binary I got the following output.  
```  
hacker@man~helpful-programs:~$ /challenge/challenge --help  
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]  
  
optional arguments:  
  -h, --help            show this help message and exit  
  --fortune             read your fortune  
  -v, --version         get the version number  
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG  
                        get the flag, if given the correct value  
  -p, --print-value     print the value that will cause the -g option to give you the flag  
```  
2. I first printed the value using `-p` which was 603, then I used `-g 603` to print the flag.  
```  
hacker@man~helpful-programs:~$ /challenge/challenge -p  
The secret value is: 603  
hacker@man~helpful-programs:~$ /challenge/challenge -g 603  
Correct usage! Your flag: pwn.college{wafOMwajO6zoxzYa_0M-3zVizYd.QX3IDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt that many commands and programs don't have man pages and documentation for those can seen through `--help` arguments.  
Many other arguments can be used such as `-h`, `-?` etc.  
  
## References  
The problem statement was the reference used.  
```  
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).  
  
In this level, you will practice reading a program's documentation with --help. Try it out!  
```

# 7. Help for Builtins  
The challenge prompted me to use the `help` command to find the documentation for builtins, through that finding the flag.  
  
## My Solve  
**Flag:** `pwn.college{AJ5q9AkEWIxfW8M7IY42uyUjpu3.QX0ETO0wCM2EDNzEzW}`  
  
I used `help` to find the usage of `challenge` command which was a builtin for this challenge. Using that I found the correct argument and value to put with that argument.  
```  
hacker@man~help-for-builtins:~$ help challenge  
challenge: challenge [--fortune] [--version] [--secret SECRET]  
    This builtin command will read you the flag, given the right arguments!  
  
    Options:  
      --fortune         display a fortune  
      --version         display the version  
      --secret VALUE    prints the flag, if VALUE is correct  
  
    You must be sure to provide the right value to --secret. That value  
    is "AJ5q9AkE".  
hacker@man~help-for-builtins:~$ challenge --secret AJ5q9AkE  
Correct! Here is your flag!  
pwn.college{AJ5q9AkEWIxfW8M7IY42uyUjpu3.QX0ETO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt what are builtins. Builtins are commands which are built in to the shell and are handled internally by the shell.   
The usage of `help` with builtins.  
  
## References  
The problem statement provided was used as the reference.  
```  
Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!  
```
