Manipulation de fichier
=======================

Ouverture d'un fichier
----------------------

.. code:: python

    # Lecture :
    f = open('fichier.txt', 'r')
    print(f.readlines())

    # Rembobine au début
    f.seek(0)

    # Ferme le fichier
    f.close()

    with open('fichier.txt', 'r) as file:
        # Récupération et affichage des lignes sous forme d'un tableau
        print(file.readlines())
        # On rembobine
        file.seek(0)

        # Affichage brute du fichier
        for line in file.readlines():
            print(line)
        file.close()

        # Equivalent
        file.seek(0)
        for line in file.readlines():
            print(line.strip())
        file.close()

        # Même chose mais en profitant du fait que l'objet file peut-être parcouru avec for
        file.seek(0)
        for line in file:
            print(line.strip())
        file.close()

Exercice :

- Ouvrir un fichier texte et l'afficher ligne par ligne ;
- Ouvrir un fichier inexistant ;
- Parcourir un fichier fermé ;
- Afficher le contenu d'un fichier (ligne par ligne).

A quoi sert la méthode ``strip`` ?

Création d'un fichier
---------------------

.. code:: python

    # Nouveau fichier :
    f = open('new.txt', 'w')
    f.write("test")
    f.close()

    # Concaténation en fin de fichier :
    f = open('new.txt', 'a')
    f.write("test2")
    f.close()

Exercice :

- Créer un nouveau fichier et le fermer ;
- Ouvrir un fichier existant et le fermer ;
- Ajouter 3 lignes contenants leur numéro (un par ligne) ;
- Ouvrir en ajout sur un fichier inexistant.
