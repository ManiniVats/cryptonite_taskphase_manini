# PerceivingPermissions
Linux Permissions

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

## Groups And Files
The `chgroup` command is used to change group ownership.

Here we need to change the group owner of `/flag` from `root` to `hacker`
```
acker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{MidSWg2QxNFsj97sJwONmV-VHjc.dFzNyUDL5gDO0czW}
hacker@permissions~groups-and-files:~$
```
flag: `pwn.college{MidSWg2QxNFsj97sJwONmV-VHjc.dFzNyUDL5gDO0czW}`

## Fun With Group Names
Like the previous challenge we need to change group owner here, but the group owner of `hacker` is not `hacker`, which we can find out by using the `id` command.
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp3980) groups=1000(grp3980)
```
Thus the group owner of `hacker` here is `grp3980`
```
hacker@permissions~fun-with-groups-names:~$ chgrp grp3980 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{IAdJb4PV6NPJlIEFJm72vixeB90.dJzNyUDL5gDO0czW}
hacker@permissions~fun-with-groups-names:~$
```
flag:`pwn.college{IAdJb4PV6NPJlIEFJm72vixeB90.dJzNyUDL5gDO0czW}`

## Changing Permissions 
We can use `chmod` command to modify an existing permission mode by tweaking permissions with the mode format of `WHO+/-WHAT`
> WHO is user/group/other and WHAT is read/write/execute

Here we need to change the permissions of the `/flag` file to read it, keeping in mind that it is owned by `root`
```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{URHHvFg0SSlkGU6vZK6-BHCfVEj.dNzNyUDL5gDO0czW}
hacker@permissions~changing-permissions:~$
```
flag: `pwn.college{URHHvFg0SSlkGU6vZK6-BHCfVEj.dNzNyUDL5gDO0czW}`

## Executable Files 
Since it's not given who the owner of the file `/flag` is, we first find that out:
```
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r-xr--r-x 1 hacker hacker 32 Jul  4 06:37 /challenge/run
hacker@permissions~executable-files:~$
```
Thus, `hacker` is the owner of the `/flag` file, but doesn't have executing permissions. Thus we use `chmod` to rectify it accordingly:
```
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{IVup5FTlkYqX8n1Zp-HZGXXk9Nv.dJTM2QDL5gDO0czW}
hacker@permissions~executable-files:~$
```
flag:`pwn.college{IVup5FTlkYqX8n1Zp-HZGXXk9Nv.dJTM2QDL5gDO0czW}`

## Permission Tweaking Practice
Here we practice `chmod` by starting off with running `/challenge/run`:
```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
```
Comparing the current and needed permissions, `g-r` and `o-r` are required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g-r,o-r /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rw-rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
```
Comparing the current and needed permissions, `g+wr` and `o+wr` are required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g+wr,o+wr /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": rw-rw-rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-rw-rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
```
Comparing the current and needed permissions, `u-r` is required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod u-r /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": -w-rw-rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxrwxrw-
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
```
Comparing the current and needed permissions, `g+x` and `u+x` are required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g+x,u+x /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": -wxrwxrw-
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wx---rw-
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
```
Comparing the current and needed permissions, `g-rwx` is required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g-rwx /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": -wx---rw-
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wx--xrwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
```
Comparing the current and needed permissions, `g+x` and `o+x` are required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g+x,o+x /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": -wx--xrwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wxrwxrwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
```
Comparing the current and needed permissions, `g+rw` is required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g+rw /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": -wxrwxrwx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wx-wx-wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
```
Comparing the current and needed permissions, `g-r` and `o-r` are required:
```
hacker@permissions~permission-tweaking-practice:~$ chmod g-r,o-r /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
```
On getting permissions right eight times in a row, the challenge lets us `chmod u+r /flag` to make it readable:
```
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{gsdj1VjN7tbGU2OmLQUPu7YVhG9.dBTM2QDL5gDO0czW}
hacker@permissions~permission-tweaking-practice:~$
```
flag: `pwn.college{gsdj1VjN7tbGU2OmLQUPu7YVhG9.dBTM2QDL5gDO0czW}`

##
