# IV. Poupée russe

🌞 **Récupérer le fichier meow**

- (https://gitlab.com/it4lik/b1-os/-/blob/main/tp/2/meow)
- téléchargez-le à l'aide de la commande suivante  
  
**REPONSE :**
```
wget https://gitlab.com/it4lik/b1-os/-/raw/main/tp/2/meow
```

**CMD :**
```
--2024-11-10 12:40:31--  https://gitlab.com/it4lik/b1-os/-/raw/main/tp/2/meow
Resolving gitlab.com (gitlab.com)... 172.65.251.78, 2606:4700:90:0:f22e:fbec:5bed:a9b9
Connecting to gitlab.com (gitlab.com)|172.65.251.78|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18016947 (17M) [application/octet-stream]
Saving to: ‘meow’

meow                          100%[=================================================>]  17.18M  24.5MB/s    in 0.7s

2024-11-10 12:40:33 (24.5 MB/s) - ‘meow’ saved [18016947/18016947]
```

🌞 **Trouver le dossier dawa/**

- Le fichier `meow` récupéré est une archive compressée.
- Utilisez la commande `file /path/vers/le/fichier` pour déterminer le type du fichier.
- Renommez le fichier correctement (si c'est une archive compressée ZIP, il faut ajouter `.zip` à son nom).
- Extrayez l'archive avec une commande.
- Répétez ces opérations jusqu'à trouver le dossier `dawa/`.
```
mv /home/senkai/meow /home/senkai/meow.zip
unzip /home/senkai/meow.zip -d /home/senkai/
file /home/senkai/extracted_file
```

**REPONSE :**
```
file /home/senkai/meow
```
**CMD :**
```
/home/senkai/meow: Zip archive data, at least v2.0 to extract, compression method=deflate
```

**REPONSE :** 
```
mv /home/senkai/meow /home/senkai/meow.zip
unzip /home/senkai/meow.zip
cd dawa
```
**CMD :** 
```
Archive:  /home/senkai/meow.zip
inflating: /home/senkai/meow
```

🌞 **Dans le dossier `dawa/`, déterminer le chemin vers**

- le seul fichier de 15Mo
- le seul fichier qui ne contient que des `7`
- le seul fichier qui est nommé `cookie`
- le seul fichier caché (un fichier caché c'est juste un fichier dont le nom commence par un `.`)
- le seul fichier qui date de 2014
- le seul fichier qui a 5 dossiers-parents
  - je pense que vous avez vu que la structure c'est 50 `folderX`, chacun contient 50 dossiers `X`, et chacun contient 50 `fileX`
  - bon bah là y'a un fichier qui est contenu dans `folderX/X/X/X/X/` et c'est le seul qui 5 dossiers parents comme ça

REPONSE :
```
senkai@TPOS:~/Downloads/dawa$ find . -type f -size 15M
./folder31/19/file39
senkai@TPOS:~/Downloads/dawa$  grep -L '[^7]' * -r
folder43/38/file41
senkai@TPOS:~/Downloads/dawa$ find . -type f -name "cookie"
./folder14/25/cookie
senkai@TPOS:~/Downloads/dawa$ find . -type f -name ".*"
./folder32/14/.hidden_file 
senkai@TPOS:~/Downloads/dawa$ find . -type f -newermt "2014-01-01" ! -newermt "2015-01-01"
./folder36/40/file43
senkai@TPOS:~/Downloads/dawa$ find . -type f -path './*/*/*/*/*/*'
./folder37/45/23/43/54/file43
```
