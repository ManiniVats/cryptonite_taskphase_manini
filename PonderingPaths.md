# Pondering Paths
Basics of Linux file paths.
## The Root
To invoke a program, we need to provide its path on the command line, which starts from `/`

In order to get the flag, we need to invoke the program `pwn`, which is situated in the root directory `/`.
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{Il7iAoEU007gRfERTLo3d85r-ic.dhzN5QDL5gDO0czW}
hacker@paths~the-root:~$
```
>[!NOTE]
>A path that starts with the root directory, is referred to as an `'absolute path'`.

Here, upon invoking the `run` program, we are rewarded with the flag `pwn.college{Il7iAoEU007gRfERTLo3d85r-ic.dhzN5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Program and Absolute Paths
Here, rather than being directly in the root directory, the program `run` is situated in another directory `challenge`, which in turn, is in the root directory `/`.
```
Connected!
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{ojecaZRxBB_fyZ-jLN4Z0iGUgm6.dVDN1QDL5gDO0czW}
hacker@paths~program-and-absolute-paths:~
```
> Again, an 'absolute path' is invoked.

Here, we are rewarded with the flag `pwn.college{ojecaZRxBB_fyZ-jLN4Z0iGUgm6.dVDN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Position Thy Self
We can navigate around directories by using the `cd` _command_ and passing a path to it as an _argument_. 

Here, when we execute `/challenge/run`, it shows an error, stating that we are not in the correct directory:
```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
```
So now we know that the flag is located in the `/usr/include` directory.

Thus, now using the `cd` command, we get:
```
hacker@paths~position-thy-self:~$ cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{cQ9yphISZfsLAHIVwgyPKeBy72q.dZDN1QDL5gDO0czW}
```
> `cd` stands for *c*hange *d*irectory

Here, we are rewarded with the flag `pwn.college{cQ9yphISZfsLAHIVwgyPKeBy72q.dZDN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Position Elsewhere
This challenge is a practice in continuation with the last sub-topic.
So similarly, when we execute `/challenge/run`, it shows an error, stating that we are not in the correct directory:
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
```
So now we know that the flag is located in the `/var` directory.

Thus, now using the `cd` command, we get:
```
hacker@paths~position-elsewhere:~$ cd /var
hacker@paths~position-elsewhere:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{oJs4DxojICfM5JZVwQFn-cJ-t9-.ddDN1QDL5gDO0czW}
```

Here, we are rewarded with the flag `pwn.college{oJs4DxojICfM5JZVwQFn-cJ-t9-.ddDN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Position Yet Elsewhere
This challenge, again, is a practice in continuation with the last sub-topic.
So similarly, when we execute `/challenge/run`, it shows an error, stating that we are not in the correct directory:
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /home directory.
Please use the `cd` utility to change directory appropriately.
```
So now we know that the flag is located in the `/home` directory.

Thus, now using the `cd` command, we get:
```
hacker@paths~position-yet-elsewhere:~$ cd /home
hacker@paths~position-yet-elsewhere:/home$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4lEDUy4tWOgAqx6fimBsR2lO2xj.dhDN1QDL5gDO0czW}
```

Here, we are rewarded with the flag `pwn.college{4lEDUy4tWOgAqx6fimBsR2lO2xj.dhDN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Implicit Relative Paths, from /
Current Working Directory `cwd` does not matter for absolute paths, but does for relative paths.
> A relative path is any path that does not start at root `/` and is interpreted relative to our `cwd`.

Here, we need to run `/challenge/run` using a relative path while having a `cwd` of `/`

With the help of the hint given, we know that the relative path is `challenge/run`
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{kWbDsmUkeffjp7MYyzD9iJfilGn.dlDN1QDL5gDO0czW}
```
Here, we are rewarded with the flag `pwn.college{kWbDsmUkeffjp7MYyzD9iJfilGn.dlDN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Explicit Relative Paths, from /
Here, we need to use relative path along with an implicit entry `.`, which refers back to the same directory.
Thus, when we try to execute `challenge/run` using just a relative path, we get an error:
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
```
Now we know that our path starts with `.`
```
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{IXGwdUEdLLuIyNLfLwZbQDVRDnS.dBTN1QDL5gDO0czW}
hacker@paths~explicit-relative-paths-from-:/$
```

>[!Important]
>In Linux, `challenge`, `./challenge`, `./././challenge` and `challenge/.` are all identical relative paths.

Here, we are rewarded with the flag `pwn.college{IXGwdUEdLLuIyNLfLwZbQDVRDnS.dBTN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Implicit Relative Path
Given that we have to run our program with `/challenge` as the `cwd`.

But here, we get an error because of the linux security protocol where it automatically avoids looking in the current directory when we provide a 'naked' path:
> A naked path directly specifies which directory to descend into from the current directory.
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
ssh-entrypoint: run: command not found
```
To overcome this, we have to tell tell Linux that we explicitly want to execute a program in the current directory, using `.` like in the previous challenge.
```
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4SVJWTaIcpZYFwd6HU8zm89nGt4.dFTN1QDL5gDO0czW}
```
**This is necessary, or else we could accidentally execute a program in our `cwd` that happened to have the same name as the core system utilities.**

Here, we are rewarded with the flag `pwn.college{4SVJWTaIcpZYFwd6HU8zm89nGt4.dFTN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Home Sweet Home
`hacker@paths~home-sweet-home:~$`

The `~` in this prompt is the `cwd`, with `~` being shorthand for `/home/hacker`. 

Whenever `~` is provided as the start of an argument, it will expand it to our home directory: 
```
hacker@paths~home-sweet-home:~$ echo LOOK: ~
LOOK: /home/hacker
```
>[!IMPORTANT]
>The expansion of `~` is an absolute path, and only the _leading_ `~` is expanded.

Here, we need to specify a file (with certain constraints) as an argument on the command line, after which, `/challenge/run` will write a copy of the flag to that particular file.

In accordance with the given constraints in the challenge, let `m` be the specified file. Thus, its absolute path will be `~/m`.
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/m
Writing the file to /home/hacker/m!
... and reading it back to you:
pwn.college{IBh5IDLIzhLno-w4Vw41viW8Vd9.dNzM4QDL5gDO0czW}
```
Here, we are rewarded with the flag `pwn.college{IBh5IDLIzhLno-w4Vw41viW8Vd9.dNzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

>[!NOTE]
>`cd` uses our home directory as the default destination:
```
hacker@paths~home-sweet-home:~$ cd /tmp
hacker@paths~home-sweet-home:/tmp$ cd
hacker@paths~home-sweet-home:~$
```

