  596  cd ../exercice-2-nginx/
  597  mkdir -p ~/tp-nginx
  598  touch ~/tp-nginx/index.html
  599  nano ~/tp-nginx/index.html
  600  docker container run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html nginx
  601  nano ~/tp-nginx/index.html 
  604  touch ~/tp-nginx/about.html
  605  echo "c la page about" >> ~/tp-nginx/about.html
  606  docker stop dev-web 
  607  dock rm dev
  608  docker rm dev-web 
  609  docker container run -d --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html:ro nginx
  610  docker exec -it dev-web bash
  611  docker rm -f dev-web 
  612  history > COMMANDS.md
