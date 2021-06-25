# TP Docker pour la conteneurisationd de l'application Joomla

- Voici ma solution pour la conteneurisation de l'application joomla
- Le .zip qui vous a été remis est un repo git hébergé sur github. Je peux le passer en public si vous préférez.

## Fonctionnement 

- La stack repose sur quatre conteneurs, deux volumes docker, et d'autres volumes sour la forme de bind-mount.
- L'application est stockée dans un volume docker créé par le conteneur joomla, qui est accessible par deux conteneurs, nginx-ssl et php-fpm
- J'ai choisi d'utiliser un conteneur séparé pour les données, car en cas de changement de configuration sur un des conteneurs applicatifs, celui-ci ne sera jamais affecté.
- Le conteneur nginx est le point d'entrée de l'application, et fait appel au conteneur php-fpm pour le traitement php. 
- La particularité du conteneur Nginx est qu'il s'agit d'une version customisée avec l'ajout de letsecrypt, qui permet d'obtenir un certificat à la création de la stack. - La configuration actuelle permet d'obetnir un certificat pour l'adresse joomla.vidalenche.fr. Un volume est dédié au stockage des certificats, il ne sera pas donc pas nécéssaire d'obtenir un nouveau certificat à chaque lancement. Le service renouvellera son certificat avant qu'il expire de manière automatique.
- Le conteneur php écoute sur le port 9000, et comunique avec Nginx pour traiter les requêtes.
- Enfin, le conteneur mariadb n'a subit aucune modification, il n'y a donc pas de fichier Dockerfile utilisé.
- La seule chose à savoir à propos de ce conteneur est que les informations sensibles comme les mots de passe sont fournis sous la forme de variables d'environnement qui ne sont pas dans le dépôt, (cf: gitignore)

## Déploiement de la stack 

 
  Pour créer les volumes nécéssaires aux bind mounts, vous aurez besoin de créer les dossiers suivants.
  /opt/docker/volumes/mariadb/
  /opt/docker/volumes/joomla_logs/php-fpm
  /opt/docker/volumes/joomla_logs/nginx
  /opt/docker/volumes/joomla_logs/mariadb

 *  Une fois cette étape réalisée, se rendre dans le dossier docker-compose puis éxécuter la commande suivante.
  
  ```sh
  docker-compose up --build
  ```

  La stack devrait alors démarrer.
  
  La preuve que tout fonctionne se situe à l'adresse https://joomla.vidalenche.fr
  

  
  
