# NGINX
# 1 -Description
C'est un serveur web open-source qui,
depuis son succès initial en tant que serveur web, est maintenant aussi utilisé comme reverse proxy, 
cache HTTP, et load balancer.

Reverse proxy : c'est un type de serveur, habituellement placé en frontal de serveurs web.

Cache HTTP : les performances des sites et applications web peuvent être significativement améliorées en réutilisant les ressources déjà collectées précédemment. 

Load balencer : elle désigne le processus de répartition d’un ensemble de tâches sur un ensemble de ressources.
# 2 -Avantages
- plus performant qu'Apache dans le traitement de nombreuses connexions simultanées.
- nginx utilise considérablement moins de stockage par connexion client.
- mieux lorsqu’il s’agit de traiter un contenu statique
- Surpasse Apache dans la gestion du contenu statique
# 3 -Installation
- Actualiser les différents éléments du paquet NGINX de manière à posséder les versions les plus récentes:

$ sudo apt-get update

$ sudo apt-get install nginx
- Vérifier si le logiciel fonctionne en bonne et due forme, charger la "landingpage de NGINX"

"WELCOME TO NGINX" s'affiche ---> c'est instlallé
-  Pour la configuration consulter le dossier: 

/etc/nginx 

et dans le fichier de configuration:

nginx.conf. 

- A chaque modifications, il est nécessaire de redémarrer le serveur, commandes:

$ sudo service nginx reload

$ sudo service nginx restart

 Les paramètres stop et start, On peut interrompre et reprendre le service en cours.

- La syntaxe du fichier de configuration présente les caractéristiques suivantes :

Avec les paramètres stop et start, vous pouvez respectivement interrompre et reprendre le service en cours.

- La syntaxe du fichier de configuration présente les caractéristiques suivantes :

○ Réglages : tous les réglages commencent par le nom variable respectif. Un espace vide délimite deux arguments et la ligne se termine toujours par un point-virgule.

$ worker_connections 768;
○ Paramètres avancés : certains paramètres tels que les events-variable comportent des arguments qui leurs sont propres. Ces sous-directives sont entourées par des accolades ({}).

$ events {
  
  worker_connections 768;
  
  multi_accept on;
  
}

○ Signe dièse (#): Il s’agit de directives (instructions) désactivées à l’aide du caractère dièse. En enlevant ce signe, On réactive le réglage correspondant.

 --> # multi_accept on;
 
○ Tabulations et espaces vides : NGINX interprète les espaces libres multiples et les tabulations comme un seul espace vide. Lors de la configuration de NGINX,
il convient de faire attention à la propreté et lisibilité de la structure du ficher de configuration.


