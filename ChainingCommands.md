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
