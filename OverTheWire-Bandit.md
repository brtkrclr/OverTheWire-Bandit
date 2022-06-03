# OverTheWire
Hi! In this paper you can find out the solutions of OverTheWire-Bandit Game! Enjoy it and push your limits!


## Bandit Level 0 → 1 Solution
Let's open a terminal.The goal of this level is for you to log into the game using **SSH**. The host to which you need to connect is **bandit.labs.overthewire.org**, on **port 2220**. The **username is bandit0** and the **password is bandit0**. Once logged in, go to the Level 1 page to find out how to beat Level 1.

```console
ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit:~$ 
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme 
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
here is the password for the next level. 

---------------------------------------------------------------------



## Bandit Level 1 → 2 Solution
Let's open a terminal. The password for the next level is stored in a file called - **located in the home directory**

#### Helpful Reading Material

    Google Search for “dashed filename”
    Advanced Bash-scripting Guide - Chapter 3 - Special Characters


```console
ssh bandit1@bandit.labs.overthewire.org -p 2220
bandit0@bandit:~$ 
bandit0@bandit:~$ ls
-
bandit0@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

bandit0@bandit:~$ cat < -
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
As you can see you can not use cat command directly to the '-'. There are several ways to print it. You can see two of them. cat ./- basically tells that print the file under the current directory. cat < - does the same thing but by using stdin (**look for stdin,stdout,std,stderr**) here is our password for the next level. 

----------------------------------------------------------

## Bandit Level 2 → 3 Solution
Let's open a terminal. The password for the next level is stored in a file called spaces in this filename located in the home directory

#### Helpful Reading Material

    Google Search for “spaces in filename”


```console
ssh bandit2@bandit.labs.overthewire.org -p 2220
bandit2@bandit:~$ ls
spaces in this filename

bandit2@bandit:~$ cat spaces\ in\ this\ filename 
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
We have a file which inluced spaces, in order to cat it you can either type "cat" and press "TAB" button to complete the file or as you can see type like this.

--------------------------------------------------------

## Bandit Level 3 → 4 Solution
Let's open a terminal. The password for the next level is stored in a hidden file in the inhere directory.

```console
ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -all
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
bandit3@bandit:~/inhere$ cat .hidden 
pIwrPrtPN36QITSp3EQaw936yaFoFgAB


```
Firstly I tried to list "inhere" directory but as you can see it didn't give any results. So I though there might be a hidden file. In Linux and Unix systems, the files starting with . (a dot) are hidden files.

-------------------------------------------------------------

## Bandit Level 4 → 5 Solution
Let's open a terminal. The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

```console
ssh bandit4@bandit.labs.overthewire.org -p 2220
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ cat ./-file00
�/`2ғ�%��rL~5�g��� �����
bandit4@bandit:~/inhere$ file ./-file0*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh



```
Inside of the directory there are couple of files. I tried to see what is inside but as you can see it is not a text that I can read. Instead of trying one by one I used "file" command to see their types. -file0* means inclued all starting with -file0 (as you know start means all). And here we go, -file07 has ASCII text, which is the password for the next level.

------------------------------------------------------------------

## Bandit Level 5 → 6 Solution
Let's open a terminal. The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

```console
ssh bandit5@bandit.labs.overthewire.org -p 2220
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ cd maybehere00/
bandit5@bandit:~/inhere/maybehere00$ ls
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3

```
At firt I was thinking to check each directory and print each files. But it was saying **human-readable, 1033 bytes in size and not executable**. Hmm with these hint I thought I might use "find" command. I read "man" file at first to see which commands I can use. For the size I can use "find -size xx c" , for readable "find -readable", Let's try with these informations.

```console
bandit5@bandit:~/inhere$ find -readable -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2 
DXjZPULLxYr17uwoI01bNLQbtFemEgo7

```

--------------------------------------------------------------------

## Bandit Level 6 → 7 Solution
Let's open a terminal. The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size


```console
ssh bandit6@bandit.labs.overthewire.org -p 2220
bandit6@bandit:~$ ls

```
At firt I was thinking to check each directory and print each files. But it was saying **user bandit7, group bandit6, 33 bytes in size**. Like I did in level 5 I checked "man" file of "find" command. It has "user", "group" properties as well. It gave me nothing, which means under this directory you can not find any values related with these properties. I tried upper directory and got something.

```console
bandit6@bandit:~$ find  -user bandit7 -group bandit6 -size 33c 
bandit6@bandit:~$ 
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 
find: ‘/root’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit31-git’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/etc/lvm/archive’: Permission denied
find: ‘/etc/lvm/backup’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/26531/task/26531/fd/6’: No such file or directory
find: ‘/proc/26531/task/26531/fdinfo/6’: No such file or directory
find: ‘/proc/26531/fd/5’: No such file or directory
find: ‘/proc/26531/fdinfo/5’: No such file or directory
find: ‘/cgroup2/csessions’: Permission denied
find: ‘/boot/lost+found’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/screen/S-bandit11’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/screen/S-bandit13’: Permission denied
find: ‘/run/screen/S-bandit0’: Permission denied
find: ‘/run/screen/S-bandit29’: Permission denied
find: ‘/run/screen/S-bandit1’: Permission denied
find: ‘/run/screen/S-bandit10’: Permission denied
find: ‘/run/screen/S-bandit25’: Permission denied
find: ‘/run/screen/S-bandit30’: Permission denied
find: ‘/run/screen/S-bandit9’: Permission denied
find: ‘/run/screen/S-bandit28’: Permission denied
find: ‘/run/screen/S-bandit18’: Permission denied
find: ‘/run/screen/S-bandit5’: Permission denied
find: ‘/run/screen/S-bandit7’: Permission denied
find: ‘/run/screen/S-bandit16’: Permission denied
find: ‘/run/screen/S-bandit26’: Permission denied
find: ‘/run/screen/S-bandit8’: Permission denied
find: ‘/run/screen/S-bandit15’: Permission denied
find: ‘/run/screen/S-bandit4’: Permission denied
find: ‘/run/screen/S-bandit3’: Permission denied
find: ‘/run/screen/S-bandit19’: Permission denied
find: ‘/run/screen/S-bandit31’: Permission denied
find: ‘/run/screen/S-bandit17’: Permission denied
find: ‘/run/screen/S-bandit2’: Permission denied
find: ‘/run/screen/S-bandit22’: Permission denied
find: ‘/run/screen/S-bandit21’: Permission denied
find: ‘/run/screen/S-bandit14’: Permission denied
find: ‘/run/screen/S-bandit24’: Permission denied
find: ‘/run/screen/S-bandit23’: Permission denied
find: ‘/run/shm’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/tmp’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/log’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied

bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs


```
------------------------------------------------------------------

## Bandit Level 7 → 8 Solution
Let's open a terminal. The password for the next level is stored in the file data.txt next to the word millionth


```console
ssh bandit7@bandit.labs.overthewire.org -p 2220
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ cat data.txt | grep millionth
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV


```
It was an easy one if you know how to use |  (pipe). A pipe is a form of redirection (transfer of standard output to some other destination) that is used in Linux and other Unix-like operating systems to send the output of one command/program/process to another command/program/process for further processing. As you can see from the command, I gave the output of  "cat" command (which is print), to grep which means find.

------------------------------------------------------------------

## Bandit Level 8 → 9 Solution
Let's open a terminal. The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

```console
ssh bandit8@bandit.labs.overthewire.org -p 2220
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ cat data.txt | sort | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR


```
It was an easy one as well, you just need to sort it and find the only line of text that occurs only once which is **unique**. Basically you need to use **cat, sort and uniq** command. For further informations please check the man files.

------------------------------------------------------------------

## Bandit Level 9 → 10 Solution
Let's open a terminal. The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

```console
bandit9@bandit:~$ cat data.txt 
�L�lω;��ßOܛ��ǤX��NdT$��x7��@D@�o��+D��B��M֢�Z/,_��w��#�5���
                                                          Ў�e�&�-��Ϣ�6Q8��J�%fa�
�np�6l
|c���WW"&8��f��
��VJ�$�S~����d�
               �p�k�U�;ֿ�v�Am��H��tɘ�3�ߘ�(ǟ�E'
                                             ���'��:��uP�ע��������g�
!�'�


```
In this part I used **strings** command to see the strings and also used **grep** because it preceded by several "=" characters. 

```console
bandit9@bandit:~$ strings data.txt | grep ==
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

```


------------------------------------------------------------------

## Bandit Level 10 → 11 Solution
Let's open a terminal. The password for the next level is stored in the file data.txt, which contains base64 encoded data

Helpful Reading Material

    Base64 on Wikipedia


```console
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==
bandit10@bandit:~$ cat data.txt  | base64 -d
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

```
In this part I used **base64** command to see the decrypted version of the ciphertext.



------------------------------------------------------------------

## Bandit Level 11 → 12 Solution
Let's open a terminal. The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
Helpful Reading Material

    Rot13 on Wikipedia


```console
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

```
You can either use online ROT13 decoder or as I did use **tr** command (translate) to decode. ROT13 is a simple letter substitution cipher that replaces a letter with the 13th letter after it in the alphabet


------------------------------------------------------------------




