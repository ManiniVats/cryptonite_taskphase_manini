# Chaining Commands

## Chaining with Semicolons
`;` separates commands like how _Enter_ separates lines

Here we need to run `/challenge/pwn` and then `/challenge/college`, chaining them with `;`.
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{c5ims6OEfchzwch37V_q9fUPbkk.dVTN4QDL5gDO0czW}
hacker@chaining~chaining-with-semicolons:~$
```
flag: `pwn.college{c5ims6OEfchzwch37V_q9fUPbkk.dVTN4QDL5gDO0czW}`

## Your First Shell Script
We can also put commands in a file, called a shell script, and run them by executing the file

Here, we need to run `/challenge/pwn` and then `/challenge/college`, in a _shell script_ called `x.sh`, then run it with `bash`

![image](https://github.com/user-attachments/assets/4807413a-6e11-4240-8376-7ff403266bca)

```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{8Af9xOrXcOV03QKbGwVUu_3Eqle.dFzN4QDL5gDO0czW}
hacker@chaining~your-first-shell-script:~$
```
flag: `pwn.college{8Af9xOrXcOV03QKbGwVUu_3Eqle.dFzN4QDL5gDO0czW}`

## Redirecting Script Output
We can use piping `|` from our script to another program.

Here, we need to create the script as in the previous challenge and pipe its output into the `/challenge/solve` command.

```
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{QviJCSjlCt8qV8nVCJOSIPXpok7.dhTM5QDL5gDO0czW}
hacker@chaining~redirecting-script-output:~$
```
flag: `pwn.college{QviJCSjlCt8qV8nVCJOSIPXpok7.dhTM5QDL5gDO0czW}`

## Executable Shell Scripts
We can directly run a `.sh` file without using the `bash` command by making the file _executable_

Here we need to make a shellscript that will invoke `/challenge/solve`, make it executable, and run it without explicitly invoking bash.
```
hacker@chaining~executable-shell-scripts:~$ touch solve.sh
hacker@chaining~executable-shell-scripts:~$ nano solve.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x solve.sh
hacker@chaining~executable-shell-scripts:~$ ./solve.sh
Congratulations on your shell script execution! Your flag:
pwn.college{s3vFlyMYpSvwVYFkTkDVxDXKg29.dRzNyUDL5gDO0czW}
hacker@chaining~executable-shell-scripts:~$
```
flag: `pwn.college{s3vFlyMYpSvwVYFkTkDVxDXKg29.dRzNyUDL5gDO0czW}`
