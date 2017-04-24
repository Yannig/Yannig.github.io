Au secours, j'ai perdu mon mot de passe root
============================================

Méthode pour réinitialiser un mot de passe
------------------------------------------

Le fait de perdre son mot de passe root ou d'utilisateur n'est jamais très malin mais il ne s'agit pas d'une situation très critique. Nous cela, nous allons suivre la procédure suivante :

- Tout d'abord, booter sur une clé USB ou un DVD bootable avec le disque de la machine ;
- Monter le disque correspondant à ma machine (soit par le gestionnaire de fichier soit en utilisant la commande ``mount`` ;
- Passer en tant que root (généralement ``sudo su -``) ;
- Déterminer le chemin où le disque est monté (commande ``df``) ;
- Se positionner avec chroot dans le répertoire de la racine (ex : ``chroot /media/xubuntu/uuid-de-mon-disque``) ;
- Changer le mot de passe de l'utilisateur avec la commande **passwd** (ex : ``passwd yannig``).

Il existe toutefois quelques restrictions. Notamment, il faut que la distribution sur la clé USB sur laquelle vous bootez soit de la même architecture (32 ou 64 bits) que la machine que vous tentez de réparer.

Quelques informations sur les mots de passe
-------------------------------------------

En réalité, la commande **passwd** va modifier les fichiers suivants :
- /etc/passwd : ce dernier contient la liste des utilisateurs ;
- /etc/shadow : contient les hashs des mots de passe des utilisateurs ainsi que quelques informations sur ces derniers (date de création, utilisateur vérouillé etc.).

Ici, nous parlons de hash. En informatique, il s'agit de la signature d'un mot de passe. Pour faire simple, il ne faut jamais stocker les mots de passe dans un fichier même avec une protection forte. En effet, si jamais un utilisateur malveillant arrive à récupèrer le fichier /etc/shadow, ce dernier pourrait s'en servir afin de deviner le type de mot de passe que vous utilisez.

Quelques fonctions de hashage
-----------------------------

Ces fonctions de hashage sont énormément utilisées en informatique. Quelques points intéressants sur ces fonctions :

- Leur calcul est généralement très rapide ;
- Leur résultat a une taille fixe et très instable : un tout petit changement de valeur entraine un changement complet de la signature ;
- Le calcul inverse est très coûteux : si vous ne disposez que de la signature, il est très difficile de revenir à la chaîne d'origine.

Ces caractéristiques font qu'on les utilise énormément pour le chiffrement des communications (SSL, https etc.) et dans la création de signature (mot de passe, transfert de fichier etc.).

crc
~~~

Complétement obsolète. Il s'agit historiquement de l'une des plus ancienne fonction de signature. Son principe est de parcourir tous les octets dans un fichier, d'en faire la somme et de s'en servir pour savoir si le fichier a bien transféré.

Son calcul peut se faire avec la commande **cksum**.

md5
~~~

Très peu sécurisé mais déjà bien meilleur que cksum. Généralement utilisé pour 'signer' des fichiers. La commande **md5sum** peut-être utilisé pour faire ce calcul.

::

    md5sum test.sql
    a132fdd63e4ad7d9b0074812c8251cb4  test.sql

A noter qu'il existe une variante de cet algo avec un salage (cf :ref:`principe-du-salage`).

sha-1/256/512
~~~~~~~~~~~~~

Meilleur alternative à md5sum (attention toutefois à sha-1 qui a été compromis dernièrement par Google). Il est très utilisé en algo de chiffrement ou pour la signature de contenu surtout dans les version sha-256 et sha-512.

Comme pour md5, il est possible de lancer le calcul de ces hashages avec les commandes du même nom :

::

    # sha-1 :
    sha1sum test.sql
    07a1fe937d34e9f7ca0b67fdcf59ff84ee518c33  test.sql

    # sha-256 :
    sha256sum test.sql
    d0aae491031f14cbe228b1686ee21285a6f49eade39cff58caef308b5b4ba073  test.sql

    # sha-512 :
    sha512sum test.sql
    f55f50c6dc4bc303a363e04a2b20fe7b22f7df14fefce9ac1dd918697f41ca1cdbcae164422a54ab29c9ccc52be8bfc8fa3cd16998a900c1320699cf71b0ff91  test.sql

.. note:: Il est possible d'ajouter un salage pour rendre l'algorithme encore plus sûr.

.. _principe-du-salage:

Principe du salage (salt)
~~~~~~~~~~~~~~~~~~~~~~~~~

La technique du salage consiste à tirer un nombre aléatoire et de l'ajouter à l'élément que nous souhaitons signer. Prenons un petit exemple avec la signature du mot de passe 'mdp' :

- Tout d'abord, l'ordinateur tire un chiffre aléatoire sur 4 octets (ex : 457977332 soit 0x1B4C2DF4 en hexadécimal) ;
- On ajoute cette chaîne au mot de passe 'mdp' ;
- On passe le tout à la fonction de hashage ;
- On stocke le salage qui nous a permis de faire notre somme et le résultat de notre hashage.

En quoi cette opération est plus sûr