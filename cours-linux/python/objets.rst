Les objets en Python
====================

Introduction
------------

Un objet Python est une structure. On y retrouve :

- Des champs ;
- Des méthodes.

Exemple de déclaration :

.. code:: python

   class test():

      def __init__(self):
          print('INIT')

      def method1(self):
          print('method1')

   a = test()
   a.method1()

