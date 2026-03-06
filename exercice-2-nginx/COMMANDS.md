# Créer le dossier de travail
mkdir tp-nginx
cd .\tp-nginx

# Créer la page d'accueil en version 1.0
echo "<h1>Version 1.0</h1>" > index.html

# Lancer un conteneur 
docker container run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx

# Vérifier : http://localhost:8080

# Modifier le fichier local sans redémarrer
echo "<h1>Version 2.0</h1>" > index.html

# Vérifier : http://localhost:8080

# Ajouter une nouvelle page
echo "<h1>About page</h1>" > about.html

# Vérifier dans le navigateur : http://localhost:8080/about.html

# Supprimer le conteneur de développement
docker container rm -f dev-web

# Relancer le conteneur avec le bind mount en lecture seule
docker container run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html:ro nginx

# Ouvrir un shell dans le conteneur
docker container exec -it dev-web sh

# Essayer de créer un fichier dans le dossier monté
touch /usr/share/nginx/html/test.html 
  --> ERROR

# Sortir du shell du conteneur
exit

# Supprimer le conteneur
docker container rm -f dev-web

# Supprimer le dossier de travail local
cd ..
Remove-Item -Recurse -Force .\tp-nginx

# Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ?
Parce que le conteneur utilise un bind mount. Les fichiers du dossier local sont directement partagés avec le conteneur, donc toute modification sur la machine hôte est immédiatement visible dans le conteneur.

# Quelle est l'utilité du mode lecture seule ?
Le mode read only :ro empêche le conteneur de modifier les fichiers montés. Cela permet de protéger les données et d’éviter des modifications accidentelles.

# Quelle est la différence entre un bind mount et un volume ?
Un bind mount relie un dossier de la machine au conteneur.
Un volume Docker est géré par Docker.