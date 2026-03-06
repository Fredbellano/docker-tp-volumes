docker volume create logs_volume

docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log entry from logger1' >> /var/logs/app.log"

docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log entry from logger2' >> /var/logs/app.log"

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

docker rm logger1
docker rm logger2

docker volume ls

docker volume rm logs_volume