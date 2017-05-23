Initiation au langage Python
============================

Le contenu de ce cours est largement inspiré du cours en ligne suivant : https://openclassrooms.com/courses/apprenez-a-programmer-en-python

N'hésitez pas à le consulter pour aller plus loin.

Intallation de l'interpréteur
-----------------------------

Sous Linux, l'interpréteur python est déjà présent sur votre machine : pas besoin de l'installer. Il existe également sous Windows sous la forme de package à installer.

Lancement de python
-------------------

Le lancement de python se fait en tapant la commande python. Ci-dessous un exemple de ce que nous obtenons :

::

    Python 2.7.12 (default, Nov 19 2016, 06:48:10) 
    [GCC 5.4.0 20160609] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> 

.. note:: Il s'agit de la version 2.7 de python. Pour une version plus récente, il faudra lancer python3.5 pour la version 3.5.

Découverte de python
--------------------

Avant de faire notre premier programme, nous allons tout d'abord voir ensemble comment lancer l'interpréteur et y faire quelques opérations simple :

- Faire un calcul simple : 1 + 2, 2.2 + 2.8, 3.11 + 2.08 ;
- Gestion chaîne de caractères : concaténation et substitution ;
- Calcul : division, division entière, reste de division, 1/3 ;

A la découverte des variables
-----------------------------

- Utilisation de variable : nom de variable valide (attention aux mots clés comme if, else, etc.) ;
- Les types de variables (entiers, flottants, texte) ;
- Astuce sur l'assignation :
    - Multiassignation : a = b = 2 ;
    - Permutation : a,b = b,a ;
    - Incrémentation : a += 1 ;
- Affichage d'élément avec **print** ;
- Saisir une variable avec **raw_input** ;
- substitution d'élément dans une chaîne (attention aux différents types !) ;
- Récupérer le type d'une variable avec type (type('test') => str).

Les structures conditionnelles
------------------------------

- if, elif et else : utiliser pour tester certaines conditions

.. code-block:: python

   #!/usr/bin/env python
   # -*- coding: utf-8 -*-
   if a < 10:
       print('a est plus petit que 10')
   elif a == 10:
       print('a est égal à 10')
   else:
       print('a est plus grand que 10')


Les conditions que l'on peut utiliser :

==========  ===========================
Opérateur    Signification
==========  ===========================
<            Strictement inférieur à
----------  ---------------------------
>            Strictement supérieur à
----------  ---------------------------
<=           Inférieur ou égal à
----------  ---------------------------
>=           Supérieur ou égal à
----------  ---------------------------
==           Égal à
----------  ---------------------------
!=           Différent de
==========  ===========================

Évaluation de condition : les booléens
--------------------------------------

If ne sait travailler qu'avec des booléens (vrai ou faux). Il est possible de faire l'évaluation et éventuellement de l'assigner dans une variable.

.. code-block:: python

   vrai = True
   faux = False
   a = 20
   evaluation_vrai = a == 20 # => True
   evaluation_faux = a < 0   # => False
   # Utilisation dans une structure de condition :
   if evaluation_vrai:
      print('a égal 20')

