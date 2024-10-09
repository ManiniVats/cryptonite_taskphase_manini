# Digesting Documentation
Looking for help on how to use programs in Linux

## Learning from documentation
The correct usage of programs depends on the proper specification of arguments to them.

Here, we are required to run the program `/challenge/challenge` with the help of the argument `--giveflag`
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{QP6KEBndBccdUbecOI9bdYAJ6zK.dRjM5QDL5gDO0czW}
hacker@man~learning-from-documentation:~$
```

Here we are rewarded with the flag `pwn.college{QP6KEBndBccdUbecOI9bdYAJ6zK.dRjM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Learning Complex Usage
Some commands take arguments to their arguments.

According to the given documentation, we need to get our flag by passing it as an argument to the argument `--printfile` to the command `/challenge/challenge`:
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{k1aCgJYqBD1cEIhlhiyfvcTywE1.dVjM5QDL5gDO0czW}
hacker@man~learning-complex-usage:~$
```
Here we are rewarded with the flag `pwn.college{k1aCgJYqBD1cEIhlhiyfvcTywE1.dVjM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Reading Manuals
The `man` command displays the manual of the command you pass as an argument to it. 

>[!IMPORTANT]
>The arguments to the `man` command aren't file paths, but just the names of the entries themselves.

To get the flag, we must use a secret option, which we will learn about through the manual on `challenge`

Thus, on running `man challenge`, we get its manual in which the description is as follows:
```
DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --rjjabl NUM
              print the flag if NUM is 284
```
Thus, to print the flag we need to use the argument `--rjjabl NUM` where `NUM` is 284.
```
hacker@man~reading-manuals:~$ /challenge/challenge --rjjabl 284
Correct usage! Your flag: pwn.college{UEUrJTLjjablwe2gontRJn_mbu8.dRTM4QDL5gDO0czW}
hacker@man~reading-manuals:~$
```

Here we are rewarded with the flag `pwn.college{UEUrJTLjjablwe2gontRJn_mbu8.dRTM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Searching Manuals
When the manual is too big to search, we can use `/` function to search for the required keyword.

Here we need to search for `flag` keyword and then scroll by hitting `n` and `N` to get the required option:
```
 --lqkjdmb
              This argument will give you the flag!
```
```
hacker@man~searching-manuals:~$ /challenge/challenge  --lqkjdmb
Initializing...
Correct usage! Your flag: pwn.college{Qd1s-kULk4qV07-dRFbVTv7CAN_.dVTM4QDL5gDO0czW}
```

Here we are rewarded with the flag `pwn.college{Qd1s-kULk4qV07-dRFbVTv7CAN_.dVTM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Searching For Manuals 
Here, we must go to the manual of `man` by using `man man` and find out how to search for the hidden manpage that will in turn tell us how to use `/challenge/challenge`.

After opening the `man` manpage, we find out:
```
 man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular  expression.   Print
           out any matches.  Equivalent to apropos printf.
```
Now, on running `man -k flag`, we get:
```
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
oreggwanpd (1)       - print the flag!
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure ...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and confi...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure...
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
```
Thus, now, to find out how to use `/challenge/challenge`, we need to open the `oreggwanpd` manpage.

On running `man oreggwanpd `, 
```
DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --oreggw NUM
              print the flag if NUM is 443
```
Thus, to get the flag, we need to pass `--oreggw NUM` as the argument to the command `/challenge/challenge` where `NUM` is 443
```
hacker@man~searching-for-manuals:~$ /challenge/challenge --oreggw 443
Correct usage! Your flag: pwn.college{or4eEgDL4SWA-LgwanApNJ_W3NV.dZTM4QDL5gDO0czW}
hacker@man~searching-for-manuals:~$
```
Here we are rewarded with the flag `pwn.college{or4eEgDL4SWA-LgwanApNJ_W3NV.dZTM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Helpful Programs
Some programs don't have a man page, but might tell us how to run them if invoked with a special argument like `--help`, `-h` or `-?`.

Here, we need to try and read `/challenge/challenge`'s program's documentation with `--help` argument:
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$
```
From this infromation, we can say that `-g GIVE_THE_FLAG` will give us our flag, but we don't know the string value of `GIVE_THE_FLAG` yet. Thus, by using `-p` first, we will get the value to be put into `-g`:
```
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 345
hacker@man~helpful-programs:~$
```
Now that we know the value to be `345`, we use the `-g` argument:
```
hacker@man~helpful-programs:~$ /challenge/challenge -g 345
Correct usage! Your flag: pwn.college{YTCdnAdvM3ioHteSYKWkyYVJhLT.ddjM4QDL5gDO0czW}
hacker@man~helpful-programs:~$
```
Here we are rewarded with the flag `pwn.college{YTCdnAdvM3ioHteSYKWkyYVJhLT.ddjM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## Help For Builtins
Builtins, rather than being programs with man pages and help options, are built into the shell itself. They are invoked just like commands.

Given that this challenge's `challenge` command is a shell builtin and that we need to lookup its `help` to figure out the secret value to pass to it.
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "EXNKlLlK".
```
Now we know that we need to pass `--secret VALUE` as the argument where `VALUE` is `EXNKlLlK`:
```
hacker@man~help-for-builtins:~$ challenge --secret EXNKlLlK
Correct! Here is your flag!
pwn.college{EXNKlLlKaJLV3cwuZNBd0zyG00L.dRTM5QDL5gDO0czW}
```
Here we are rewarded with the flag `pwn.college{EXNKlLlKaJLV3cwuZNBd0zyG00L.dRTM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.
