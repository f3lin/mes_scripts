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
