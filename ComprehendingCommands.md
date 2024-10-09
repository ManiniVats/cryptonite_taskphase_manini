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

Here, a `delete_me` file has been created in our home directory. To obtain the flag, we need to remove this file and run `/challenge/check`:
```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{gbiddWOFrkjSePbLEhpb4cQtHXn.dZTOwUDL5gDO0czW}
hacker@commands~removing-files:~$
```

Here we are rewarded with the flag `pwn.college{gbiddWOFrkjSePbLEhpb4cQtHXn.dZTOwUDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## hidden files
There is a convention that files that start with a `.` don't show up by default in `ls` 

To view them with `ls`, we need to invoke it with the `-a` flag.

Here, it is given that our flag is hidden as a dot-prepended file in the root directory `/`.
```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-25687381125059  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
```
Now that we know that our flag is in `.flag-25687381125059`, we just need to cat it out:
```
hacker@commands~hidden-files:/$ cat .flag-25687381125059
pwn.college{gvUujNHlEP0IR21HTxy94PBspf-.dBTN4QDL5gDO0czW}
hacker@commands~hidden-files:/$
```

Here we are rewarded with the flag `pwn.college{gvUujNHlEP0IR21HTxy94PBspf-.dBTN4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## An Epic Filesystem Quest
_getting errors_

## making directories
We can make directories using the `mkdir` command.

Here, we need to create a `/tmp/pwn` directory and make a `college` file in it.
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{c2uatGIm5redgskIgcIkv-ZbK9q.dFzM4QDL5gDO0czW}
hacker@commands~making-directories:~$
```

Here we are rewarded with the flag `pwn.college{c2uatGIm5redgskIgcIkv-ZbK9q.dFzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## finding files
The `find` command takes arguments describing the search criteria and the search location.

>[!NOTE]
>If we don't specify a search criteria, `find` matches every file, while if we don't specify a search location, it uses the `cwd`.

Here, our flag, named `flag` has been hidden in a random directory.
```
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.G9qthVCks5’: Permission denied
/usr/local/share/radare2/5.9.5/flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/opt/radare2/shlr/capstone/.git/refs/tags/flag
/opt/radare2/libr/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$
```

Ignoring the inaccesible (`Permission Denied`) file systems, we start checking for our flag:
```
hacker@commands~finding-files:~$ cat /usr/local/share/radare2/5.9.5/flag
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
```
We do this until we finally get our flag:
```
hacker@commands~finding-files:~$ cat /opt/radare2/shlr/capstone/.git/refs/tags/flag
pwn.college{oqfK2d7be6gZhpev7lVcRFL39gy.dJzM4QDL5gDO0czW}
hacker@commands~finding-files:~$
```
Thus, we `find` our flag in the `/opt/radare2/shlr/capstone/.git/refs/tags/flag` directory

Here we are rewarded with the flag `pwn.college{oqfK2d7be6gZhpev7lVcRFL39gy.dJzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## linking files
A file is an address at which the contents of that file live. 

A `hard link` is an alternate address that indexes that data, thus they immediately yield the necessary data. 

A `soft/symbolic link`, instead, contains the original file name. When we access the symbolic link, Linux reads the original file name, and then automatically accesses that file.

Symbolic links are created with `ln` as command and with `-s` as argument

> Soft links are also known as symlinks.

>[!NOTE]
>The `file` command recognises symlinks.

Here, we need to link `/home/hacker/not-the-flag` to `/flag` so that executing `/challenge/catflag` will get us the flag stored in `/flag`:
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{gqB_S2JdM0hl0b6Y7uswvXsX859.dlTM1UDL5gDO0czW}
hacker@commands~linking-files:~$
```
>[!CAUTION]
>>The original file path comes before the link path in this command.

Here we are rewarded with the flag `pwn.college{gqB_S2JdM0hl0b6Y7uswvXsX859.dlTM1UDL5gDO0czW}`, upon submitting of which, the challenge is completed.
