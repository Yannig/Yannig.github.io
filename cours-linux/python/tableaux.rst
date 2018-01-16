Les tableaux en Python
======================

La manipulation de tableau (ou liste) en Python est très facile à réaliser. Nous avons vu deux exemples avec ``range`` et les chaînes de caractères. Nous allons aller un peu plus loin dans leur utilisation.

Déclaration d'un tableau
------------------------

Il suffit pour cela d'affecter la valeur ``[]`` à une variable (ex : ``a = []``).

Pour affecter directement des éléments dans un tableau, vous pouvez les ajouter en mettant en les valeurs à affecter entre crochets séparées par des virgules. Exemple :

.. code-block:: python

    a = [ 1, 2, 3 ]

Ajout de valeur dans un tableau
-------------------------------

Vous pouvez passer par l'instruction ``append`` : ``a.append(4)``

Vous pouvez également utiliser l'instruction suivante : ``a += [ 4 ]``

Accès à un membre de la liste
-----------------------------

Vous pouvez accéder aux membres du tableau en précisant le rang de la valeur à accéder. Exemple :

.. code-block:: python

    a = [ 1, 2, 3 ]
    # Accès à l'élément 1 (premier dans le tableau) :
    a[0]

.. warning:: Les accès au tableau commence par l'indice **0**.

Fonctions utiles sur un tableau
-------------------------------

La fonction ``len``.

.. note:: Fonctionne également sur les chaînes de caractères.

Les fonctions ``max`` ou ``min``.

Itération sur un tableau
------------------------

