
docker volume create logs_volume


docker run -it --name logger1 -v logs_volume:/var/logs alpine sh

echo "Premiere ligne de log" >> /var/logs/app.log
exit


docker run -it --name logger2 -v logs_volume:/var/logs alpine sh

echo "Deuxieme ligne de log" >> /var/logs/app.log
exit


# VERIFICATION DU FICHIER

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log


docker rm logger1
docker rm logger2



docker volume ls

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log


# NETTOYAGE FINAL

docker volume rm logs_volume