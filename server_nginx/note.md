# Documentation des Commandes et Procédures Apprises

## Création d'un Fichier d'Archive

Pour créer un fichier d'archive compressé :

```bash
sudo tar -czvf wordpress.tar
```

Exemple de sortie :
```
wordpress/
wordpress/index.php
wordpress/wp-login.php
...
```

## Transfert de Fichiers entre Serveurs

Pour transférer le contenu d'un serveur vers un autre en utilisant `rsync` :

```bash
rsync -av -e ssh --progress --delete wordpress.tar vagrant@192.168.10.12:/vagrant/wordpress/
```

Exemple de sortie :
```
sending incremental file list
wordpress.tar
...
```

## Création d'un Lien Symbolique

Pour activer un fichier de configuration en créant un lien symbolique :

```bash
sudo ln -s /etc/nginx/sites-available/wordpress.conf /etc/nginx/sites-enabled/wordpress.conf
```

Aucune sortie ne sera affichée après l'exécution de cette commande.

## Utilisation de la Commande `netstat`

### Linux

Pour vérifier si le port 80 est en écoute sur un serveur Linux :

```bash
sudo netstat -tuln | grep :80
```

Exemple de sortie :
```
tcp6       0      0 :::80                   :::*                    LISTEN
```

### Windows

Pour vérifier si le port 80 est en écoute sur un serveur Windows :

```bash
netstat -an | find ":80" | find "LISTENING"
```

Exemple de sortie :
```
TCP    0.0.0.0:80             0.0.0.0:0              LISTENING
```

## Gestion des Permissions

### Changer le Propriétaire du Répertoire

Pour s'assurer que l'utilisateur actuel est propriétaire du répertoire de sauvegarde :

```bash
sudo chown -R $USER:$USER /home/vagrant/backups
```

Aucune sortie ne sera affichée après l'exécution de cette commande.

### Donner les Permissions d'Écriture

Pour donner les permissions d'écriture au propriétaire pour le répertoire de sauvegarde :

```bash
chmod u+w /home/vagrant/backups
```

Aucune sortie ne sera affichée après l'exécution de cette commande.

## Copie de Fichiers depuis une Machine Virtuelle Vagrant

Pour copier un fichier depuis une machine virtuelle Vagrant (VM) vers la machine hôte, vous avez plusieurs options :

- Utiliser vagrant scp : Vagrant fournit une commande intégrée appelée scp pour copier de manière sécurisée des fichiers entre la machine hôte et la machine invité. Voici la syntaxe :

```bash
vagrant scp <nom-vm>:/chemin/vers/le/fichier/source /chemin/vers/le/fichier/destination
```

Remplacez <nom-vm> par le nom de votre VM et spécifiez les chemins vers les fichiers source et destination en conséquence.

Utiliser les Dossiers Partagés : Si vous avez configuré des dossiers partagés entre votre machine hôte et la machine invitée dans votre Vagrantfile, vous pouvez simplement copier le fichier vers le dossier partagé depuis la VM, et il sera automatiquement disponible sur la machine hôte.

Utiliser SSH : Vous pouvez utiliser des outils SSH standard tels que scp ou rsync pour copier des fichiers entre la VM et la machine hôte. Voici un exemple utilisant scp :

```bash
scp vagrant@<adresse-ip-vm>:/chemin/vers/le/fichier/source /chemin/vers/le/fichier/destination
```

remplacez <adresse-ip-vm> par l'adresse IP de votre VM et spécifiez les chemins vers les fichiers source et destination en conséquence.