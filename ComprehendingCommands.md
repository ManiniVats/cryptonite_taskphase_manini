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
