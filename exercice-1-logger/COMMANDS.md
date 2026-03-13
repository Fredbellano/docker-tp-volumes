  571  git checkout -b tp/Lucas-Hennebelle
  574  docker volume create --name logs_volume
  587  docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo '[logger1]' >> /var/logs/app.log"
  588  docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo '[logger2]' >> /var/logs/app.log"
  589  docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
  590  docker rm logger1 logger2
  591  docker volume ls --filter name=logs_volume
  592  docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
  593  docker volume rm logs_volume
  594  history > COMMANDS.md
