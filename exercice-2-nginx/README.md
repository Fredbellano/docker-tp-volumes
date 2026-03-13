
## Exercice 2 — Le serveur web en développement

### 📋 Contexte
Vous développez un site web statique avec **Nginx**. Vous voulez modifier vos fichiers HTML sur votre machine et voir les changements **en temps réel** dans le conteneur.

### 🎯 Objectifs
- Utiliser un **bind mount** pour le développement
- Modifier des fichiers en live
- Tester le mode lecture seule

### 📝 Consignes

1. Créez un dossier `~/tp-nginx` avec un fichier `index.html` contenant un titre "Version 1.0"

2. Lancez un conteneur Nginx nommé `dev-web` qui :
   - Monte votre dossier sur `/usr/share/nginx/html`
   - Expose le port `8080`

3. Accédez à `http://localhost:8080` et vérifiez que la page s'affiche

4. **Sans toucher au conteneur**, modifiez `index.html` pour afficher "Version 2.0"

5. Rechargez la page dans le navigateur

6. Ajoutez un fichier `about.html` et accédez à `http://localhost:8080/about.html`

7. Supprimez le conteneur et relancez-le avec le bind mount en **lecture seule**

8. Essayez de créer un fichier depuis l'intérieur du conteneur

9. Nettoyez

### ❓ Questions
- Pourquoi n'avez-vous pas eu besoin de redémarrer le conteneur après modification ? Comme le dossier est sur notre machine il a pas besoin de se recharger et les infos sont trasmises directement
- Quelle est l'utilité du mode lecture seule ? Eviter que par exemple si quelqu'un accède au conteneur il puisse écrire dedans
- Quelle est la différence entre un bind mount et un volume ? Un bind mount alloue un espace de la machine que les conteneurs peuvent utiliser alors qu'un volume est un espace créer pour que les conteneurs le gère eux même