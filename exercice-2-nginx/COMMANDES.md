# Lancer le conteneur NGINX dev-web
docker run -d --name dev-web -p 8080:80 -v C:\Users\jareb\tp-nginx:/usr/share/nginx/html nginx

# Je vous confirme que tout se modifie correctement sans toucher au conteneur

# Supprimer le conteneur
docker rm -f dev-web
# Et le relancer en lecture seule
docker run -d --name dev-web -p 8080:80 -v C:\Users\jareb\tp-nginx:/usr/share/nginx/html:ro nginx

# Essayer de créer un fichier
docker exec -it dev-web sh
touch /usr/share/nginx/html/test.html
# réponse :
Erreur : permission denied

# Supprimer le conteneur
docker rm -f dev-web



- Nous n'avons pas eu besoin de redémarrer le conteneur car le bind mount relie directement le dossier local au conteneur, ce qui fait que toute modification sur le host est directement visible sur le conteneur

- L'utilité du mode lecteure seule permet d'empêcher le conteneur de modifier les fichiers sur l'host, et donc de protéger les données sensibles ou fichiers de config.

- Un bind mount relie directement un dossier de l'ordinateur au conteneur, permettant de voir et modifier les fichiers en temps réel, tandis qu’un volume persiste même si le conteneur est supprimé, et est principalement utilisé pour stocker des données de manière sûre et partagée entre conteneurs.