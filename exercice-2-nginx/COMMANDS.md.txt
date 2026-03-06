docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx
echo "<h1>Version 2.0</h1>" > index.html
echo "<h1>About page</h1>" > about.html

docker rm -f dev-web

docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html:ro nginx

docker exec -it dev-web sh
touch /usr/share/nginx/html/test.html

docker rm -f dev-web
cd ..
Remove-Item -Recurse -Force .\tp-nginx