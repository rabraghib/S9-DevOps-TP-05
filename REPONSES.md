# TP 7 – Actions tierces et actions personnalisées

## Partie 1 – Utiliser des actions tierces (`uses` et `with`)

- **Q1. Pourquoi `actions/checkout` n'a-t-il pas besoin de `with` alors que `setup-node` en a besoin ?** `checkout` utilise par défaut le dépôt et la référence de l'exécution. `setup-node` peut utiliser le Node.js déjà présent dans le `PATH`. Ici, `with: node-version: 20` sélectionne explicitement Node.js 20.
- **Q2. Pourquoi le job `verify` ne retrouve-t-il pas `report.txt` sans l'artefact ?** Chaque job s'exécute sur un runner avec son propre espace de travail. `needs: build` fixe l'ordre d'exécution. Le téléchargement de `build-report` transfère le fichier généré par `build`.
