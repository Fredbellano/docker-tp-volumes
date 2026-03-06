# Commandes - Exercice 1

## 1. Créer le volume nommé

```bash
docker volume create logs_volume
```
Crée un volume Docker nommé `logs_volume`. Les données stockées dans ce volume persistent indépendamment des conteneurs.

---

## 2. Lancer logger1 et écrire dans le fichier

```bash
docker run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo '[logger1] $(date) - Démarrage du service' >> /var/logs/app.log"
```
- `--name logger1` : nomme le conteneur
- `-v logs_volume:/var/logs` : monte le volume sur `/var/logs` dans le conteneur
- `alpine` : image légère Linux
- `sh -c "echo ... >> /var/logs/app.log"` : ajoute une ligne dans le fichier de log (`>>` = append sans écraser)

---

## 3. Lancer logger2 et ajouter une ligne dans le même fichier

```bash
docker run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo '[logger2] $(date) - Connexion utilisateur' >> /var/logs/app.log"
```
Même volume monté → le fichier `app.log` est partagé entre `logger1` et `logger2`. La ligne s'ajoute à la suite.

---

## 4. Afficher le contenu du fichier avec un conteneur éphémère

```bash
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
```
- `--rm` : supprime automatiquement le conteneur après exécution
- `cat /var/logs/app.log` : affiche le contenu du fichier

---

## 5. Supprimer les conteneurs logger1 et logger2

```bash
docker rm logger1 logger2
```
Supprime les deux conteneurs. Le volume et ses données ne sont **pas** supprimés.

---

## 6. Vérifier que le volume existe toujours

```bash
docker volume ls --filter name=logs_volume
```
Liste les volumes filtrés par nom. Le volume apparaît toujours malgré la suppression des conteneurs.

## 6b. Vérifier que les données sont intactes

```bash
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
```
Lance un nouveau conteneur éphémère sur le même volume : les deux lignes écrites par `logger1` et `logger2` sont toujours présentes.

---

## 7. Supprimer le volume

```bash
docker volume rm logs_volume
```
Supprime définitivement le volume et toutes les données qu'il contient.
