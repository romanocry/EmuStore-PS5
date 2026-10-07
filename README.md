# EmuStore PS5 — prototype 0.4.0

**Projet porté par RomainJ.**

Store natif PS5 en français, utilisable à la manette. Cette version conserve l'interface avec grille des émulateurs, statuts installés/absents/mise à jour et pictogrammes PS5 × ○ △ □.

**Prototype : compatibilité réelle non validée sur console.**

## Télécharger

- [Release v0.4.0](https://github.com/romanocry/EmuStore-PS5/releases/tag/v0.4.0)
- [Archive installable EmuStore-PS5-v0.4.0.zip](https://github.com/romanocry/EmuStore-PS5/releases/download/v0.4.0/EmuStore-PS5-v0.4.0.zip)
- [Empreinte SHA-256](SHA256SUMS.txt)
- [Notes de version et vérifications](RELEASE-v0.4.0.md)

Le ZIP contient le dossier **PPSA97631**, le binaire, le module système, les ressources et les licences.

## Installer ou remplacer le store

1. Fermer EmuStore sur la console.
2. Extraire le ZIP sur le PC.
3. Avec le FTP de l'environnement homebrew, copier le dossier **PPSA97631** entier dans **/data/homebrew/**. Pour remplacer une ancienne version, remplacer uniquement les fichiers de ce dossier.
4. Faire redétecter les applications par ShadowMountPlus, puis lancer EmuStore.
5. Utiliser les commandes affichées à l'écran.

La console doit disposer d'un environnement homebrew adapté, d'un accès Internet et des permissions nécessaires. Les prérequis propres à chaque émulateur restent applicables. Aucun jeu, BIOS ou clé fourni.

## Sources et documentation antérieure

**Les sources exactes de v0.4.0 n'ont pas été récupérées et ne sont pas incluses dans cette publication.**

Les [sources v0.3.1](EmuStore-PS5-v0.3.1-sources.zip) et la [documentation v0.3.1](docs/README-v0.3.1.md) sont conservées pour référence. Elles décrivent la version précédente. Les archives « Source code » automatiques de GitHub reflètent les fichiers du dépôt ; elles ne sont pas les sources du binaire v0.4.0.

## Crédits et licences

- Projet et catalogue : **RomainJ.**
- Développement assisté par OpenAI Codex.
- Base native et renderer : BlackBearReloaded, **GPL-3.0-or-later**.
- Émulateurs et dépendances : leurs auteurs et licences respectifs.

Voir [LICENSE](LICENSE), [CREDITS.md](CREDITS.md) et [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
