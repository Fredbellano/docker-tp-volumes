# Exercice 1

# Création du volume

```bash
docker volume create logs_volume
```
# Lancement du conteneur logger1

```bash
docker run -d --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log écrit par logger1' >> /var/logs/app.log && tail -f /dev/null"
```
# Lancement du conteneur logger2

```bash
docker run -d --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log ajouté par logger2' >> /var/logs/app.log && tail -f /dev/null"
```
# Vérification du contenu du fichier

```bash
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
```

# Suppression des conteneurs

```bash
docker rm -f logger1 logger2
```

# Vérification que le volume existe toujours

```bash
docker volume ls
```

# Vérification que les données sont intactes

```bash
docker run --rm -v logs_volume:/var/logs alpine cat /var/logs/app.log
```

# Nettoyage

```bash
docker volume rm logs_volume
```
