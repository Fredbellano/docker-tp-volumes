docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx
echo "<h1>About page</h1>" > about.html
docker rm -f dev-web
docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html:ro nginx
docker exec -it dev-web sh
touch /usr/share/nginx/html/test.html
ls /usr/share/nginx/html
exit
docker rm -f dev-web
