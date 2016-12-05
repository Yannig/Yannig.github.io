Les partitions sous Linux
=========================

Qu'est-ce qu'une partition ?
----------------------------

Les partitions sous Linux sont les équivalents des lettres des lecteurs Windows. La différence va se trouver dans le fait que toutes les partitions sont montées dans une arborescence unique. Ci-dessous quelques exemples de partitions :

================  ==========================  ======================
Partition Linux   Équivalent lettre Windows   Point de montage
================  ==========================  ======================
sda1               C:                          /
----------------  --------------------------  ----------------------
sdb1               D:                          /home
================  ==========================  ======================

Les partitions peuvent être créées à l'aide de **gparted** (en mode graphique) ou **fdisk** en ligne de commande. Une partition se définie sur un disque à l'aide des éléments suivants :

- Un disque (sda, sdb, ...) ;
- Un numéro de partition (1, 2, ...).

La première partition du premier disque sera sda1, la seconde sda2. La 1ier partition du second disque sera vu comme sdb1 et ainsi de suite.

Gestion d'une partition
-----------------------

Les partitions sont montées automatiquement au démarrage grâce au contenu du fichier **/etc/fstab**. L'affichage du contenu de ce fichier peut se faire à l'aide de la commande suivante :

.. code-block:: bash

    cat /etc/fstab

::

    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    # / was on /dev/sda1 during installation
    UUID=a337176a-5cae-44b3-82e2-0d9052821927 /               ext4    errors=remount-ro 0       1
    # swap was on /dev/sda5 during installation
    UUID=797fe69c-2ba2-442f-9eda-2aa836ff6162 none            swap    sw              0       0
    /dev/sdb /var/lib/docker btrfs   defaults        0       0

.. note:: Les distributions modernes n'utilisent pas directement le nom de la partition (ex : /dev/sda1) mais son identifiant unique (UUID). Cet identifiant peut se retrouver en regardant le contenu du répertoire **/dev/disk/by-uuid**

Chaque partition est ensuite formatée dans un système de fichier. Dans la plupart des cas on aura du ext4 ou swap mais on peut également retrouver xfs ou btrfs pour les partitions natives Linux et vfat ou ntfs dans le cas de partition Windows ou lors de l'utilisation d'une clé USB.

Il est possible de lister les partitions montées par un système Linux à l'aide de la commande **df** :

.. code-block:: bash

    df -h

::

    Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
    udev               4,9G       0  4,9G   0% /dev
    tmpfs             1000M    9,2M  991M   1% /run
    /dev/sda1           40G     28G   11G  74% /
    tmpfs              4,9G    479M  4,5G  10% /dev/shm
    tmpfs              5,0M    4,0K  5,0M   1% /run/lock
    tmpfs              4,9G       0  4,9G   0% /sys/fs/cgroup
    tmpfs             1000M     20K 1000M   1% /run/user/1000
    tmpfs             1000M       0 1000M   0% /run/user/0

.. note:: le type de système de fichier **tmpfs** est un cas particulier et correspond à des partitions volatiles : elles sont gérées par le système. Elles servent d'espace temporaire ou à exposer des mécanismes du Kernel Linux.
