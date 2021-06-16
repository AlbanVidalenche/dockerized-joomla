Voici Mon TP Docker pour la conteneurisationd de l'application Joomla

- J'ai choisi d'utiliser un volume docker pour la partie concernant les fichiers de joomla.
  Cela permet d'utiliser différentes versions de joomla en selectionnant simplement un volume plus récent

- Pour la partie logs et base de donnée, j'ai choisi des bind mounts, qui selon moi facilitent les sauvegardes de BDD et l'accès aux logs


  Pour construire le volume voici la procédure à suivre 
  Télécharger la derniere version de Joomla, puis la décompresser dans un nouveau dossier. 
  Se rendre dans le dossier puis exécuter les commandes suivantes.
  '''docker volume create joomla_data'''
  docker container create --name temp -v joomla_data:/data busybox
  docker cp . temp:/data
 
  Pour créer les volumes nécéssaires aux bind mounts, vous aurez besoin de créer les dossiers suivants.
  /opt/docker/volumes/mariadb/
  /opt/docker/volumes/joomla_logs/php-fpm
  /opt/docker/volumes/joomla_logs/nginx
  /opt/docker/volumes/joomla_logs/mariadb

  Une fois cette étape réalisée, se rendre dans le dossier docker-compose puis éxécuter la commande suivante.
  docker-compose up --build

  La stack devrait alors démarrer.
  
  La preuve que tout fonctionne se situe à l'adresse https://joomla.albanv.fr
  

  
  