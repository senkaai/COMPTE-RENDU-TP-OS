# II. Ptits challenges de cracking

## 1. Install Ghidra

🌞 **Avec une commande `apt search`, déterminez si le paquet `ghidra` est disponible**

```
senkai@TPOS:~/work$ apt search ghidra
Sorting... Done
Full Text Search... Done
```

🌞 **Ajouter l'URL des dépôts Kali à vos dépôts existants**

```
senkai@TPOS:~/work$ sudo nano /etc/apt/sources.list
```

🌞 **Ajoutez la clé publique des gars de chez Kali**

```
senkai@TPOS:~/work$ sudo wget https://archive.kali.org/archive-key.asc -O /etc/apt/trusted.gpg.d/kali-archive-keyring.asc
--2024-11-20 08:57:13--  https://archive.kali.org/archive-key.asc
Resolving archive.kali.org (archive.kali.org)... 192.99.45.140, 2607:5300:60:508c::
Connecting to archive.kali.org (archive.kali.org)|192.99.45.140|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3155 (3.1K) [application/octet-stream]
Saving to: ‘/etc/apt/trusted.gpg.d/kali-archive-keyring.asc’

/etc/apt/trusted.gpg.d/kali-a 100%[=================================================>]   3.08K  --.-KB/s    in 0s

2024-11-20 08:57:13 (55.4 MB/s) - ‘/etc/apt/trusted.gpg.d/kali-archive-keyring.asc’ saved [3155/3155]
```

🌞 **Mettez à jour la liste des dépôts que votre OS connaît actuellement**

```
senkai@TPOS:~/work$ sudo apt update -y
Get:1 http://security.debian.org/debian-security bookworm-security InRelease [48.0 kB]
Hit:2 http://deb.debian.org/debian bookworm InRelease
Get:3 http://deb.debian.org/debian bookworm-updates InRelease [55.4 kB]
Get:5 http://security.debian.org/debian-security bookworm-security/main Sources [126 kB]
Get:6 http://security.debian.org/debian-security bookworm-security/main amd64 Packages [204 kB]
Get:7 http://security.debian.org/debian-security bookworm-security/main Translation-en [125 kB]
Get:4 http://kali.download/kali kali-rolling InRelease [41.5 kB]
Get:8 http://kali.download/kali kali-rolling/main amd64 Packages [20.3 MB]
Get:9 http://kali.download/kali kali-rolling/contrib amd64 Packages [112 kB]
Get:10 http://kali.download/kali kali-rolling/non-free amd64 Packages [197 kB]
Get:11 http://kali.download/kali kali-rolling/non-free-firmware amd64 Packages [10.6 kB]
Fetched 21.2 MB in 7s (3,061 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1239 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

🌞 **Avec une commande `apt search`, déterminez si le paquet `ghidra` est disponible**

```
senkai@TPOS:~/work$ apt search ghidra
Sorting... Done
Full Text Search... Done
ghidra/kali-rolling 11.0+ds-0kali1 amd64
  Software Reverse Engineering Framework

ghidra-data/kali-rolling 10.5-0kali1 all
  FID databases for Ghidra

ghidra-dbgsym/kali-rolling 11.0+ds-0kali1 amd64
  debug symbols for ghidra

quark-engine/kali-rolling 23.9.1-0kali2 all
  Android Malware (Analysis | Scoring System)

rz-ghidra/kali-rolling 0.7.0-0kali1+b1 amd64
  ghidra decompiler and sleigh disassembler for rizin

rz-ghidra-dbgsym/kali-rolling 0.7.0-0kali1+b1 amd64
  debug symbols for rz-ghidra
```

🌞 **Installez le paquet `ghidra`**

```
senkai@TPOS:~/work$ sudo apt install ghidra
```

## 2. Patch manuel programme simple

```
senkai@TPOS:~/work$ wget https://gitlab.com/it4lik/b1-os/-/raw/main/cours/cracking/code_demo/password_2.c
senkai@TPOS:~/work$ gcc -o password_2 password_2.c -lssl -lcrypto -Wno-deprecated-declarations
senkai@TPOS:~/work$ ghidra

JNZ à JZ :
        
                     LAB_0010127d                                    XREF[1]:     0010124f(j)  
        0010127d 48 8b 45 e0     MOV        RAX,qword ptr [RBP + local_28]
        00101281 48 83 c0 08     ADD        RAX,0x8
        00101285 48 8b 00        MOV        RAX,qword ptr [RAX]
        00101288 48 8d 55 f0     LEA        RDX=>local_18,[RBP + -0x10]
        0010128c 48 89 d6        MOV        RSI,RDX
        0010128f 48 89 c7        MOV        RDI,RAX
        00101292 e8 51 ff        CALL       compute_md5                                      undefined compute_md5()
                 ff ff
        00101297 48 8d 45 f0     LEA        RAX=>local_18,[RBP + -0x10]
        0010129b ba 10 00        MOV        EDX,0x10
                 00 00
        001012a0 48 8d 0d        LEA        RCX,[correct_hash]
                 69 0d 00 00
        001012a7 48 89 ce        MOV        RSI=>correct_hash,RCX
        001012aa 48 89 c7        MOV        RDI,RAX
        001012ad e8 8e fd        CALL       <EXTERNAL>::memcmp                               int memcmp(void * __s1, void * _
                 ff ff
        001012b2 85 c0           TEST       EAX,EAX
        001012b4 74 0c           JZ         LAB_001012c2
        001012b6 b8 00 00        MOV        EAX,0x0
                 00 00
        001012bb e8 f9 fe        CALL       spawn_shell                                      undefined spawn_shell()
                 ff ff
        001012c0 eb 23           JMP        LAB_001012e5
```
```
senkai@TPOS:~$ ls -l
total 35256
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Desktop
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Documents
drwxr-xr-x 2 senkai senkai     4096 Nov 10 12:49 Downloads
drwxr-xr-x 2 senkai senkai     4096 Nov  7 11:30 gameshell
-rw-r--r-- 1 senkai senkai 18016044 Jan 21  2024 meow
-rw-r--r-- 1 senkai senkai 18016947 Nov 10 12:40 meow.zip
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Music
-rw-r----- 1 senkai senkai    16536 Nov 20 10:49 password_2.1
-rw-r----- 1 senkai senkai        0 Nov 20 10:11 PASSWORD.gpr
drwxr-x--- 5 senkai senkai     4096 Nov 20 10:12 PASSWORD.rep
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Pictures
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Public
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Templates
drwxr-xr-x 2 senkai senkai     4096 Nov  6 12:29 Videos
drwxr-xr-x 3 senkai senkai     4096 Nov 20 10:19 work
senkai@TPOS:~$ chmod 755 password_2.1
senkai@TPOS:~$ ./password_2.1 1
Access granted! Spawning shell...
```
## 3. Root-me

```
senkai@TPOS:~/ch1$ ./ch1.bin
############################################################
##        Bienvennue dans ce challenge de cracking        ##
############################################################

Veuillez entrer le mot de passe : 123456789
Bien joue, vous pouvez valider l'epreuve avec le pass : 123456789!
```

```
senkai@TPOS:~/ch2$ ./ch2.bin
############################################################
##        Bienvennue dans ce challenge de cracking        ##
############################################################

username: john
password: the ripper
Bien joue, vous pouvez valider l'epreuve avec le mot de passe : 987654321 !
```

## 4. Ptit chall maison

> Hint : ce challenge repose sur l'exploitation d'un *int overflow*.

🌞 **Récupérer le flag du programme [`kaddate_challenge`](./kaddate_challenge)**

```
senkai@senkai:~$ sudo wget https://gitlab.com/it4lik/b1-os/-/raw/main/tp/5/kaddate_challenge
senkai@senkai:~$ ./kaddate_challenge
Can you be the first to send us a Message ?
Enter you message:
hehe
Sorry hehe , you are not the first user (count=5). No flag for you.

```

```
0x5 en 0x0
        00101306 48 89 45 f8     MOV        qword ptr [RBP + local_10],RAX
        0010130a 31 c0           XOR        EAX,EAX
        0010130c 48 8d 05        LEA        RAX,[s_Can_you_be_the_first_to_send_us_a_00102   = "Can you be the first to send 
                 1d 0d 00 00
        00101313 48 89 c7        MOV        RDI=>s_Can_you_be_the_first_to_send_us_a_00102   = "Can you be the first to send 
        00101316 e8 85 fd        CALL       <EXTERNAL>::puts                                 int puts(char * __s)
                 ff ff
        0010131b c6 45 cf 00     MOV        byte ptr [RBP + -0x31],0x0
                             LAB_0010131f                                    XREF[1]:     00101406(j)  
        0010131f 48 8d 05        LEA        RAX,[s_Enter_you_message:_0010205c]              = "Enter you message: "
                 36 0d 00 00
        00101326 48 89 c7        MOV        RDI=>s_Enter_you_message:_0010205c,RAX           = "Enter you message: "
        00101329 e8 72 fd        CALL       <EXTERNAL>::puts                                 int puts(char * __s)
                 ff ff

```

```
senkai@senkai:~$ chmod 755 kaddate_challenge
senkai@senkai:~$ ./kaddate_challenge
Can you be the first to send us a Message ?
Enter you message:
hehe
Congrats hehe, you are the first user (count=0).
Flag: b1-os{PetitB1deviendraGrandPetitB1}
```