# Création du volume 
docker volume create logs_volume

# Build et Run d'un premier conteneur qui créera le fichier app.log
docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'premier log' > /var/logs/app.log"

# Création d'un 2e logger avec le même point de montage pour ajouter une ligne à app.log
docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log 2 test' >> /var/logs/app.log"

# Lecture des données avec conteneur éphémère
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Suppression des conteneurs
docker rm logger1 logger2


# Vérification de la présence des données
docker volume ls
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# Suppression du volume 
docker volume rm logs_volume

### ❓ Questions
- Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?
La suppression des conteneurs n'entrainent pas la suppression du volume

- Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?
Car docker utilise des montages de type "bind" qui permettent à plusieurs namespaces de pointer vers le même fichier hôte.