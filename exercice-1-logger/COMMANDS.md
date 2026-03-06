# Exercice 1


# Création du volume nommé

docker volume create logs_volume

# Lancement du conteneur logger1 avec montage du volume et écriture d'une première ligne de log

docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log 1 - démarrage du service' >> /var/logs/app.log"

# Lancement du conteneur logger2 avec le même volume et ajout d’une seconde ligne dans le même fichier

docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log 2 - seconde écriture' >> /var/logs/app.log"

# Vérification du contenu du fichier avec un conteneur éphémère

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Suppression des conteneurs logger1 et logger2

docker rm logger1 logger2

# Vérification que le volume existe toujours après suppression des conteneurs

docker volume ls

# Vérification que les données sont toujours présentes dans le volume

docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Nettoyage final : suppression du volume

docker volume rm logs_volume