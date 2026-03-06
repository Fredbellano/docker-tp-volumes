docker volume create logs-data
docker volume ls
docker run --name logger1 -v logs-data:/var/logs alpine sh -c "echo 'Log du conteneur 1' >> /var/logs/app.log"
docker run --name logger2 -v logs-data:/var/logs alpine sh -c "echo 'Log du conteneur 2' >> /var/logs/app.log"
docker run --name log-reader -v logs-data:/var/logs alpine cat /var/logs/app.log
docker run --name log-reader -v logs-data:/var/logs alpine cat /var/logs/app.log
docker rm logger1 logger2 log-reader
docker volume ls
docker volume rm logs-data
