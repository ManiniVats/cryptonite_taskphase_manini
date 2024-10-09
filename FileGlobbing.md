# File Globbing
Globbing lets us reference files without typing out their full paths.

## Matching with *
The shell treats `*` as a _wildcard_ and tries to replace that argument with any files with matching pattern.

In this challenge, we need to change our directory to `/challenge`, but use globbing to keep the argument limited to four characters at the most.
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{oh9-BChh7D9ee9Wq0wm0hFdZ3xL.dFjM4QDL5gDO0czW}
hacker@globbing~matching-with-:/challenge$
```

Here we are rewarded with the flag `pwn.college{oh9-BChh7D9ee9Wq0wm0hFdZ3xL.dFjM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Matching with ?
