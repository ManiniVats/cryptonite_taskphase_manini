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

- FD 0: Standard Input
- FD 1: Standard Output
- FD 2: Standard Error
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
`<` is used to redirect input to programs.

In this challenge, we need to redirect the `PWN` file to `/challenge/run` and have the `PWN` file contain the value `COLLEGE`. Thus we need to use both input and output redirection.
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{gO7k70y1wOvh8O1PIbk8lrStCR3.dBzN1QDL5gDO0czW}
hacker@piping~redirecting-input:~$
```
flag: `pwn.college{gO7k70y1wOvh8O1PIbk8lrStCR3.dBzN1QDL5gDO0czW}`

## Grepping Stored Results
Here we need to redirect the output of `/challenge/run` to `/tmp/data.txt` and grep it for the flag.

First, we execute `/challenge/run > /tmp/data.txt` for the output redirection:
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
[PASS] Success! You have satisfied all exe
```
Now, we know that our flag contains `pwn.college`. Thus, grepping `/tmp/data.txt` for it, we get the flag:
```
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{MTJXMZ0FBKdFOhNL2hqKxiqlKzU.dhTM4QDL5gDO0czW}
hacker@piping~grepping-stored-results:~$
```
flag: `pwn.college{MTJXMZ0FBKdFOhNL2hqKxiqlKzU.dhTM4QDL5gDO0czW}`

## Grepping Live Output
Here we need to grep for our flag in the output of `/challenge/run` using pipe operator `|` .

By using `|`, output from the command to the left of the `|` will be connected to the input of the command to the right of the `|`.
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{MLirc788SOcPX_a_pobnhNE6kjK.dlTM4QDL5gDO0czW}
hacker@piping~grepping-live-output:~$
```
flag: `pwn.college{MLirc788SOcPX_a_pobnhNE6kjK.dlTM4QDL5gDO0czW}`

## Grepping Errors 
The `>&` operator redirects a FD to another FD. 

Here we need to `grep` through errors directly.

>[!NOTE]
>We cannot use `|` here since it redirects only standard _output_ to another program, not errors.

Thus, we will first redirect standard error to standard output by using `2>&1` and then `pipe` them to grep for our flag :
```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{scIfEy2QOTjJRwHtJrjFEeU6OW5.dVDM5QDL5gDO0czW}
hacker@piping~grepping-errors:~$
```
flag: `pwn.college{scIfEy2QOTjJRwHtJrjFEeU6OW5.dVDM5QDL5gDO0czW}`

## Duplicating Piped Data with tee
The `tee` command duplicates data flowing through our `pipes` to any number of files provided on the command line.

In this challenge, we need to pipe the output of `/challenge/pwn` into `/challenge/college` but also need to figure out the code to intercept the output of `pwn`.

_getting errors_

## Writing To Multiple Programs
The `tee` command is designed to write to files and to standard output only. But we can write a command as `>(command)` to pass it in as a file.

Here, we need to run the `/challenge/hack` command, and duplicate its output as input to both the `/challenge/the` and the `/challenge/planet`:
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{8jjbhISON5yV6-eZpmNfHwkfoRP.dBDO0UDL5gDO0czW}
hacker@piping~writing-to-multiple-programs:~$
```
flag: `pwn.college{8jjbhISON5yV6-eZpmNfHwkfoRP.dBDO0UDL5gDO0czW}`



