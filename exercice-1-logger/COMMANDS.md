docker volume create logs_volume

docker run -d --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log de logger1' >> /var/logs/app.log && tail -f /dev/null"

docker run -d --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log de logger2' >> /var/logs/app.log && tail -f /dev/null"

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

docker rm -f logger1 logger2

docker volume ls

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

docker volume rm logs_volume

# reponses au question :
Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?

Les conteneurs sont supprimés, mais le volume reste présent.
Les données stockées dans le volume sont donc conservées.

Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?

Plusieurs conteneurs peuvent monter le même volume sur un chemin identique ou différent.
Ils accèdent alors aux mêmes fichiers stockés dans ce volume.
