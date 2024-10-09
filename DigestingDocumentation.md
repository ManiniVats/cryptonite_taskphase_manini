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
