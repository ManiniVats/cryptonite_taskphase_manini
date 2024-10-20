# PerceivingPermissions
Linus Permissions

## Changing File Ownership

Here we need to run `chown hacker /flag` to give the ownership of `/flag` to hacker.

> `chown` can only be used by the root user

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{cTRSS84MwPj-2pQCQmGjefwx-ys.dFTM2QDL5gDO0czW}
hacker@permissions~changing-file-ownership:~$
```
flag: `pwn.college{cTRSS84MwPj-2pQCQmGjefwx-ys.dFTM2QDL5gDO0czW}`
