Gestion des fichiers sous Linux
===============================

Opérations simples
------------------

Lister les fichiers d'un répertoire
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pour connaître le contenu d'un répertoire, on peut utiliser la commande **ls** :

.. code-block:: bash

    ls

Afin d'avoir plus d'information, il est possible d'ajouter les options suivantes :

- ls -l : Affichage des informations étendues sur les fichiers ;
- ls -ltr : affichage dans l'ordre temporel inverse.

Ci-dessous un exemple de lancement de ls -l :

::

    -rwxr-xr-x  1 yannig micro      101 févr. 24  2015 test.sh
    drwxr-xr-x  6 yannig micro     4096 nov.  22 18:31 bin
    -rw-r--r--  1 yannig micro     1055 nov.   6 11:06 README
    lrwxrwxrwx  1 yannig micro       60 mars   2  2015 readme -> README
    drwx------ 22 yannig micro     4096 juin  23 09:22 protege

Dans cette capture d'écran, nous retrouvons quelques informations intéressantes :

- Le type/droits sur les fichiers (exemple : -rwxr-xr-x) ;
- Le propriétaire (ici l'utilisateur yannig) ;
- Le groupe (ici micro) ;
- La date de création (ex : févr. 24  2015 ou nov.   6 11:06) ;
- le nom du fichier.

On peut voir la présence de 5 fichiers :

- test.sh : script shell exécutable ;
- bin : répertoire ;
- README : fichier texte ;
- readme : lien symbolique pointant vers README ;
- protege : répertoire protégé en accès.

Recherche de fichier
~~~~~~~~~~~~~~~~~~~~

Dans le cas où vous ne sauriez pas où vous avez stocké un fichier, vous pouvez également faire appel à la commande **find**.

Elle vous donnera tous les fichiers se trouvant dans le répertoire courant ainsi que dans les sous-répertoires.

Gestion des répertoires
~~~~~~~~~~~~~~~~~~~~~~~

Il est possible d'utiliser un ensemble d'utilitaire pour gérer l'état d'un répertoire :

- Création avec la commande **mkdir** ;
- Suppression d'un répertoire (il doit être vide) avec **rmdir** ;
- Renommage d'un répertoire avec la commande **mv**.

Gestion d'un fichier texte
~~~~~~~~~~~~~~~~~~~~~~~~~~

Il existe de nombreuses commandes permettant de consulter ou créer/manipuler les fichiers sous Linux. Nous nous limiterons aux commandes suivantes :

- Affichage du contenu d'un fichier texte : cat, more ou less NOM_FICHIER ;
- Rechercher une valeur dans le fichier : grep CHAINE NOM_FICHIER ;
- Compter le nombre de ligne dans un fichier : wc -l NOM_FICHIER ;
- Renommage d'un fichier : mv NOM_ORIGINE NOUVEAU_NOM ;
- Suppression d'un fichier : rm NOM_FICHIER.

Liens symboliques
~~~~~~~~~~~~~~~~~

Les liens symboliques sous Linux n'ont pas vraiment d'équivalent sous Windows (on peut néanmoins le comparer à un raccourci Windows). Il s'agit d'un fichier un peu particulier qui permet de pointer vers une ressource qui se trouve ailleurs. On peut l'utiliser indifféremment pour un fichier ou un répertoire.

Leur création se fait à l'aide de la commande **ln** avec l'option **-s**. Exemple :

.. code-block:: bash

    ln -s source alias

Leur suppression se fait comme pour les fichiers à l'aide de la commande **rm**.

Gestion des droits
------------------

Nous avons appris à manipuler les fichiers. Nous allons maintenant voir comment attribuer des droits ou les retirer dans le cas où vous ne voudriez pas les laisser en accès libre.

Gestion propriétaire
~~~~~~~~~~~~~~~~~~~~

Pour connaître le propriétaire d'un fichier, il faut utiliser la commande **ls -l**. Afin de changer le propriétaire, il est possible d'utiliser les commandes suivantes :

- chown NOM_UTILISATEUR NOM_FICHIER : change le propriétaire du fichier ;
- chgrp NOM_GROUPE NOM_FICHIER : change le groupe propriétaire d'un fichier.

