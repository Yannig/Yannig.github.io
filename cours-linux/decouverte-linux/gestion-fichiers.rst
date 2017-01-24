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

Changement des droits
~~~~~~~~~~~~~~~~~~~~~

Les droits sur un fichier peuvent se voir sur la partie droite de la commande **ls -l**. Chaque colonne va indiquer les droits pour les éléments suivants :

- Le type de fichier (d pour dossier et - pour un fichier) ;
- Les droits du propriétaire sur 3 caractères ;
- Les droits du groupe sur 3 caractères ;
- Les droits pour les autres également sur 3 caractères.

Chaque séquence représentent les droits sous la forme des lettres rwx (pour read/write/exec). La présence d'un tiret marque l'absence de ce droit. Ces droits peuvent aussi être appliqué en utilisant :

- Une représentation octale avec des chiffres de 0 à 7 ;
- Soit une valeur par ajout/retrait de droit.

Ci-dessous quelques exemples de valeur :

=================  ==========================  ==============================================================================
Exemple de droit    Valeur vu avec **ls -l**    Droits correspondants
=================  ==========================  ==============================================================================
777                 rwxrwxrwx                   Tous les droits à tous le monde
-----------------  --------------------------  ------------------------------------------------------------------------------
664                 rw-rw-r--                   Droit lecture/écriture pour user et groupe et droit lecture pour les autres
-----------------  --------------------------  ------------------------------------------------------------------------------
750                 rwxr-x---                   Execution/lecture pour utilisateur et groupe, droit écriture pour le
                                                propriétaire. Rien pour les autres
-----------------  --------------------------  ------------------------------------------------------------------------------
u+rx                r?x??????                   Ajout des droits lecture/exécution pour le propriétaire en plus de ceux
                                                existants
-----------------  --------------------------  ------------------------------------------------------------------------------
g+rx,o+r            ???r?xr??                   Ajout des droits lecture pour tous le groupe et les autres et droits
                                                d'exécution sur le groupe.
-----------------  --------------------------  ------------------------------------------------------------------------------
a+rx                r?xr?xr?x                   Ajout des droits lecture/exécution pour tous en plus de ceux existants
=================  ==========================  ==============================================================================

.. note:: Il existe d'autre type de droit (u+s ou o+t) très spécifique au système que nous ne verrons pas ici.

Ce changement de droit se fait à l'aide de l'outil **chmod** :

.. code-block:: bash

    # Attribution droit en lecture à tous sur le fichier /tmp/test
    chmod a+r /tmp/test

Gestion propriétaire
~~~~~~~~~~~~~~~~~~~~

L'affichage du propriétaire d'un fichier, se fait là encore avec la commande **ls -l**. Afin de changer le propriétaire, il est possible d'utiliser les commandes suivantes :

- chown UTILISATEUR NOM_FICHIER : change le propriétaire du fichier ;
- chgrp GROUPE NOM_FICHIER : change le groupe propriétaire d'un fichier.

Exercice sur la gestion des fichiers
------------------------------------

Réaliser les opérations suivantes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Créer un répertoire **/tmp/test**
- Recopier le fichier **/etc/debian_version** dans le répertoire /tmp/test
- Afficher son contenu
- Afficher les informations sur ce fichier
- Attribuer des droits en écriture à tous
- Afficher les informations sur ce fichier
- Essayer de supprimer le répertoire **/tmp/test**
- Supprimer le fichier **/tmp/test/debian_version**
- Réessayer de supprimer le répertoire **/tmp/test**
