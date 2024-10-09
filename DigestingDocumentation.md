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



