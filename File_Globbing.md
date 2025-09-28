# 1. Matching with `*`  
The challenge prompted me to change my directory by using the `*` glob, and executing the `run` binary.  
  
## My Solve  
**Flag:** `pwn.college{ojzM0oviPu3iHw_x2lM77aT6Mo-.QXxIDO0wCM2EDNzEzW}`  
  
The challenge made it compulsory that the argument used with `cd` must be less than 4 characters, so the argument I used was `/ch*` which changed my directory to `/challenge`. Then I ran the binary to print the flag.  
```  
This challenge resets your working directory to /home/hacker unless you change  
directory properly...  
This challenge resets your working directory to /home/hacker unless you change  
directory properly...  
hacker@globbing~matching-with-:~$ cd /ch*  
hacker@globbing~matching-with-:/challenge$ ./run  
You ran me with the working directory of /challenge! Here is your flag:  
pwn.college{ojzM0oviPu3iHw_x2lM77aT6Mo-.QXxIDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learned what are globs, how the `*` glob can be used.  
`*` can be used as a multiple character wild entry.
  
## References  
The problem statement was the reference used.
```
Now, practice this yourself! Starting from your home directory, change your directory to `/challenge`, but use globbing to keep the argument you pass to `cd` to at most four characters! Once you're there, run `/challenge/run` for the flag!
```

# 2. Matching with `?`  
The challenge prompted me to use the `?` glob instead of `*` to change my directory and running the binary.  
  
## My Solve  
**Flag:** `pwn.college{o6MWWjf3txhP-Fw-eh8H9brKk5U.QXyIDO0wCM2EDNzEzW}`  
  
In the challenge statement, it was provided that `c` and `l` have to replaced by `?` in the argument of `cd`, hence I used `/?ha??enge` with `cd` and ran the `run` binary.  
```  
This challenge resets your working directory to /home/hacker unless you change  
directory properly...  
This challenge resets your working directory to /home/hacker unless you change  
directory properly...  
hacker@globbing~matching-with-:~$ cd /?ha??enge  
hacker@globbing~matching-with-:/challenge$ ./run  
You ran me with the working directory of /challenge! Here is your flag:  
pwn.college{o6MWWjf3txhP-Fw-eh8H9brKk5U.QXyIDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt the usage of `?` glob.   
`?` is used as single character wild entry.  
  
## References  
The problem statement was the reference used.  
```  
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!  
```

# 3. Matching with `[]`  
The challenge prompted me to pass the `[]` glob as an argument to the `run` binary to print the flag.  
  
## My Solve  
**Flag:** `pwn.college{Q01V2iGMANhsyDK4zRXkiTb42Va.QXzIDO0wCM2EDNzEzW}`  
  
I first changed my directory to `/challenge/files` then I passed `flag_[bash]` as an argument to `/challenge/run` to print the flag.  
```  
hacker@globbing~matching-with-:~$ cd /challenge/files  
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]  
You got it! Here is your flag!  
pwn.college{Q01V2iGMANhsyDK4zRXkiTb42Va.QXzIDO0wCM2EDNzEzW}  
```    
## What I Learned  
I learnt the usage of `[]` glob and how it can be used as a single character wild entry for a subset of potential characters.  
  
## References  
The problem statement provided was the reference used.  
```  
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!  
```

# 4. Matching paths with `[]`  
The challenge prompted to use `[]` in defining paths and pass it as argument to `/challenge/run` binary.  
  
## My Solve  
**Flag:** `pwn.college{AMGZ2GyFJ4jnFwSUV0DYjWawgW2.QX0IDO0wCM2EDNzEzW}`  
  
From the home directory I ran `/challenge/run` binary using the argument `/challenge/files/file_[bash]` and was prompted with the flag.  
```  
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]  
You got it! Here is your flag!  
pwn.college{AMGZ2GyFJ4jnFwSUV0DYjWawgW2.QX0IDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learned that `[]` glob can be used while defining paths.  
## References  
The problem statement was the reference used.  
```  
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!  
```

# 5. Multiple Globs  
The challenge prompted me to define a path using more than one glob.  
  
## My Solve  
**Flag:** `pwn.college{ki5a8f1Sb6LuIA_KZqKD5OemNiv.0lM3kjNxwCM2EDNzEzW}`  
  
I used `*p*` as an argument with `/challenge/run` binary which covers all the files that contain the letter `p`.  
```  
hacker@globbing~multiple-globs:~$ cd /challenge/files  
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*  
You got it! Here is your flag!  
pwn.college{ki5a8f1Sb6LuIA_KZqKD5OemNiv.0lM3kjNxwCM2EDNzEzW}  
```  
  
## What I Learned  
I learned that I can use multiple globs at once to define a path.  
  
## References  
The problem statement provided was the reference used  
```  
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).  
  
Now you try it. We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.  
```

# 6. Mixing Globs  
The challenge prompted to mix globs while defining a path and pass it as an argument to `run` binary and get the flag.  
  
## My Solve  
**Flag:** `pwn.college{8fgAzhVIPJ-8QqOll4uO32wjrO5.QX1IDO0wCM2EDNzEzW}`  
  
1. I first changed my directory to `/challenge/files` and used `ls` to list all the files. Through this I noticed that no other files other than `challenging`, `pwning`, `educational` started with their corresponding letters.  
```  
hacker@globbing~mixing-globs:~$ cd /challenge/files  
hacker@globbing~mixing-globs:/challenge/files$ ls  
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful  
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty  
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial  
```  
2. So I used the path `[cep]*` which is 6 characters long and that prompted me the flag.  
```  
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*  
You got it! Here is your flag!  
pwn.college{8fgAzhVIPJ-8QqOll4uO32wjrO5.QX1IDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt that globs can be mixed with each other while defining paths or file names.  
  
## References  
The problems statement provided was the reference used.  
```  
Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!  
```

# 7. Exclusionary Globbing  
The challenge prompted to use globbing to filter out files.  
  
## My Solve  
**Flag:** `pwn.college{QlpTeELLdSsf3CPMJbhX2qknzeP.QX2IDO0wCM2EDNzEzW}`  
  
I first changed my directory to `/challenge/files` and then ran `/challenge/run` binary with the argument that excludes files starting with `p`, `w` or `n` i.e `[^pwn]*`  
```  
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files  
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*  
You got it! Here is your flag!  
pwn.college{QlpTeELLdSsf3CPMJbhX2qknzeP.QX2IDO0wCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt how filtering works while globbing. `^` and `!` can be used to filter.  
  
## References  
The problem statement provided was the reference used.  
```  
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!  
  
NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.  
```

# 8. Tab Completion
The challenge prompted to complete the path using `tab` key.

## My Solve
**Flag: ** `pwn.college{McNDl3uTOlhtaz8iIUion8gS-lj.0FN0EzNxwCM2EDNzEzW}`

I typed in `cat /challenge/pwn` then pressed `tab` key through which it autocompleted the path to `/challenge/pwncollege` and the flag was printed.

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{McNDl3uTOlhtaz8iIUion8gS-lj.0FN0EzNxwCM2EDNzEzW}
```

## What I learned
I learnt the usage of `tab` key while scripting, and how it can be used to autocomplete and why it is safer than globbing with `*`.

## References
The problem statement was the reference used.
```
This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!
```

# 9. Multiple options for tab completetion  
Similar to last challenge, but here `tab` provided more than one option.  
  
## My Solve  
**Flag:** `pwn.college{QQQ1A-tuAR-uew-4-Bq5lQj4Mi6.0lN0EzNxwCM2EDNzEzW}`  
  
I first typed `cat /challenge/files/p` and then pressed `tab` key. That showed me all the files starting with `pwncollege`, through which I found the flag file, and printed the flag.  
```  
hacker@globbing~multiple-options-for-tab-completion:~$ ls /challenge/files/pwn  
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking  
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag  
pwn.college{QQQ1A-tuAR-uew-4-Bq5lQj4Mi6.0lN0EzNxwCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt that using `tab`, I can look at multiple options if exist.  
  
## References  
The problem statement provided was the reference used.  
```  
What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.  
  
This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!  
```

# 10. Tab completion on commands  
The challenge prompted me to autocomplete commands using `tab` key.  
  
## My Solve  
**Flag:** `pwn.college{ohVcBdskOaGatlkhoX-VySyGU5g.0VN0EzNxwCM2EDNzEzW}`  
  
I typed in `pwncollege` in the shell and pressed `tab` key which prompted me with the right command and printed the flag.  
```  
hacker@globbing~tab-completion-on-commands:~$ pwncollege-28417  
Correct! Here is your flag:  
pwn.college{ohVcBdskOaGatlkhoX-VySyGU5g.0VN0EzNxwCM2EDNzEzW}  
```  
  
## What I Learned  
I learnt that `tab` completion is not just limited to paths or files, it can be used for commands too.  
  
## References  
The problem statement provided was the reference used.  
```  
Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!  
  
NOTE: You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!  
```
