### Exercice 2 : Manipulations pratiques sur VM Linux (temps estimé : 2h30)

VM SRVLX01.

#### Partie 1 : Gestion des utilisateurs

- Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel.
  ```
  # commande de creation du compte alex
  useradd alex

  # rattachement du compte alex au groupe sudo
  usermod -aG sudo alex

  # vérification de la création de l'utilisateur alex et des groupes associés
  id alex
  ``` 

- Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ?

  *Rattacher le compte à des groupes dont la gestion des droits est configurée selon les besoins qui lui sont associés.*
  

#### Partie 2 : Configuration de SSH

- Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.
  ```
  # modification des droits du root dans le fichier de configuration ssh (/etc/ssh/sshd_config)
  PermitRootLogin no
  ```

- Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.
    ```
  # modification des droits d'accès dans le fichier de configuration ssh (/etc/ssh/sshd_config) pour l'utilisateur unique alex
  allowUsers alex
  ```

- Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe
  ```
  PubkeyAuthentication yes
  PasswordAuthentication no
  ```
![config_ssh](/home/wilder/Images/Captures d’écran)

  ```
  # activer le changement de configuration
  sudo systemctl restart sshd
  ```
  

#### Partie 3 : Analyse du stockage

- Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?
  ```
  df -hT
  ```
  *Les systèmes de fichiers sont ext4 et ext2*
  
- Q.2.3.2 Quel type de système de stockage ils utilisent ?
  ```
  ls blk
  ```
  *Les systèmes de stockage sont configurés en RAID et LVM* 

- Q.2.3.3 Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID
  ```
  # ajout du 2e disque dans virtualbox et initialisation
  ```
  lsblk
  sda / sda1 8G
  sdb 8G
  ```
  ```
  sudo fdisk /dev/sdb
  n, p, entrée, entrée, entrée, t, fd, w
  ```
  ```
  lsblk
  sda / sda1 8G
  sdb / sdb1 8G
  ```
  
  
- Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.
  ```
  sudo pvcreate /dev/sdb1
  sudo pvdisplay
  ```
  ```
  sudo vgcreate storage00 /dev/sdb1
  sudo vgdisplay
  ```
  

- Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?

#### Partie 4 : Sauvegardes

Le logiciel bareos est installé sur le serveur.
Les composants bareos-dir, bareos-sd et bareos-fd sont installés avec une configuration par défaut.

- Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.

#### Partie 5 : Filtrage et analyse réseau

- Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?

- Q.2.5.2 Quels types de communications sont autorisées ?

- Q.2.5.3 Quels types sont interdit ?

- Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.
