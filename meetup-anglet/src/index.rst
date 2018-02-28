Meetup IAC Anglet
=================

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

.. revealjs:: Qui suis-je

   .. rv_note::

      - Administrateur système et Java
      - Auteur d'un livre sur Ansible

.. revealjs:: Infrastructure as Code
   :data-background: #052535

   .. image:: images/infrastructure-as-code.png

   .. rv_note::

      - On va revenir sur la notion d'agilité
      - Les changements qui en découlent
      - Mise en application sur un cas simple

.. revealjs:: Principe agilité
   :data-background: #ffffff

   .. image:: images/principe-agilite.png

   .. rv_note::

    - Feedbacks régulier
    - Production de livrables intermédiaires

.. revealjs:: Une première réponse

    - Intégration continue
    - Déploiement continue

   .. rv_note::

    - Automatisation de vos process
    - Concentration sur ce qui a de la valeur
    - Attention de ne pas se prendre les pieds dans le tapis

.. revealjs:: Augmentation fréquence livraisons

   .. image:: images/hamster-cage.gif

.. revealjs:: Gestion environnements


   .. rv_note::

    Invariablement, vous devriez augmenter le nombre de serveur

    Mais vous allez sûrement faire à des changements de versions

    Et un jour, le dev va vouloir faire des Microservices

.. revealjs:: Scalabilité sysadmin

   .. image:: images/sysadmin-no-root-access.jpg

   .. rv_note::

    - Un jour vous allez devoir le voir
    - Avant de raler contre lui, essayons de comprendre son travail

.. revealjs:: Document d'installation
   :data-background: #ffffff
   :data-transition: slide

   .. image:: images/exemple-pti.png

.. revealjs:: Installation batchs Java

   19 pages de littérature inoubliable

   .. rv_note::

    - Un cartouche (3 pages)
    - Une table des matières
    - Une présentation (3 pages)
    - Des prérequis (2 pages)
    - Les commanges à lancer (10 pages)

.. revealjs:: Tout ça pour ...
   :data-background: #ffffff
   :data-transition: slide

   .. image:: images/is-that-all-you-got.gif
      :width: 800

   .. rv_note::

    - Un groupe
    - Un utilisateur
    - Un JDK
    - Quelques répertoires

.. revealjs:: Maintenant, il faut ...

   .. rv_note::

    - Un serveur d'application
    - Une base de données
    - Un serveur Apache
    - Installer l'application
    - De la surveillance
    - Configurer la sauvegarde
    - ...

.. revealjs:: Et vous avez ...
   :data-background: #ffffff

   .. rv_note::

    - environ 400 pages de littérature à suivre
    - les zones d'ombres
    - les gestes non documentés

.. revealjs:: Mais vous devez également ...

   .. rv_note::

    - Gérer plusieurs environnements
    - Lancer l'installation plusieurs fois (scalabilité tomcat)
    - Gérer la production
    - Exploiter les plateformes

.. revealjs:: Préparez-vous, ça va chauffer
   :data-background: #f8d62d
   :data-transition: zoom

   .. image:: images/dragon-to-slay.png
      :width: 800

.. revealjs:: Création d'infra

   Vite, tous dans le cloud !

   .. rv_note::

    - Mise à disposition rapide
    - Paiement à la consommation

.. revealjs:: Scalabilité et erreurs

  .. image:: images/ikea-henj-1.jpg
      :align: right
      :width: 460

  .. image:: images/ikea-henj-2.jpg
      :align: right
      :width: 460

  .. rv_note::

    - Vous devez toujours gérer votre installation
    - Documenter vos gestes
    - Problème de reproductibilité des installations

.. revealjs:: Comment sortir de cette situation
   :data-background: #ffffff
   :data-transition: slide

   .. image:: images/brain-to-bin.png

   .. rv_note::

    - Traduire les gestes en description
    - Shell (problème réentrance)
    - DevOps (Idempotence ou Immutabilité)

.. revealjs:: Les outils DevOps

   .. rv_note::

    - Décrire les gestes
    - Passer à un automate
    - Appliquer cette description

.. revealjs:: Attention aux surprises
   :data-background: #dd5726

   Surtout en cas de pépin

   .. rv_note::

    - Modification d'un fichier géré par l'automate
    - Relance de l'installation
    - Perte de la modification

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

   .. rv_note::

    - Azure AWS
    - Ansible idempotence
    - Docker immutable Microservice

.. revealjs:: Utilisation d'Ansible
   :data-background: #ffffff

   .. image:: images/ansible-architecture.png

   .. rv_note::

      - Description des gestes
      - Liste de machines
      - Lancement du programme
      - C'est prêt !

.. revealjs:: Le playbook

   .. rv_code::

    - name: "Create JDK directory"
      file:
        path: "/opt/jdk"
        state: directory
    - name: "Uncompress JDK"
      unarchive:
        src: "jdk-9.0.4_linux-x64_bin.tar.gz"
        dest: "/opt/jdk"

.. revealjs:: L'inventaire

   .. rv_code::

     [batch]
     demo-batch1

     [tomcat]
     demo-tomcat1

     [all:vars]
     ansible_connection=docker
     docker_network_name=demo.meetup


.. revealjs:: Utilisation d'Ansible

    - Description plateforme attendue
    - Demande de provisionnement
    - Installer un JDK
    - Installer un Tomcat
    - Déployer une application
    - Détruire un environnement

.. revealjs:: Démo

   .. image:: images/devops-demo.png
      :width: 750

.. revealjs:: Ce qu'il faut retenir
   :data-background: #ffffff
   :data-transition: slide

   .. rv_note::

    - Flocon de neige
    - Animaux de compagnie vs Bétail
    - L'infra se gére comme du code
    - En conséquence l'exploitation également
    - Repenser certains aspects

.. revealjs::
   :data-background: #60beb6

   .. image:: images/ask-me-anything.gif

Index
=====

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
