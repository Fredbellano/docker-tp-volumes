# Comment rendre votre TP

## 1. Fork le repository

Cliquez sur le bouton **Fork** en haut à droite de cette page.

## 2. Cloner votre fork

```bash
git clone https://github.com/VOTRE-USERNAME/docker-tp-images.git
cd docker-tp-images
```

## 3. Créer une branche avec votre nom

```bash
git checkout -b tp/prenom-nom
```

## 4. Faire les exercices
Pour chaque exercice, créez les fichiers demandés.

## 5. Format de rendu obligatoire

Pour chaque dossier d'exercice, le rendu doit contenir:

- un `Dockerfile` qui répond a la consigne
- un fichier de commandes separe au format Markdown: `COMMANDS.md`

Regle importante:

- le `README.md` de l'exercice decrit uniquement la consigne, le contexte et les criteres
- les commandes ne doivent pas etre ecrites dans le `README.md`
- toutes les commandes doivent etre dans le fichier dedie `COMMANDS.md`

Structure attendue (exemple):

```text
exercice-x/
  README.md
  Dockerfile
  COMMANDS.md
```
