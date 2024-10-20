# Comprehending Commands
Useful Linux Commands

## cat: not the pet, but the command! 
`cat` is used for reading out files. It concatenates multiple files if provided multiple arguments.

Here, we need to read out the contents of the `flag` file situated in our home directory: 
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{I4t6A240O0K11PIAwijeU1MtXtf.dFzN1QDL5gDO0czW}
hacker@commands~cat-not-the-pet-but-the-command:~$
```
Here we are rewarded with the flag `pwn.college{I4t6A240O0K11PIAwijeU1MtXtf.dFzN1QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## catting absolute paths
We can also specify `cat`'s arguments as absolute paths.

This challenge requires us to retrieve our flag from the root directory:
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{4WVgNYuHGOp91J2aVIwS9F98Eum.dlTM5QDL5gDO0czW}
hacker@commands~catting-absolute-paths:~$
```
Here we are rewarded with the flag `pwn.college{4WVgNYuHGOp91J2aVIwS9F98Eum.dlTM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## more catting practice
This challenge is similar to the above challenge, but here we cannot `cd` directly into the directory where the flag is stored. 

Thus, we need to retrieve this flag by its absolute path only.

When we ssh into the challenge it tells us the absolute path where the flag is kept:
```
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/debug/flag. Go cat it out **without** cding into that
directory!
```
Now we know that `/lib/debug/flag` is the absolute path required.
```
hacker@commands~more-catting-practice:~$ cat /lib/debug/flag
pwn.college{MMhm8Cr8_tAOHYIF7BumRLjsEf-.dBjM5QDL5gDO0czW}
hacker@commands~more-catting-practice:~$
```

Here we are rewarded with the flag `pwn.college{MMhm8Cr8_tAOHYIF7BumRLjsEf-.dBjM5QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## grepping for a needle in haystack
Sometimes, we need to find a particular set of data in a large file, which would be just like finding a needle in a haystack.

The `grep` command helps search the file for lines of text containing SEARCH_STRING and print them to the console.

Here, we have been given the absolute path of the flag as `/challenge/data.txt`

We know that our flag always starts with `pwn.college`, thus making it the SEARCH_STRING.

Thus, grepping for flag:
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{kAyMqSFRL7PQFAWIQyUsyZ4edmY.ddTM4QDL5gDO0czW}
```

Here we are rewarded with the flag `pwn.college{kAyMqSFRL7PQFAWIQyUsyZ4edmY.ddTM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## listing files
The `ls` command lists files in all the directories provided to it as arguments, and in the `cwd` if no arguments are provided.

Here, we have to find `/challenge/run` which has been renamed and kept in the `/challenge` directory, by listing out all the files in it.
```
hacker@commands~listing-files:~$ ls /challenge
1780-renamed-run-6197  DESCRIPTION.md
hacker@commands~listing-files:~$
```
Now we know that the absolute path of the required file is `/challenge/1780-renamed-run-6197`
```
hacker@commands~listing-files:~$ /challenge/1780-renamed-run-6197
Yahaha, you found me! Here is your flag:
pwn.college{QoJgXb33NfkodTajV4Wm0WqMBYK.dhjM4QDL5gDO0czW}
hacker@commands~listing-files:~$
```

Here we are rewarded with the flag `pwn.college{QoJgXb33NfkodTajV4Wm0WqMBYK.dhjM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## touching files
We can create a new, blank file by _touching_ it with the `touch` command.
In this challenge, we need to create two files, `/tmp/pwn` and `/tmp/college`, and run `/challenge/run` to get the flag:
```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{g_IYFI3eFzQPrg9YKcubDFSoif1.dBzM4QDL5gDO0czW}
hacker@commands~touching-files:~$
```

Here we are rewarded with the flag `pwn.college{g_IYFI3eFzQPrg9YKcubDFSoif1.dBzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## removing files
To clean up, we can remove files by the command `rm`.

Here, a `delete_me` file has been created in our home directory. To obtain the flag, we need to remove this file and run `/challenge/check`:
```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{gbiddWOFrkjSePbLEhpb4cQtHXn.dZTOwUDL5gDO0czW}
hacker@commands~removing-files:~$
```

Here we are rewarded with the flag `pwn.college{gbiddWOFrkjSePbLEhpb4cQtHXn.dZTOwUDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## hidden files
There is a convention that files that start with a `.` don't show up by default in `ls` 

To view them with `ls`, we need to invoke it with the `-a` flag.

Here, it is given that our flag is hidden as a dot-prepended file in the root directory `/`.
```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-25687381125059  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
```
Now that we know that our flag is in `.flag-25687381125059`, we just need to cat it out:
```
hacker@commands~hidden-files:/$ cat .flag-25687381125059
pwn.college{gvUujNHlEP0IR21HTxy94PBspf-.dBTN4QDL5gDO0czW}
hacker@commands~hidden-files:/$
```

Here we are rewarded with the flag `pwn.college{gvUujNHlEP0IR21HTxy94PBspf-.dBTN4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## An Epic Filesystem Quest
In this challenge, we need to play and complete a game using `ls`, `cd`, and `cat` commands, with the help of hints given at each level.

We start by `cd`ing into the root directory `/`, and find `HINT` using the `ls` command, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
HINT  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin   challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat HINT
Great sleuthing!
The next clue is in: /opt/aflplusplus/qemu_mode/qemuafl/include/fpu

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
Since the next clue is _trapped_, we will now directly `ls` the contents of the path given to find `TEASER-TRAPPED`, which we then `cat`out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/aflplusplus/qemu_mode/qemuafl/include/fpu
TEASER-TRAPPED  softfloat-helpers.h  softfloat-macros.h  softfloat-types.h  softfloat.h
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/aflplusplus/qemu_mode/qemuafl/include/fpu/TEASER-TRAPPED
Lucky listing!
The next clue is in: /usr/share/doc/binutils-aarch64-linux-gnu
```
We now `cd` into `/usr/share/doc/binutils-aarch64-linux-gnu`, and use `ls` command to find `DISPATCH`, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/doc/binutils-aarch64-linux-gnu
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ ls
DISPATCH  README.cross  bfd  changelog.Debian.gz  copyright  gas  gprof  ld  test-summary.gz
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cat DISPATCH
Yahaha, you found me!
The next clue is in: /usr/share/javascript/mathjax/unpacked/localization/qqq

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
Since the next clue is _trapped_, we will now directly `ls` the contents of the path given to find `MEMO-TRAPPED`, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ ls /usr/share/javascript/mathjax/unpacked/localization/qqq
FontWarnings.js  HTML-CSS.js  HelpDialog.js  MEMO-TRAPPED  MathML.js  MathMenu.js  TeX.js  qqq.js
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cat /usr/share/javascript/mathjax/unpacked/localization/qqq/MEMO-TRAPPED
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/itsdangerous-1.1.0.egg-info

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
Since the next clue is _trapped_, we will now directly `ls` the contents of the path given to find `README-TRAPPED`, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ ls /usr/lib/python3/dist-packages/itsdangerous-1.1.0.egg-info
PKG-INFO  README-TRAPPED  dependency_links.txt  top_level.txt
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cat /usr/lib/python3/dist-packages/itsdangerous-1.1.0.egg-info/README-TRAPPED
Yahaha, you found me!
The next clue is in: /usr/lib/python3/dist-packages/sage/geometry/polyhedron/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
```
Since the next clue is _hidden_, we need to pass `-a` argument to the `ls` command, to find the hidden clue `.DOSSIER`, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ ls -a /usr/lib/python3/dist-packages/sage/geometry/polyhedron/__pycache__
.                                base.cpython-38.pyc                              library.cpython-38.pyc
..                               base_QQ.cpython-38.pyc                           misc.cpython-38.pyc
.DOSSIER                         base_RDF.cpython-38.pyc                          palp_database.cpython-38.pyc
__init__.cpython-38.pyc          base_ZZ.cpython-38.pyc                           parent.cpython-38.pyc
all.cpython-38.pyc               cdd_file_format.cpython-38.pyc                   plot.cpython-38.pyc
backend_cdd.cpython-38.pyc       constructor.cpython-38.pyc                       ppl_lattice_polygon.cpython-38.pyc
backend_field.cpython-38.pyc     double_description.cpython-38.pyc                ppl_lattice_polytope.cpython-38.pyc
backend_normaliz.cpython-38.pyc  double_description_inhomogeneous.cpython-38.pyc  representation.cpython-38.pyc
backend_polymake.cpython-38.pyc  face.cpython-38.pyc
backend_ppl.cpython-38.pyc       lattice_euclidean_group_element.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cat /usr/lib/python3/dist-packages/sage/geometry/polyhedron/__pycache__/.DOSSIER
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/prompt_toolkit/contrib/completers

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```
Since the next clue is _trapped_, we will now directly `ls` the contents of the path given to find `BLUEPRINT-TRAPPED`, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ ls /usr/lib/python3/dist-packages/prompt_toolkit/contrib/completers
BLUEPRINT-TRAPPED  __init__.py  __pycache__  system.py
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cat /usr/lib/python3/dist-packages/prompt_toolkit/contrib/completers/BLUEPRINT-TRAPPED
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/bcma
```
Thus, we now `ls` the contents of `/opt/linux/linux-5.4/drivers/bcma` to find `REVELATION`, which we then `cat` out to get the next clue:
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ ls /opt/linux/linux-5.4/drivers/bcma
Kconfig     bcma_private.h              driver_chipcommon_pflash.c  driver_mips.c      host_soc.c
Makefile    core.c                      driver_chipcommon_pmu.c     driver_pci.c       main.c
README      driver_chipcommon.c         driver_chipcommon_sflash.c  driver_pci_host.c  scan.c
REVELATION  driver_chipcommon_b.c       driver_gmac_cmn.c           driver_pcie2.c     scan.h
TODO        driver_chipcommon_nflash.c  driver_gpio.c               host_pci.c         sprom.c
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cat /opt/linux/linux-5.4/drivers/bcma/REVELATION
Lucky listing!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Asana-Math/Size3

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```
Since the next clue is _delayed_, we cannot directly `ls` the contents of the path given. 

We first need to `cd` into it, then use `ls` command to find `POINTER`, which we then `cat` out to finally finish the game and get the flag.
```
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/binutils-aarch64-linux-gnu$ cd /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Asana-Math/Size3
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Asana-Math/Size3$ ls
POINTER  Regular
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Asana-Math/Size3$ cat POINTER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{0IJ2ZPwoNZbTjREJJ9_8xGK5jvH.dljM4QDL5gDO0czW}
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Asana-Math/Size3$
```

Here we are rewarded with the flag `pwn.college{0IJ2ZPwoNZbTjREJJ9_8xGK5jvH.dljM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## making directories
We can make directories using the `mkdir` command.

Here, we need to create a `/tmp/pwn` directory and make a `college` file in it.
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{c2uatGIm5redgskIgcIkv-ZbK9q.dFzM4QDL5gDO0czW}
hacker@commands~making-directories:~$
```

Here we are rewarded with the flag `pwn.college{c2uatGIm5redgskIgcIkv-ZbK9q.dFzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## finding files
The `find` command takes arguments describing the search criteria and the search location.

>[!NOTE]
>If we don't specify a search criteria, `find` matches every file, while if we don't specify a search location, it uses the `cwd`.

Here, our flag, named `flag` has been hidden in a random directory.
```
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.G9qthVCks5’: Permission denied
/usr/local/share/radare2/5.9.5/flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/opt/radare2/shlr/capstone/.git/refs/tags/flag
/opt/radare2/libr/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$
```

Ignoring the inaccesible (`Permission Denied`) file systems, we start checking for our flag:
```
hacker@commands~finding-files:~$ cat /usr/local/share/radare2/5.9.5/flag
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
```
We do this until we finally get our flag:
```
hacker@commands~finding-files:~$ cat /opt/radare2/shlr/capstone/.git/refs/tags/flag
pwn.college{oqfK2d7be6gZhpev7lVcRFL39gy.dJzM4QDL5gDO0czW}
hacker@commands~finding-files:~$
```
Thus, we `find` our flag in the `/opt/radare2/shlr/capstone/.git/refs/tags/flag` directory

Here we are rewarded with the flag `pwn.college{oqfK2d7be6gZhpev7lVcRFL39gy.dJzM4QDL5gDO0czW}`, upon submitting of which, the challenge is completed.

## linking files
A file is an address at which the contents of that file live. 

A `hard link` is an alternate address that indexes that data, thus they immediately yield the necessary data. 

A `soft/symbolic link`, instead, contains the original file name. When we access the symbolic link, Linux reads the original file name, and then automatically accesses that file.

> Soft links are also known as symlinks.

Symbolic links are created with `ln` as command and with `-s` as argument


>[!NOTE]
>The `file` command recognises symlinks.

Here, we need to link `/home/hacker/not-the-flag` to `/flag` so that executing `/challenge/catflag` will get us the flag stored in `/flag`:
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{gqB_S2JdM0hl0b6Y7uswvXsX859.dlTM1UDL5gDO0czW}
hacker@commands~linking-files:~$
```
>[!CAUTION]
>The original file path comes before the link path in this command.

Here we are rewarded with the flag `pwn.college{gqB_S2JdM0hl0b6Y7uswvXsX859.dlTM1UDL5gDO0czW}`, upon submitting of which, the challenge is completed.
