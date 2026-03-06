

2. Lancez un conteneur Nginx nommé `dev-web` qui :
   - Monte votre dossier sur `/usr/share/nginx/html`
   - Expose le port `8080`


docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx


3. Accédez à `http://localhost:8080` et vérifiez que la page s'affiche
OK

4. **Sans toucher au conteneur**, modifiez `index.html` pour afficher "Version 2.0"

echo "<h1>Version 2.0</h1>" > index.html

5. Rechargez la page dans le navigateur
OK

6. Ajoutez un fichier `about.html` et accédez à `http://localhost:8080/about.html`

echo "<h1>About page</h1>" > about.html

7. Supprimez le conteneur et relancez-le avec le bind mount en **lecture seule**

docker container rm -f dev-web
docker container run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html:ro nginx

8. Essayez de créer un fichier depuis l'intérieur du conteneur

docker container exec -it dev-web sh
touch /usr/share/nginx/html/test.html

--> error

exit

9. Nettoyez

docker container rm -f dev-web
Remove-Item -Recurse -Force .\tp-nginx



### ❓ Questions
- Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ?

    le bind mount relie le dossier au conteneur

- Quelle est l'utilité du mode lecture seule ?

protège les fichiers et evite les modifications

- Quelle est la différence entre un bind mount et un volume ?

le bind mount a un lien direct avec le dossier alors que avec un volume le stockage est géré par docker
