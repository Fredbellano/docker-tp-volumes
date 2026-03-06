# Je crée un volume Docker nommé logs_volume
docker volume create logs_volume

# Je lance un conteneur alpine nommé logger1 qui écrit une ligne dans le fichier app.log
docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log de logger1' >> /var/logs/app.log"

# Je lance un deuxième conteneur alpine nommé logger2 qui ajoute une ligne dans le même fichier
docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log de logger2' >> /var/logs/app.log"

# J'affiche le contenu du fichier app.log avec un conteneur temporaire
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Je supprime les conteneurs logger1 et logger2
docker rm logger1 logger2

# Je vérifie que le volume existe toujours
docker volume ls

# Je vérifie que les données sont toujours présentes dans le volume
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Je supprime le volume pour nettoyer
docker volume rm logs_volume
