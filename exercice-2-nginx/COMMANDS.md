## Commandes pour l'exercice 2

# 1
mkdir ~/tp-nginx
echo "<h1>Version 1.0</h1>" > ~/tp-nginx/index.html

# 2
docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html nginx

# 3
docker ps

# 4
echo "<h1>Version 2.0</h1>" > ~/tp-nginx/index.html

# 5
curl http://localhost:8080

# 6
echo "<h1>About page</h1>" > ~/tp-nginx/about.html
curl http://localhost:8080/about.html

# 7
docker rm -f dev-web
docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html:ro nginx

# 8
touch /usr/share/nginx/html/asli.html

# 9
docker rm -f dev-web

# Réponses : 
- Parce qu’un bind mount relie directement un dossier de l’hôte au conteneur.
- Il empêche le conteneur de modifier les fichiers de l’hôte.
- Un blind mount gère le dossier tp nginx dans le conteneur pour voir les modifications sur le site alors que le volume garde les données meme si le conteneur est supprimé.
