# III. Programmes et paquets

## 1. Programmes et processus
➜ Dans cette partie, afin d'avoir quelque chose à étudier, on va utiliser le programme sleep.

C'est une commande (= un programme) disponible sur tous les OS. Ça permet de... ne rien faire pendant X secondes. La syntaxe c'est sleep 90 pour attendre 90 secondes. On s'en fout de sleep en soi, c'est une commande utile parmi plein d'autres, elle est pratique pour étudier les trucs que je veux vous montrer.

### A. Run then kill
🌞 Lancer un processus sleep

**Réponse :**
```
sleep 1000

ps aux | grep sleep
```
**CMD :**
```
senkai     25934  0.0  0.0   5464   888 pts/2    S+   12:40   0:00 sleep 1000
senkai     25964  0.0  0.1   6332  2152 pts/3    S+   12:41   0:00 grep sleep
```

🌞 Terminez le processus sleep depuis le deuxième terminal

**Réponse :**
```
kill 25934
```
**CMD :**
```
Terminated
```

### B. Tâche de fond
🌞 Lancer un nouveau processus sleep, mais en tâche de fond

**Réponse :**
```
sleep 1000 &
```
**CMD :**
```
[1] 25974
```

🌞 Visualisez la commande en tâche de fond

Il existe une commande pour lister les processus qu'on a lancés en tâche de fond. En utilisant cette commande, récupérez le PID du processus sleep.

**Réponse :**
```
jobs -l
```
**CMD :**
```
[1]+  25974 Running                 sleep 1000 &
```

### C. Find paths
🌞 Trouver le chemin où est stocké le programme sleep avec une commande find.

**Réponse :**
```
find / -name sleep 2>/dev/null
```
**CMD :**
```
/usr/lib/klibc/bin/sleep
/usr/bin/sleep
```

🌞 Tant qu'on est à chercher des chemins : trouver les chemins vers tous les fichiers qui s'appellent .bashrc. Utilisez la commande find encore.

**Réponse :**
```
find / -name .bashrc 2>/dev/null
```
**CMD :**
```
/home/senkai/.bashrc
/home/papier_alu/.bashrc
/etc/skel/.bashrc
```

### D. La variable PATH
🌞 Vérifier que les commandes sleep, ssh, et ping sont bien des programmes stockés dans l'un des dossiers listés dans votre PATH.

**Réponse :**
```
echo $PATH
```
**CMD :**
```
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
```

**Réponse :**
```
which sleep
which ssh
which ping
```
**CMD :**
```
/usr/bin/sleep
/usr/bin/ssh
/usr/bin/ping
```

## 2. Paquets
➜ Tous les OS Linux sont munis d'un store d'application. C'est natif. Quand tu fais apt install ou dnf install, ce genre de commandes, tu utilises ce store. On dit que apt et dnf sont des gestionnaires de paquets. Ça permet aux utilisateurs de télécharger des nouveaux programmes (ou d'autres trucs) depuis un endroit sûr.

🌞 Installer le paquet firefox.

**Réponse :**
```
apt install firefox
```
**CMD :**
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
firefox is already the newest version (128.4.0esr-1~deb12u1).
firefox set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 60 not upgraded.
```

🌞 Utiliser une commande pour lancer Firefox. Déterminer le chemin vers le programme firefox.

**Réponse :**
```
which firefox
```
**CMD :**
```
/usr/bin/firefox
```

🌞 Mais aussi déterminer l'adresse HTTP ou HTTPS des serveurs où vous téléchargez des paquets. Une commande apt install ou dnf install permet juste de faire un téléchargement HTTP. Ma question c'est donc : sur quelle(s) URL(s) vous vous connectez pour télécharger des paquets ? Il existe un dossier qui contient la liste des URLs consultées quand vous demandez un téléchargement de paquets. C'est un sous-dossier de /etc/, et ça dépend du gestionnaire de paquets que vous utilisez !

**Réponse :**
```
ls /etc/apt/
```
**CMD :**
```
apt.conf.d   keyrings          listchanges.conf.d  sources.list   sources.list.d
auth.conf.d  listchanges.conf  preferences.d       sources.list~  trusted.gpg.d
```

**REPONSE :**
```
cat /etc/apt/sources.list
```
**CMD :**
```
deb http://deb.debian.org/debian/ bookworm main non-free-firmware
deb-src http://deb.debian.org/debian/ bookworm main non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main non-free-firmware
deb-src http://security.debian.org/debian-security bookworm-security main non-free-firmware
```
