# Compte rendu TP1 - Installation d’Ubuntu Server et prise en main du shell


## Exercie 2

### **Manuel**

**1.** Rôle de la commande which :

**which** renvoie le chemin des fichiers (ou liens) qui seraient exécutés dans l'environnement courant si ses arguments avaient été donnés comme commande dans un interpréteur de commandes strictement conforme à POSIX. Pour ce faire **which** cherche dans la variable **PATH** les fichiers exécutables correspondants aux noms des arguments. **Which** ne normalise pas les chemins.

> `man which`


**2.** Recherche du mot "option" :

Il suffit de mettre /option pour rechercher le mot option dans la page which.

> `man which /option`

**3.** Quitter le manuel :

Il suffit de presser la touche "**q**".

**4.** Première page de la section 6 :

Pour y accedéder il suffit de taper la commande suivante :
>`man 6 intro`

La section 6 du manuel aborde la description de jeux et de marrant petit programme.

### **Navigation dans l'arborescence des fichiers**

**1.** Pour aller dans le dossier /var/log il faut taper la commande suivante :

>` cd /var/log`

**2.** Pour revenir dans le dossier parent il faut taper la commande suivante :

>` cd ..`

**3.** Pour revenir au dossier personnel il faut taper la commande suivante :

>` cd ~`

**4.** Pour accéder au dossier var il faut taper la commande :
>`cd ../../var`

**5.** Il est impossible d'accéder au dossier /root. Le message suivant "**Permission denied**" nous informe que nous n'avons pas la permission de rentrer dans le dossier.

**6.** La commande ne marche pas car la commande **sudo** ne s'applique qu'au programme hors **cd** est une commande intégré au système.

**7.** Voici la liste des commandes permettant la création des dossiers et fichiers suivant l'arborescence souhaitez :

Création du Dossier1 :

>`mkdir Dossier1`

On se déplace dans le Dossier 1 via la commande :

>`cd Dossier1`

Une fois situé dans le Dossier 1, nous pouvons créer le Fichier1 via la commande :
>`touch Fichier1`

Nous ressortons du Dossier1 via la commande :

>`cd ..`

Création du Dossier2 via la commande :

>`mkdir Dossier2`

On se déplace dans le Dossier 2 via la commande :

>`cd Dossier2`

Une fois situé dans le Dossier2 création des dossiers 2.1 et 2.2 :
>`mkdir Dossier2.1`

>`mkdir Dossier2.2`

On se déplace dans le Dossier 2.2 via la commande :

>`cd Dossier2/Dossier2.2`

Une fois situé dans le Dossier 2.2, on peut créer les fichiers 2 et 3 via la commande :
>`touch Fichier2`

>`touch Fichier3`

**8.** Il est impossible de supprimer le Fichier1 depuis le 
Dossier personnel car l'on ne se situe pas dans le bon dossier. Il est aussi impossible de supprimer le Dossier1.

**9.** La commande suivante permet de supprimer un dossier :
>` rmdir`

**10.** Il est impossible de le supprimer car la commande rmdir ne s'applique qu'au dossier vide. Or le Dossier 2 contient 2 fichiers.

**11.** Il suffit de faire la commande suivante :

>`rm -r Dossier2`

### **Commandes importantes**

**1.** La commande suivante permet d'afficher l'heure :
>`date`

La commande **time** est utilisée pour pour déterminer le temps d'exécution d'une certaine commande. 

**2.** La commande :

>`ls`

 permet d'afficher le contenu d'un répertoire (dans notre cas le dossier personnel).

 La commande 
 >`ls -la`

affiche tous les fichiers y compris les fichiers cachés. Les fichiers commençant par un point sont donc des fichiers cachés.

**3.** Le programme **ls** se situe dans le dossier personnel.

**4.** La commande **ll** est un alias de la commande ls -alF. Elle permet d'afficher les même données que la commande **ls -la** à la différence qu'il se termine par un **/**.

**5.** Il faut faire la commande :

>`cd /bin`

pour être dans le répertoire bin et par la suite on peut lancer soit la commande :

>`ls ` ou `ll`

pour voir l'ensemble des fichiers cachés ou non.

**6.** La commande 
>`ls ..`

permet l'affichage le nom des répertoires parents. Par exemple si l'on se situe dans le dossier2.2 et que l'on fait cette commande le résultat sera Dossier2.1 et Dossier2.2.

**7.** La commande :
>`pwd`

permet de spécifier le chemin complet du dossier courant.

**8.**  La commande :
>`echo 'yo' > plop`

permet d'écrire la chaine de caractère yo dans le fichier plop.

**9.** Executé 2 fois cela écrit le mot deux fois on se retrouve donc avec yoyo.

**10.** La commande **file** détermine le type d'un fichier.

**11.** Création du fichier toto qui contient la chaine de caractère "Hello Toto !" via la commande :

>`echo "Hello Toto !" > toto`

Lorsque l'on modifie le contenu du fichier **toto** cela modifie aussi le contenu du fichier **titi**

Si l'on supprime le fichier **toto** cela n'a aucune incidence sur le fichier **titi** car il conserve son contenu.

**12.** Lorsque l'on modifie le contenu de **titi** cela modifie aussi me contenu de **tutu** et inversement. Lorsque l'on supprime **titi** cela supprime le contenu de **tutu**.

**13.** Le raccourci clavier **CTRL + S** permet d'interrompre le défilement à l'écran tandis que le raccourci clavier **CTRL + Q** permet de reprendre le défliement.

**14.** Pour afficher les 5 premières lignes du fichier var/log/syslog il faut effectuer la ligne de commande suivante :

>`head -5 /var/log/syslog`

Pour afficher les 15 dernières lignes du fichier var/log/syslog il faut effectuer la ligne de commande suivante :

>`tail -15 /var/log/syslog`

Pour afficher les lignes 10 à 20 du fichier var/log/syslog il faut effectuer la ligne de commande suivante :

>`head -n 10 /var/log/syslog | tail -n 20`

**15.** La commande :

>`dmesg | less`

 est une commande sur les systèmes d'exploitation de type Unix qui affiche la mémoire tampon de message du noyau page par page.

 **16.** Le fichier **/etc/passwd** contient toutes les informations relatives aux utilisateurs (login, mots de passe, ...). Il est accessible via la commande :
 >`cat /etc/passwd`
 Il faut effectuer la commande suivante :

 >`man passwd`

 pour afficher la page manuel de ce fichier.

 **17.** La commande :

 >`sort +0 -r /etc/passwd`

 permet d'afficher seulement la première colonne triée par ordre alphabétique inverse.

**18.** La commande :

>`wc -l /etc/passwd`

nous donne le nombre d'utilisateur. D'après le résultat de la commande il y a 31 utilisateurs.

**19.** La commande :

>`man -k conversion`

permet d'obtenir le nombre de page comportant le mot "conversion" dans leur descritpion. On obtient donc 4 lignes de résultats qui correspondent à 4 pages du manuel comportant le mot "conversion".

**20.** La commande suivante : 
>`find / -name passwd`

permet de trouver tous les fichiers se nommant passwd présent sur la machine.

**21.** La commande suivante :

>`find / -name passwd > ~/list_passwd_files.txt 2>> /dev/null`

permet que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null.

**22.** Via la commande :

>`grep -ll`

on peut voir que l'alias ll est défini dans grep [OPTION]... PATTERNS[FILE]...

**23.** Avec la commande :

>`locate history.log`

on peut trouver le chemin menant au fichier hisotry.log. C'est le chemin suivant :
* /var/log/apt/history.log

**24.** Le fichier n'apparaît pas car il n'est pas compris dans la base de données des fichiers indéxés.

## Exercie 4 - Personnalisation du shell

1. Création d'une copie du fichier ~/.bashrc via la ligne de commande :

>`cp ~/.bashrc .bashrc_bak`

3. En effet après la manipulation de la question 2 et l'exécution de la commande suivante :

>`source .bashrc`

L'invite de commande passe en couleur. Le nom de mon dossier personnel "abitbol@serveur" devient vert et le "~" devient bleu quant au ":" et au "$" il reste blanc.

4. Le but est de modifiez l’invite de commande pour qu’elle s’aﬀiche sous la forme suivante : [heure] - user@host:chemin_courant$ avec l'heure en magenta user et l'host en vert et le chemin courant en bleu. Pour cela il faut modifier  la séquence particulière suivante:

>`\[\033[1;32m]\u@\h\[\033[00m\] `

afin qu'elle devienne comme suit et intégre les modifications citées précèdemments :

>`\[\e[35m\A\e[0m-\[\033[1;32m]\u@\h\[\033[00m\] `










