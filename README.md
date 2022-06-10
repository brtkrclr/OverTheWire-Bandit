# OverTheWire
Hi! In this paper you can find out the solutions of OverTheWire Game! Enjoy it and push your limits!


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

## Bandit Level 12 → 13 Solution
Let's open a terminal. The password for the next level is stored in the file data.txt, which is a **hexdump of a file that has been repeatedly compressed**. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

    Hex dump on Wikipedia


```console
bandit12@bandit:~$ cat data.txt 
00000000: 1f8b 0808 0650 b45e 0203 6461 7461 322e  .....P.^..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
00000020: 2653 598e 4f1c c800 001e 7fff fbf9 7fda  &SY.O...........
00000030: 9e7f 4f76 9fcf fe7d 3fff f67d abde 5e9f  ..Ov...}?..}..^.
00000040: f3fe 9fbf f6f1 feee bfdf a3ff b001 3b1b  ..............;.
00000050: 5481 a1a0 1ea0 1a34 d0d0 001a 68d3 4683  T......4....h.F.
00000060: 4680 0680 0034 1918 4c4d 190c 4000 0001  F....4..LM..@...
00000070: a000 c87a 81a3 464d a8d3 43c5 1068 0346  ...z..FM..C..h.F
00000080: 8343 40d0 3400 0340 66a6 8068 0cd4 f500  .C@.4..@f..h....
00000090: 69ea 6800 0f50 68f2 4d00 680d 06ca 0190  i.h..Ph.M.h.....
000000a0: 0000 69a1 a1a0 1ea0 194d 340d 1ea1 b280  ..i......M4.....
000000b0: f500 3406 2340 034d 3400 0000 3403 d400  ..4.#@.M4...4...
000000c0: 1a07 a832 3400 f51a 0003 43d4 0068 0d34  ...24.....C..h.4
000000d0: 6868 f51a 3d43 2580 3e58 061a 2c89 6bf3  hh..=C%.>X..,.k.
000000e0: 0163 08ab dc31 91cd 1747 599b e401 0b06  .c...1...GY.....
000000f0: a8b1 7255 a3b2 9cf9 75cc f106 941b 347a  ..rU....u.....4z
00000100: d616 55cc 2ef2 9d46 e7d1 3050 b5fb 76eb  ..U....F..0P..v.
00000110: 01f8 60c1 2201 33f0 0de0 4aa6 ec8c 914f  ..`.".3...J....O
00000120: cf8a aed5 7b52 4270 8d51 6978 c159 8b5a  ....{RBp.Qix.Y.Z
00000130: 2164 fb1f c26a 8d28 b414 e690 bfdd b3e1  !d...j.(........
00000140: f414 2f9e d041 c523 b641 ac08 0c0b 06f5  ../..A.#.A......
00000150: dd64 b862 1158 3f9e 897a 8cae 32b0 1fb7  .d.b.X?..z..2...
00000160: 3c82 af41 20fd 6e7d 0a35 2833 41bd de0c  <..A .n}.5(3A...
00000170: 774f ae52 a1ac 0fb2 8c36 ef58 537b f30a  wO.R.....6.XS{..
00000180: 1510 cab5 cb51 4231 95a4 d045 b95c ea09  .....QB1...E.\..
00000190: 9fa0 4d33 ba43 22c9 b5be d0ea eeb7 ec85  ..M3.C".........
000001a0: 59fc 8bf1 97a0 87a5 0df0 7acd d555 fc11  Y.........z..U..
000001b0: 223f fdc6 2be3 e809 c974 271a 920e acbc  "?..+....t'.....
000001c0: 0de1 f1a6 393f 4cf5 50eb 7942 86c3 3d7a  ....9?L.P.yB..=z
000001d0: fe6d 173f a84c bb4e 742a fc37 7b71 508a  .m.?.L.Nt*.7{qP.
000001e0: a2cc 9cf1 2522 8a77 39f2 716d 34f9 8620  ....%".w9.qm4.. 
000001f0: 4e33 ca36 eec0 cd4b b3e8 48e4 8b91 5bea  N3.6...K..H...[.
00000200: 01bf 7d21 0b64 82c0 3341 3424 e98b 4d7e  ..}!.d..3A4$..M~
00000210: c95c 1b1f cac9 a04a 1988 43b2 6b55 c6a6  .\.....J..C.kU..
00000220: 075c 1eb4 8ecf 5cdf 4653 064e 84da 263d  .\....\.FS.N..&=
00000230: b15b bcea 7109 5c29 c524 3afc d715 4894  .[..q.\).$:...H.
00000240: 7426 072f fc28 ab05 9603 b3fc 5dc9 14e1  t&./.(......]...
00000250: 4242 393c 7320 98f7 681d 3d02 0000       BB9<s ..h.=...

```
There is a magic number at the beginning of the file. Just read the first two bytes and check if they are equal to **0x1f8b**, it means it is a gzip file. I firstly reversed the hexdump by using **xxd -r** command and stdout by using **>** (SomeCommand > SomeFile.txt)

```console
bandit12@bandit:/tmp$ mkdir bandit
bandit12@bandit:/tmp$ cd bandit
bandit12@bandit:/tmp/bandit$ cp ~/data.txt .
bandit12@bandit:/tmp/bandit$ xxd -r data.txt > test
bandit12@bandit:/tmp/bandit$ ls
data.txt  test
bandit12@bandit:/tmp/bandit$ file test 
test: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/bandit$ mv test t.gz
bandit12@bandit:/tmp/bandit$ gzip -d t.gz 
bandit12@bandit:/tmp/bandit$ file t 
t: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/bandit$ gzip -d t.gz 
bandit12@bandit:/tmp/bandit$ file t 
t: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/bandit$ mv t b.bz
bandit12@bandit:/tmp/bandit$ ls
b.bz  data.txt
bandit12@bandit:/tmp/bandit$ bzip2 -d b.bz
bandit12@bandit:/tmp/bandit$ ls
b  data.txt
bandit12@bandit:/tmp/bandit$ file b
b: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/bandit$ mv b b.gz
bandit12@bandit:/tmp/bandit$ gzip -d b.gz 
bandit12@bandit:/tmp/bandit$ ls
b  data.txt
bandit12@bandit:/tmp/bandit$ file b
b: POSIX tar archive (GNU)
bandit12@bandit:/tmp/bandit$ mv b b.tar
bandit12@bandit:/tmp/bandit$ tar -xvf b.tar 
data5.bin
bandit12@bandit:/tmp/bandit$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/bandit$ mv data5.bin 
b.tar      data5.bin  data.txt   
bandit12@bandit:/tmp/bandit$ mv data5.bin m.tar
bandit12@bandit:/tmp/bandit$ tar -xvf m.tar 
data6.bin
bandit12@bandit:/tmp/bandit$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/bandit$ mv data6.bin n.bz
bandit12@bandit:/tmp/bandit$ bzip2 -d n.bz
bandit12@bandit:/tmp/bandit$ ls
b.tar  data.txt  m.tar  n
bandit12@bandit:/tmp/bandit$ file n
n: POSIX tar archive (GNU)
bandit12@bandit:/tmp/bandit$ mv n n.tar
bandit12@bandit:/tmp/bandit$ tar -xvf n.tar 
data8.bin
bandit12@bandit:/tmp/bandit$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/bandit$ mv data8.bin l.gz
bandit12@bandit:/tmp/bandit$ gzip -d l.gz 
bandit12@bandit:/tmp/bandit$ ls
b.tar  data.txt  l  m.tar  n.tar
bandit12@bandit:/tmp/bandit$ file l
l: ASCII text
bandit12@bandit:/tmp/bandit$ cat l 
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL


```
Such a horrible part! In this chapter I used ***mkdir, file, tar, mv, cp, gzip, bzip2 *** comments.

----------------------------------------------------------------------

## Bandit Level 13 → 14 Solution
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

Helpful Reading Material

    SSH/OpenSSH/Keys

```console
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes

```
In the main directory there is a file named as ***sshkey.private***. By using ***secureshell (SSH)*** and the private key you can connect the next level's server. 

----------------------------------------------------------------------

## Bandit Level 14 → 15 Solution
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Helpful Reading Material

    How the Internet works in 5 minutes (YouTube) (Not completely accurate, but good enough for beginners)
    IP Addresses
    IP Address on Wikipedia
    Localhost on Wikipedia
    Ports
    Port (computer networking) on Wikipedia

```console
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
bandit14@bandit:~$ netcat localhost 30000
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr


```
Password of the current level is under the directory of /etc/bandit_pass/bandit14. When we get the password it is time to submit it to localhost:3000. By using ***netcat*** I got the password of the next level. 

----------------------------------------------------------------------
