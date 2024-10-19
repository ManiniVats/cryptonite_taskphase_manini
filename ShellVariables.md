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
On `export`ing variables, they are passed onto the child process (`sh`) of the main shell process.

Here, we need to invoke `/challenge/run` with the `PWN` variable exported and set to `COLLEGE`, and the `COLLEGE` variable set to `PWN` but not exported.

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{oWcRkWGFOZhD1_xdpfDvrxxoBtQ.dJjN1QDL5gDO0czW}
sh-5.2$
```
flag: `pwn.college{oWcRkWGFOZhD1_xdpfDvrxxoBtQ.dJjN1QDL5gDO0czW}`

## Printing Exported Variables
The `env` command prints out every exported variable set in our shell. Here we need to look through it to find the `FLAG` variable.
```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=5c7cf7650a1e541b98557a5e61940441a7463bc2a864fbc81f26e9b82e367b5e
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
FLAG=pwn.college{ERSAfuNvlM5i-9i5c3G8wAdD1Q9.dhTN1QDL5gDO0czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
```

flag: `FLAG=pwn.college{ERSAfuNvlM5i-9i5c3G8wAdD1Q9.dhTN1QDL5gDO0czW}` 

## Storing Command Output
We can store the output of some command into a variable by command substitution

Here, we need to store the output of `PWN` in `/challenge/run`
```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{gO15Bn0lesoY-5kyjHOj5PeoTAN.dVzN0UDL5gDO0czW}
hacker@variables~storing-command-output:~$
```
flag:`pwn.college{gO15Bn0lesoY-5kyjHOj5PeoTAN.dVzN0UDL5gDO0czW}`

## Reading Input 
`read` halps in reading user input while `-p` helps in separating input from output.

Here we need to use `read` to set `PWN` variable to `COLLEGE`
```
hacker@variables~reading-input:~$ read -p "INPUT:" PWN
INPUT:COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MSSWu2m_tGEZ0zcfIEplEeh2yk4.dhzN1QDL5gDO0czW}
hacker@variables~reading-input:~$
```
flag: `pwn.college{MSSWu2m_tGEZ0zcfIEplEeh2yk4.dhzN1QDL5gDO0czW}`

## Reading Files
Here we need to redirect `/challenge/read/me` into the standard input of `read`, and so when `read` reads into `PWN`, we get our flag.
```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UeHEUBeZRmFxLQALMRj_UOf84dp.dBjM4QDL5gDO0czW}
hacker@variables~reading-files:~$
```
flag:`pwn.college{UeHEUBeZRmFxLQALMRj_UOf84dp.dBjM4QDL5gDO0czW}` 























