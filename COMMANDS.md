# Création d'un volume Docker nommé pour stocker les logs
docker volume create logs_volume

# Lancer un premier conteneur qui écrit une ligne dans le fichier de log
docker container run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log écrit par logger1' > /var/logs/app.log"

# Lancer un deuxième conteneur qui ajoute une ligne dans le même fichier
docker container run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log ajouté par logger2' >> /var/logs/app.log"

# Lire le contenu du fichier de log depuis un conteneur temporaire
docker container run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Supprimer les conteneurs utilisés pour écrire les logs
docker container rm logger1 logger2

# Vérifier que le volume existe toujours
docker volume ls

# Afficher les informations détaillées du volume
docker volume inspect logs_volume

# Vérifier que les données sont toujours présentes dans le volume
docker container run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Supprimer le volume pour nettoyer l'environnement
docker volume rm logs_volume


# Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?
Le volume reste présent et les données qu’il contient sont conservées. Les conteneurs peuvent être supprimés sans perdre les données stockées dans le volume.

# Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?
Plusieurs conteneurs peuvent monter le même volume Docker. Ils accèdent alors aux mêmes fichiers et peuvent lire ou écrire dans les mêmes données.