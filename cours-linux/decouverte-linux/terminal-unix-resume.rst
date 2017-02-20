Résumé commandes Unix
=====================

Commandes bash de base
----------------------

Afficher le contenu du répertoire dir :  ``ls -la dir``

Se positionner à la racine de son espace personnel :  ``cd`` ou ``cd ~`` ou ``cd $HOME``

.. note:: $HOME et ~ désignent le même chemin, le répertoire défini comme racine du login correspondant, par exemple /home/yannig.

Effacer le répertoire dir et ses sous-répertoires : ``rm -rf dir``

Renommer dir1 sous le nom de dir2 : ``mv dir1 dir2``

Effacer le terminal : ``clear``

Ajouter $HOME/bin au PATH : ``export PATH=$PATH:$HOME/bin``

Changer l'invite de commande : ``export PS1='$ '``

Les variables d'environnement comme PS1, PATH, ... sont à changer de préférence dans les fichiers de configuration de bash : .bash_login, .bash_profile, .bashrc, ...

Gestion zéro des archives tar.gz
--------------------------------

Extraire le contenu tp.tar.gz : ``tar xvfz tp.tar.gz``

Créer une archive contenant le répertoire tp : ``tar cvfz tp.tar.gz tp``

Pour créer l'archive contenant tous les fichiers du répertoiretp, il faut se positionner avant au dessus de tp. Par exemple, si le chemin absolu de tp est /home/yannig/travaux/tp, alors les commandes sont :

- ``cd /home/yannig/travaux``
- ``tar cvfz tp.tar.gz tp``

Commandes de contrôle des processus
-----------------------------------

``ps -ef`` : voir tous les processus en cours.

``ps faux`` : voir aussi les arbres de filiation.

``pstree`` affiche un arbre de tous les processus en cours.

``top`` : affichage dynamique des process.

``kill -SIGINT pid`` : interrompre le processus pid.

``kill -SIGKILL pid`` : tuer le processus pid qui résiste à SIGINT.

``killall -INT prog`` : interrompre tous les exemplaires de processus de nom prog.

``killall -KILL prog`` tuer tous les exemplaires des processus de nom prog
