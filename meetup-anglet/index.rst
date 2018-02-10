.. Meetup IAC documentation master file, created by
   sphinx-quickstart on Tue Feb  6 09:05:00 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Meetup IAC's documentation!
======================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

.. L'adoption de l'agilité change le développement des applications. Une bonne pratique est mettre en place certains outils permettant l'accéleration du déploiement. En effet, rien ne sert de sortir une application toutes les 3 semaines si vous n'êtes pas en mesure de réaliser son installation dans le même temps.
.. 
.. Une première étape peut consister à mettre en oeuvre un pipeline de déploiement continue sur des environnements existants. Cette facilité de déploiement amène souvent l'ajout de nouveaux environnements (pour pouvoir tester la robustesse, la performance etc.). Ces nouveaux environnements, si vous n'y prenez pas garde peuvent entrainer une charge de travail conséquente ainsi que d'autres problèmes (versions applicative obsoléte, cluster de machine, configuration différente).
.. 
.. L'IaC peut répondre à ce type de problématique en appliquant les mêmes méthodes que pour du code. Vous stockez dans un gestionnaire de code source la description de votre infrastructure, vous faîtes appel à un automate et ce dernier se charge d'appliquer cette description.
.. 


.. revealjs:: Meetup Agile Pays-Basque
   :subtitle: Infrastructure as Code
   :data-background: #ffffff

   .. image:: images/logo_ansible.png
      :height: 100
   .. image:: images/docker.png
      :height: 100

   `Yannig Perré <http://lesaventuresdeyannigdanslemondeit.blogspot.fr>`_ / `@Twitter <https://twitter.com/YannigPerre>`_


   .. image:: images/twitter-logo.png
      :target: https://twitter.com/YannigPerre
      :height: 40
   .. image:: images/github-icon.png
      :target: https://github.com/Yannig
      :height: 40

.. revealjs:: Infrastructure as Code

  - Un petit peu de contexte
  - Qu'est ce qu'apporte l'agilité
  - Mutation qui peuvent en découler
  - Mise en application

.. revealjs:: Un petit peu de contexte
   :data-background: #ffffff

   Manuel d'installation batchs Java

   .. image:: images/exemple-pti.png

.. revealjs:: Qu'est qu'on retrouve
   :subtitle: 19 pages de littérature inoubliable

    - Un cartouche (3 pages)
    - Une table des matières
    - Une présentation (3 pages)
    - Des prérequis (2 pages)
    - Les commanges à lancer (10 pages)

.. revealjs:: Tout ça pour ...
   
    - Un groupe
    - Un utilisateur
    - Un JDK
    - Des répertoires

.. revealjs:: Maintenant, il faut

    - Un serveur d'application
    - Une base de données
    - Un serveur Apache
    - Installer l'application
    - De la surveillance
    - Configurer la sauvegarde
    - ...

.. revealjs:: Et pour faire tout ça vous avez ...

    - environ 400 pages de littérature à suivre
    - les zones d'ombres
    - les gestes non documentés

.. revealjs:: Problème vous devez ...

    - Gérer plusieurs environnements
    - Lancer l'installation plusieurs fois

.. revealjs:: Création d'infra
   :subtitle: Vite, tous dans le cloud !

    - Mise à disposition rapide
    - Paiement à la consommation

.. revealjs:: Problème

    .. image:: images/ikea-henj-1.jpg
       :align: right
       :width: 460

    .. image:: images/ikea-henj-2.jpg
       :align: right
       :width: 460

.. revealjs:: Scalabilité et erreurs

    .. image:: images/monkey-keyboard.jpg

.. revealjs:: Comment sortir de cette situation

    .. image:: images/brain-to-bin.png

.. revealjs:: Quelques solutions
   :data-background: #ffffff

    .. image:: images/api-cloud.png
       :width: 200
    .. image:: images/terraform.svg
       :width: 200

    |

    .. image:: images/logo_ansible.png
       :width: 200
    .. image:: images/docker.png
       :width: 200

.. revealjs:: Pour la suite

    Installation du socle technique

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
