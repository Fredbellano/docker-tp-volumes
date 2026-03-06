cd D:\DOcker\docker-tp-volumes\exercice-1-logger

docker volume create marwane

docker run -d --name logger1 -v marwane:/var/logs alpine sh -c "echo '[logger1] premier log' >> /var/logs/app.log && tail -f /dev/null"

docker run -d --name logger2 -v marwane:/var/logs alpine sh -c "echo '[logger2] deuxieme log' >> /var/logs/app.log && tail -f /dev/null"

docker run --rm -v marwane:/var/logs alpine cat /var/logs/app.log

docker rm -f logger1 logger2

docker volume ls
docker run --rm -v marwane:/var/logs alpine cat /var/logs/app.log

docker volume rm marwane


- Si je supprime les conteneurs sans supprimer le volume, les données vont rester donc si je relance un nouveau conteneur je vais retrouver les fichiers (on a fait le test hier pendant la pratique)

- Les deux conteneurs utilisent le même volume, donc ils voient les mêmes fichiers.