# Hello Hackers
Basics of interacting with command line.
## Introduction To Commands
To invoke a command, we need to type that command after the prompt and hit enter.

First, to ssh into this challenge, we need to connect to the dojo over ssh:
```
mani@LAPTOP-P5ED2HO2:~$ ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@hello~intro-to-commands:~$
```
- To execute `whoami` command:
  ```
  hacker@hello~intro-to-commands:~$ whoami
  hacker
  hacker@hello~intro-to-commands:~$
  ```
> `whoami` command prints the username (hacker) to the terminal.
- To execute `hello` command:
```
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{MK-y7-bkosqwluNUYLS4O0OTLV9.ddjNyUDL5gDO0czW}
hacker@hello~intro-to-commands:~$
```
Here, upon invoking the `hello` command, we are rewarded with the flag `pwn.college{MK-y7-bkosqwluNUYLS4O0OTLV9.ddjNyUDL5gDO0czW}`, upon submitting of which, the challenge is completed.

>[!Caution]
>Commands in Linux are case sensitive: `hello` is different from `HELLO`.

## Introduction to Arguments
Our input is resolved into a command and its arguments. The first word is the command, and the subsequent words are arguments.

- Here, we run the command line `echo hello hackers`, where `echo` is the command and `hello` and `hackers` are the two arguments to the command `echo`.

```
hacker@hello~intro-to-arguments:~$ echo hello hackers
hello hackers
hacker@hello~intro-to-arguments:~$
```
> `echo` is a simple command that "echoes" all of its arguments back out onto the terminal.

- Now, we run the hello command with a single argument of hackers.
```
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{o64ku1OQyxtd-jO3EEgfBplHCpp.dhjNyUDL5gDO0czW}
hacker@hello~intro-to-arguments:~$
```

Here we are rewarded with the flag `ppwn.college{o64ku1OQyxtd-jO3EEgfBplHCpp.dhjNyUDL5gDO0czW}`, upon submitting of which, the challenge is completed.

