# TP 6 – Réponses

- **Q1.** Le runner lit `GITHUB_ENV` à la fin de la step et ajoute les variables à l’environnement des steps suivantes. Dans la step d’écriture, `APP_NAME` est encore vide.
- **Q2.** Dans `verify-env`, le log affiche `APP_NAME=<>`. Les variables écrites dans `GITHUB_ENV` sont disponibles uniquement dans les steps suivantes du même job.
- **Q3.** Chaque écriture avec `>` tronque le fichier. Si les deux écritures utilisent `>`, seul le dernier output subsiste. Avec `>>`, les deux valeurs sont conservées.
- **Q4.** `GITHUB_ENV` reste local au job. `GITHUB_OUTPUT` crée un output de step que `build.outputs` expose à `deploy` via `needs`. Les deux jobs ont affiché `1.0.0-2026-11-19`.
- **Q5.** Sans `needs: build`, `deploy` peut démarrer sans attendre `build`. Le contexte `needs` ne contient plus `build`, donc la version est vide.
