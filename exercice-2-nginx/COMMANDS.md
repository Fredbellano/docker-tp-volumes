-  mkdir tp-nginx  
    
-  touch index.html  

-  docker container run -d --name dev-web -p 8080:80 -v /home/nasonny/Projects/DockerCours/docker-tp-volumes/exercice-2-nginx/tp-nginx:/usr/share/nginx/html nginx
  
- touch about.html
-  echo "c la page about" >> about.html

- docker stop dev-web 
- docker rm dev-web 

- docker container run -d --name dev-web -p 8080:80 -v /home/nasonny/Projects/DockerCours/docker-tp-volumes/exercice-2-nginx/tp-nginx:/usr/share/nginx/html:ro nginx
- docker exec -it dev-web bash

- root@19aa3e61aef3:/# touch /usr/share/nginx/html/test.txt
- touch: cannot touch '/usr/share/nginx/html/test.txt': Read-only file system

- docker rm -f dev_web  

### ❓ Questions
- Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ?
  - Car on partage le dossier qui est sur notre PC directement donc toute modification est retransmis au conteneur
- Quelle est l'utilité du mode lecture seule ?
  - Eviter d'écrire à l'interieur du conteneur et uniquement sur le dossier sur la machine hôte
- Quelle est la différence entre un bind mount et un volume ?
  - Un bind mount utilise un chemin réel de ta machine donc ce qui permet de faire du dev live sans problème et Un volume est créé et maintenu par Docker dans son propre espace donc stocker de façon persistante uniquement pour les dockers.