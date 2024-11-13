# III. Services

## 2. Analyser un service existant

On a déjà installé et lancé le *service* SSH normalement sur votre VM Debian, ce qui vous permet de vous connecter en SSH. On va se servir de lui pour regarder à quoi ressemble un *service* déjà installé !

🌞 **S'assurer que le service `ssh` est démarré**

- avec une commande `systemctl status`

> *Vous pouvez utiliser des commandes comme `sudo systemctl list-units -t service -a` pour lister tous les services de la machine. Voilà pour le fun, si t'as envie de regarder un peu tout ce qu'il y a qui tourne. C'est littéralement tous les constituants de l'OS que t'as sous les yeux si tu le fais, puisqu'on a ajouté aucun service nous-mêmes pour le moment, à part le service SSH.*

CMD : 
```
systemctl status
```
REPONSE : 
```
● TPOS
    State: running
    Units: 277 loaded (incl. loaded aliases)
     Jobs: 0 queued
   Failed: 0 units
    Since: Wed 2024-11-13 09:33:12 CET; 45min ago
  systemd: 252.30-1~deb12u2
   CGroup: /
           ├─init.scope
           │ └─1 /sbin/init
           ├─system.slice
           │ ├─ModemManager.service
           │ │ └─498 /usr/sbin/ModemManager
           │ ├─NetworkManager.service
           │ │ └─484 /usr/sbin/NetworkManager --no-daemon
           │ ├─avahi-daemon.service
           │ │ ├─464 "avahi-daemon: running [TPOS.local]"
           │ │ └─479 "avahi-daemon: chroot helper"
           │ ├─colord.service
           │ │ └─926 /usr/libexec/colord
           │ ├─cron.service
           │ │ └─465 /usr/sbin/cron -f
           │ ├─cups-browsed.service
           │ │ └─634 /usr/sbin/cups-browsed
           │ ├─cups.service
           │ │ ├─632 /usr/sbin/cupsd -l
           │ │ └─633 /usr/lib/cups/notifier/dbus dbus://
           │ ├─dbus.service
           │ │ └─466 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --sysl>
 ESCOC
```
🌞 **Isolez la ligne qui indique le nom du programme lancé**

- un *service* lancé, c'est juste un *programme* qui a été lancé pour nous pour rappel
- quand on fait un `systemctl start <SERVICE>`, l'OS lance juste une *commande* à notre place
- quelle commande ? Dans le `systemctl status`, le nom et le PID du *programme* lancé sont indiqués, isolez donc cette ligne

CMD : 
```
systemctl status ssh | grep 'Main PID'
```
REPONSE :
```
   Main PID: 617 (sshd)
```
🌞 **Déterminer le port sur lequel écoute le service SSH**

- avec une commande `ss`, en ajoutant les options
  - `-l` pour *listen* : on affiche les programmes en écoute
  - `-t` pour *tcp* : uniquement les ports TCP
  - `-p` pour *program* : on affiche le nom du programme qui écoute
  - `-n` pour *numeric* : affichage des ports sous forme numérique
  - donc `sudo ss -lnpt` pour lister tous les *programmes* qui écoutent sur le réseau et attendent la connexion de clients
- isolez les lignes intéressantes avec un `| grep <TEXTE>`

> Le service SSH écoute par convention sur le port 22 en TCP. Vous devez donc voir une ligne qui indique une écoute sur le port 22, par le programme `sshd`.

CMD :
```
sudo ss -lnpt | grep 'sshd'
```

REPONSE : 
```
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=617,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=617,fd=4))
```
🌞 **Consulter les logs du service SSH**

- les logs du service sont consultables avec une commande `journalctl`
  - donnez une commande `journalctl` qui permet de consulter les logs du service SSH

CMD :
```
sudo journalctl -u ssh
```
REPONSE :
```
Nov 06 12:29:09 TPOS systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Nov 06 12:29:10 TPOS sshd[542]: Server listening on 0.0.0.0 port 22.
Nov 06 12:29:10 TPOS sshd[542]: Server listening on :: port 22.
Nov 06 12:29:10 TPOS systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
-- Boot c86e302faaf24998a06e3295e87e3d8e --
Nov 07 08:23:29 TPOS systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Nov 07 08:23:29 TPOS sshd[541]: Server listening on 0.0.0.0 port 22.
Nov 07 08:23:29 TPOS sshd[541]: Server listening on :: port 22.
Nov 07 08:23:29 TPOS systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Nov 07 09:13:44 TPOS sshd[1559]: Connection reset by 192.168.8.1 port 50785 [preauth]
Nov 07 09:17:09 TPOS sshd[1569]: Invalid user emrep from 192.168.8.1 port 50788
Nov 07 09:17:27 TPOS sshd[1569]: pam_unix(sshd:auth): check pass; user unknown
Nov 07 09:17:27 TPOS sshd[1569]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rho>
Nov 07 09:17:29 TPOS sshd[1569]: Failed password for invalid user emrep from 192.168.8.1 port 50788 ssh2
Nov 07 09:17:51 TPOS sshd[1569]: pam_unix(sshd:auth): check pass; user unknown
Nov 07 09:17:53 TPOS sshd[1569]: Failed password for invalid user emrep from 192.168.8.1 port 50788 ssh2
Nov 07 09:18:52 TPOS sshd[1569]: pam_unix(sshd:auth): check pass; user unknown
Nov 07 09:18:54 TPOS sshd[1569]: Failed password for invalid user emrep from 192.168.8.1 port 50788 ssh2
Nov 07 09:18:54 TPOS sshd[1569]: Connection reset by invalid user emrep 192.168.8.1 port 50788 [preauth]
Nov 07 09:18:54 TPOS sshd[1569]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.16>
Nov 07 09:23:04 TPOS sshd[1576]: Invalid user emrep from 192.168.8.1 port 50794
Nov 07 09:23:07 TPOS sshd[1576]: pam_unix(sshd:auth): check pass; user unknown
Nov 07 09:23:07 TPOS sshd[1576]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rho>
Nov 07 09:23:09 TPOS sshd[1576]: Failed password for invalid user emrep from 192.168.8.1 port 50794 ssh2
Nov 07 09:23:23 TPOS sshd[1576]: Connection reset by invalid user emrep 192.168.8.1 port 50794 [preauth]
Nov 07 09:23:34 TPOS sshd[1579]: Invalid user emrep from 192.168.8.1 port 50800
Nov 07 09:23:37 TPOS sshd[1579]: pam_unix(sshd:auth): check pass; user unknown
Nov 07 09:23:37 TPOS sshd[1579]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rho>
Nov 07 09:23:38 TPOS sshd[1579]: Failed password for invalid user emrep from 192.168.8.1 port 50800 ssh2
lines 1-29
```
## 3. Modification du service

### A. Configuration du service SSH

🌞 **Identifier le fichier de configuration du serveur SSH**

- utilisez une commande pour voir le propriétaire du fichier
- et les permissions appliquées dessus

CMD a :
```
ls -l /etc/ssh/sshd_config
```
CMD :
```
-rw-r--r-- 1 root root 3223 Jun 22 21:38 /etc/ssh/sshd_config
```
🌞 **Modifier le fichier de conf**

- exécutez un `echo $RANDOM` dans votre shell pour **demander à votre shell de vous fournir un nombre aléatoire**
  - simplement pour vous montrer la petite astuce et vous faire manipuler le shell :)
  - pour un numéro de port valide, c'est entre 1 et 65535 ! 
- **changez le port d'écoute du serveur SSH** pour qu'il écoute sur ce numéro de port
  - il faut modifier le fichier de configuration avec `nano` par exemple, une seule ligne à changer
  - dans le compte-rendu je veux un `cat` du fichier de conf
  - filtré par un `| grep` pour mettre en évidence la ligne que vous avez modifié

REPONSE :
```
echo $RANDOM
---
sudo nano /etc/ssh/sshd_config
---
#Port 27672
---
cat /etc/ssh/sshd_config | grep 'Port'
```
CMD :
```
27672
---
#Port 27672
#GatewayPorts no
```

🌞 **Redémarrer le service**

- avec une *commande* `systemctl restart <SERVICE>`

> **C'est TOUT LE TEMPS comme ça :** quand vous modifiez la configuration d'un truc, **il faut relancer le truc pour que la configuration prenne effet.** Logique, puisque c'est au démarrage qu'un *programme* regarde la configuration qu'il doit adopter.

REPONSE :
```
sudo systemctl restart ssh
```

🌞 **Effectuer une connexion SSH sur le nouveau port**

- depuis votre PC
- il faudra utiliser une option à la *commande* `ssh` pour vous connecter à la VM afin de préciser un port non-conventionnel (celui que vous avez défini dans le *fichier de configuration*)

REPONSE :
```
ssh -p 27672 senkai@192.168.8.7
```

### B. Le service en lui-même

Il existe un fichier qui définit quoi faire quand on tape `systemctl start ssh`. En effet, taper une *commande* `systemctl start` revient juste à demander à l'OS de lancer un *service* : c'est à dire un simple *programme* lancé.

Quel *programme* ? Il existe un fichier qui porte l'extension `.service` qui définit (entre autres), pour chaque *service*, quelle est le *programme* à lancer.

🌞 **Trouver le fichier `ssh.service`**

REPONSE : 
```
systemctl status ssh
---
sudo find / -name ssh.service
```
CMD :
```
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Wed 2024-11-13 10:32:15 CET; 8min ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1849 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 1850 (sshd)
      Tasks: 1 (limit: 2284)
     Memory: 3.1M
        CPU: 94ms
     CGroup: /system.slice/ssh.service
             └─1850 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
---
/usr/lib/systemd/system/ssh.service            
```
🌞 **Déterminer quel est le programme lancé**

- quand on tape une commande `systemctl start ssh`, le fichier `ssh.service` est lu, et le *programme* indiqué en face de `ExecStart=` est lancé
- isolez uniquement cette ligne

```
senkai@TPOS:~$ grep 'ExecStart=' /lib/systemd/system/ssh.service
ExecStart=/usr/sbin/sshd -D $SSHD_OPTS
```
## 4. Créez votre propre service

➜ On va se servir d'une petite commande pratique pour mettre ça en oeuvre, faites un petit test d'abord :

- depuis un terminal de la VM :

```bash
# on crée un ptit fichier bidon dans le dossier actuel
echo "meow" > meow

# on lance un ptit serveur web en une seule ligne de commande
# ptite commande python qui fait l'taf !
python3 -m http.server 8888

# vous pouvez couper la commande avec CTRL + C quand vous aurez fait le test juste après
```

- pendant que ça tourne, ouvrez un navigateur sur VOTRE PC
  - et visitez l'URL `http://<IP_VM>:8888`
  - par exemple `http://10.1.1.10:8888` si ta VM porte l'adresse IP 10.1.1.10
- ça doit fonctionner avant de continuer
  - vous devriez au moins voir le fichier `meow`

➜ Plutôt que de lancer cette commande à la main pour avoir notre ptit serveur Web, on va créer un service qui lance automatiquement cette commande !

🌞 **Déterminer le dossier qui contient la commande `python3`**

- avec une commande adaptée

```
senkai@TPOS:~$ which python3
/usr/bin/python3
```

🌞 **Créez un fichier `/etc/systemd/system/meow_web.service`**

- avec `nano`, quand on modifie un fichier qui n'existe pas, il sera créé
- déposez le contenu suivant :

```
senkai@TPOS:~$ nano /etc/systemd/system/meow_web.service
senkai@TPOS:~$ sudo !!
```

🌞 **Indiquez à l'OS que vous avez modifié les *services***

```
senkai@TPOS:~$ systemctl daemon-reload
```
🌞 **Démarrez votre service**
```
senkai@TPOS:~$ systemctl start meow_web
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ====
Authentication is required to start 'meow_web.service'.
Authenticating as: senkai,,, (utsu)
Password:
==== AUTHENTICATION COMPLETE ====
```

🌞 **Assurez-vous que le service `meow_web` est actif**
```
==== AUTHENTICATION COMPLETE ====
senkai@TPOS:~$ systemctl status meow_web
● meow_web.service - Super serveur web MEOW
     Loaded: loaded (/etc/systemd/system/meow_web.service; disabled; pr>
     Active: active (running) since Wed 2024-11-13 10:19:58 CET; 19s ago
   Main PID: 3590 (python3)
      Tasks: 1 (limit: 2284)
     Memory: 8.9M
        CPU: 133ms
     CGroup: /system.slice/meow_web.service
             └─3590 /usr/bin/python3 -m http.server 8888

```
🌞 **Déterminer le PID du *processus* Python en cours d'exécution**
```
senkai@TPOS:~$ ps -eo pid,user,cmd | grep 'python3 -m http.server' | grep -v grep
   3590 root     /usr/bin/python3 -m http.server 8888
```
🌞 **Prouvez que le *programme* écoute derrière le port 8888**
```
senkai@TPOS:~$ sudo ss -tlp | grep ':8888'
LISTEN 0      5            0.0.0.0:8888       0.0.0.0:*    users:(("python3",pid=3590,fd=3))
```

🌞 **Faire en sote que le *service* se lance automatiquement au démarrage de la machine**
```
senkai@TPOS:~$ systemctl enable meow_web
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-unit-files ====
Authentication is required to manage system service or unit files.
Authenticating as: senkai ,,, (senkai)
Password:
==== AUTHENTICATION COMPLETE ====
==== AUTHENTICATING FOR org.freedesktop.systemd1.reload-daemon ====
Authentication is required to reload the systemd state.
Authenticating as: senkai ,,, (senkai)
Password:
==== AUTHENTICATION COMPLETE ====
```