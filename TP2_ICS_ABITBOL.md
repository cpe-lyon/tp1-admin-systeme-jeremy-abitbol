 # TP 2 - Bash

 ### Exercice 1. Variables d’environnement


 1. Dans quels dossiers bash trouve-t-il les commandes tapées par l’utilisateur? 

La variable PATH indique à bash où trouver les commandes tapées parl’utilisateur. Quand on tape une commande,bash regarde successivement dans chacun de ces dossiers jusqu’à la trouver.

>`printenv PATH`

Le résultat est le suivant :
* /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

 2. Quelle variable d’environnement permet à la commande cd tapée sans argument de vous ramener dans votre répertoire personnel? 

 La variable d'environnement **HOME** permet à la commande cd tapée sans argument de nous ramener dans notre répertoire personnel.

 3. Explicitez le rôle des variables LANG, PWD, OLDPWD, SHELL et _. 
 
 La variable **LANG** permet de définir la langue et le codage de caractère informatique. La commande suivante :
 >`printenv LANG`

 retourne *fr_FR.UTF-8*

 La variable **PWD** indique le chemin vers le dossier personnel. Dans notre cas la commande suivante :
 >`printenv PWD`

 retourne */home/abitbol*.

 La variable **OLDPWD** indique le dernier changement effectué via la commande **cd** dernièrement. La commande suivante :

 >`printenv PWDOLD`

 retourne */home/abitbol/Dossier1*

 La variable **SHELL** indique le chemin suivant : */bin/bash* qui est le chemin menant à l'interpreteur SHELL utilisé par défaut.

 La variable **_** indique la dernier commande utilisé par l'utilisateur.  La commande suivante :
 >`printenv _`

 retourne */usr/bin/printenv*

 
 4. Créez une variable locale MY_VAR (le contenu n’a pas d’importance). Vérifiez que la variable existe. 

La commande suivante permet de créer la varibla locale MY_VAR avec le contenu *"bonjour"*.

>`MY_VAR="bonjour"`

Pour afficher le contenu, on fait la commande suivante :

>`echo $MY_VAR`

 5. Tapez ensuite la commande bash. Que fait-elle? La variable MY_VAR existe-t-elle? Expliquez. A la fin de cette question, tapez la commande exit pour revenir dans votre session initiale. 

 La commande **bash** ouvre une nouvelle invite de commande SHELL, ce qui fait disparaitre le contenu de notre variable MY_VAR.
 
 6. Transformez MY_VAR en une variable d’environnement et recommencez la question précédente. Expliquez. 

 Même en ouvrant une nouvelle fenêtre **Shell** le contenu de la variable est visible et consultable. La variable étant devenu globale elle est donc accesible via n'importe qu'elle invite de commande shell contrairement à la variable globale.
 
 7. Créer la variable d’environnement NOMS  ayant pour contenu vos noms de binômes séparés par un espace. Afficher la valeur de NOMS pour vérifier que l’affectation est correcte.

 La commande suivante permet de créer la variable d'environnement NOMS :
 >`export NOMS="abitbol jeremy"`

 Avec la commande suivante on peut vérifier le contenu de la variable d'environnement :

 >`echo $NOMS`

 qui retourne *abitbol jeremy* et donc le bon résultat. L'affectation est juste.

 8. Ecrivez une commande qui affiche ”Bonjour à vous deux, binôme1 binôme2!” (où binôme1 et binôme2 sont vos deux noms) en utilisant la variable NOMS. 
`
Voici la commande :
 >`echo "Bonjour à vous deux, $NOMS"`
 
 qui retourne le résultat demandé :

 *Bonjour à vous deux, abitbol jeremy*

 9. Quelle différence y a-t-il entre donner une valeur vide à une variable et l’utilisation de la commande unset? 

 Il n'y a aucune différence entre donner une valeur vide à une variable et l'utilisation de la commande unset. Le résultat reste le même une ligne de résultat vide. 

 10. Utilisez la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre dossier personnel d’après bash)

La commande suivante permet d'écrire la phrase *$HOME = chemin* :

 >`echo '$HOME='"$HOME"`

 retourne le résultat suivant :
*$HOME=/home/abitbol*

## Programmation Bash


Pour créer le dossier "script" il faut effectuer la commande suivante :
>`mkdir script`

Pour aller dans le dossier script il faut effectuer la commande suivante :
>`cd script`

Pour afficher le chemin jusqu'au script il faut effectuer la commande suivante :
>`pwd`

qui retourne le résultat suivant :

>`/home/abitbol/script`
 
Et enfin, on peut ajouter le chemin de la manière suivante :

>`export PATH=$PATH:/home/abitbol/script`


### Exercice 2. Contrôle de mot de passe 

Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par l’utilisateur ne doit pas s’afficher.


La commande suivante permet la création du fichier :

>`touch testpwd.sh`

Il faut rendre le script exécutable via la commande :

>`chmod u+x testpwd.sh`

La commande suivante permet de rentrer dans nano :

>`nano testpwd.sh`

Voici le code effectué pour le contrôleur de mot de passe :
<pre>
#!/bin/bash                             
PASSWORD="test"
echo "Veuillez saisir votre mot de passe"
read -s mdp
if [ $mdp = $ PASSWORD ]; then
    echo "Mot de passse correcte"
else
    echo "Mot de passe incorrecte"
fi
</pre>
Avec la ligne de commande suivante je peux lancer le script :
>`./testpwd.sh`

Cela me permet de vérifier si monde script fonctionne.

### Exercice 3. Expressions rationnelles 

Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre est un nombre réel.

La commande suivante permet la création du fichier :

>`touch exo3.sh`

Il faut rendre le script exécutable via la commande :

>`chmod u+x exo3.sh`

La commande suivante permet de rentrer dans nano :

>`nano exo3.sh`

Voici le code effectué pour le contrôle d'utilisateur:
<pre>
#!/bin/bash
function is_number()
{
    re='^[+-]?[0-9]+([.][0-9]+)?$'
    if ! [[ $1 =~ $re ]]; then
        return 1
    else
        return 0
    fi
}
is_number $1
if [ "$?" = "0" ]; then
    echo "C'est un nombre réel"
else
    echo "Ce n'est pas un nombre réel"
fi
</pre>
Avec la ligne de commande suivante je peux lancer le script :
>`./exo3.sh *parametre*`

Le mot parametre entre étoile est le paramètre que prend la fonction.

Cela me permet de vérifier si monde script fonctionne.

### Exercice 4. Contrôle d’utilisateur

Écrivez un script qui vérifie l’existence d’unutilisateur dont le nom est donné en paramètre du script. Si le script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation:nom_du_scriptnom_utilisateur”, où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre script, le message doit changer automatiquement)

La commande suivante permet la création du fichier :

>`touch control_user.sh`

Il faut rendre le script exécutable via la commande :

>`chmod u+x control_user.sh`

La commande suivante permet de rentrer dans nano :

>`nano control_user.sh`

Voici le code effectué pour le contrôle d'utilisateur:
<pre>
#!/bin/bash
new_user=$1
id -u "$new_user"> /dev/nul 2>&1
if [ "$?" = "0" ]; then
    echo "Utilisateur valide"
elif [ -z "$new_user" ]; then
    echo "Utilisation : $0 nom_utilisateur"
else
    echo "Utilisateur invalide"
fi
</pre>

Avec la ligne de commande suivante je peux lancer le script :
>`./control_user.sh *parametre*`

Le mot parametre entre étoile est le paramètre que prend le script. Le script marche avec ou sans paramètre et affiche des résultats différents qui sont correctes.

Cela me permet de vérifier si monde script fonctionne.

### Exercice 5. Factorielle 

Écrivez un programme qui calcule la factorielle d’un entier naturel passé en paramètre (on supposera que l’utilisateur saisit toujours un entier naturel).

La commande suivante permet la création du fichier :

>`touch facto.sh`

Il faut rendre le script exécutable via la commande :

>`chmod u+x facto.sh`

La commande suivante permet de rentrer dans nano :

>`nano facto.sh`

Voici le code effectué pour le contrôle d'utilisateur:
<pre>
#!/bin/bash
fact()
{
    n=$1
    if [ $n = 0 ]; then
        echo 1
    else 
        echo $(( n * `fact $( n - 1 ))` ))
    fi
}
echo `fact $1`
</pre>

Avec la ligne de commande suivante je peux lancer le script :
>`./facto.sh *parametre*`

Le mot parametre entre étoile est le paramètre que prend le script. Cela me permet de vérifier si monde script fonctionne.

### Exercice 6. Le juste prix

Écrivez un script qui génère un nombre aléatoire entre 1 et 1000 et demande à l’utilisateur de le deviner. Le programme écrira ”C’est plus!”, ”C’est moins!” ou ”Gagné!” selon les cas (vous utiliserez $RANDOM).


La commande suivante permet la création du fichier :

>`touch juste_prix.sh`

Il faut rendre le script exécutable via la commande :

>`chmod u+x juste_prix.sh`

La commande suivante permet de rentrer dans nano :

>`nano juste_prix.sh`

Voici le code effectué pour le contrôle d'utilisateur:
<pre>
#!/bin/bash

echelle=1000
randomnumber=$RAMDOM

let "randomnumber %= $echelle"

echo "Veuillez saisir un nombre aléatoire entre 1 et 1000"
read number

while [ $number -ne $randomnumber ]
do
    if [ $number -lt $randomnumber ]; then
        echo "C'est plus !"
    elif [$number -gt $randomnumber ]; then
        echo "C'est moins !"
    fi

echo "Veuillez saisir un aujtre nombre"
read newnumber
number=$newnumber

done

if [ $number -eq $randomnumber ]; then
    echo "C'est gagné !"
fi
</pre>

Avec la ligne de commande suivante je peux lancer le script :
>`./juste-prix.sh`

Cela me permet de vérifier si monde script fonctionne.

### Exercice 7. Statistiques 


