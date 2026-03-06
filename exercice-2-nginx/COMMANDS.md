cd D:\DOcker\docker-tp-volumes\exercice-2-nginx

docker run -d --name dev-web -p 8080:80 -v "D:/DOcker/docker-tp-volumes/exercice-2-nginx/tp-nginx:/usr/share/nginx/html" nginx:alpine

curl.exe http://localhost:8080

# j'ai modifie a la main pour mettre Version 2.0

curl.exe http://localhost:8080

# J'ai crée a la main about.html

curl.exe http://localhost:8080/about.html

docker rm -f dev-web
docker run -d --name dev-web -p 8080:80 -v "D:/DOcker/docker-tp-volumes/exercice-2-nginx/tp-nginx:/usr/share/nginx/html:ro" nginx:alpine

docker exec dev-web sh -c "echo test > /usr/share/nginx/html/inside.txt"

docker rm -f dev-web

-Car le conteneur lit directement les fichiers de ton PC 

-Sa permet comme son nom l'indique de simplement lire mais pas ecrire 

-bind mount c'est le dossier du Pc et Volume c'est l'espace gerer par Docker 