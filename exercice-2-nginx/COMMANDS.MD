# Je crée le dossier du projet
mkdir tp-nginx

# Je me place dans le dossier
cd tp-nginx

# Je crée un fichier index.html avec la version 1.0
echo "<h1>Version 1.0</h1>" > index.html

# Je lance un conteneur Nginx avec un bind mount sur mon dossier et le port 8082
docker run -d --name dev-web -p 8082:80 -v ${PWD}:/usr/share/nginx/html nginx

# Je modifie index.html pour afficher Version 2.0
# (modification faite dans VS Code)

# Je crée une nouvelle page about.html
echo "<h1>About page</h1>" > about.html

# Je supprime le conteneur dev-web
docker rm -f dev-web

# Je relance le conteneur avec le bind mount en lecture seule
docker run -d --name dev-web -p 8082:80 -v ${PWD}:/usr/share/nginx/html:ro nginx

# J'entre dans le conteneur
docker exec -it dev-web sh

# Je me place dans le dossier monté
cd /usr/share/nginx/html

# Je teste la création d'un fichier (doit échouer car le dossier est en lecture seule)
touch test.txt

# Je quitte le conteneur
exit

# Je supprime le conteneur pour nettoyer
docker rm -f dev-web