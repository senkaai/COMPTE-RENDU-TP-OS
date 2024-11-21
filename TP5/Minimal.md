# 0. Prérequis

🌞 **Créer un répertoire de travail dans votre répertoire personnel**

```
cd ~
pwd
mkdir work
cd work
```

# I. Programme minimal

## 1. Compilation

➜ **Créer fichier nommé `hello1.c` avec le contenu suivant :**

```
senkai@TPOS:~/work$ nano hello1.c
```

```
  GNU nano 7.2                                            hello1.c *
void _start() {
    const char message[] = "Hello, World!\n";
    asm volatile (
        "mov $4, %%eax\n\t"          // Syscall number for write (4 in 32-bit)
        "mov $1, %%ebx\n\t"          // File descriptor 1 (stdout)
        "mov %[msg], %%ecx\n\t"      // Pointer to the message
        "mov %[len], %%edx\n\t"      // Length of the message
        "int $0x80"                  // Make the syscall (32-bit interrupt)
        :
        : [msg] "r" (message), [len] "r" (14)
        : "eax", "ebx", "ecx", "edx"
    );

    asm volatile (
        "mov $1, %%eax\n\t"          // Syscall number for exit (1 in 32-bit)
        "xor %%ebx, %%ebx\n\t"       // Exit code 0
        "int $0x80"                  // Make the syscall
        :
        :
        : "eax", "ebx"
    );
}
```

## 2. Analyse du programme compilé

> *Référez-vous au [mémo des commandes autour des programmes](../../cours/memo/program.md) pour les commandes de cette partie.*

🌞 **Retrouvez à l'aide de `readelf` l'architecture pour laquelle le programme est compilé**
```
senkai@TPOS:~/work$ readelf -h hello1
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Position-Independent Executable file)
  Machine:                           Intel 80386
  Version:                           0x1
  Entry point address:               0x1000
  Start of program headers:          52 (bytes into file)
  Start of section headers:          13308 (bytes into file)
  Flags:                             0x0
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         11
  Size of section headers:           40 (bytes)
  Number of section headers:         21
  Section header string table index: 20
  ```
🌞 **Afficher la liste des *sections* contenues dans le *programme***

```
senkai@TPOS:~/work$ readelf -S hello1
There are 21 section headers, starting at offset 0x33fc:

Section Headers:
  [Nr] Name              Type            Addr     Off    Size   ES Flg Lk Inf Al
  [ 0]                   NULL            00000000 000000 000000 00      0   0  0
  [ 1] .interp           PROGBITS        00000194 000194 000013 00   A  0   0  1
  [ 2] .note.gnu.bu[...] NOTE            000001a8 0001a8 000024 00   A  0   0  4
  [ 3] .gnu.hash         GNU_HASH        000001cc 0001cc 000018 04   A  4   0  4
  [ 4] .dynsym           DYNSYM          000001e4 0001e4 000010 10   A  5   1  4
  [ 5] .dynstr           STRTAB          000001f4 0001f4 000001 00   A  0   0  1
  [ 6] .text             PROGBITS        00001000 001000 00005d 00  AX  0   0  1
  [ 7] .eh_frame_hdr     PROGBITS        00002000 002000 00001c 00   A  0   0  4
  [ 8] .eh_frame         PROGBITS        0000201c 00201c 000058 00   A  0   0  4
  [ 9] .dynamic          DYNAMIC         00003f8c 002f8c 000068 08  WA  5   0  4
  [10] .got.plt          PROGBITS        00003ff4 002ff4 00000c 04  WA  0   0  4
  [11] .comment          PROGBITS        00000000 003000 00001f 01  MS  0   0  1
  [12] .debug_aranges    PROGBITS        00000000 00301f 000020 00      0   0  1
  [13] .debug_info       PROGBITS        00000000 00303f 000070 00      0   0  1
  [14] .debug_abbrev     PROGBITS        00000000 0030af 000062 00      0   0  1
  [15] .debug_line       PROGBITS        00000000 003111 000054 00      0   0  1
  [16] .debug_str        PROGBITS        00000000 003165 000085 01  MS  0   0  1
  [17] .debug_line_str   PROGBITS        00000000 0031ea 00001b 01  MS  0   0  1
  [18] .symtab           SYMTAB          00000000 003208 0000b0 10     19   6  4
  [19] .strtab           STRTAB          00000000 0032b8 00006a 00      0   0  1
  [20] .shstrtab         STRTAB          00000000 003322 0000d9 00      0   0  1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  D (mbind), p (processor specific)
```

🌞 **Affichez le code *assembleur* de la section `.text` à l'aide d'`objdump`**

```
senkai@TPOS:~/work$ objdump -d -j .text hello1

hello1:     file format elf32-i386


Disassembly of section .text:

00001000 <_start>:
    1000:       55                      push   %ebp
    1001:       89 e5                   mov    %esp,%ebp
    1003:       57                      push   %edi
    1004:       56                      push   %esi
    1005:       53                      push   %ebx
    1006:       83 ec 10                sub    $0x10,%esp
    1009:       e8 4b 00 00 00          call   1059 <__x86.get_pc_thunk.ax>
    100e:       05 e6 2f 00 00          add    $0x2fe6,%eax
    1013:       c7 45 e5 48 65 6c 6c    movl   $0x6c6c6548,-0x1b(%ebp)
    101a:       c7 45 e9 6f 2c 20 57    movl   $0x57202c6f,-0x17(%ebp)
    1021:       c7 45 ed 6f 72 6c 64    movl   $0x646c726f,-0x13(%ebp)
    1028:       c7 45 f0 64 21 0a 00    movl   $0xa2164,-0x10(%ebp)
    102f:       8d 75 e5                lea    -0x1b(%ebp),%esi
    1032:       bf 0e 00 00 00          mov    $0xe,%edi
    1037:       b8 04 00 00 00          mov    $0x4,%eax
    103c:       bb 01 00 00 00          mov    $0x1,%ebx
    1041:       89 f1                   mov    %esi,%ecx
    1043:       89 fa                   mov    %edi,%edx
    1045:       cd 80                   int    $0x80
    1047:       b8 01 00 00 00          mov    $0x1,%eax
    104c:       31 db                   xor    %ebx,%ebx
    104e:       cd 80                   int    $0x80
    1050:       90                      nop
    1051:       83 c4 10                add    $0x10,%esp
    1054:       5b                      pop    %ebx
    1055:       5e                      pop    %esi
    1056:       5f                      pop    %edi
    1057:       5d                      pop    %ebp
    1058:       c3                      ret

00001059 <__x86.get_pc_thunk.ax>:
    1059:       8b 04 24                mov    (%esp),%eax
    105c:       c3                      ret
```

## 2. Librairie et compilation dynamique

➜ Toujours le même code, mais en utilisant `printf()` cette fois. **Créer un fichier `hello2.c` avec le contenu suivant** :

```
senkai@TPOS:~/work$ nano hello2.c
```

```
  GNU nano 7.2                                            hello2.c *                                                    

#include <stdio.h>

int main()
{
    printf("Hello, World!\n");
}
```

### B. Intro compilation dynamique

➜ **On peut maintenant compiler le code**

```bash
gcc -fno-stack-protector -g -m32 -o hello2 hello2.c
```

### C. Tracer les appels à des librairies

🌞 **Tracez à l'aide de la commande `ldd` les *librairies* appelées par...**
```
senkai@TPOS:~/work$ ldd hello2
        linux-gate.so.1 (0xf7f75000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d31000)
        /lib/ld-linux.so.2 (0xf7f77000)
senkai@TPOS:~/work$ ldd hello1
        statically linked
senkai@TPOS:~/work$ file $(which ls) ldd $(which ls)
/usr/bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=15dfff3239aa7c3b16a71e6b2e3b6e4009dab998, for GNU/Linux 3.2.0, stripped
ldd:         cannot open `ldd' (No such file or directory)
/usr/bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=15dfff3239aa7c3b16a71e6b2e3b6e4009dab998, for GNU/Linux 3.2.0, stripped
senkai@TPOS:~/work$ file $(which firefox) ldd $(which firefox)
/usr/bin/firefox: POSIX shell script, ASCII text executable
ldd:              cannot open `ldd' (No such file or directory)
/usr/bin/firefox: POSIX shell script, ASCII text executable
```

🌞 **Parmi les *librairies* appelées par *hello2*, déterminer le type du fichier nommé `libc.so.X`**

```
senkai@TPOS:~/work$ ldd hello2
        linux-gate.so.1 (0xf7f2a000)
        libc.so.6 => /lib32/libc.so.6 (0xf7ce6000)
        /lib/ld-linux.so.2 (0xf7f2c000)
senkai@TPOS:~/work$ file /lib32/libc.so.6
/lib32/libc.so.6: ELF 32-bit LSB shared object, Intel 80386, version 1 (GNU/Linux), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=b3f5646d25dc90cc34d2507f197561065c7e630c, for GNU/Linux 3.2.0, stripped        
```

## 3. Compilation statique

➜ **Copiez le fichier `hello2.c` en un fichier `hello3.c`, puis *compilez*-le avec la *commande* suivante** :

```bash
gcc -static -fno-stack-protector -g -m32 -o hello3 hello3.c
```

🌞 **Affichez le type des fichiers `hello2` et `hello3`**

```
senkai@TPOS:~/work$ file hello2
hello2: ELF 32-bit LSB pie executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=7d77ed5ac2042aa7b9c4213e711df3861407b264, for GNU/
Linux 3.2.0, with debug_info, not stripped
senkai@TPOS:~/work$ file hello3
hello3: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, BuildID[sha1]=169d0f9e325d9a5ca59f73a47daa9ac08628c675, for GNU/Linux 3.2.0, with debug_info, not stripped
```

Différence :
```
hello2: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked
hello3: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked
```

🌞 **Affichez leurs tailles**

```
senkai@TPOS:~/work$ du -h hello2
16K     hello2
senkai@TPOS:~/work$ du -h hello3
728K    hello3
```

## 4. Compilation cross-platform

🌞 **Affichez l'*architecture* de votre *CPU***

```
senkai@TPOS:~/work$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 183
model name      : Intel(R) Core(TM) i7-14650HX
stepping        : 1
microcode       : 0xffffffff
cpu MHz         : 2419.200
cache size      : 30720 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 22
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
bogomips        : 4838.40
clflush size    : 64
cache_alignment : 64
address sizes   : 39 bits physical, 48 bits virtual
power management:
```

🌞 **Vérifiez que vous avez la commande `x86-64-linux-gnu-gcc`**

```
senkai@TPOS:~/work$ which x86_64-linux-gnu-gcc
/usr/bin/x86_64-linux-gnu-gcc
```

🌞 **Compilez votre fichier `hello3.c` dans un fichier cible nommé `hello4` vers une autre *architecture* que la vôtre**

```
arm-linux-gnueabi-gcc -o hello4 hello3.c
```

🌞 **[Désassemblez](../../cours/memo/glossary.md#désassembler) `hello3` et `hello4` à l'aide d'`objdump`**

```
senkai@TPOS:~/work$ objdump -d hello3 > hello3_disassembly.txt
objdump -d hello4 > hello4_disassembly.txt
```

🌞 **Essayez d'exécuter le *programme* `hello4`**

```
senkai@TPOS:~/work$ ./hello4
-bash: ./hello4: cannot execute binary file: Exec format error
```