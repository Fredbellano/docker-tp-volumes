# Lancer le serveur avec Bind Mount
docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html nginx

# Supression du conteneur actuel
docker rm -f dev-web

# Relancer un conteneur en mode lecture seule
docker run -d --name dev-web -p 8080:80 -v ${PWD}:/usr/share/nginx/html:ro nginx

# Test d'écriture depuis le conteneur
docker exec dev-web touch /usr/share/nginx/html/hack.txt
# Réponse du container :
# touch: cannot touch '/usr/share/nginx/html/hack.txt': Read-only file system

# Nettoyage 
docker rm -f dev-web


### ❓ Questions
- Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ?
Car nginx lis les fichiers du disque à chaque requête et comme le container est un mirroir de notre dossier, il voit directement les modifications
- Quelle est l'utilité du mode lecture seule ?
Le mode lecture seule est utile en terme de sécurité en empêchant de motifier les fichiers sources
- Quelle est la différence entre un bind mount et un volume ?
un bind mount pointe vers un chemin précis chez l'hôte tandis que le volume est géré par Docker 