

Dossier créé sans commande
pareil pour l'index.html


Lancer un conteneur nginx nommé devweb & exposé en 8080:

`docker run -d --name dev-web -p 8080:80 -v /tp-nginx:/usr/share/nginx/html nginx`

verification de la page faite

Modifier l'html pour afficher "Version 2.0":

`echo "<h1>Version 2.0</h1>" > /tp-nginx/index.html`

retirer le conteneur dev-web:
`docker stop dev-web`
`docker rm dev-web`

relancer en lecture seule & créer un fichier dans le conteneur:
`docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html:ro nginx`
`docker exec dev-web touch /usr/share/nginx/html/test.txt`

nETTOYAGE COMPLET:

`docker stop dev-web`
`docker rm dev-web`