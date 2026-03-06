# TP Docker - Gestion des volumes

Le but est de vous faire pratiquer, pas a pas, la persistance des donnees avec Docker via les volumes et les bind mounts.

## Objectifs pedagogiques

A la fin du TP, vous devez etre capable de:
- creer et utiliser un volume nomme
- comprendre la persistance des donnees au-dela du cycle de vie d'un conteneur
- partager des donnees entre plusieurs conteneurs
- utiliser un bind mount pour le developpement local
- utiliser le mode lecture seule (`:ro`) sur un montage
- choisir entre volume et bind mount selon le contexte

## Organisation du TP

Le TP est compose de 2 exercices progressifs:

1. `exercice-1-logger`
- Journalisation persistante partagee entre conteneurs
- Focus: volume nomme, ecriture/lecture multi-conteneurs, persistance apres suppression

2. `exercice-2-nginx`
- Site statique Nginx avec edition en live depuis l'hote
- Focus: bind mount, feedback temps reel, mode lecture seule

## Ce que vous devez rendre

Dans chaque dossier d'exercice, vous devez fournir:
- `README.md` (consigne / contexte / criteres, sans commandes)
- `COMMANDS.md` (toutes les commandes executees pour realiser l'exercice)

Le format attendu est precise dans [CONTRIBUTING.md](./CONTRIBUTING.md).

## Methode de travail conseillee

- Lire d'abord la consigne de l'exercice.
- Realiser un premier montage qui fonctionne.
- Verifier le comportement (partage, persistance, lecture seule).
- Tester les cas de suppression/recreation de conteneur.
- Documenter vos commandes dans `COMMANDS.md`.

## Evaluation

Vous serez evalues sur:
- la conformite a la consigne
- la bonne utilisation des volumes et bind mounts
- la capacite a demonstrer la persistance des donnees
- la maitrise des options de montage (dont `:ro`)
- la clarte du rendu

Bon TP.
