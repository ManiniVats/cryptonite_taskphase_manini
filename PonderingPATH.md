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
