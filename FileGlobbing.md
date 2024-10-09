# File Globbing
Globbing lets us reference files without typing out their full paths.

## Matching with *
The shell, upon encountering `*`, tries to replace that argument with any files with matching pattern.

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
`?` works  just like `*`, but only matches one character.

In this challenge, we need to change our directory to `/challenge` using `?` instead of `c` and `l` in the argument to `cd`.
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{4T3nEaVEQCX7Bnz6XBhzNSRPgKz.dJjM4QDL5gDO0czW}
hacker@globbing~matching-with-:/challenge$
```
Here we are rewarded with the flag `pwn.college{4T3nEaVEQCX7Bnz6XBhzNSRPgKz.dJjM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Matching with []
`[]` is a limited form of ?, in the sense that instead of matching any character, it will look for some subset of potential characters, specified within the `[]`.

Here, we need to change our `cwd` to `/challenge/files` and run `/challenge/run` with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

To bracket-glob file_b, file_a, file_s, and file_h, the argument needed would be `file_[bash]`.
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{4u0YNbcvmvStcBYDnzA4zMmit9j.dNjM4QDL5gDO0czW}
hacker@globbing~matching-with-:/challenge/files$
```
Here we are rewarded with the flag `pwn.college{4u0YNbcvmvStcBYDnzA4zMmit9j.dNjM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Matching paths with []
