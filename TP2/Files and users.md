# II. Files and users


## 1. Fichiers

### A. Find me

🌞 Trouver le chemin vers le répertoire personnel de votre utilisateur
**REPONSE :**
```
echo $HOME
```
**CMD :**
```
/home/senkai
```

🌞 Vérifier les permissions du répertoire personnel de votre utilisateur
**REPONSE :**
```
ls -l $HOME
```
**CMD :**
```
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Desktop
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Documents
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Downloads
drwxr-xr-x 2 senkai senkai 4096 Nov  7 11:30 gameshell
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Music
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Pictures
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Public
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Templates
drwxr-xr-x 2 senkai senkai 4096 Nov  6 12:29 Videos
```

🌞 Trouver le chemin du fichier de configuration du serveur SSH

**REPONSE :**
```
find / -name sshd_config 2>/dev/null
```
**CMD :**
```
/etc/ssh/sshd_config
```

🌞 Trouver le chemin du fichier de logs SSH

**REPONSE :**
```
find /var/log -name auth.log
```
**CMD :**
```
find: ‘/var/log/auth.log’
```

## 2. Users

### A. Nouveau user
🌞 Créer un nouvel utilisateur 

**REPONSE :**
```
root@TPOS:~# useradd -m -d /home/papier_alu marmotte
root@TPOS:~# passwd marmotte
```
**CMD :**
```
New password:
Retype new password:
passwd: password updated successfully
```

### B. Infos enregistrées par le système

🌞 Prouver que cet utilisateur a été créé

**REPONSE :**
```
cat /etc/passwd | grep marmotte
```
**CMD :**
```
marmotte:x:1001:1001::/home/marmotte:/bin/sh
```
🌞 Déterminer le hash du password de l'utilisateur marmotte

**REPONSE :**
```
cat /etc/shadow | grep marmotte
```
**CMD :**
```
marmotte:$y$j9T$yBSf4Z954ryjmUy1hp/m31$51vu2F4oG.rAIW3HnaTSNW..cZQKh05PUhaCzKKnss7:20034:0:99999:7:::
```

🌞 Tapez une commande pour vous déconnecter : fermer votre session utilisateur

**REPONSE :**
```
exit
```
**CMD :**
```
logout
Connection to 192.168.8.7 closed.
```

🌞 Assurez-vous que vous pouvez vous connecter en tant que l'utilisateur marmotte

**REPONSE :**
```
ssh marmotte@192.168.8.7
ls /home/senkai
```
**CMD :**
```
logoutmarmotte@192.168.8.7's password:
ls: cannot open directory '/home/senkai': Permission denied
```