
## Exercice 1 — Le journal de bord persistant

### 📋 Contexte
Vous développez un système de journalisation. Chaque conteneur écrit des logs dans un fichier. Vous devez garantir que les logs **survivent** à la suppression des conteneurs et qu'ils soient **partagés** entre plusieurs conteneurs.

### 🎯 Objectifs
- Créer un volume nommé
- Écrire des données depuis plusieurs conteneurs
- Vérifier la persistance après suppression

### 📝 Consignes

1. Créez un volume Docker nommé `logs_volume`

2. Lancez un conteneur `alpine` nommé `logger1` qui :
   - Monte le volume sur `/var/logs`
   - Écrit une ligne de log dans `/var/logs/app.log`

3. Lancez un deuxième conteneur `alpine` nommé `logger2` qui :
   - Monte le **même** volume
   - Ajoute une autre ligne dans le **même** fichier

4. Lancez un troisième conteneur éphémère qui affiche le contenu du fichier

5. Supprimez les conteneurs `logger1` et `logger2`

6. Vérifiez que le volume existe toujours et que les données sont intactes

7. Nettoyez en supprimant le volume

### ❓ Questions
- Que se passe-t-il si vous supprimez les conteneurs sans supprimer le volume ?
- Comment plusieurs conteneurs peuvent-ils partager les mêmes données ?