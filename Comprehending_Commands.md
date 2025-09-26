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

# 5. Comparing Files

The challenge prompted me to use the `diff` command to distinguish between two files, to find the real flag mixed with the decoys.

## My Solve

**Flag:** `pwn.college{sjoNcZjFLEgCJ1-1SIH6AGa9Xm6.01MwMDOxwCM2EDNzEzW}`

First I changed the directory to `challenge` directory and then used the `diff` command to distinguish between the files `decoys_only.txt` and `decoys_and_real.txt`.

```

hacker@commands~comparing-files:~$ cd /challenge

hacker@commands~comparing-files:/challenge$ diff decoys_only.txt decoys_and_real.txt

26a27

> pwn.college{sjoNcZjFLEgCJ1-1SIH6AGa9Xm6.01MwMDOxwCM2EDNzEzW}

```

## What I Learned

I learnt the usage of `diff` command, and its output.
If it provides `1a2`, that means after line 1 of file 1, add line 2 of file 2.
## References

The problem statement provided was the reference used.

```
Now for your challenge! There are two files in /challenge:
    /challenge/decoys_only.txt contains 100 fake flags
    /challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!
```

# 6.  Listing Files

The challenge prompted me to located the `run` binary using the `ls` command in the `challenge` directory.
## My Solve

**Flag:** `pwn.college{A0sT67nmXpECA2az6Xnqm2s64Tl.QX4IDO0wCM2EDNzEzW}`

First, I changed my directory to `challenge` using `cd` command, then I used `ls` command to locate the new binary file and executed it.

```

hacker@commands~listing-files:~$ cd /challenge

hacker@commands~listing-files:/challenge$ ls

29611-renamed-run-2073  DESCRIPTION.md

hacker@commands~listing-files:/challenge$ ./29611-renamed-run-2073

Yahaha, you found me! Here is your flag:

pwn.college{A0sT67nmXpECA2az6Xnqm2s64Tl.QX4IDO0wCM2EDNzEzW}

```

## What I Learned

I learnt the usage of `ls` command and how it used to list files in a specific directory.

## References

The problem statement provided was the reference used

`In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.`

# 7. touching files

The challenge asked me create two files at specified locations and then execute the `run` binary.
## My Solve

**Flag:** `pwn.college{kixs3012xPNTHE31lgOOItrw1rl.QXwMDO0wCM2EDNzEzW}`

I create the file `pwn` and `college` in the `tmp` directory using the `touch` command. Then I executed the `ran` binary.

```

hacker@commands~touching-files:~$ touch /tmp/pwn

hacker@commands~touching-files:~$ touch /tmp/college

hacker@commands~touching-files:~$ /challenge/run

Success! Here is your flag:

pwn.college{kixs3012xPNTHE31lgOOItrw1rl.QXwMDO0wCM2EDNzEzW}

```

## What I Learned

I learnt the usage of `touch` which is used for the creation of files.

## References

The problem statement provided was the reference used.

`It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!`Q

# 8. removing files  
The challenge prompted me to remove a file from the home directory and then execute the `check` to read the flag.  
  
## My Solve  
**Flag:** `pwn.college{gdqsnA7atAt2HVT8edg1hiu1mG_.QX2kDM1wCM2EDNzEzW}`  
  
I used the `rm` command to delete the `delete_me` file in the home directory, and then executed the binary `/challenge/check` to read the flag.  
```  
hacker@commands~removing-files:~$ rm -rf delete_me  
hacker@commands~removing-files:~$ /challenge/check  
Excellent removal. Here is your reward:  
pwn.college{gdqsnA7atAt2HVT8edg1hiu1mG_.QX2kDM1wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the of the remove command i.e `rm`, which is used to remove a specified file on the system.  
  
## References  
The problem statement was the reference used.  
`Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!`

# 9. moving files  
The challenged asked to move a file to a specific directory and then execute the `check` binary to read the flag.  
  
## My Solve  
**Flag:** `pwn.college{Av91hpPXjwQVEKz2tmx28HRaIQW.0VOxEzNxwCM2EDNzEzW}`  

By using `mv` command, I moved the `flag` file to `/tmp/hack-the-planet` directory and then executed the `/challenge/check` binary to read the flag.  
```  
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet  
Correct! Performing 'mv /flag /tmp/hack-the-planet'.  
hacker@commands~moving-files:~$ /challenge/check  
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:  
pwn.college{Av91hpPXjwQVEKz2tmx28HRaIQW.0VOxEzNxwCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the usage of `mv` command.  
Syntax of `mv` command is `mv file_to_move destination`.  
  
## References  
The problem statement was the reference used.  
`This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.`

# 10. hidden files  
The challenge prompted to list hidden files in `/` directory, and then read the contents of the file.  
  
## My Solve  
**Flag:** `pwn.college{gQ0qHNTCMcPnvTFEMYhQBypP7x6.QXwUDO0wCM2EDNzEzW}`  
  
I first listed all the hidden files in the `/` using the `-a` argument of `ls`.  
Then I used `cat` to read the contents of that hidden file.  
```  
hacker@commands~hidden-files:~$ ls / -a  
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var  
..  .flag-75312680416529  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr  
hacker@commands~hidden-files:~$ cat /.flag-75312680416529  
pwn.college{gQ0qHNTCMcPnvTFEMYhQBypP7x6.QXwUDO0wCM2EDNzEzW  
```  
  
## What I Learned  
I learnt how hidden files look in Linux, and how to list them.  
  
## References  
The problem statement was the reference used.  
`Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.`

# 11. An Epic Filesystem Quest

The challenge prompted to me to find a hidden flag, by reading through clues spread around the filesystem.

## My Solve
**Flag:** `pwn.college{k7VmHuL4joiO6XZBWnTppc34lzE.QX5IDO0wCM2EDNzEzW}`

1. The challenge's first clue was held up in `/` directory. So I used `ls`, and I found the file `BLUEPRINT` and used `cat` to read the file.
```
hacker@commands~an-epic-filesystem-quest:~$ ls /
BLUEPRINT  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin        challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:~$ cat /BLUEPRINT
Great sleuthing!
The next clue is in: /usr/share/doc/libbrlapi0.7

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
2. I changed my `cwd` to `/usr/share/doc/libbrlapi0.7` and using `ls` found the file `NUGGET`
   and read it using `cat`.
```
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/share/doc/libbrlapi0.7
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libbrlapi0.7$ cat NUGGET
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/sage/libs/flint/__pycache__
```
3. Similarly I changed my `cwd` to specified directory and located the file `INSIGHT`
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libbrlapi0.7$ cd /usr/lib/python3/dist-packages/sage/libs/flint/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/libs/flint/__pycache__$ ls
INSIGHT  __init__.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/libs/flint/__pycache__$ cat INSIGHT
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/py/_path

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
4. In the specified location, I found the file `REVELATION`
```
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/libs/flint/__pycache__$ cd /usr/lib/python3/dist-packages/py/_path
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/py/_path$ ls
REVELATION  __init__.py  __pycache__  cacheutil.py  common.py  local.py  svnurl.py  svnwc.py
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/py/_path$ cat REVELATION
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/arch/h8300/include/uapi

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
5. Following the steps above, I found the file `CUE`
```
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/py/_path$ cd /opt/linux/linux-5.4/arch/h8300/include/uapi
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ ls
CUE  asm
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ cd CUE
bash: cd: CUE: Not a directory
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ cat CUE
Congratulations, you found the clue!
The next clue is in: /usr/lib/python3/dist-packages/jedi/inference

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
6. This time it was specified the file would not open if i change my `cwd` to the specified location, So I used `ls` and `cat` from the last specified directory only
```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ ls /usr/lib/python3/dist-packages/jedi/inference
MEMO-TRAPPED  base_value.py  dynamic_params.py  helpers.py     parser_cache.py  sys_path.py
__init__.py   cache.py       filters.py         imports.py     recursion.py     usages.py
__pycache__   compiled       finder.py          lazy_value.py  signature.py     utils.py
analysis.py   context.py     flow_analysis.py   names.py       star_args.py     value
arguments.py  docstrings.py  gradual            param.py       syntax_tree.py
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ cat /usr/lib/python3/dist-packages/jedi/inference/MEMO-TRAPPED
Tubular find!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
7.  Repeated the above, and found the file `NOTE-TRAPPED`
```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ ls /opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index
NOTE-TRAPPED  __init__.py  __pycache__  collector.py  package_finder.py  sources.py
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/NOTE-TRAPPED
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/sage/ext

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
8. Repeating the above, I found the file `TRACE-TRAPPED`
```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ ls /usr/lib/python3/dist-packages/sage/ext
TRACE-TRAPPED                                 interpreters
__init__.py                                   memory.cpython-38-x86_64-linux-gnu.so
__pycache__                                   memory.pyx
ccobject.h                                    memory_allocator.cpython-38-x86_64-linux-gnu.so
cplusplus.pxd                                 memory_allocator.pxd
fast_callable.cpython-38-x86_64-linux-gnu.so  memory_allocator.pyx
fast_callable.pxd                             mod_int.h
fast_callable.pyx                             mod_int.pxd
fast_eval.cpython-38-x86_64-linux-gnu.so      solaris_fixes.h
fast_eval.pxd                                 stdsage.pxd
fast_eval.pyx
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ cat /usr/lib/python3/dist-packages/sage/ext/TRACE-TRAPPED
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/staging/mt7621-pci-phy

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
```
9. The next file was hidden, so I used `ls -a` to locate the file, found the file `.LEAD` and was prompted with the flag.
```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ ls -a /opt/linux/linux-5.4/drivers/staging/mt7621-pci-phy
.  ..  .LEAD  Kconfig  Makefile  TODO  mediatek,mt7621-pci-phy.txt  pci-mt7621-phy.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$ cat /opt/linux/linux-5.4/drivers/staging/mt7621-pci-phy/.LEAD
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{k7VmHuL4joiO6XZBWnTppc34lzE.QX5IDO0wCM2EDNzEzW}
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi$
```

## What I learned
I used all the command already learnt.

## References
The problem statement was reference used.
```
In this challenge, I have _hidden the flag_! Here, you will use `ls` and `cat` to follow my breadcrumbs and find it! Here's how it'll work:

0. Your first clue is in `/`. Head on over there.
1. Look around with `ls`. There'll be a file named HINT or CLUE or something along those lines!
2. `cat` that file to read the clue!
3. Depending on what the clue says, head on over to the next directory (or don't!).
4. Follow the clues to the flag!
```

# 12. making directories  
The challenge prompted to create a directory and in that directory a file. After that executing the binary would read me the flag.  
  
## My Solve  
**Flag:** `pwn.college{Ml_oXvmVPknynB6i3WPO1CybMRo.QXxMDO0wCM2EDNzEzW}`  
  
I first created the directory `/tmp/pwn` using `mkdir` command and then used `touch` to create a file `college` int that directory. Then executing the `/challenge/binary` prompted me the flag.  
```  
hacker@commands~making-directories:~$ mkdir /tmp/pwn  
hacker@commands~making-directories:~$ touch /tmp/pwn/college  
hacker@commands~making-directories:~$ /challenge/run  
Success! Here is your flag:  
pwn.college{Ml_oXvmVPknynB6i3WPO1CybMRo.QXxMDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the usage of `mkdir` command, creating my first directory using the command terminal.  
  
## References  
The problem statement was the reference used  
`Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!`

# 13. finding files  
The challenge prompted to use the `find` command to find the `flag` file in the entire filesystem.  
  
## My Solve  
**Flag:** `pwn.college{gXhZ2SZnULJWuoSJrz6R9ED8rwL.QXyMDO0wCM2EDNzEzW}`  
  
1. I first used `find / -name 'flag` command and located a lot of files with the name `flag`  
```hacker@commands~finding-files:~$ find / -name 'flag'  
find: �/root�: Permission denied  
find: �/etc/ssl/private�: Permission denied  
find: �/tmp/tmp.TpSOPGOVKK�: Permission denied  
/usr/local/lib/python3.8/dist-packages/pwnlib/flag  
/usr/share/perl/5.30.0/TAP/Formatter/flag  
find: �/var/cache/apt/archives/partial�: Permission denied  
find: �/var/cache/ldconfig�: Permission denied  
find: �/var/cache/private�: Permission denied  
find: �/var/log/private�: Permission denied  
find: �/var/log/apache2�: Permission denied  
find: �/var/log/mysql�: Permission denied  
find: �/var/lib/apt/lists/partial�: Permission denied  
find: �/var/lib/mysql-files�: Permission denied  
find: �/var/lib/mysql�: Permission denied  
find: �/run/mysqld�: Permission denied  
find: �/run/sudo�: Permission denied  
find: �/proc/tty/driver�: Permission denied  
find: �/proc/1/task/1/fd�: Permission denied  
find: �/proc/1/task/1/fdinfo�: Permission denied  
find: �/proc/1/task/1/ns�: Permission denied  
find: �/proc/1/fd�: Permission denied  
find: �/proc/1/map_files�: Permission denied  
find: �/proc/1/fdinfo�: Permission denied  
find: �/proc/1/ns�: Permission denied  
find: �/proc/7/task/7/fd�: Permission denied  
find: �/proc/7/task/7/fdinfo�: Permission denied  
find: �/proc/7/task/7/ns�: Permission denied  
find: �/proc/7/fd�: Permission denied  
find: �/proc/7/map_files�: Permission denied  
find: �/proc/7/fdinfo�: Permission denied  
find: �/proc/7/ns�: Permission denied  
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag  
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag  
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag  
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag  
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag  
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag  
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag  
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag  
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag  
```  
2. Then ignoring the files where it showed `Permission denied`, I tried using cat on all the files one by one. The first location turned out to be a `directory`. But the second file turned out to be the actual `flag` file.  
```  
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag  
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory  
hacker@commands~finding-files:~$ cat /usr/share/perl/5.30.0/TAP/Formatter/flag  
pwn.college{gXhZ2SZnULJWuoSJrz6R9ED8rwL.QXyMDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the usage of `find` command and its syntax.  
  
## References  
The problem statement was the reference used.  
`Now it's your turn. I've hidden the flag in a random directory on the filesystem. It's still called flag. Go find it! Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it. Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there! Finally, find can take a while; be patient!`

# 14. linking files  
The challenge prompted to link two files, to read out the flag by executing the `catflag` binary.  
## My Solve  
**Flag:** `pwn.college{ksZbTZ1XXdLcq45z_h56oiN-G5G.QX5ETN1wCM2EDNzEzW}`  
  
I created a link from the file `/flag` to `~/not-the-flag` as the `/challenge/catflag` reads the file `not-the-flag`, through this I tricked the binary to read me the actual flag at `/flag`.  
```  
hacker@commands~linking-files:~$ ln -s /flag ~/not-the-flag  
hacker@commands~linking-files:~$ /challenge/catflag  
About to read out the /home/hacker/not-the-flag file!  
pwn.college{ksZbTZ1XXdLcq45z_h56oiN-G5G.QX5ETN1wCM2EDNzEzW}  
hacker@commands~linking-files:~$  
```  
  
## What I Learned  
I learnt the meaning and usage of links, how a hard and a symbolic link is defined and what is the difference between the both.  
The syntax of creating a symbolic link is `ln -s original_file_fath link_path` .  
  
## References  
The problem statement was the reference used.  
```  
A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:  
  
hacker@dojo:~$ file /tmp/myfile  
/tmp/myfile: ASCII text  
hacker@dojo:~$ file ~/ourfile  
/home/hacker/ourfile: symbolic link to /tmp/myfile  
hacker@dojo:~$  
  
Okay, now you try it! In this level the flag is, as always, in /flag, but /challenge/catflag will instead read out /home/hacker/not-the-flag. Use the symlink, and fool it into giving you the flag!  
```
