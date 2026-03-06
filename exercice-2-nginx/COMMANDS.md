
mkdir tp-nginx
cd tp-nginx



docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx



docker rm -f dev-web


docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html:ro nginx


docker exec -it dev-web sh


touch test.txt
exit


docker rm -f dev-web