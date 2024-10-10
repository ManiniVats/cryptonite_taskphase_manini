# Practicing Piping
Input and Output redirection

## Redirecting Output
We can redirect the output of a command to desired file using `>` character.

Here we need to write the word `PWN` to the filename `COLLEGE`
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{0yKLE7o8TlNBxpTfjpQP4oogp_K.dRjN1QDL5gDO0czW}
hacker@piping~redirecting-output:~$
```
flag: `pwn.college{0yKLE7o8TlNBxpTfjpQP4oogp_K.dRjN1QDL5gDO0czW}`

## Redirecting More Output
Here we are required to redirect the output of the command `/challenge/run` into a file called `myflag`.
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$
```
Now since the flag is in `myflag`, we can `cat` it out:
```
hacker@piping~redirecting-more-output:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{E6IjprYfe25Tzc46_nsdBrTGpF3.dVjN1QDL5gDO0czW}
hacker@piping~redirecting-more-output:~$
```
flag: `pwn.college{E6IjprYfe25Tzc46_nsdBrTGpF3.dVjN1QDL5gDO0czW}`

## Appending Output
`>` creates a new output file every time, deleting the old contents.
If we want the outputs from all different commands that we ran to keep appending to the same file, we use `>>` instead of `>`

Here we need to redirect the output of the command `/challenge/run` in append mode `>>` to `/home/hacker/the-flag` to get the whole flag.
```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
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
```
Now we can `cat` out the contents of `/home/hacker/the-flag`: 
```
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{gQtOa3HkwevB5MNRqqeKH5w2Ah7.ddDM5QDL5gDO0czW}
                              ^
     that is the second half /|\
                              |
```
flag: `pwn.college{gQtOa3HkwevB5MNRqqeKH5w2Ah7.ddDM5QDL5gDO0czW}`

>[!CAUTION]
>Here, if we redirect in _truncate_ mode `>` rather than _append_ mode `>>`, then we would be able to see the second half of the flag only.

## Redirecting Errors
When we redirect process communication, we do it by FD number:
-FD 0: Standard Input
-FD 1: Standard Output
-FD 2: Standard Error
> FD: File Descriptor

In this challenge, we need to redirect the output of `/challenge/run`, to `myflag`, and the errors to `instructions`, and then `cat` out `myflag`:
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gqXZJOVOLN6QS2M1esHGDTimlS8.ddjN1QDL5gDO0czW}

hacker@piping~redirecting-errors:~$
```
flag: `pwn.college{gqXZJOVOLN6QS2M1esHGDTimlS8.ddjN1QDL5gDO0czW}`

## Redirecting Input 
