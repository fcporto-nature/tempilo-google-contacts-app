# TEMPILO Google Contacts Sync

> **Écrit par une IA.** Ce projet a été développé par Claude Code
> (Anthropic), un agent IA, pour le compte de TEMPILO. Les commits
> portent la mention `Co-Authored-By` correspondante.

Page native Twenty CRM qui synchronise les contacts dans les deux sens avec
Google Contacts, sans jamais créer de doublon ni écraser une donnée
existante.

## Features

- Synchronisation bidirectionnelle Google ↔ Twenty, avec règle stricte de
  non-écrasement (complète les champs vides seulement).
- Twenty → Google limité aux points de contact d'opportunités (pas toute
  la base).
- Comparaison à plusieurs niveaux : email, téléphone, champs contact de
  l'opportunité, puis nom complet en dernier recours.
- Deux modes : synchro complète, ou vérification rapide des 50 derniers
  contacts modifiés de chaque côté.
- Synchro automatique 2x/jour à un horaire aléatoire hors des heures
  ouvrées (7h-19h, Europe/Paris).
- Réservé aux administrateurs Twenty, avec confirmation avant chaque
  action manuelle et seuil de sécurité sur les synchros automatiques.
- Historique des 50 dernières synchros avec détail des actions.

Le backend (service Node.js séparé, appelé par cette page) vit dans
`/mnt/data/tempilo/apps/google-contacts-sync/app/` — voir son propre
README pour la configuration (clés API, variables d'environnement).

## Getting started

Setup instructions live in [SETUP.md](SETUP.md).

## Publishing

The `Publish` workflow (`.github/workflows/publish.yml`) publishes the app to npm with provenance using [npm trusted publishing](https://docs.npmjs.com/trusted-publishers). To publish:

1. On npmjs.com register this repository as a trusted publisher of your package, pointing at the `publish.yml` workflow.
2. Bump the version in `package.json`, then push a version tag (e.g. `git tag v1.0.0 && git push --tags`) or run the workflow manually from the Actions tab.

Publishing with provenance is also how you prove ownership when claiming your app in a Twenty marketplace.

## Changelog

Notable changes are documented in [CHANGELOG.md](CHANGELOG.md).

## Learn more

- [Twenty Apps documentation](https://docs.twenty.com/developers/extend/apps/getting-started/quick-start)
- [twenty-sdk CLI reference](https://www.npmjs.com/package/twenty-sdk)
- [Discord](https://discord.gg/cx5n4Jzs57)
