
# 1. Translating Characters

This challenge prompted me to swap the case of characters in a string using the `tr` command.

## My Solve

**Flag:** `pwn.college{YhoGk_OhKnKg6ubl6giQXPp7RCm.01MxEzNxwCM2EDNzEzW}`

I piped the output of the `run` binary to the `tr` command. I provided two character sets to `tr`: the first with all lowercase then uppercase letters, and the second with all uppercase then lowercase letters. This swapped the case of the output and revealed the flag.

```
hacker@data~translating-characters:~$ /challenge/run | tr 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ' 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'
YOUR CASE-SWAPPED FLAG:pwn.college{YhoGk_OhKnKg6ubl6giQXPp7RCm.01MxEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `tr` command can be used to translate characters from one set to another.

## References

The problem statement provided was the reference used.

```
One of the purposes of piping data is to modify it.
...
One of these is tr, which translates characters it receives over standard input and prints them to standard output.
...
In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa).
Can you undo it with tr and get the flag?
```

# 2. Deleting Characters

This challenge prompted me to delete specific decoy characters from a string using `tr`.

## My Solve

**Flag:** `pwn.college{Ajgbl2DhTceKcwBkqOPnyFf480c.0FNxEzNxwCM2EDNzEzW}`

The output from the `run` binary had `^` and `%` characters mixed in with the flag. I piped the output to the `tr` command with the `-d` flag to delete both characters and clean up the string.

```
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{Ajgbl2DhTceKcwBkqOPnyFf480c.0FNxEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `tr -d` command can be used to delete a specific set of characters from standard input.

## References

The problem statement provided was the reference used.

```
tr can also translate characters to nothing (i.e., delete them).
This is done via a -d flag and an argument of what characters to delete:

hacker@dojo:~$ echo PAWN | tr -d A
PWN
hacker@dojo:~$
Pretty simple!
Now you give it a try.
I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters.
Use tr -d to remove them!
```

# 3. Deleting Newlines

This challenge prompted me to remove newline characters from an output stream.

## My Solve

**Flag:** `pwn.college{88jOE3Q_aYTtNlovrTpbVqHMWme.0VNxEzNxwCM2EDNzEzW}`

The program's output had the flag split across multiple lines. I piped the output to `tr -d "\n"` to delete all the newline characters, which combined everything into a single line.

```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{88jOE3Q_aYTtNlovrTpbVqHMWme.0VNxEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt how to delete newline characters using `tr -d`. The newline is represented as `\n` and must be quoted.

## References

The problem statement provided was the reference used.

```
A common class of characters to remove is a line separator.
This happens when you have a stream of data that you want to turn into a single line for further processing.
You can specify newlines almost like any other character, by escaping them:

hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!

\n is a standin for this newline, and it must be in quotes to prevent the shell interpreter itself from trying to interpret it and pass it to tr instead.
Now, let's combine this with deletion.
In this challenge, we'll inject a bunch of newlines into the flag.
Delete them with tr's -d flag and the escaped newline specification!
```

# 4. Extracting first lines with head

This challenge prompted me to pipe the first few lines of a program's output to another program.

## My Solve

**Flag:** `pwn.college{s9csfSqTVNcbUnDhNnzjP-AQno5.0lNxEzNxwCM2EDNzEzW}`

I created a pipeline of three commands. I piped the output of `/challenge/pwn` to `head -n 7` to get only the first seven lines, and then piped that result to `/challenge/college` to get the flag.

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | (/challenge/college)
Congratulations, you piped the right codes!
pwn.college{s9csfSqTVNcbUnDhNnzjP-AQno5.0lNxEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `head` command is used to get the first few lines of an input stream, and the number of lines can be specified with the `-n` flag.

## References

The problem statement provided was the reference used.

```
In your Linux journey, you'll experience situations where you need to grab just the early output of very verbose programs.
For this, you'll reach for head!
The head command is used to display the first few lines of its input...
...
By default, it shows the first 10 lines, but you can control this with the -n option...
...
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right!
```

# 5. Extracting specific sections of text

This challenge prompted me to extract a specific column of data from a text stream.

## My Solve

**Flag:** `pwn.college{sMqRrR75dygNb5QBIi5CXe6_z01.01NxEzNxwCM2EDNzEzW}`

The program's output had the flag characters in the second column, separated by spaces. I piped the output to `cut -d " " -f 2` to extract only the second column, then piped that result to `tr -d "\n"` to join the characters into the final flag.

```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{sMqRrR75dygNb5QBIi5CXe6_z01.01NxEzNxwCM2EDNzEzW}
```

## What I Learned

I learnt how to use the `cut` command to extract columns of text. The `-d` flag sets the delimiter, and the `-f` flag selects the column number.

## References

The problem statement provided was the reference used.

```
Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd column.
For this, there's the cut command.
...
The -d argument specifies the column delimiter (how columns are separated).
The -f argument specifies the field number (which column to extract).
...
In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns.
Use cut to extract the flag characters, then pipe them to tr -d "\n" ... to join them together into a single line.
```

# 6. Sorting Data

This challenge prompted me to sort a file and extract a specific line to find the flag.

## My Solve

**Flag:** `pwn.college{YyhW95wOIHDHL67BGOn_SuBuQyL.0FM0MDOxwCM2EDNzEzW}`

The challenge stated the real flag would be the last one after an alphabetical sort. I sorted the file in reverse alphabetical order with `sort -r`, which put the correct flag on the first line. Then, I piped that to `head -n 1` to get just the flag.

```
hacker@data~sorting-data:~$ sort /challenge/flags.txt -r | head -n 1
pwn.college{YyhW95wOIHDHL67BGOn_SuBuQyL.0FM0MDOxwCM2EDNzEzW}
```

## What I Learned

I learnt that the `sort` command is used to order lines of text. Besides `-r` for reverse order, other useful flags are `-n` for sorting numbers, `-u` for showing only unique lines, and `-R` for randomizing the order.

## References

The problem statement provided was the reference used.

```
Files (or output lines of commands) aren't always in the order you need them!
The sort command helps you organize data.
...
-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!
...
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them.
When sorted alphabetically, the real flag will be at the end...
Go get it!
```
