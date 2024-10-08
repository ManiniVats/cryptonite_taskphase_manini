# Comprehending Commands
Useful Linux Commands

## cat: not the pet, but the command! 
`cat` is used for reading out files. It concatenates multiple files if provided multiple arguments.

Here, we need to read out the contents of the `flag` file situated in our home directory:
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{I4t6A240O0K11PIAwijeU1MtXtf.dFzN1QDL5gDO0czW}
hacker@commands~cat-not-the-pet-but-the-command:~$
```
Here we are rewarded with the flag `pwn.college{I4t6A240O0K11PIAwijeU1MtXtf.dFzN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## catting absolute paths
We can also specify `cat`'s arguments as absolute paths.

This challenge requires us to retrieve our flag from the root directory:
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{4WVgNYuHGOp91J2aVIwS9F98Eum.dlTM5QDL5gDO0czW}
hacker@commands~catting-absolute-paths:~$
```
Here we are rewarded with the flag `pwn.college{4WVgNYuHGOp91J2aVIwS9F98Eum.dlTM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## more catting practice
This challenge is similar to the above challenge, but here we cannot `cd` directly into the directory where the flag is stored. 

Thus, we need to retrieve this flag by its absolute path only.

When we ssh into the challenge it tells us the absolute path where the flag is kept:
```
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/debug/flag. Go cat it out **without** cding into that
directory!
```
Now we know that `/lib/debug/flag` is the absolute path required.
```
hacker@commands~more-catting-practice:~$ cat /lib/debug/flag
pwn.college{MMhm8Cr8_tAOHYIF7BumRLjsEf-.dBjM5QDL5gDO0czW}
hacker@commands~more-catting-practice:~$
```

Here we are rewarded with the flag `pwn.college{MMhm8Cr8_tAOHYIF7BumRLjsEf-.dBjM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## grepping for a needle in haystack
Sometimes, we need to find a particular set of data in a large file, which would be just like finding a needle in a haystack.

The `grep` command helps search the file for lines of text containing SEARCH_STRING and print them to the console.

Here, we have been given the absolute path of the flag as `/challenge/data.txt`

We know that our flag always starts with `pwn.college`, thus making it the SEARCH_STRING.

Thus, grepping for flag:
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{kAyMqSFRL7PQFAWIQyUsyZ4edmY.ddTM4QDL5gDO0czW}
```

Here we are rewarded with the flag `pwn.college{kAyMqSFRL7PQFAWIQyUsyZ4edmY.ddTM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## listing files
The `ls` command lists files in all the directories provided to it as arguments, and in the `cwd` if no arguments are provided.

Here, we have to find `/challenge/run` which has been renamed and kept in the `/challenge` directory, by listing out all the files in it.
```
hacker@commands~listing-files:~$ ls /challenge
1780-renamed-run-6197  DESCRIPTION.md
hacker@commands~listing-files:~$
```
Now we know that the absolute path of the required file is `/challenge/1780-renamed-run-6197`
```
hacker@commands~listing-files:~$ /challenge/1780-renamed-run-6197
Yahaha, you found me! Here is your flag:
pwn.college{QoJgXb33NfkodTajV4Wm0WqMBYK.dhjM4QDL5gDO0czW}
hacker@commands~listing-files:~$
```

Here we are rewarded with the flag `pwn.college{QoJgXb33NfkodTajV4Wm0WqMBYK.dhjM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## touching files
We can create a new, blank file by _touching_ it with the `touch` command.
In this challenge, we need to create two files, `/tmp/pwn` and `/tmp/college`, and run `/challenge/run` to get the flag:
```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{g_IYFI3eFzQPrg9YKcubDFSoif1.dBzM4QDL5gDO0czW}
hacker@commands~touching-files:~$
```

Here we are rewarded with the flag `pwn.college{g_IYFI3eFzQPrg9YKcubDFSoif1.dBzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## removing files
To clean up, we can remove files by the command `rm`.

Here, a `delete_me` file has been created in our home directory. To obtain the flag, we need to remove the file and run `/challenge/check`:
```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{gbiddWOFrkjSePbLEhpb4cQtHXn.dZTOwUDL5gDO0czW}
hacker@commands~removing-files:~$
```

Here we are rewarded with the flag `pwn.college{gbiddWOFrkjSePbLEhpb4cQtHXn.dZTOwUDL5gDO0czW}`, upon submitting of which, the challenge is completed.








