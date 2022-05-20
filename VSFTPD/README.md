# VSFTPD
# 1 -Description
vsFTPd (Very Secure FTP Daemon, est un serveur FTP qui mise beaucoup sur la sécurité. Il est l'un des premiers logiciels serveurs à mettre en œuvre 
la séparation des privilèges, minimisant ainsi les risques de piratage.

FTP veut dire « File Transfert Protocol » ou Protocole de transfert de Fichier.
C’est un langage qui va permettre l’échange de fichiers entre 2 ordinateurs, et plus exactement entre un serveur et un client.

- serveur FTP: Le serveur FTP est un logiciel qui va répondre aux demandes des clients. Lorsque le serveur reçoit une demande, 
il vérifie les droits et si le client à les droits suffisants, il répond à cette demande 
sinon la demande est rejetée.

- client FTP: C’est lui qui va être à l’initiative de toutes les transactions.
Il se connecte au serveur FTP, effectue les commandes (récupération ou dépôt de fichiers) puis se déconnecte. 
# 2 - Avantage
- Dispose d'une sauvegarde automatique.
- Il donne le contrôle sur le transfert. Autrement dit, on peut choisir le mode dans lequel les données sont transférées sur le réseau.
- On peut travailler avec les répertoires sur les systèmes distants, supprimer ou renommer les fichiers distants tout en transférant 
les données entre 2 hôtes. 
# 3 -Installation et configuration
Dans le terminal, saisir la commande suivante pour installer Vsftpd :
```
$sudo apt update
$sudo apt install vsftpd -y
$sudo apt install vsftpd -v
```

Pour vérifier si l'installation du serveur est réussi, la commande:

```
$sudo systemctl status vsftpd
```
Pour une partage de fichier, il est nécessaire d'utiliser un application comme FileZila, qui est une application FTP multiplateforme gratuite et open source, composée de FileZilla Client et FileZilla Server.

 * On peut télécharger gratuitement FileZila dans ce lien: 
 <https://filezilla-project.org/>
  Ajout d'un nouveau utilisateur
Afin d'établir un transfert de fichier pour un mutli-user, il est important d'ajouter des utilisateur pour interagir avec le serveur.

Voici les étapes à suivre:

* Ajouter un utilisateur

```
$sudo adduser ftpuser
```

* Créer un nouveau dossier pour l'utilisateur

```
$sudo mkdir /home/ftpuser/ftp
$sudo mkdir /home/ftpuser/ftp/fichier
```

* Changer la permission et la propriétaire du dossier

```
$sudo chown nobody:nogroup /home/ftpuser/ftp 
$sudo chmod a-w /home/ftpuser/ftp
$sudo chown ftpuser:ftpuser /home/ftpuser/ftp/fichier
```

###  Configuration du serveur VSFTPD
* Créer un backup pour le ficher vsftpd.conf

```
$sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak
```

* Modifier le ficher vsftpd.conf

```
$sudo nano /etc/vsftpd.conf
```

* Vérification du serveur vsftpd

```
$sudo systemctl restart vsftpd
$sudo systemctl status vsftpd
```

###  Test du serveur VSFTPD
Le but de ce test est de transférer un fichier provenant d'un utilisateur externe vers le propritaire


et si on vérifie les fichiers dans le dossier de destination, les fichiers transferés devront être dans la destination.
```
$sudo cd /home/ftpuser/ftp/fichier
$/home/ftpuser/ftp/fichier# ls -al
```
<!-- RETOUR -->
**<a href='https://github.com/Onja74/SYS-1'>RETOUR</a>**
