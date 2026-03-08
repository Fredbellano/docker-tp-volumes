## Commandes pour l'exercice 1

# 1
docker volume create logs_volume

# 2
docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log depuis logger1' >> /var/logs/app.log"

# 3
docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log depuis logger2' >> /var/logs/app.log"

# 4
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# 5
docker rm logger1 logger2

# 6
docker volume ls
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# 7
docker volume rm logs_volume

# Réponses : 
- On remarque que les données restent dans le volume.
- Grace à -v logs_volume:/var/logs qui permet à plusieurs conteneurs de monter le meme volume.
