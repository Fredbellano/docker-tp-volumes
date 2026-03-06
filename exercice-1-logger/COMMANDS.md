- docker volume create --name logs_volume

- docker container run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Bonjour depuis logger1' >> /var/logs/app.log"

- docker container run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Bonjour depuis logger2' >> /var/logs/app.log"

- docker run -v logs_volume:/var/logs alpine cat /var/logs/app.log

  - Bonjour depuis logger1 
  - Bonjour depuis logger2

- docker rm logger1 logger2   

- docker volume ls
DRIVER    VOLUME NAME
local     logs_volume

- docker run -v logs_volume:/var/logs alpine cat /var/logs/app.log

  - Bonjour depuis logger1 
  - Bonjour depuis logger2

- docker volume rm logs_volume   


### Questions
- Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?
  - Rien le volume est toujours disponible et donc peut être utilisé par un nouveau container
- Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?
  - Si ils partageant le même volume, alors ils peuvent partager les mêmes données

