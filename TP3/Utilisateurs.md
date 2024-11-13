
# I. Utilisateurs

## 1. Liste des users

🌞 **Afficher la ligne du fichier qui concerne votre utilisateur**

- mettez uniquement cette ligne en évidence
- pas `root`, l'autre, que vous avez créé à l'installation
- faites déjà un `cat` du fichier pour voir à quoi ressemble son contenu

REPONSE :
```
cat /etc/passwd | grep senkai
```
CMD
```
senkai:x:1000:1000:LE PRINCE,,,:/home/senkai:/bin/bash
```
🌞 **Afficher la ligne du fichier qui concerne votre utilisateur ET celle de `root` en même temps**

REPONSE :
```
cat /etc/passwd | grep -E 'root|senkai'
```
CMD
```
root:x:0:0:root:/root:/bin/bash
senkai:x:1000:1000:LE PRINCE,,,:/home/senkai:/bin/bash
```

🌞 **Afficher la liste des groupes d'utilisateurs de la *machine***

- ptite recherche par vous-mêmes pour trouver quel fichier c'est !
- le même sous tous les OS Linux :)

REPONSE : 
```
cat /etc/group | cut -d":" -f1
```
CMD :
```
root
daemon
bin
sys
adm
tty
disk
lp
mail
news
uucp
man
proxy
kmem
dialout
fax
voice
cdrom
floppy
tape
sudo
audio
dip
www-data
backup
operator
list
irc
src
shadow
utmp
video
sasl
plugdev
staff
games
users
nogroup
systemd-journal
systemd-network
crontab
input
sgx
kvm
render
netdev
systemd-timesync
messagebus
_ssh
ssl-cert
avahi-autoipd
bluetooth
avahi
lpadmin
pulse
pulse-access
scanner
saned
lightdm
polkitd
rtkit
colord
senkai
marmotte
```

🌞 **Afficher la ligne du fichier qui concerne votre utilisateur ET celle de `root` en même temps**

- afficher uniquement le nom d'utilisateur et le chemin vers leur répertoire personnel (celui de votre utilisateur est dans `/home`, celui de `root` c'est `/root`)
- on peut demander à `cut` d'afficher plusieurs colonnes avec `-fx,y` où `x` et `y` sont les deux numéros de colonnes qu'on veut afficher
- mettez uniquement ces deux lignes en évidence

CMD :
```
cat /etc/passwd | grep -E 'root|senkai' | cut -d: -f1,6
```
REPONSE :
```
root:/root
senkai:/home/senkai
```
## 2. Hash des passwords

Le *hash* des mots de passe des utilisateurs est stocké dans un fichier aussi : le fichier `/etc/shadow`.

🌞 **Afficher la ligne qui contient le hash du mot de passe de votre utilisateur**

- mettez uniquement cette ligne en évidence

CMD :
```
cat /etc/shadow | grep senkai
```
REPONSE :
```
senkai:$y$j9T$/kncXtF4FfezJ5ntyknUS/$04AjEpWSTF7IMASS2s2L5llnQTVIRuTDFEwbCRWiKN0:20033:0:99999:7:::
```

## 3. Sudo

### B. Practice

🌞 **Créer un groupe d'utilisateurs**

- il devra s'appeler `stronk_admins`

CMD :
```
sudo groupadd stronk_admins
```

🌞 **Créer un utilisateur**

- il devra s'appeler `imbob`
- il devra avoir un mot de passe défini
- il devra appartenir aux groupes `imbob` et `stronk_admins`

CMD : 
```
sudo useradd -m -s /bin/bash imbob
---
sudo passwd imbob
---
sudo usermod -aG imbob,stronk_admins imbob
```
🌞 **Prouver que l'utilisateur `imbob` est créé**

- en affichant une seule ligne du fichier `/etc/passwd`

CMD :
```
grep 'imbob' /etc/passwd
```
REPONSE :
```
imbob:x:1002:1003::/home/imbob:/bin/bash
```
🌞 **Prouver que l'utilisateur `imbob` a un password défini**

- en affichant une seule ligne du fichier `/etc/shadow`

CMD : 
```
sudo grep 'imbob' /etc/shadow
```
REPONSE :
```
imbob:$y$j9T$3N7QyE/arIZB0tXelm8kf0$dJTqsNaix8pkWfxhJzfGrrbeGu9OFcr0buyTNjbtTN3:20039:0:99999:7:::  
```
🌞 **Prouver que l'utilisateur `imbob` appartient au groupe `stronk_admins`**

- la liste des groupes et de leurs membres c'est dans `/etc/group`
- affichez une seule ligne

CMD : 
```
grep 'stronk_admins' /etc/group
```
REPONSE : 
```
stronk_admins:x:1002:imbob
```
🌞 **Créer un deuxième utilisateur**

- il devra s'appeler `imnotbobsorry`
- il devra avoir un mot de passe défini
- il devra appartenir au groupe `imnotbobsorry`

CMD :
```
sudo useradd -m -s /bin/bash imnotbobsorry
---
sudo passwd imnotbobsorry
---
sudo usermod -aG imnotbobsorry imnotbobsorry
```
🌞 **Modifier la configuration de `sudo` pour que**

- les membres du groupes `stronk_admins` ait le droit de taper des commandes `apt` en tant que `root`
- l'utilisateur `imbob` peut taper n'importe quelle commande en tant que `root`

CMD : 
```
sudo visudo
---
%stronk_admins ALL=(ALL) NOPASSWD: /usr/bin/apt
---
imbob ALL=(ALL:ALL) ALL
```

🌞 **Créer le dossier `/home/goodguy`** (avec une commande)

CMD :
```
sudo mkdir /home/goodguy
```
🌞 **Changer le répertoire personnel de `imbob`**

- avec une commande `usermod`, définissez ce dossier comme le *répertoire personnel* de `imbob`
- prouvez que le changement est effectif en affichant le contenu du fichier `passwd`

CMD :
```
sudo usermod -d /home/goodguy -m imbob
---
grep 'imbob' /etc/passwd
```
REPONSE : 
```
imbob:x:1002:1003::/home/goodguy:/bin/bash
```

🌞 **Créer le dossier `/home/badguy`**

CMD :
```
sudo mkdir /home/badguy
```

🌞 **Changer le répertoire personnel de `imnotbobsorry`**

- avec une commande `usermod`, définissez ce dossier `/home/badguy` comme le *répertoire personnel* de `imnotbobsorry`
- prouvez que le changement est effectif en affichant le contenu du fichier `passwd`

CMD :
```
sudo usermod -d /home/badguy -m imnotbobsorry
---
grep 'imnotbobsorry' /etc/passwd
```
REPONSE : 
```
imnotbobsorry:x:1003:1004::/home/badguy:/bin/bash
```

🌞 **Prouver que les permissions du dossier `/home/gooduy` sont incohérentes**

- ça n'appartient pas à l'utilisateur `imbob`
- ce qui est chelou, l'utilisateur il peut se connecter, mais il peut pas créer quoique ce soit dans son propre *répertoire personnel*, genre dans son propre dossier "Mes Documents"

CMD :
```
ls -ld /home/goodguy
```
REPONSE :
```
drwxr-xr-x 2 root root 4096 Nov 12 12:14 /home/goodguy
```
🌞 **Modifier les permissions de `/home/goodguy`**

- le dossier doit appartenir à `imbob`
- pareil pour tout son contenu
- avec une commande `chown` (il faudra mettre options et arguments)
  
CMD :
```
sudo chown -R imbob:imbob /home/goodguy
```
🌞 **Modifier les permissions de `/home/badguy`**

- le dossier doit appartenir à `imnotbobsorry`
- pareil pour tout son contenu

CMD :
```
sudo chown -R imnotbobsorry:imnotbobsorry /home/badguy
```

🌞 **Connectez-vous sur l'utilisateur `imbob`**

- il faut utiliser la commande `su - <USER>` pour ouvrir une nouvelle session en tant qu'un utilisateur
  - ça doit sortir aucun message d'erreur particulier
- si tu fais `pwd` tu devrais être dans le dossier `/home/goodguy` tout de suite après connexion (le *répertoire personnel* de `imbob` !)
- si tu fais `sudo echo meow` ou n'importe quelle autre commande avec `sudo`, ça devrait fonctionner

CMD :
```
su - imbob
---
pwd
---
sudo echo meow
```
REPONSE :
```
/home/goodguy
---
meow
```

🌞 **Connectez-vous sur l'utilisateur `imnotbobsorry`**

- il faut utiliser la commande `su - <USER>` pour ouvrir une nouvelle session en tant qu'un utilisateur
  - ça doit sortir aucun message d'erreur particulier
- si tu fais `pwd` tu devrais être dans le dossier `/home/badguy` tout de suite après 
- si tu fais `sudo echo meow` ou n'importe quelle autre commande avec `sudo`, ça ne devrait fonctionner PAS fonctionner
  - sauf les commandes `sudo apt...`, essaie un `sudo apt update` pour voir ?

CMD :
```
su - imnotbobsorry
---
pwd
---
sudo echo meow
---
sudo apt update
```

REPONSE : 
```
/home/badguy
---
imnotbobsorry is not in the sudoers file.
---
imnotbobsorry@TPOS:~$ sudo apt update
Get:1 http://security.debian.org/debian-security bookworm-security InRelease [48.0 kB]
Hit:2 http://deb.debian.org/debian bookworm InRelease
Get:3 http://deb.debian.org/debian bookworm-updates InRelease [55.4 kB]
Get:4 http://security.debian.org/debian-security bookworm-security/main Sources [125 kB]
Get:5 http://security.debian.org/debian-security bookworm-security/main amd64 Packages [204 kB]
Get:6 http://security.debian.org/debian-security bookworm-security/main Translation-en [125 kB]
Fetched 557 kB in 1s (469 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
66 packages can be upgraded. Run 'apt list --upgradable' to see them.
```