# Shell Variables
This module is about the variables supported by the command line, called the 'shell'.

## Printing Variables
Given that our flag is in the variable `FLAG`, we can print it by prepending it with `$`so as to access the variable:
```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{scRraDvYMKHpFAVVT122V-54H0a.ddTN1QDL5gDO0czW}
```
flag: pwn.college{scRraDvYMKHpFAVVT122V-54H0a.ddTN1QDL5gDO0czW}

## Setting Variables
We can also write values to variables by using `=`

Here, we need to set the `PWN` variable to the value `COLLEGE`:
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{cnVx-uZfLPTpj6NnPo8kYiO48qZ.dlTN1QDL5gDO0czW}
```
flag: pwn.college{cnVx-uZfLPTpj6NnPo8kYiO48qZ.dlTN1QDL5gDO0czW}

## Multi-Word Variables
To have more than 1 word to be set as a value to a variable, using `VAR=WORD1 WORD2` would not work as the shell would interpret the next word to the _space_ (`WORD2`) as a command.

Thus we need to quote `"` all the words to be put as value to the given variable.

Here, we need to set the variable `PWN` to `COLLEGE YEAH`:
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{QHmNOBptAm4v5wbejEgqHCPDg93.dBjN1QDL5gDO0czW}
```
flag: pwn.college{QHmNOBptAm4v5wbejEgqHCPDg93.dBjN1QDL5gDO0czW}

## Exporting Variables
