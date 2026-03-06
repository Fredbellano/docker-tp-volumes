mkdir C:\tp-nginx
mkdir C:\tp-nginxecho "<h1>Version 1.0</h1>" > C:\tp-nginx\index.html

docker run -d --name dev-web -p 8080:80 -v C:\tp-nginx:/usr/share/nginx/html nginx

echo "<h1>Version 2.0</h1>" > C:/tp-nginx/index.html

echo "<h1>Page About</h1>" > C:/tp-nginx/about.html

docker rm -f dev-web

docker run -d --name dev-web -p 8080:80 -v C:\tp-nginx:/usr/share/nginx/html:ro nginx

docker exec dev-web sh -c "echo '<h1>Test</h1>' > /usr/share/nginx/html/test.html"
                                                  
sh: can't create /usr/share/nginx/html/test.txt: Read-only file system

docker rm -f dev-web   

Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ?

parce qu'il est monté sur ma machine et donc n'a pas besoin d'être redémarré.

Quelle est l'utilité du mode lecture seule ?

Empêcher les modifications de fichier ou autres.

Quelle est la différence entre un bind mount et un volume ?

Le volume est indépendant de l'hôte alors que le mount est directement lié à lui.