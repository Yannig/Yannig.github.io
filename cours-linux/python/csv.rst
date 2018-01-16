Ouverture de fichier CSV
========================

Création d'un fichier CSV
-------------------------

Sous LibreOffice, créer une feuille de tableur avec les données suivantes :

========  =======  ========
Ville     Surface  Habitant
========  =======  ========
Boussy          5      6000
--------  -------  --------
Paris          50   1500000
--------  -------  --------
Pau           150    100000
--------  -------  --------
Draveil        40     30000
========  =======  ========

Sauvegarder ce fichier sous le nom **test.csv** (en utilisant le format CSV). Ci-dessous le contenu du fichier vu avec la commande cat :

::

    $ cat test.csv

Contenu brute du fichier :

::

    Ville,Surface,Habitant
    Boussy,5,6000
    Paris,50,1500000
    Pau,150,100000
    Draveil,40,30000

Lecture du fichier en Python
----------------------------

Il est possible de lire le contenu de ce fichier de la manière suivante :

- Ouverture du fichier avec la fonction **open** ;
- Parcours du fichier avec une boucle **for** ;
- Affichage de chaque ligne.

Ci-dessous une implémentation possible :

.. code:: python

    fichier = open("test.csv")

    for ligne in fichier:
        print(ligne)

Cette première version est comme d'habitude un peu naïve. Nous allons l'améliorer afin de répondre aux exigences suivantes :

- Supprimer le retour chariot surnuméraire à chaque ligne (avec la méthode **strip**) ;
- Afficher le contenu de la ligne sous la forme d'un tableau (avec la méthode **split**).

En intégrant ces améliorations, notre programme prendra la forme suivante :

.. code:: python

    fichier = open("test.csv")

    for ligne in fichier:
        colonnes = ligne.strip().split(',')
        print(colonnes)

Lecture du fichier avec la librairie CSV
----------------------------------------

Python dispose nativement d'une bibliothéque **csv**. Nous allons voir comment l'utiliser et surtout qu'elle est le gain de son utilisation.

Pour se faire, nous aurons besoin d'ajouter les choses suivantes :

- Import de la bibliothéque (``import csv``) ;
- Ouverture du fichier ;
- Passage du fichier à la fonction ``csv.reader`` ;
- Parcours du fichier et affichage.

Le programme suivant respecte cette micro spécification :

.. code:: python

    import csv

    fichier = open("test.csv")
    fichier_csv = csv.reader(open(fichier))

    for ligne in fichier_csv:
        print(ligne)

Ci-dessous le résultat de l'exécution de ce programme :

::

    ['Ville', 'Surface', 'Habitant']
    ['Boussy', '5', '6000']
    ['Paris', '50', '1500000']
    ['Pau', '150', '100000']
    ['Draveil', '40', '30000']

Ici, la ligne prend directement la forme d'un tableau. Il n'y a plus besoin de faire le nettoyage de la ligne avant son utilisation.

Autre rafinement, il est possible de renvoyer les lignes du tableau sous la forme d'un tableau associatif. En effet, chaque colonne a une signification du fait de la présence d'une entête sur la première ligne. La librairie csv est en mesure d'utiliser cette première ligne afin de structurer l'information. Pour cela, il faut remplacer la fonction ``csv.reader`` par ``csv.DictReader``. Ci-dessous le programme intégrant ce changement :

.. code:: python

    import csv

    fichier = open("test.csv")
    fichier_csv = csv.DictReader(open(fichier))

    for ligne in fichier_csv:
        print(ligne)

Ci-dessous vous retrouverez la sortie de la nouvelle version de ce programme :

::

    {'Surface': '5', 'Habitant': '6000', 'Ville': 'Boussy'}
    {'Surface': '50', 'Habitant': '1500000', 'Ville': 'Paris'}
    {'Surface': '150', 'Habitant': '100000', 'Ville': 'Pau'}
    {'Surface': '40', 'Habitant': '30000', 'Ville': 'Draveil'}

Avantages de cette nouvelle version :

- Le nombre de ligne renvoyé par le programme correspond au nombre d'enregistrement ;
- L'ordre des colonnes dans le tableau n'a plus d'importance.

Exercices
---------

Faire le programme permettant d'afficher pour chaque ville le nombre d'habitant au km².

Correction :
