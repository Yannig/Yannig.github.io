Création d'un timelapse en shell
================================

Nous avons vu comment réaliser un petit jeu en shell. Nous allons voir aujourd'hui un autre exercice : la création d'un timelapse.

Le principe du timelapse est simple : prendre des photos à intervalle régulier et les assembler pour en faire un film.

La séance va comprendre plusieurs phases :

- Recherche des outils qui nous permettront de faire notre travail ;
- Expérimentation autour des outils ;
- Création du script.

Créer nos photos
----------------

Avant toute chose, il nous faut prendre des photos à intervalle régulier. Gphoto fait partie des logiciels permettant de déclencher automatiquement un appareil photo. L'installation se fait assez facilement à l'aide de la commande **apt** :

::

    apt install gphoto2

Découverte de gphoto
--------------------

À partir de l'aide en ligne, trouver les opérations suivantes :

- Lister les appareils photos branchés ;
- Prendre des photos en ligne de commande ;
- Lancer cette prise de photo toutes les secondes.

::

    # Prendre des photos toutes les secondes
    gphoto2  --auto-detect --capture-image-and-download -I 1

Préparation de nos photos
-------------------------

Pour gagner un peu de temps, nous allons nous appuyer sur plusieurs ensembles de photos :

- Défilement des nuages ;
- Pousse de champignons ;
- Passage de voitures à un carrefour avec un feu ;
- Astrophotographie ;
- etc.

Retailler les photos
--------------------

Les photos d'origine sont au format JPG et font une taille de 3456x2304. Sachant qu'une vidéo Full-HD fait 1080 pixels de hauteur et 720 pixels pour une vidéo HD, nous allons devoir la réduire.

Pour cela, nous allons nous servir du programme convert.

Faire une vidéo en partant d'images
-----------------------------------

L'outil ffmpeg ou mencoder/mplayer sont connus pour créer/convertir des vidéos. Procéder à l'installation d'un des deux et au test de leur fonctionnement.

Un exemple de lancement :

::

    mencoder "mf://*.JPG" -mf fps=15:type=jpg -ovc x264 -x264encopts bitrate=3000

Création de la vidéo
--------------------

Maintenant que nous savons retailler nos photos et les assembler dans une vidéo, nous allons nous faire un script qui va nous permettre d'enchaîner toutes ces étapes. Pour cela :

- Créer un script shell **convert.sh** dans le répertoire des photos ;
- Le rendre exécutable ;
- Faire une boucle d'affichage des noms des fichiers ;
- Modifier le programme pour appeler convert en créant les fichiers dans un sous répertoire resize ;
- Une fois tous les fichiers retaillés, lancer mencoder.

Si vous avez bien suivi, le fichier devrait ressembler à ce qui suit :

.. code-block:: bash

    # Boucle sur tous les fichiers
    for i in *.JPG
    do
      # Affichage de son nom + conversion en 1440 de largeur
      echo $i
      convert -resize 1440 $i 1440_$i
    done
    mencoder "mf://1440_*.JPG" -mf fps=15:type=jpg -ovc x264 -x264encopts bitrate=3000
    # Ménage
    rm -f 1440_*.JPG

Ajoutons du son
---------------

Des logiciels de montage vidéo comme kdenlive vous permettrez de le faire via une interface graphique. Si on reste sur l'utilisation de mencoder, nous pouvons nous appuyer sur l'option -audiofile.

Modifier le shell pour y ajouter un son.