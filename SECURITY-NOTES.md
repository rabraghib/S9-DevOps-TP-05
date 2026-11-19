# Partie 2 – Sécurité des actions tierces

## Observation de `actions/setup-node`

- Badge de créateur vérifié sur la [fiche GitHub Marketplace](https://github.com/marketplace/actions/setup-node-js-environment).
- **5 027 étoiles** relevées sur le dépôt.
- Code source TypeScript dans [`src/`](https://github.com/actions/setup-node/tree/v4/src).

## Questions

- **Q3. Pourquoi épingler `@v4` plutôt que `@main` ?** La branche `main` avance à chaque mise à jour et peut introduire des changements imprévus. Le tag `v4` cible une version majeure, mais il peut lui aussi être déplacé. Un SHA complet fixe le commit exact.
- **Q4. Le badge « créateur vérifié » garantit-il qu'une action est sûre ?** Non. GitHub vérifie le créateur. Cette vérification ne constitue pas un audit de l'action ni de ses dépendances.
- **Q5. Quelles sont deux vérifications à faire avant d'utiliser une action d'un fournisseur inconnu en production ?**
  1. Relire le code et les dépendances du commit retenu, en contrôlant notamment les accès aux secrets et les communications réseau.
  2. Vérifier que le SHA à épingler correspond à une version publiée dans le dépôt officiel du fournisseur.

[Recommandations de sécurité de GitHub](https://docs.github.com/en/actions/reference/security/secure-use#using-third-party-actions)
