# II. Processes

## 1. Jouer avec la commande ps

La commande `ps` permet de lister les *[processus](../../cours/memo/glossary.md#processus)* en cours d'exécution sur la machine. Elle possède plein d'options pour affiner l'affichage.

Quand on veut juste la liste de tout, on tape généralement `ps -ef`.

On va se servir de la commande `ps` pour faire mumuse avec le terminal, en affichant des trucs pouvant être utiles dans la vraie vie.

🌞 **Affichez les processus `bash`**

- une commande `ps` puis vous filtrez la sortie pour afficher que les `bash`

> `bash` c'est l'un des shells en CLI les plus utilisés sur les systèmes Linux. Lister les processus `bash` revient donc un peu à lister les sessions (légitimes) ouvertes sur la machine.

CMD : 
```
ps -ef | grep 'bash'
```

REPONSE : 
```
senkai      1137    1133  0 09:34 pts/0    00:00:00 -bash
senkai      1649    1137  0 09:52 pts/0    00:00:00 grep bash
```
🌞 **Affichez tous les processus lancés par votre utilisateur**

- uniquement ceux qui sont lancés par votre utilisateur, pas ceux lancés par `root` ou autres

> P'tit compte-rendu de toutes les applications qu'un utilisateur donné a lancé actuellement. Toujours utile !

CMD :
```
ps -u senkai
```

REPONSE :
```
    726 ?        00:00:00 systemd
    727 ?        00:00:00 (sd-pam)
    743 ?        00:00:00 pulseaudio
    744 ?        00:00:00 gnome-keyring-d
    748 ?        00:00:00 dbus-daemon
    752 ?        00:00:00 xfce4-session
    800 ?        00:00:00 ssh-agent
    810 ?        00:00:00 at-spi-bus-laun
    816 ?        00:00:00 dbus-daemon
    826 ?        00:00:00 at-spi2-registr
    836 ?        00:00:00 gpg-agent
    838 ?        00:00:00 xfwm4
    841 ?        00:00:00 gvfsd
    853 ?        00:00:00 xfsettingsd
    862 ?        00:00:00 xfce4-panel
    866 ?        00:00:00 Thunar
    871 ?        00:00:00 xfdesktop
    874 ?        00:00:00 light-locker
    878 ?        00:00:00 xfce4-power-man
    881 ?        00:00:00 xfce4-notifyd
    882 ?        00:00:00 applet.py
    885 ?        00:00:00 polkit-gnome-au
    886 ?        00:00:00 nm-applet
    888 ?        00:00:00 xiccd
    889 ?        00:00:00 panel-6-systray
    893 ?        00:00:00 dconf-service
    894 ?        00:00:00 panel-8-pulseau
    898 ?        00:00:00 panel-9-power-m
    900 ?        00:00:00 panel-10-notifi
    902 ?        00:00:00 gvfs-udisks2-vo
    912 ?        00:00:00 gvfsd-trash
    918 ?        00:00:00 gvfsd-metadata
    967 ?        00:00:00 panel-14-action
   1133 ?        00:00:00 sshd
   1137 pts/0    00:00:00 bash
   1654 ?        00:00:00 xfconfd
   1665 pts/0    00:00:00 ps
```

🌞 **Affichez le top 5 des processus qui utilisent le plus de RAM**

- je sais pas si j'ai besoin de préciser pourquoi c'est utile de savoir ça
- si t'as plus de *RAM*, t'aimes bien savoir qui te la mange !
- uniquement 5 lignes doivent s'afficher et elles ne contiennent QUE le nom du processus et la *RAM* utilisée

CMD : 
```
ps --sort=-%mem -eo comm,%mem | head -n 6
```

REPONSE :
```
COMMAND         %MEM
lightdm-gtk-gre  5.6
Xorg             4.9
xfwm4            4.8
Xorg             3.8
xfdesktop        3.0
```

🌞 **Affichez le *PID* du processus du service SSH**

- le nom du *programme* c'est `sshd`
- vous ne devez afficher qu'une seule ligne car un seul *programme* est lancé quand vous démarrez le service SSH
- toutes les autres lignes qui s'affichent sont les *processus* lancés pour gérer vos sessions SSH actuellement en cours
- il existe donc un seul *processus* SSH en cours d'exécution qui est le *parent* de tous les autres *processus* SSH (qui sont ses *enfants*)

CMD : 
```
ps -C sshd -o pid
```

REPONSE :
```
    PID
    617
   1124
   1133
```
🌞 **Affichez le nom du processus avec l'identifiant le plus petit**

- votre *commande* doit afficher le processus qui a le plus petit identifiant sans le connaître à l'avance
  - l'identifiant d'un processus c'est son *PID* (*Process IDentifier*)
  - sans connaître ni son nom ni son *PID* à l'avance, proposer une *commande* qui n'affiche que lui
  - si on trie la liste par *PID*, suffit d'afficher que la première ligne, non ?...
- **une seule ligne doit être affichée**
- la *commande* doit tout le temps fonctionner quoi !

CMD :
```
ps -e --sort=pid -o comm= | head -n 1
```
REPONSE :
```
systemd
```
## 2. Parent, enfant, et meurtre

Quand on lance un *programme* on le fait toujours depuis un *processus* déjà en cours d'exécution. Genre quand on double-clique sur l'icone de Firefox pour le lancer, on le fait depuis l'interface graphique de l'OS, qui est un *processus* en cours d'exécution.

On dit alors que le nouveau *processus* lancé est l'enfant du *programme* qui le lance (lui est le *processus parent*).

🌞 **Déterminer le *PID* de votre shell actuel**

- quand on ouvre un terminal sous Linux, généralement, le shell c'est `bash`
- donc déterminez le *PID* du *processus* `bash` dans lequel vous tapez des *commandes*
- n'affichez qu'une seule ligne

CMD :
```
echo $$
```
REPONSE : 
```
1137
```
🌞 **Déterminer le *PPID* de votre shell actuel**

- le *PPID* c'est pour *Parent PID* : l'identifiant du *processus* parent
- avec une *commande* `ps` et des *options* usuelles, l'info va sortir
- n'affichez qu'une seule ligne

CMD :
```
ps -o ppid= -p $$
```
REPONSE :
```
1133
```
🌞 **Déterminer le nom de ce *processus***

- donc, votre `bash` est l'enfant d'un *processus* : lequel ?
- vous venez de repérer son PID juste avant, facile de repérer son nom maintenant
- n'affichez qu'une seule ligne

CMD :
```
ps -p 1133 -o comm=
```
REPONSE :
```
sshd
```

🌞 **Lancer un *processus* `sleep 9999` en tâche de fond**

- avec le caractère `&` comme au TP précédent
- déterminer avec une *commande* `ps` son PID et son PPID
  - vous n'afficherez qu'une seule ligne
- vous devriez constater que son PPID, c'est votre `bash`

CMD :
```
sleep 9999 &
---
ps -C sleep -o pid,ppid
```
REPONSE :
```
[1] 1702
---
    PID    PPID
   1702    1137
```

🌞 **Fermez votre session SSH**

- genre complètement déconnectez-vous de vos sessions SSH
- puis reconnecte-toi avec une nouvelle connexion SSH
- est-ce que le *processus* `sleep` lancé en tâche de fond s'exécute toujours ?
- prouver que oui ou non en une seule *commande*

```
$ ps -C sleep
    PID TTY          TIME CMD
   1702 ?        00:00:00 sleep
```

➜ **Pour les curieux, un ptit trick**

- si un *processus* n'a plus de parent, on dit qu'il est orphelin
- ça arrive parfois plus ou moins dans des cas légitimes, quand le *processus* parent crash par exemple
- un orphelin se fait immédiatement adopté ! Par l'OS lui-même (le ptit privilégié woaw)
- ptit trick bash pour créer un *processus* orphelin ('vais pas expliquer les détails de la syntaxe ici meow)

```bash
( ( sleep 9999) & )
```

- si tu fais un `ps` tu verras que le *processus* est bien orphelin car il a été adopté par un process qui porte un PID très élevé, et pas n'importe lequel hehe !
