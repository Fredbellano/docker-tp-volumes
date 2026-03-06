# Commandes - Exercice 2

## 1. Créer le dossier et le fichier index.html Version 1.0

```powershell
New-Item -ItemType Directory -Force -Path "$HOME\tp-nginx"
Set-Content "$HOME\tp-nginx\index.html" '<h1>Version 1.0</h1>'
```
Crée le dossier `~/tp-nginx` et un fichier `index.html` contenant "Version 1.0".

---

## 2. Lancer le conteneur Nginx avec bind mount

```bash
docker run -d --name dev-web -v "$HOME/tp-nginx:/usr/share/nginx/html" -p 8081:80 nginx
```
- `-d` : lance en arrière-plan
- `--name dev-web` : nomme le conteneur
- `-v "$HOME/tp-nginx:/usr/share/nginx/html"` : bind mount — lie le dossier local directement dans le conteneur. Toute modification locale est immédiatement visible dans le conteneur.
- `-p 8081:80` : expose le port 80 du conteneur sur le port 8081 de la machine

---

## 3. Vérifier que la page s'affiche

```bash
curl http://localhost:8081
```
Retourne `<h1>Version 1.0</h1>`.

---

## 4. Modifier index.html sans toucher au conteneur

```powershell
Set-Content "$HOME\tp-nginx\index.html" '<h1>Version 2.0</h1>'
```
Modifie le fichier directement sur la machine hôte. Grâce au bind mount, le changement est **instantanément** visible dans le conteneur sans redémarrage.

---

## 5. Vérifier la mise à jour

```bash
curl http://localhost:8081
```
Retourne maintenant `<h1>Version 2.0</h1>` sans avoir redémarré le conteneur.

---

## 6. Ajouter about.html et y accéder

```powershell
Set-Content "$HOME\tp-nginx\about.html" '<h1>About</h1><p>Page about du site</p>'
```

```bash
curl http://localhost:8081/about.html
```
Le fichier créé localement est immédiatement servi par Nginx.

---

## 7. Relancer en lecture seule

```bash
docker rm -f dev-web
docker run -d --name dev-web -v "$HOME/tp-nginx:/usr/share/nginx/html:ro" -p 8081:80 nginx
```
- `:ro` (read-only) : le conteneur peut **lire** les fichiers mais ne peut pas les modifier.

---

## 8. Tenter d'écrire depuis l'intérieur du conteneur

```bash
docker exec dev-web sh -c "echo test > /usr/share/nginx/html/test.txt"
```
Résultat : `Read-only file system` — l'écriture est bloquée par le mode `:ro`.

---

## 9. Nettoyage

```bash
docker rm -f dev-web
```
```powershell
Remove-Item -Recurse -Force "$HOME\tp-nginx"
```
Supprime le conteneur et le dossier local `tp-nginx`.
