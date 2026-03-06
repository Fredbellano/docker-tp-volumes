docker volume create logs_volume

docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Test' >> /var/logs/app.log"

docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'test 2' >> /var/logs/app.log"

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

docker rm logger1 logger2

docker volume ls

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

docker volume rm logs_volume

Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?

Les données restent intactes

Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?

En montant le même volume nommé dans plusieurs conteneurs
