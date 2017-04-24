Correction exercice sur le shell
================================

Ci-dessous une implémentation possible pour l'exercice proposé :

.. code-block:: bash

    # Calcul d'un nombre entre 0 et 99
    # Pour mémoire on fait le calcul du reste d'une division euclidienne
    # https://fr.wikipedia.org/wiki/Division_euclidienne

    let i=$$%100
    # On ajoute 1 pour être sur un chiffre entre 1 et 100.
    let i=i+1
    # On l'affiche pour faire de la mise au point
    echo $i

    while true
    do
      echo "Saisir un chiffre entre 1 et 100"
      read j
      if [ "$i" = "$j" ]; then
        echo "Bravo, vous avez trouvé"
        exit
      fi
      echo "Essaye encore"
      if [ $j -lt $i ]; then
        echo "Trop petit"
      else
        echo "Trop grand"
      fi
    done
