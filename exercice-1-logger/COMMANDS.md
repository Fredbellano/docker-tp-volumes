- docker volume create logs_volume
- docker container run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'bonjour' >> /var/logs/app.log"
- docker container run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'bonjour de la deuxième ligne' >> /var/logs/app.log"
- docker container run --rm --name logger3 -v logs_volume:/var/logs alpine cat /var/logs/app.log
- docker rm logger2 logger1
- docker container run --rm --name logger3 -v logs_volume:/var/logs alpine cat /var/logs/app.log
- docker ps -a
- docker volume ls
- docker volume rm logs_volume 


### ❓ Questions
- Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?
  - les données restent stockés dans le volume
- Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?
  - S'ils sont montés sur le même volume