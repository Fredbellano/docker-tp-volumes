mkdir ~/tp-nginx
echo "<h1>Version 1.0</h1>" > ~/tp-nginx/index.html

docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html nginx

echo "<h1>Version 2.0</h1>" > ~/tp-nginx/index.html

echo "<h1>About</h1>" > ~/tp-nginx/about.html

docker rm dev-web

docker run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html:ro nginx

docker exec -it dev-web sh

touch /usr/share/nginx/html/test.html

docker rm dev-web

rm ~/tp-nginx