# 1. création du volume

docker volume create logs_volume

# 2. Lancez un conteneur `alpine` nommé `logger1` qui :
   - Monte le volume sur `/var/logs`
   - Écrit une ligne de log dans `/var/logs/app.log`

docker container run --name logger1 -v logs_volume:/var/logs alpine sh -c "echo 'Log écrit par logger1' > /var/logs/app.log"


# 3. Lancez un deuxième conteneur `alpine` nommé `logger2` qui :
   - Monte le **même** volume
   - Ajoute une autre ligne dans le **même** fichier

docker container run --name logger2 -v logs_volume:/var/logs alpine sh -c "echo 'Log ajouté par logger2' >> /var/logs/app.log"

4. Lancez un troisième conteneur éphémère qui affiche le contenu du fichier

5. Supprimez les conteneurs `logger1` et `logger2`

6. Vérifiez que le volume existe toujours et que les données sont intactes

7. Nettoyez en supprimant le volume
