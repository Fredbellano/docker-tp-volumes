## docker pull nginx
## docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx\~\tp-nginx:/usr/share/nginx/html:rw -d nginx
## docker rm -f dev-web
## docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx\~\tp-nginx:/usr/share/nginx/html:ro -d nginx
## root@a800da8dc6e7:/usr/share/nginx/html# ls
## about.html  index.html
## root@a800da8dc6e7:/usr/share/nginx/html# touch test.html
## touch: cannot touch 'test.html': Read-only file system
## docker rm -f dev-web


le changement était bien en temps réel et le read only m'empechait de créer un nouveau fichier



PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx\~\tp-nginx:/usr/share/nginx/html:ro -d nginx
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker exec -it dev-web /bin/bash
root@a800da8dc6e7:/# ls
bin  boot  dev  docker-entrypoint.d  docker-entrypoint.sh  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@a800da8dc6e7:/# cd usr/
root@a800da8dc6e7:/usr# ls
bin  games  include  lib  lib64  libexec  local  sbin  share  src
root@a800da8dc6e7:/usr# cd share/nginx/html/
root@a800da8dc6e7:/usr/share/nginx/html# ls
about.html  index.html
root@a800da8dc6e7:/usr/share/nginx/html# touch test.html
touch: cannot touch 'test.html': Read-only file system
root@a800da8dc6e7:/usr/share/nginx/html# exit 
exit
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker rm -f dev-web
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> 




Console complète :  





PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> mkdir

applet de commande mkdir à la position 1 du pipeline de la commande
Fournissez des valeurs pour les paramètres suivants :
Path[0]: ^X
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> mkdir -p ~/tp-nginx


    Répertoire : C:\Users\Hicha


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        06/03/2026     17:39                tp-nginx


PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
df0b66c867e4: Pull complete
b47f187216b6: Pull complete
eedda9fd8786: Pull complete
35ff83c394d6: Pull complete
1ad233904a11: Pull complete
17d0911eaf62: Pull complete
Digest: sha256:0236ee02dcbce00b9bd83e0f5fbc51069e7e1161bd59d99885b3ae1734f3392e
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker run --name dev-web -p 8080:80 -v ~/tp-nginx:/usr/share/nginx/html:rw -d nginx               
>> 
e08cf8ccb81d9d7840933add2ce269d9d8db744880a7af77f70596ae0a6cfd3b
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker stop dev-web 
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker rm dev-web  
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\tp-nginx:/usr/share/nginx/html:rw -d nginx
>>
f41b62c2b8924267849955ee98a2b1f91269a7f954737568676a43e03a21292b
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker stop dev-web
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker rm dev-web
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx\~\tp-nginx:/usr/share/nginx/html:rw -d nginx
>> 
732047f9ee84f756c55e2f7061a4eb29dc886aef823af700d36a68538eee8676
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> echo "<h1>Version 2.0</h1>" > ~/tp-nginx/index.html
>>
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker stop dev-web                                                                                
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker rm dev-web                                                                                  
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx\~\tp-nginx:/usr/share/nginx/html:r -d nginx 
>> 
docker: Error response from daemon: invalid mode: r

Run 'docker run --help' for more information
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker run --name dev-web -p 8080:80 -v C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx\~\tp-nginx:/usr/share/nginx/html:ro -d nginx
>> 
a800da8dc6e79d654b4edad6dcee47ea4b65ca90bfe75ece738769b1136d5d94
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker exec -it dev-web
docker: 'docker exec' requires at least 2 arguments

Usage:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

See 'docker exec --help' for more information
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker exec -it dev-web /bin/bash
root@a800da8dc6e7:/# ls
bin  boot  dev  docker-entrypoint.d  docker-entrypoint.sh  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@a800da8dc6e7:/# cd usr/
root@a800da8dc6e7:/usr# ls
bin  games  include  lib  lib64  libexec  local  sbin  share  src
root@a800da8dc6e7:/usr# cd share/nginx/html/
root@a800da8dc6e7:/usr/share/nginx/html# ls
about.html  index.html
root@a800da8dc6e7:/usr/share/nginx/html# touch test.html
touch: cannot touch 'test.html': Read-only file system
root@a800da8dc6e7:/usr/share/nginx/html# exit 
exit
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> docker rm -f dev-web
dev-web
PS C:\Users\Hicha\Desktop\dev\cours-docker\docker-tp-volumes\exercice-2-nginx> 