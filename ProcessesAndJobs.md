# Processes And Jobs 
Viewing and interacting with processes

##Listing Processes
We can use `ps` to list processes.

Here `/challnge/run` has been renamed to random file which we need to find in the `/challenge` directory by grepping through the processes list busing `ps -ef` or `ps aux`

```
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   06:14   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2240 ?        S    06:14   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    06:14   0:00 /challenge/25942-run-6540
root          72  0.0  0.0   2744  1280 ?        S    06:14   0:00 sleep 6h
hacker        73  0.0  0.0   5240  3840 pts/0    Ss   06:14   0:00 /run/dojo/bin/ssh-entrypoint
hacker        90  0.0  0.0   7868  3520 pts/0    R+   06:15   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/25942-run-6540
Yahaha, you found me! Here is your flag:
pwn.college{U2vCoVTBpC15BGsp24bGH0-9aIv.dhzM4QDL5gDO0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
flag:`pwn.college{U2vCoVTBpC15BGsp24bGH0-9aIv.dhzM4QDL5gDO0czW}`

## Killing Processes
Here, we need to find `/challenge/dont_run` and `kill` it using its PID, after which we can run `/challenge/run` to get our flag:
```
hacker@processes~killing-processes:~$ ps aux | grep /challenge/dont_run
hacker        73  0.0  0.0   4976  3200 ?        Ss   06:18   0:00 /challenge/dont_run
hacker        93  0.0  0.0   4140  2560 pts/0    S+   06:19   0:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{kRZp1kOP4gQZsPGdcLVVcWXNsYI.dJDN4QDL5gDO0czW}
hacker@processes~killing-processes:~$
```
> PID: Process Identifier , PS: Process Status

flag:`pwn.college{kRZp1kOP4gQZsPGdcLVVcWXNsYI.dJDN4QDL5gDO0czW`

## Interrupting Processes
To get rid of the process clogging up the terminal, we use `Ctrl-C` to interrupt it.

Here, `/challenge/run` won't give us the flag until we _interrupt_ it.
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{8lxUwb7vcQxsa-y0FZmRNJiq2Y6.dNDN4QDL5gDO0czW}
hacker@processes~interrupting-processes:~$
```
flag: `pwn.college{8lxUwb7vcQxsa-y0FZmRNJiq2Y6.dNDN4QDL5gDO0czW}`

## Suspending Processes
Instead of killing or interrupting, we can also _suspend_ a process by using `Ctrl-Z`

Here we need to run our process, suspend it, then launch another copy while the first one is suspended so that there is another copy of itself running, using the same terminal.
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 06:35 pts/0    00:00:00 bash /challenge/run
root          84      82  0 06:35 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 06:35 pts/0    00:00:00 bash /challenge/run
root          89      65  0 06:36 pts/0    00:00:00 bash /challenge/run
root          91      89  0 06:36 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{ouaMDcrCGpabquKRb7v0soCr6mt.dVDN4QDL5gDO0czW}
```
flag:`pwn.college{ouaMDcrCGpabquKRb7v0soCr6mt.dVDN4QDL5gDO0czW}`

## Resuming Processes
By using the `fg` command, we can _resume_ the processes we initially suspended

Here, we need to suspend `/challenge/run` and then resume it to get our flag:
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{47oQZlfsjSPSTsziMyIYbAsdQDI.dZDN4QDL5gDO0czW}
Don't forget to press Enter to quit me!

Goodbye!
```
flag: `pwn.college{47oQZlfsjSPSTsziMyIYbAsdQDI.dZDN4QDL5gDO0czW}`

## Backgrounding Processes
Here we need to run our process, suspend it, then background by using `bg` command and launch another copy while the first one is running in the background so that another copy of itself is running, _not suspended_, using the same terminal.
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{0pnF6dW_Vv4TZ-L9jo9_VLzCnGp.ddDN4QDL5gDO0czW}
hacker@processes~backgrounding-processes:~$
```
flag: `pwn.college{0pnF6dW_Vv4TZ-L9jo9_VLzCnGp.ddDN4QDL5gDO0czW}`

## Foregrounding Processes
Upon running `/challenge/run`, we learn that to get our flag, we need to suspend our process, resume it in the background, and then bring it to the foregrounf.
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
```
Thus,

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{k4TMZyAObx7_fZAapD6pndi_EJV.dhDN4QDL5gDO0czW}
hacker@processes~foregrounding-processes:~$


```
flag: `pwn.college{k4TMZyAObx7_fZAapD6pndi_EJV.dhDN4QDL5gDO0czW}`

## Starting Background Processes
Here we need to background `/challenge/run` without suspending it by appending `&` to it.
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{8OvVWsjCCY4gTlN1GpBXdIZvGVL.dlDN4QDL5gDO0czW}
```
flag: `pwn.college{8OvVWsjCCY4gTlN1GpBXdIZvGVL.dlDN4QDL5gDO0czW}`

## Process Exit Codes
We can an access the exit code of the most recently-terminated command using the special `?` variable 
> Commands that succeed return `0` while commands that fail return a non-zero value, most commonly `1`

Here we need to retrieve the exit code returned by `/challenge/get-code` and then run `/challenge/submit-code` with that error code as an argument
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
139
```
Thus `139` is to be used as the argument:
```
hacker@processes~process-exit-codes:~$ /challenge/submit-code 139
CORRECT! Here is your flag:
pwn.college{k_PiSb_2wEy2MmL_AECbVX46hI7.dljN4UDL5gDO0czW}
hacker@processes~process-exit-codes:~$
```
flag: `pwn.college{k_PiSb_2wEy2MmL_AECbVX46hI7.dljN4UDL5gDO0czW}`





```
