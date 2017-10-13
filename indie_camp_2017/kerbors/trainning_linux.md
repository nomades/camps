---
title: Entrainement et acculturation
description: à l'utilisation d'un ordinateur sous Linux
image_url:
---

# [[IndieCamp Kerbors](https://frama.link/indiecamp-kerbors-2017)] Atelier Geek - Session #0

* [Atelier #0](https://hackmd.io/s/rJw31KgDb)
* [Atelier #1](https://hackmd.io/s/rJDXkRHDW)
* [Atelier #2](https://hackmd.io/s/SyHcRZPPb)

Ce PAD décrit un atelier d'initiation aux **commandes Linux** réalisé sur l'indiecamp à Kerbors.

Ce document est mis à disposition par tou.te.s les contributeurs et contributrices de l'Indiecamp Kerbors 2017, selon les termes de la [licence Creative Commons CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

<img style="display: block; margin: 0 auto;" src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-sa.png" width="40%">

# 1er exercice

## Informations sur le système

**Quel est le système installé ?**

    uname -a

**Qui sont les utilisateurs du système ?**    

    who

## Ouvrir & fermer le terminal

**Ouvrir un terminal avec un autre compte**      

     su user
     
**Fermer ce terminal**

    exit

## Utiliser la commande `man`

**Tester la commande man**

```!
     TCPDUMP(8)                                                         System Manager's Manual                                                   TCPDUMP(8)

     NAME
         tcpdump - dump traffic on a network

    SYNOPSIS
       tcpdump [ -AbdDefhHIJKlLnNOpqStuUvxX# ] [ -B buffer_size ]
               [ -c count ]
               [ -C file_size ] [ -G rotate_seconds ] [ -F file ]
               [ -i interface ] [ -j tstamp_type ] [ -m module ] [ -M secret ]
               [ --number ] [ -Q in|out|inout ]
               [ -r file ] [ -V file ] [ -s snaplen ] [ -T type ] [ -w file ]
               [ -W filecount ]
               [ -E spi@ipaddr algo:secret,...  ]
               [ -y datalinktype ] [ -z postrotate-command ] [ -Z user ]
               [ --time-stamp-precision=tstamp_precision ]
               [ --immediate-mode ] [ --version ]
               [ expression ]

    DESCRIPTION
       Tcpdump  prints  out  a description of the contents of packets on a network interface that match the boolean expression; the description is
       preceded by a time stamp, printed, by default, as hours, minutes, seconds, and fractions of a second since midnight.  It can  also  be  run
       with  the  -w  flag, which causes it to save the packet data to a file for later analysis, and/or with the -r flag, which causes it to read
       from a saved packet file rather than to read packets from a network interface (please note tcpdump is protected  via  an  enforcing  appar‐
       mor(7)  profile  in Ubuntu which limits the files tcpdump may access).  It can also be run with the -V flag, which causes it to read a list
       of saved packet files. In all cases, only packets that match expression will be processed by tcpdump.

       Tcpdump will, if not run with the -c flag, continue capturing packets until it is interrupted by a SIGINT signal (generated,  for  example,
       by  typing  your  interrupt character, typically control-C) or a SIGTERM signal (typically generated with the kill(1) command); if run with
       the -c flag, it will capture packets until it is interrupted by a SIGINT or SIGTERM signal or the specified number  of  packets  have  been
       processed.

       When tcpdump finishes capturing packets, it will report counts of:

              packets ``captured'' (this is the number of packets that tcpdump has received and processed);

              packets  ``received  by filter'' (the meaning of this depends on the OS on which you're running tcpdump, and possibly on the way the
              OS was configured - if a filter was specified on the command line, on some OSes it counts packets regardless of  whether  they  were
    
    Manual page tcpdump(8) line 1 (press h for help  or q to quit)

```

**Les commandes documentées**

```!
    man man
```

![](https://i.imgur.com/Fb9fcNR.png)

## Explorer des répertoires & fichiers

**Lister le contenu du répertoire /etc**

     ls /etc
      
![](https://i.imgur.com/XUpzwSj.png)

**Lister de manière détaillée le contenu du répertoire /etc.**
    
      ls -l /etc
      ls -la /etc
 
**Lister le contenu du répertoire /dev**

     ls -l /dev
   
**Lister le contenu du fichier /etc/passwd**

     cat /etc/passwd

```!
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
...
user,,,:/var/run/hplip:/bin/false
nico:x:1000:1000:Nico,,,:/home/nico:/bin/bash
```

**Lister le contenu du fichier /etc/shadow**

    cat /etc/shadow

**Afficher par ordre alphabétique les utilisateurs définis dans le fichier /etc/passwd**

    cat /etc/passwd | sort

```!
backup:x:34:34:backup:/var/backups:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
cupsys:x:100:106::/home/cupsys:/bin/false
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
games:x:5:60:games:/usr/games:/bin/sh
...
root:x:0:0:root:/root:/bin/bash
sync:x:4:65534:sync:/bin:/bin/sync
syslog:x:102:102::/home/syslog:/bin/false
sys:x:3:3:sys:/dev:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
```
**Rechercher les fichiers du répertoire /etc contenant la chaine de caractères "root"** 	

    grep root /etc/*

**Localiser le fichier "stdio.h" dans le système de fichiers de votre installation** 

    find / -name stdio.h

```!
find: /tmp/kde-root: Permission non accordée
/usr/include/bits/stdio.h
/usr/include/stdio.h
```

**À l'aide de la commande `od`, illustrer la différence entre les fichier de type ASCII (texte) DOS, UNIX et MAC. Utiliser le fichier ASCII Dos `montexte.dos` fourni en lien et créer les fichiers ASCII Unix `montexte.unix` et ASCII MAC `montexte.mac` avec le même contenu au moyen d'un éditeur texte (e.g. Kate) puis comparer (v. Macintosh si l'éditeur le permet).**

    od -x monfichier.dos`

```!
0000000 6e75 0a0d 6564 7875 0a0d 7274 696f 0d73
0000020 710a 6175 7274 0d65 630a 6e69 0d71 730a
0000040 7869 0a0d 6573 7470 0a0d 0a0d 0a0d 0a0d
0000060 0a0d 0a0d
0000064
od -c monfichier.dos
0000000 u n \r \n d e u x \r \n t r o i s \r
0000020 \n q u a t r e \r \n c i n q \r \n s
0000040 i x \r \n s e p t \r \n \r \n \r \n \r \n
0000060 \r \n \r \n
0000064
od -x monfichier.unix
0000000 6e75 640a 7565 0a78 7274 696f 0a73 7571
0000020 7461 6572 630a 6e69 0a71 6973 0a78 6573
0000040 7470 0a0a 0a0a 0a0a
0000050
od -c monfichier.unix
0000000 u n \n d e u x \n t r o i s \n q u
0000020 a t r e \n c i n q \n s i x \n s e
0000040 p t \n \n \n \n \n \n
0000050
od -x monfichier.mac
0000000 6e75 640d 7565 0d78 7274 696f 0d73 7571
0000020 7461 6572 630d 6e69 0d71 6973 0d78 6573
0000040 7470 0d0d 0d0d 0d0d
0000050
od -c monfichier.unix
0000000 u n \r d e u x \r t r o i s \r q u
0000020 a t r e \r c i n q \r s i x \r s e
0000040 p t \r \r \r \r \r \r
0000050
```
:::info
* Codage des fins de ligne sous Dos par les deux caracteres 0x0D et 0x0A. 
* Codage des fins de ligne sous Unix par le seul caractere 0x0A. 
* Codage des fins de ligne sous Macintosh par le seul caractere 0x0D. 
:::

**Tester le contenu d'un fichier texte en version Unix / Dos / Mac**
    
    cmp monfichier.unix monfichier.dos

    diff monfichier.unix monfichier.dos

    diff monfichier.unix monfichier.mac

**Combien de lignes, de mots et de caractères comportent les fichiers "montexte.unix", "montexte.dos" et "montexte.mac"?**	

    wc monfichier.unix

```!
12 7 40 monfichier.unix
```

    wc monfichier.dos

```!
12 7 52 monfichier.dos
```

    wc monfichier.mac

```!
0 7 40 monfichier.mac
```

# 2e exercice

**Se localiser dans la hiérarchie**

    pwd

**Détecter la présence de fichiers**
    
    ls -la

```!
drwxr-xr-x 2  nico nico 4096 2007-02-01 11:25 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:25 ..
```

> Ce sont les entrées vers la racine du repertoire et la racine du répertoire père

**Entrer du texte dans Mon_fichier**

    echo aaaaaaaaaaaaaaaaaa > Mon_fichier
    
**Lister le contenu de Mon_fichier**

    cat Mon_fichier

```!
aaaaaaaaaaaaaaaaaa
```
**Lister son propre répertoire**

    ls

```!
Mon_fichier
```
    ls -l

```!
total 12
drwxr-xr-x 2  nico nico 4096 2007-02-01 11:28 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:25 ..
-rw-r--r-- 1  nico nico   19 2007-02-01 11:28 Mon_fichier
```

**Lister les catalogues /bin et /dev**

    ls /bin
    ls /dev

**Créer les sous-répertoires `Source` et `Data`**

    mkdir Source Data

**Se positionner dans `Source`**

    cd source

**Lister les répertoires**
    
    ls -la

```!
total 8
drwxr-xr-x 2 nico nico 4096 2007-02-01 11:29 .
drwxr-xr-x 4 nico nico 4096 2007-02-01 11:29 ..
```
**Revenir sous le répertoire de départ et détruire `Source`**

    cd ..
    rmdir Source

**Créer un deuxième fichier `Mon_fichier_2`**

    touch Mon_fichier_2
    ls -la

```!
total 16
drwxr-xr-x  3 nico nico 4096 2007-02-01 11:31 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:31 ..
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:29 Data
-rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
-rw-r--r--  1 nico nico    0 2007-02-01 11:31 Mon_fichier_2
```

**Copier chaque fichier en fichier .old** 	

    cp Mon_fichier Mon_fichier.old
    cp Mon_fichier_2 Mon_fichier_2.old
    ls -la

```!
total 20
drwxr-xr-x 3  nico nico 4096 2007-02-01 11:39 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:31 ..
drwxr-xr-x 2  nico nico 4096 2007-02-01 11:29 Data
-rw-r--r-- 1  nico nico   19 2007-02-01 11:28 Mon_fichier
-rw-r--r-- 1  nico nico    0 2007-02-01 11:31 Mon_fichier_2
-rw-r--r-- 1  nico nico    0 2007-02-01 11:38 Mon_fichier_2.old
-rw-r--r-- 1  nico nico   19 2007-02-01 11:38 Mon_fichier.old
```
**Créer un répertoire `Old`**

    mkdir old

**Déplacer les fichiers avec l’extension .old dans le répertoire `Old`**
    
    mv *.old Old
    ls -la Old
    
```!
total 12
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 .
drwxr-xr-x  4 nico nico 4096 2007-02-01 11:39 ..
-rw-r--r--  1 nico nico    0 2007-02-01 11:38 Mon_fichier_2.old
-rw-r--r--  1 nico nico   19 2007-02-01 11:38 Mon_fichier.old
```
    ls -l

```!
total 20
drwxr-xr-x  4 nico nico 4096 2007-02-01 11:39 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:31 ..
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:29 Data
-rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
-rw-r--r--  1 nico nico    0 2007-02-01 11:31 Mon_fichier_2
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 Old
```

**Copier les fichiers sans extension dans le répertoire `Data`**
    
    cp * Data
    ls -la Data
    
```!
total 12
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:41 .
drwxr-xr-x  4 nico nico 4096 2007-02-01 11:39 ..
-rw-r--r--  1 nico nico   19 2007-02-01 11:41 Mon_fichier
-rw-r--r--  1 nico nico    0 2007-02-01 11:41 Mon_fichier_2
```

    ls -l

```!
total 20
drwxr-xr-x  4 nico nico 4096 2007-02-01 11:39 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:31 ..
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:41 Data
-rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
-rw-r--r--  1 nico nico    0 2007-02-01 11:31 Mon_fichier_2
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 Old
```

**Sous le répertoire de départ, créer un lien matériel `Mon_lien` équivalent à `Mon_fichier_2`**

    ln Mon_fichier_2 Mon_lien
    ls -la

```!
total 20
drwxr-xr-x  4 nico nico 4096 2007-02-01 11:54 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:43 ..
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:41 Data
-rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
-rw-r--r--  2 nico nico    0 2007-02-01 11:31 Mon_fichier_2
-rw-r--r--  2 nico nico    0 2007-02-01 11:31 Mon_lien
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 Old
```
**Lister les deux fichiers `Mon_lien` et `Mon_fichier_2` en affichant leur numéro d’inode**

    ls -lai
    
```!
total 20
 16457 drwxr-xr-x  4 nico nico 4096 2007-02-01 11:54 .
868403 drwxr-xr-x 22 nico nico 4096 2007-02-01 11:43 ..
 16619 drwxr-xr-x  2 nico nico 4096 2007-02-01 11:41 Data
 16624 -rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
 16597 -rw-r--r--  2 nico nico    0 2007-02-01 11:31 Mon_fichier_2
 16597 -rw-r--r--  2 nico nico    0 2007-02-01 11:31 Mon_lien
 16632 drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 Old
```

> Leurs numéros d'inode sont identiques donc ces deux fichiers n'en sont physiquement qu'un seul.

**Supprimer `Mon_lien`. `Mon_fichier_2` a-t-il disparu ?**

    rm Mon_lien
    ls -lai
    
```!
total 20
 16457 drwxr-xr-x  4 nico nico 4096 2007-02-01 11:56 .
868403 drwxr-xr-x 22 nico nico 4096 2007-02-01 11:43 ..
 16619 drwxr-xr-x  2 nico nico 4096 2007-02-01 11:41 Data
 16624 -rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
 16597 -rw-r--r--  1 nico nico    0 2007-02-01 11:31 Mon_fichier_2
 16632 drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 Old
```

> "Mon_fichier_2" existe toujours.

**Sous votre répertoire de départ, créez un lien symbolique `Mon_nouveau_lien` sur `Mon_fichier_2`**	
```
ln -s Mon_fichier_2 Mon_nouveau_lien
```

**Lister les deux fichiers `Mon_nouveau_lien` et `Mon_fichier_2`**

    ls -la

```!
total 20
drwxr-xr-x  4 nico nico 4096 2007-02-01 11:57 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:43 ..
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:41 Data
-rw-r--r--  1 nico nico   19 2007-02-01 11:28 Mon_fichier
-rw-r--r--  1 nico nico    0 2007-02-01 11:31 Mon_fichier_2
lrwxrwxrwx  1 nico nico   13 2007-02-01 11:57 Mon_nouveau_lien -> Mon_fichier_2
drwxr-xr-x  2 nico nico 4096 2007-02-01 11:39 Old
```

> Le lien est clairement mis en evidence par le caractere `l` et par l'affichage du nom du fichier lie. La taille n'est pas bonne.

**Supprimer `Mon_fichier_2`. `Mon_nouveau_lien` a-t-il disparu ?**

    rm Mon_fichier_2
    ls -la

```!
total 20
drwxr-xr-x 4 nico nico 4096 2007-02-01 11:59 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:43 ..
drwxr-xr-x 2 nico nico 4096 2007-02-01 11:41 Data
-rw-r--r-- 1 nico nico 19 2007-02-01 11:28 Mon_fichier
lrwxrwxrwx 1 nico nico 13 2007-02-01 11:57 Mon_nouveau_lien -> Mon_fichier_2
drwxr-xr-x 2 nico nico 4096 2007-02-01 11:39 Old
```

> Le lien existe toujours mais est brisé. Il est caracterisé par un code couleur spécifique dans le shell utilisé.

**Quelle est la taille totale des fichiers contenus dans votre répertoire ?**

    du -b

```!
4115 ./Old
4115 ./Data
12358 .
```
> La taille est approximative en raison de l'utilisation de blocs de 512 octets.

**Effacer tous les fichiers créés**

    rm -r *
    ls -la
    
```!
total 8
drwxr-xr-x  2 nico nico 4096 2007-02-01 12:03 .
drwxr-xr-x 22 nico nico 4096 2007-02-01 11:43 ..
```

# 3e exercice

## Créer un espace de travail pour 4 utilisateurs

**1. Création des groupes et des utilisateurs**

Création de 2 groupes :

        groupadd group1
        groupadd group2
        cat /etc/group
        ...
        group1:x:1001:
        group2:x:1002:

Création de 4 utilisateurs : 

```
useradd -m u1
useradd -m u2
useradd -m u3
useradd -m u4
cat /etc/passwd
...
u1:x:1001:100::/home/u1:/bin/sh
u2:x:1002:100::/home/u2:/bin/sh
u3:x:1003:100::/home/u3:/bin/sh
u4:x:1004:100::/home/u4:/bin/sh
```

```
ls -l /home
```

```
total 20
...
drwxr-xr-x 2 u1 users 4096 2007-02-01 12:12 u1
drwxr-xr-x 2 u2 users 4096 2007-02-01 12:12 u2
drwxr-xr-x 2 u3 users 4096 2007-02-01 12:12 u3
drwxr-xr-x 2 u4 users 4096 2007-02-01 12:12 u4
```

Placement des utilisateurs dans leurs groupes : 

        usermod -G group1 u1
        usermod -G group1,group2 u2
        usermod -G group2 u3
        usermod -G group1,group2 u4
        cat /etc/group
        ...
        group1:x:1001:u1,u2,u4
        group2:x:1002:u2,u3,u4

Changement de propriétaire des répertoires : 

```
chown u1:group1 /home/u1
chown u2:group1 /home/u2
chown u3:group2 /home/u3
chown u4:group2 /home/u4
```

Création des répertoires communs : 

```
mkdir /home/group1
mkdir /home/group2
```

Mise en place des permissions pour permettre aux utilisateurs d'écrire dans le répertoire de leur groupe : 

```
chgrp group1 /home/group1
chgrp group2 /home/group2
```

Mise en place de la permission pour protéger de l'effacement tout en autorisant l'écriture : 

> À ce stade, on ne sait pas résoudre la dernière problématique. Soit on fait confiance aux utilisateurs, soit on passe par `root` pour ajouter les fichiers et on ne donne pas la permission «w».

Cas le plus permissif

        chmod g=rwx /home/group1
        
ou

        chmod 770 /home/group1

Cas le moins permissif

        chmod g=700 /home/group1

Activation d'un utilisateur

        passwd u1
        Enter new UNIX password:
        Retype new UNIX password:
        passwd : le mot de passe a été mis à jour avec succès
        cat/etc/shadow
        ...
        u1:$1$kiUUra9s$AxchvKz0J9OBJPXO8qNf./:13545:0:99999:7:::
        u2:!:13545:0:99999:7:::
        u3:!:13545:0:99999:7:::
        u4:!:13545:0:99999:7:::

**2. Modification du profil**

Script possible, dans `/etc/profile` pour éviter de le recopier pour chaque utilisateur

        echo "Bienvenue"
        echo "entrez U pour travailler dans votre repertoire"
        echo "entrez G pour travailler dans le repertoire de votre groupe"
        read CHX
        while [ $CHX != 'U' ] && [ $CHX != 'G' ]
        do
        echo "Entrez U ou G ..."
        read CHX
        done
        if [ $CHX == "G" ]
        then
        case $USER in
        "u1") export HOME=/home/group1;;
        "u2") export HOME=/home/group1;;
        "u3") export HOME=/home/group2;;
        "u4") export HOME=/home/group2;;
        esac
        cd $HOME
        fi

**3. Choix de la valeur du umask**

Les valeurs conseillées sont:
- 066 pour échanger facilement des fichiers avec l'ensemble des utilisateurs
- 067 pour échanger des fichiers seulement avec les membres des groupes dont on est membre,
- 077 pour travailler seul

Les valeurs 066 et 067 offrent le meilleur compromis entre la sécurité et la souplesse. Elles permettent le parcours des répertoires sans en autoriser l'examen avec la commande "ls" tout en autorisant l'accès à des répertoires fils dont les droits seront plus permissifs, utilisés pour échanger des fichiers…" dans "Unix utilisation administration système et réseau" par Christian Pellisier. Dans notre exemple, on choisit plutôt la valeur 067.
