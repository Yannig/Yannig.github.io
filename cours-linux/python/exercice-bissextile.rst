Mon premier programme : année bissextile
========================================

Petit rappel, une année bissextile se produit avec la fréquence suivante :

- Tous les 4 ans (1998, 2004, 2008) ;
- Les années finissant en 00 ne sont pas bissextile (1900, 1800, 1700 etc.) sauf tout les 400 ans (400, 800 etc.) ;
- Sinon, elle n'est pas bissextile.

Le programme doit faire les choses suivantes :

- Saisir l'année ;
- La convertir en entier (avec la fonction int()) ;
- Déterminer si l'année est bissextile ;
- Afficher un message indiquant le type de l'année courante.


.. code-block:: python

    # Version naïve
    
    annee = raw_input("Merci de saisir l'année : ")
    # Passage en entier
    annee = int(annee)

    # Par défaut, on est pas sur une année bissextile
    bissextile = False
    # Tous les 400 ans, c'est une année bissextile
    if annee % 400 == 0:
      bissextile = True
    elif annee % 100 == 0:
      bissextile = False
    elif annee % 4 == 0:
      bissextile = True

    if bissextile:
        print("L'année saisie est bissextile.")
    else:
        print("L'année saisie n'est pas bissextile.")

Une version un peu moins naïve :

.. code-block:: python

    annee = int(raw_input("Saisissez une année : "))

    if annee % 400 == 0 or (annee % 4 == 0 and annee % 100 != 0):
        print("L'année saisie est bissextile.")
    else:
        print("L'année saisie n'est pas bissextile.")
