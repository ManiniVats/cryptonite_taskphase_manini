# Untangling Users

## Becoming root with su
To become the root user, one of the commands used is `su`the switch user command. It makes sure that the user knows the root password.

In this challenge, we need to provide the given password `hack-the-planet` to `su` in order to become the root and hence get the flag.
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{Mtc9OLpK6ygkG22fM38wXIu3tAG.dVTN0UDL5gDO0czW}
root@users~becoming-root-with-su:/home/hacker#
```
flag: `pwn.college{Mtc9OLpK6ygkG22fM38wXIu3tAG.dVTN0UDL5gDO0czW}`

## Other users with su 
We can also give a username as an argument to `su` to switch to that user instead of the root.

In this challenge we need to switch to the `zardus` user and then run `/challenge/run`, given that the password is `dont-hack-me`
```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{cdAkgi8KEtCtjBC_W2j2iv1XrYu.dZTN0UDL5gDO0czW}
zardus@users~other-users-with-su:/home/hacker$
```
flag: `pwn.college{cdAkgi8KEtCtjBC_W2j2iv1XrYu.dZTN0UDL5gDO0czW}`

## Cracking Passwords
When we input a password into `su`, it one-way-encrypts (hashes) it and compares the result against the stored value. If, by any _unwanted_ leaks, we have the hashed value of the password, we can start cracking passwords.

This challange has given us a leak of `/etc/shadow` in `/challenge/shadow-leak`. We need to crack zardus's password and run `/challenge/run` to get the flag.

We use `John The Ripper` method for this as follows:

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04807g/s 279.9p/s 279.9c/s 279.9C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```
Thus now we know that the password is `aardvark`
```
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{8fVntJBLfx-jn2HfFKazmDq6fEK.ddTN0UDL5gDO0czW}
zardus@users~cracking-passwords:/home/hacker$
```
flag: `pwn.college{8fVntJBLfx-jn2HfFKazmDq6fEK.ddTN0UDL5gDO0czW}`

## Using Sudo 
`Sudo`(superuser do) defaults to running a command as root and unlike `su`, does not authenticate via password.

In this challenge, we have been giving `sudo` access and we need to use it to read the flag.
```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{YRw55CmyWY3dkgTI0Xe5NgjcM04.dhTN0UDL5gDO0czW}
hacker@users~using-sudo:~$
```
flag:`pwn.college{YRw55CmyWY3dkgTI0Xe5NgjcM04.dhTN0UDL5gDO0czW}`

