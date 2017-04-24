Introduction à la programmation Shell
=====================================

Le shell sous Linux est un langage qui posséde tout ce dont vous avez besoin pour des petits besoins :

- Gestion de variable ;
- Vérification de condition (if then else) ;
- Affichage d'éléments ;
- Boucle de programme (while, for etc.).

Dans ce qui va suivre, nous allons faire une petite introduction sur le sujet.

Gestion de variable
-------------------

En shell, il n'y a pas de déclaration de variable. Si vous en avez besoin, faîtes votre affectation et vous pourrez réaccéder à la valeur plus tard sans problème.

.. code-block:: bash

    # Affectation
    a=1
    # Affichage du contenu de la variable
    echo $a

Il est également possible de saisir la valeur d'une variable à l'aide du mot clé **read**.

.. code-block:: bash

    # Lecture de la valeur de a
    echo "Merci de rentrer une valeur pour a"
    read a
    # Affichage du contenu de la variable
    echo "Vous avez saisi la valeur suivante : $a"

Faire un calcul
---------------

Là encore, rien de bien difficile si ce n'est qu'il faut ajouter le mot clé **let** en début de ligne.

.. code-block:: bash

    # Affectation
    a=1
    b=2

    # calcul de c
    let c=a+b

    # Affichage du résultat
    echo "c a pour valeur $c"

    # Une division
    let d=a/2

    # Le reste d'une division
    let e=100%4

Vérification d'une condition
----------------------------

En plus des opérations classiques d'affectation, il est possible de vérifier la valeur d'une variable afin de faire un traitement sous certaines conditions.

.. code-block:: bash

    # Affectation
    a=1
    # Est-ce que a est plus grand que 0 ?
    if [ "$a" -gt 0 ]; then
      echo "a est plus grand que 0"
    fi

    b=""
    # Est ce que b est vide ?
    if [ -z "$b" ]; then
      echo "Il n'y a rien dans la variable b"
    else
      echo "Il y a quelque chose dans la variable b (b=$b)"
    fi

Mettre fin à l'exécution de mon shell
-------------------------------------

Il est possible d'arrêter à tout moment le déroulement de mon programme en utilisant le mot clé **exit**. Par défaut, le code retour sera de 0 (ce qui équivaut à le programme c'est bien passé). Si vous mettez une autre valeur que 0, par convention, le système considérera que le programme c'est mal passé.

.. code-block:: bash

    # Lancement d'un test sur le contenu d'une variable
    msg="erreur"

    if [ $msg = "erreur" ]; then
      echo "Il y a une erreur"
      exit 1
    else
      echo "Tout va bien"
    fi

Quelques variables à connaître
------------------------------

Par défaut, le shell de votre session initialise plein de variables différentes. En voici quelques unes qui pourraient vous être utile :

- **$$** : PID du process courant. Peut vous servir comme chiffre aléatoire ;
- **$HOME** : Contient par défaut le chemin de votre utilisateur (ex : /home/yannig) ;
- **$USER** : Votre nom d'utilisateur (ex : yannig) ;
- **$PATH** : Chemin dans lequel le shell va faire sa recherche des binaires du système ;
- **$LANG** : Langue configuré dans votre système.

Si vous voulez voir toutes les variables disponibles sur votre système, vous pouvez utiliser les commandes **env** ou **set**. Ces commandes vous afficheront la liste des variables à disposition.

Boucles de controle
-------------------

Les mots clés **while** et **for** permettent de gérer des boucles d'exécution.

.. code-block:: bash

    # Boucle sur saisie de l'utilisateur
    a=""

    while [ "$a" = "" ]
    do
      echo "Merci de saisir quelque chose"
      read a
    done
    echo "Fin de la boucle while"

.. code-block:: bash

    # Boucle sur quelques éléments
    for i in 1 2 3
    do
      echo "i contient $i"
    done
    echo "Fin de la boucle for"

Exercice
--------

Réaliser un petit jeu qui va réaliser les choses suivantes :

Calcul du nombre aléatoire
~~~~~~~~~~~~~~~~~~~~~~~~~~

- Tirer un nombre aléatoire entre 0 et 100 ;
- L'afficher

Mise en place d'un boucle
~~~~~~~~~~~~~~~~~~~~~~~~~

- Mettre en place la boucle infinie
- Inviter l'utilisateur à saisir un nombre entre 0 et 100 ;
- Faire le test si égalité => sortie du programme ;
- Si inférieur => indiquer que le chiffre est plus grand ;
- Si supérieur => indiquer que le chiffre est moins grand.
