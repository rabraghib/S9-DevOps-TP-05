# TP 7 – Actions tierces et actions personnalisées

## Partie 1 – Utiliser des actions tierces (`uses` et `with`)

- **Q1. Pourquoi `actions/checkout` n'a-t-il pas besoin de `with` alors que `setup-node` en a besoin ?** `checkout` utilise par défaut le dépôt et la référence de l'exécution. `setup-node` peut utiliser le Node.js déjà présent dans le `PATH`. Ici, `with: node-version: 20` sélectionne explicitement Node.js 20.
- **Q2. Pourquoi le job `verify` ne retrouve-t-il pas `report.txt` sans l'artefact ?** Chaque job s'exécute sur un runner avec son propre espace de travail. `needs: build` fixe l'ordre d'exécution. Le téléchargement de `build-report` transfère le fichier généré par `build`.

## Partie 3 – Créer une action composite locale

- **Q6. Pourquoi `actions/checkout` doit-il s'exécuter avant l'appel d'une action locale ?** Le chemin `./.github/actions/build-info` est résolu dans l'espace de travail du runner. `checkout` y place le dépôt et le fichier `action.yml` avant l'appel.
- **Q7. Pourquoi `shell: bash` est-il obligatoire pour les steps `run` d'une action composite ?** La syntaxe d'une action composite exige un interpréteur explicite pour chaque step `run`. Ici, Bash exécute les commandes et la redirection vers `GITHUB_OUTPUT`.

## Partie 4 – action Docker

| Step | Durée mesurée | Résultat |
| --- | ---: | --- |
| `Run build info action` | 1 s | `my-app-1.0.0` |
| `Run Docker hello action` | 8 s | `Hello, GitHub Actions` |

Sur cette exécution, l'étape Docker inclut la construction de l'image Alpine et le lancement du conteneur. L'action composite exécute directement ses commandes Bash sur le runner.

[Exécution réussie avec `build-report`](https://github.com/rabraghib/S9-DevOps-TP-05/actions/runs/44612514464) · [Capture d'écran](captures/01-build-report.jpg)
