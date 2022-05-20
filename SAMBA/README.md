# SAMBA
# 1 - Description
Samba est un ensemble d'outils permettant de partager des ressources telles que des imprimantes et des fichiers sur un réseau hétérogène. C’est un serveur fichier

Un serveur fichier : Un serveur de fichiers permet de partager des données à travers un réseau.

Il sert à partager un disque Linux pour des machines Windows
ou une imprimante Linux avec des machines Windows
ou partager une imprimante Windows à partir d’un hôte LinuxGérer des listes de machines présentes sur le réseau et leur mise à disposition pour tous types de clients
# 2 - Avantages
- Sur une machine classique, Samba est plus performant 
- Samba permet de définir des niveaux d'accès très pointus, très proches de ceux proposés par un serveur Windows NT.
- Samba est une alternative économique et robuste par rapport à un serveur Windows NT.
- Samba est un logiciel libre, distribué sous licence gratuite.
# 3 - Installation et configuration

###  Installation

- Saisir la commande suivante pour installer Samba :
```
$sudo apt update
$sudo apt install samba
```
- Pour vérifier si l'installation est réussi:
```
$sudo whereis samba
```
- Ce qui suit devrait être sa sortie:
```
samba: /usr/sbin/samba /usr/lib/samba /etc/samba /usr/share/samba /usr/share/man/man7/samba.7.gz /usr/share/man/man8/samba.8.gz
```

###  Configuration
- Lorsque l'installation est terminée, nous devons créer un répertoire pour le partager

```
$sudo mkdir /home/<username>/sambashare/
```
N.B: Il faut remplacer ***\<username\>*** par le nom d'utilisateur choisie.

- Le fichier de configuration pour Samba se trouve à **/etc/samba/smb.conf**.

- Pour ajouter le nouveau répertoire en tant que partage, nous éditons le fichier en exécutant:
```
$sudo nano /etc/samba/smb.conf
```

En bas du fichier, ajoutez les lignes suivantes :
```
[sambashare]
    comment = Samba on Linux
    path = /home/<username>/sambashare
    read only = no
    browsable = yes
```

- Après la configuration, redémarrer Samba :
```
$sudo service smbd restart
```
- Mettez à jour les règles de pare-feu pour autoriser le trafic Samba :
```
$sudo ufw allow samba
```

- Configuration des comptes d'utilisateurs 
Comme le  Samba n'utilise pas le mot de passe du compte système, nous devons configurer un mot de passe Samba pour notre compte utilisateur :
```
$sudo smbpasswd -a username
```
N.B: Le nom d'utilisateur utilisé doit appartenir à un compte système, sinon il ne sera pas enregistré.

### Et voilà, samba est prêt à utiliser

<a href='https://github.com/Onja74/SYS-1'>RETOUR</a>
