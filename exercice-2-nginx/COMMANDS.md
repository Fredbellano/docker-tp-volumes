- mkdir -p ~/tp-nginx
- echo "<h1>Version 1.0</h1>" > ~/tp-nginx/index.html
- docker run --name dev-web -v /home/raphael/tp-nginx:/usr/share/nginx/html -p 8080:80 -d nginx
- nano ~/tp-nginx/index.html
- echo "<h1>About</h1>" > ~/tp-nginx/about.html
- docker rm -f dev-web
- docker run --name dev-web -v /home/raphael/tp-nginx:/usr/share/nginx/html:ro -p 8080:80 -d nginx
- docker run --rm -v /home/raphael/tp-nginx:/usr/share/nginx/html:ro alpine sh -c "echo 'test' > /usr/share/nginx/html/test.txt"                                                  
  - sh: can't create /usr/share/nginx/html/test.txt: Read-only file system
- docker rm -f dev-web   


### ❓ Questions
- Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ?
    parce qu'il est monté sur ma machine et donc n'a pas besoin d'être redémarré.
- Quelle est l'utilité du mode lecture seule ?
    empêcher la modification des données.
- Quelle est la différence entre un bind mount et un volume ?
    le volume est indépendant de l'hôte alors que le mount est directement lié à lui.