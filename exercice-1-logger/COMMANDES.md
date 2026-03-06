# Créer le volume
docker volume create logs_volume

# logger 1
docker run --name logger1 -v logs_volume:/var/logs alpine echo "Log 1" >> /var/logs/app.log

# logger 2
docker run --name logger2 -v logs_volume:/var/logs alpine echo "Log 2" >> /var/logs/app.log

# troisième conteneur
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# supprimer les conteneurs
docker rm logger1 logger2

# vérifier que le volume existe
docker volume ls
# et les données
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log

# supprimer le volume 
docker volume rm logs_volume


- Si on supprime les conteneurs sans supprimer le volume, rien ne se passera pour les données. Docker sépare le stockage des conteneurs, donc on pourra par exemple créer un nouveau conteneur qui montera le même volume, et on retrouvera toujours nos données

- Docker permet de monter un volume unique sur plusieurs conteneur où chaque conteneur peut lire et écrire dans ce même volume. Le volume agit comme un dossier partagé persistant, indépendant des conteneurs.