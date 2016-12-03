Création d'une clé USB Linux
============================

Téléchargement de Lili USB
--------------------------

Première étape, récupérer la dernière version de Lily USB sur le site suivant : http://www.linuxliveusb.com/fr/download

Lancer l'installation en se rendant sur le répertoire des téléchargements.

Lancement de Lili USB
---------------------

Dans le menu, lancer Lili USB :

.. image: cle-usb/lancement-lili-usb.png

.. figure: cle-usb/fenetre-lili-usb.png
   :align: right

   Fenêtre principale de Lili USB

Dans la fenêtre de Lili, renseigner les champs suivants :

- La lettre du lecteur correspondant à la clé USB ;
- La source (iso) ;
- Eventuellement la persistance ;
- Cocher formatage en fat32 ;
- Enfin cliquer sur l'éclair pour lancer la préparation de la clé.

Ceci fait, nous allons pouvoir lancer la clé USB live sur notre PC.

Lancement de Linux depuis la clé USB
------------------------------------

Au redémarrage de la machine, appuyer sur la touche F2 pour entrer dans le bios. Se rendre dans la section **Boot** et s'assurer de la présence de la clé USB dans la liste des disques et surtout que la clé se trouve devant en ordre de priorité le disque dur (ligne HDD0). Utiliser les touches F5/F6 pour éventuellement changer les priorités. Ceci fait, faire F10 et confirmer la sauvegarde (**[YES]**).

Le PC portable devrait alors afficher un logo de Linux Mint. Surtout ne pas laisser la machine démarrer directement et appuyer sur une touche (un bug graphique en mode normal empêche de pouvoir démarrer proprement). Dans le menu qui apparaît, sélectionner l'option **Fail safe** qui désactivera certaines options au démarrage de Linux.

[Tab] nomodeset avant les --

