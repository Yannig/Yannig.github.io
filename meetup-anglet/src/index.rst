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

.. revealjs:: Infrastructure as Code
   :data-background: #052535

   .. image:: images/infrastructure-as-code.png

   .. rv_note::

      - Changements introduits par l'agilité
      - Qu'est ce qu'apporte l'agilité
      - Mutation qui peuvent en découler
      - Mise en application

.. revealjs:: Principe agilité
   :data-background: #ffffff

   .. image:: images/principe-agilite.png

.. revealjs:: Ce qui se traduit par ...

    - Augmentation fréquence livraisons
    - Intégration continue
    - Déploiement continue
    - Augmentation environnements

.. revealjs:: Scalabilité sysadmin

   .. image:: images/sysadmin-no-root-access.jpg

   .. rv_note::

    - Où les trouver
    - Les former
    - Vite, faisons des procédures

.. revealjs:: Document d'installation
   :data-background: #ffffff
   :data-transition: slide

   .. image:: images/exemple-pti.png

.. revealjs:: Installation batchs Java
   :subtitle: 19 pages de littérature inoubliable

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

.. revealjs:: Maintenant, il faut

    - Un serveur d'application
    - Une base de données
    - Un serveur Apache
    - Installer l'application
    - De la surveillance
    - Configurer la sauvegarde
    - ...

.. revealjs:: Et vous avez ...
   :data-background: #ffffff

    - environ 400 pages de littérature à suivre
    - les zones d'ombres
    - les gestes non documentés

.. revealjs:: Mais vous devez également ...

    - Gérer plusieurs environnements
    - Lancer l'installation plusieurs fois
    - Gérer la production
    - Exploiter les plateformes

.. revealjs:: Préparez-vous, ça va chauffer
   :data-background: #f8d62d
   :data-transition: zoom

   .. image:: images/dragon-to-slay.png
      :width: 800

.. revealjs:: Création d'infra
   :subtitle: Vite, tous dans le cloud !

    - Mise à disposition rapide
    - Paiement à la consommation

.. revealjs:: Problème

  .. image:: images/charlot-les-temps-modernes.gif
     :width: 800

.. revealjs:: Scalabilité et erreurs

  .. image:: images/ikea-henj-1.jpg
      :align: right
      :width: 460

  .. image:: images/ikea-henj-2.jpg
      :align: right
      :width: 460

.. revealjs:: Comment sortir de cette situation
   :data-background: #ffffff
   :data-transition: slide

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
   :subtitle: Création de VM/container

    - Description plateforme attendue
    - Demande de provisionnement

.. revealjs:: Démo

   .. image:: images/devops-demo.png
      :width: 750

.. revealjs:: Ce qu'il faut retenir
   :data-background: #ffffff
   :data-transition: slide

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