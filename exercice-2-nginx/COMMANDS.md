mkdir ~/tp-nginx
cd ~/tp-nginx
echo "<h1>Version 1.0</h1>" > index.html

docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html nginx

echo "<h1>Version 2.0</h1>" > index.html

echo "<h1>About Page</h1>" > about.html

docker rm -f dev-web

docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html:ro nginx

docker exec -it dev-web sh
touch /usr/share/nginx/html/test.txt

docker rm -f dev-web
rm -rf ~/tp-nginx

# reponses aux questions :

Pourquoi n’avez-vous pas eu besoin de redémarrer le conteneur ?
Parce que le bind mount synchronise directement le dossier de la machine hôte avec le conteneur.

Quelle est l’utilité du mode lecture seule ?
Il empêche le conteneur de modifier les fichiers du système hôte.

Différence entre bind mount et volume ?
Un bind mount utilise un dossier du système hôte, alors qu’un volume est géré par Docker.
