
créer le volume Docker: 

`docker volume create logs_volume`

Lancement d'un conteneur alpine monté sur var/logs:

`docker run -d --name logger1 -v logs_volume:/var/logs alpine sleep 3600`

Ecriture du premier message & verification:

`docker exec logger1 sh -c "echo '[Logger1] OY ZEUBI!' > /var/logs/app.log"`

`docker exec logger1 cat /var/logs/app.log`


Lancer un deuxieme conteneur

`docker run -d --name logger2 -v logs_volume:/var/logs alpine sleep 3600`

Ajouter un deuxieme message & vreif:

`docker exec logger2 sh -c "echo '[Logger2] Deuxième message' >> /var/logs/app.log"`
`docker exec logger2 cat /var/logs/app.log`


Lancer le 3ème conteneur ephémère:

`docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log`

Supprimez les conteneurs :

`docker stop logger1 logger2`
`docker rm logger1 logger2`

Verification :
`docker volume ls`
`docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log`


Suppression des volumes :

`docker volume rm logs_volume`



