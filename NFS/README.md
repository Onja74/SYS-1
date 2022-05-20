# NFS
# 1- Description
Le NFS, pour Network File System, est un protocole permettant à un ordinateur d'accéder à des fichiers extérieurs via un réseau.
Dans la pratique, l'utilisateur, à partir de son ordinateur, va pouvoir accéder à des fichiers stockés sur un serveur distant, 
à l'aide du protocole NFS qui fonctionne selon le mode client/serveur.
# 2- Avantages:
- possibilité donnée à plusieurs ordinateurs d'utiliser les mêmes fichiers 
- réduction des coûts de stockage grâce au partage des applications
- cohérence des données et fiabilité car tous les utilisateurs peuvent lire le même ensemble de fichiers 
- frais d'administration système réduits.
# 3- Installation:
- Sur le serveur Debian, mettez à jour le cache des paquets :
```
$ sudo apt-get update
```
- Puis, installer le paquet "nfs-kernel-server" :
```
$ sudo apt-get install nfs-kernel-server
```
- Configurer le serveur NFS pour qu'il démarre automatiquement avec le système :
```
$ sudo systemctl enable nfs-server.service
```
Le paquet est installé.

# 4-  Déclarer un partage NFS /etc/exports:
-Commençons par créer le partage :
```
$ mkdir /srv/partagenfs
```
-Puis, on applique les droits sur le partage :
```
$ chown nobody:nogroup /srv/partagenfs/
chmod 755 /srv/partagenfs/
```
- Pour déclarer les partages NFS, il faut s'appuyer sur le fichier``` "/etc/exports" ```. 
C'est dans ce fichier que nous allons déclarer notre fichier ``` "/srv/partagenfs" ```. Editer le fichier :

$ sudo nano /etc/exports
- Dans ce fichier, voici la ligne à ajouter pour déclarer notre partage :
```
$ /srv/partagenfs 192.168.100.0/24(rw,sync,anonuid=65534,anongid=65534,no_subtree_check)
```
- Pour que la configuration soit prise en compte :
```
$ exportfs -a
```
- Pour stopper et fermer les partages NFS, il faut exécuter :
```
$ exportfs -ua
```
- Afficher la liste des partages NFS sur l'hôte précisé, c'est à dire notre machine Debian :
```
$ showmount -e 192.168.100.121
```
### Le partage NFS est prêt.

<a href='https://github.com/Onja74/SYS-1'>RETOUR</a>
