# Pondering Paths
Basics of Linux file paths.
## The Root
To invoke a program, we need to provide its path on the command line, which starts from `/`

In order to get the flag, we need to invoke the program `pwn`, which is situated in the root directory `/`.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{Il7iAoEU007gRfERTLo3d85r-ic.dhzN5QDL5gDO0czW}
hacker@paths~the-root:~$
```
>[!NOTE]
>A path that starts with the root directory, is referred to as an `'absolute path'`.

Here, upon invoking the `run` program, we are rewarded with the flag `pwn.college{Il7iAoEU007gRfERTLo3d85r-ic.dhzN5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Program and Absolute Paths
Here, rather than being directly in the root directory, the program `run` is situated in another directory `challenge`, which in turn, is in the root directory `/`.
```
Connected!
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{ojecaZRxBB_fyZ-jLN4Z0iGUgm6.dVDN1QDL5gDO0czW}
hacker@paths~program-and-absolute-paths:~
```
> Again, 'absolute path' is invoked.

Here, we are rewarded with the flag `pwn.college{ojecaZRxBB_fyZ-jLN4Z0iGUgm6.dVDN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Position Thy Self
