Correction exercice gestion fichiers
====================================

Exercice sur les fichiers
-------------------------

========================================================================  =========================
Opération                                                                  Commande
========================================================================  =========================
Créer un répertoire **/tmp/test**                                          ``mkdir /tmp/test``
------------------------------------------------------------------------  -------------------------
Recopier le fichier **/etc/debian_version** dans le répertoire /tmp/test   ``cp /etc/debian_version /tmp/test/.``
------------------------------------------------------------------------  -------------------------
Afficher son contenu                                                       ``cat /tmp/test/debian_version``
------------------------------------------------------------------------  -------------------------
Afficher les informations sur ce fichier                                   ``ls -l /tmp/test/debian_version``
------------------------------------------------------------------------  -------------------------
Attribuer des droits en écriture à tous                                    ``chmod a+x /tmp/test/debian_version``
------------------------------------------------------------------------  -------------------------
Afficher les informations sur ce fichier                                   ``ls -l /tmp/test/debian_version``
------------------------------------------------------------------------  -------------------------
Essayer de supprimer le répertoire **/tmp/test**                           ``rmdir /tmp/test``
------------------------------------------------------------------------  -------------------------
Supprimer le fichier **/tmp/test/debian_version**                          ``rm /tmp/test/debian_version``
------------------------------------------------------------------------  -------------------------
Réessayer de supprimer le répertoire **/tmp/test**                         ``rmdir /tmp/test``
========================================================================  =========================
