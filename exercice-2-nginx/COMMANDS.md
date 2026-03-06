# Exercice 2 

```
~/tp-nginx/
└── index.html
```

Contenu du fichier :

```html
<h1>Version 1.0</h1>
```

## Lancer le conteneur Nginx

```bash
docker run -d --name dev-web -p 8080:80 -v %cd%\tp-nginx:/usr/share/nginx/html nginx
```

## Vérifier le site

```
http://localhost:8080
```

## Modifier le fichier en live

```html
<h1>Version 2.0</h1>
```

## Ajouter une nouvelle page

```
~/tp-nginx/about.html
```

```
http://localhost:8080/about.html
```

## Relancer le conteneur en lecture seule

```bash
docker stop dev-web
docker rm dev-web
```

```bash
docker run -d --name dev-web -p 8080:80 -v %cd%\tp-nginx:/usr/share/nginx/html:ro nginx
```

## Tester l'écriture dans le conteneur

```bash
docker exec -it dev-web bash
```

```bash
touch /usr/share/nginx/html/test.html
```

## Nettoyage

Supprimer le conteneur :

```bash
docker stop dev-web
docker rm dev-web
```
