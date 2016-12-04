Démarrage Linux via clé USB
===========================

Une fois la clé prête, il va être nécessaire de démarrer sous Linux.

Lancement de Linux depuis la clé USB
------------------------------------

Au redémarrage de la machine, appuyer sur la touche F2 pour entrer dans le bios. Se rendre dans la section **Boot** et s'assurer de la présence de la clé USB dans la liste des disques et surtout que la clé se trouve devant en ordre de priorité le disque dur (ligne HDD0). Utiliser les touches F5/F6 pour éventuellement changer les priorités. Ceci fait, faire F10 et confirmer la sauvegarde (**[YES]**).

Le PC portable devrait alors afficher un logo de Linux Mint. Surtout ne pas laisser la machine démarrer directement et appuyer sur une touche.

.. note:: Un bug graphique sur les portables de l'association empêche de pouvoir démarrer proprement en mode normal. Ce bug disparait en utilisant en utilisant le mode **fail safe**.

Dans le menu qui apparaît, sélectionner l'option **Fail safe** qui désactivera certaines options au démarrage de Linux.

Découverte du bureau
--------------------

Il suffit maintenant d'attendre un petit peu jusqu'à l'apparition du bureau Linux XFCE.

Passons à la découverte du bureau XFCE : :ref:`decouverte-bureau-xfce`.
