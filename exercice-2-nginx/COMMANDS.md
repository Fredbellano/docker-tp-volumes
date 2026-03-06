# Exercice 2

# 1. Création du dossier `tp-nginx` et du fichier `index.html`
```powershell
mkdir $HOME\tp-nginx
Set-Content -Path "$HOME\tp-nginx\index.html" -Value "<h1>Version 1.0</h1>"


# Lancement du conteneur Nginx dev-web avec bind mount et exposition du port 8080

docker run -d --name dev-web -p 8080:80 -v "${HOME}\tp-nginx:/usr/share/nginx/html" nginx:alpine

# Modification du fichier index.html sans redémarrer le conteneur

Set-Content -Path "$HOME\tp-nginx\index.html" -Value "<h1>Version 2.0</h1>"

# Vérification de la mise à jour de la page

curl http://localhost:8080

# Ajout d’un fichier about.html

Set-Content -Path "$HOME\tp-nginx\about.html" -Value "<h1>About page</h1>"

# Vérification de l’accès à la page about.html

curl http://localhost:8080/about.html

# Suppression du conteneur dev-web

docker rm -f dev-web

# Relancement du conteneur avec le bind mount en lecture seule

docker run -d --name dev-web -p 8080:80 -v "${HOME}\tp-nginx:/usr/share/nginx/html:ro" nginx:alpine

# Tentative de création d’un fichier depuis l’intérieur du conteneur

docker exec dev-web sh -c "echo '<h1>Test</h1>' > /usr/share/nginx/html/test.html"

# Nettoyage final

docker rm -f dev-web
Remove-Item -Recurse -Force "$HOME\tp-nginx"