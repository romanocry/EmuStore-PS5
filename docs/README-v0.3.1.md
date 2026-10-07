# EmuStore PS5 — prototype 0.3.1

**Projet porté par RomainJ.**

Catalogue natif PS5 de 15 applications, en français et à la manette.
Les versions sont fixes : aucune recherche ou installation de mise à jour.

## Compatibilité : cible 4.xx à 13.60, non certifiée

Cette version vise un environnement homebrew natif entre 4.xx et 13.60.
**Aucune de ces versions n'a été testée avec EmuStore sur une console ici.**
Les adaptations réseau et fichiers ne garantissent pas le démarrage sur tous
les firmwares : le chargeur natif, ses permissions, les imports système et
le runtime restent déterminants. Ne pas publier ce ZIP comme « compatible
4.xx–13.60 confirmé ».

La base upstream annonce ses propres essais sur 6.02 et 12.70 ; ces essais
ne portent pas sur EmuStore. Le firmware minimal des émulateurs n'est pas
abaissé par le store. Voir `COMPATIBILITE.md`.

Le dossier installable et les sources sont disponibles dans les [Releases](../../releases).

## Installer le store

1. Fermer EmuStore s'il est ouvert.
2. Extraire l'archive sur le PC.
3. Avec le FTP etaHEN, copier le dossier **PPSA97631** entier dans
   **/data/homebrew/**. Si une version precedente existe, remplacer les fichiers de ce seul
   dossier (ne pas toucher aux dossiers des autres applications).
4. Faire redétecter les applications par ShadowMountPlus puis ouvrir EmuStore.
   Si nécessaire, redémarrer la PS5 et réactiver l'environnement homebrew habituel.
5. Croix choisit Installer ; une seconde pression confirme.

Commandes : directions pour choisir ; L1/R1 pour avancer ou reculer de six
fiches ; Croix pour installer ; Rond pour annuler ou quitter hors installation. **Carre** ouvre le diagnostic.
Les pages affichent six fiches. Un transfert en cours bloque ces commandes.

La console doit avoir accès à Internet. ShadowMountPlus doit donner au store
un accès en écriture à `/data`. Aucun mécanisme d'élévation n'est intégré.

## Catalogue

Les tailles ci-dessous sont décimales, arrondies vers le haut. L'espace libre
requis couvre l'archive, les fichiers extraits et une marge de 256 Mio.

| Application | Version | Téléchargement | Espace libre requis | Lancement |
| --- | --- | ---: | ---: | --- |
| PSXS5 | v1.2.0 | 8 Mo | 309 Mo | Tuile PS5 / ShadowMountPlus |
| PS5SX2 | vk-285-130 | 18 Mo | 338 Mo | Tuile PS5 / ShadowMountPlus |
| ProsperoEden | v1.000.070 | 39 Mo | 417 Mo | Tuile PS5 / ShadowMountPlus |
| PS5CEMU-HAR | v3.0.0 | 51 Mo | 476 Mo | Tuile PS5 / ShadowMountPlus |
| XPSemu | alpha-1 | 17 Mo | 351 Mo | Tuile PS5 / ShadowMountPlus |
| Snes9x PS5 | v2.0 | 24 Mo | 427 Mo | Installateur ELF puis tuile PS5 |
| Genesis Plus GX | v1.2 | 29 Mo | 431 Mo | Installateur ELF puis tuile PS5 |
| RetroArch PS5 | v0.6.7-alpha.6 | 716 Mo | 2357 Mo | Tuile PS5 / ShadowMountPlus |
| Castation | v0.4.0 | 5 Mo | 290 Mo | Homebrew Launcher |
| pFBNeo | v7.2 | 55 Mo | 489 Mo | Homebrew Launcher |
| pGBA | v7.2 | 43 Mo | 419 Mo | Homebrew Launcher |
| pGEN | v7.2 | 43 Mo | 424 Mo | Homebrew Launcher |
| pNES | v7.2 | 44 Mo | 421 Mo | Homebrew Launcher |
| pSNES | v7.2 | 44 Mo | 421 Mo | Homebrew Launcher |
| X360PS5 | v0.1.1 | 6 Mo | 302 Mo | Tuile PS5 / ShadowMountPlus |

**X360PS5 est uniquement un prototype de diagnostic : il ne lance aucun jeu
Xbox 360 et son auteur n'annonce aucun test sur PS5.** Cette mention apparaît
sur sa fiche et pendant la confirmation. Ne pas le confondre avec XPSemu,
qui concerne la Xbox originale.

## Trois méthodes d'installation

- **Dossiers natifs** : le store télécharge, vérifie et extrait les fichiers
  dans `/data/homebrew/<identifiant>`. ShadowMountPlus gère les tuiles.
- **Castation et les cinq pEMU** : le store installe leur dossier complet dans
  `/data/homebrew/`, puis il faut les ouvrir dans le **Homebrew Launcher**.
  Ces paquets ne deviennent pas des tuiles natives via ShadowMountPlus seul.
  Aucun fichier PKG PS4, PC, Switch ou Vita n'est utilisé.
- **Snes9x et Genesis Plus GX** : le store télécharge et vérifie l'ELF officiel,
  puis l'envoie au chargeur ELF de la console, sur **127.0.0.1:9021**.
  Ce chargeur doit déjà être actif dans l'environnement etaHEN. L'installateur
  officiel installe l'application et reste disponible comme helper.
  Le store attend au maximum une minute que les trois fichiers essentiels
  apparaissent. « Fichiers présents » n'est pas une validation du fonctionnement
  de l'émulateur ; vérifier également la notification de l'installateur.
  Si le résultat est « envoyé, installation non confirmée », inspecter la console
  avant de réessayer. Aucun payload n'est envoyé à une autre machine.

Le store refuse une destination déjà présente, y compris pour les installateurs
ELF. Il ne sert pas à mettre à jour des émulateurs. Les fichiers ELF officiels
ne sont pas modifiés ; leurs propres opérations relèvent de leur auteur.

## Prérequis particuliers

- **PS5SX2** : Helper téléchargé dans `/data/emustore/PS5SXHelper.elf`.
  Charger le Helper avec kstuff avant de jouer. Ajouter `PPSA99203` à
  `/data/whitelist.txt` si nécessaire selon la procédure de cette release.
  BIOS dans `/data/PCSX2/bios`, jeux dans `/data/PCSX2/games`.
- **XPSemu** : Helper téléchargé dans `/data/emustore/xpsemu_tools.elf`.
  Charger ce Helper avec kstuff, et ajouter `PPSA97358` à `/data/whitelist.txt`.
  L'auteur précise de n'utiliser qu'un seul des helpers XPSemu / PS5SX2,
  puisqu'ils remplissent le même rôle. Ne pas lancer les deux simultanément.
  Fichiers Xbox (BIOS, MCPX, disque) dans `/data/xemu`, jeux dans `/data/xemu/games`.
- **PS5CEMU-HAR** : ajouter `PPSA99360` à la liste « app jailbreak » d'etaHEN,
  selon la documentation de l'auteur. Wii U et Nintendo 3DS dans la même application.
- **Snes9x** : ROMs dans `/data/snes9x/roms` ; L3 + R3 ouvre le menu.
- **Genesis Plus GX** : ROMs dans les sous-dossiers de `/data/genplus/roms` ;
  BIOS Sega CD éventuel dans `/data/genplus/bios` ; L3 + R3 ouvre le menu.
- **RetroArch** : package complet, cœurs et ressources compris. Les BIOS et
  jeux sont à apporter séparément. Le service WebUI de l'émulateur est sur le
  port 6769 lorsqu'il tourne. Cette release est une alpha.
- **Castation** : jeux dans `/data/homebrew/Castation/games` ; BIOS facultatif
  dans `/data/homebrew/Castation/bios`, sinon sélectionner le BIOS HLE.
- **pEMU** : choisir les dossiers de ROMs selon la configuration de chaque
  application. Les cinq paquets PS5 sont installés séparément.

Le store ne modifie ni l'autoload etaHEN, ni les listes d'autorisations.
Les jeux, BIOS, clés et firmwares ne sont ni fournis ni téléchargés.
Les émulateurs peuvent posséder leur propre fonction de mise à jour ; le store
n'active ni ne désactive ces fonctions internes.

## Limites et tests

**Aucun essai réel sur PS5 11.60 n'a été réalisé ici.** La compilation et les tests
sur ordinateur ne prouvent pas la compatibilité du store ni de chaque émulateur
avec ton firmware. Voir `VALIDATION.md` pour les contrôles effectués.

- Vérification HTTPS, taille exacte et SHA-256 épinglé de chaque téléchargement.
- Extraction en flux, avec limites adaptées à chaque archive et contrôle des
  chemins. Les liens symboliques et chemins sortant du dossier sont refusés.
- Vérification des fichiers attendus avant publication du dossier.
- Aucune installation existante n'est écrasée. `/data/PCSX2` existant bloque
  aussi l'installation de PS5SX2 ; ne pas le supprimer pour forcer l'opération.
- Les doublons sur USB ne sont pas détectés : éviter d'installer le même titre
  à plusieurs emplacements.
- Ne pas fermer le store pendant une installation. Une interruption électrique
  peut laisser `/data/emustore/stage-*` ou une installation partielle. Examiner
  ces dossiers lorsque le store est fermé ; ne pas supprimer les données de jeux.
- Un fichier retiré ou modifié chez son auteur provoque un échec, jamais
  l'acceptation silencieuse d'un remplacement.
- L'identifiant du store PPSA97631 est choisi pour ce prototype, non réservé.

## Sources et compilation

Les sources complètes sont dans [`EmuStore-PS5-v0.3.1-sources.zip`](EmuStore-PS5-v0.3.1-sources.zip), à extraire avant compilation, sous GPL-3.0-or-later ; les dépendances
conservent leurs licences dans `assets/licenses/`.
Base : https://github.com/blackbearreloaded/ps5-native-app-boilerplate
Commit : 6cec460f2c23f65f4c16692b9c9a9722a410c23a.

Sous Ubuntu / WSL :

```sh
sudo apt install clang-18 llvm-18 lld-18 ninja-build make git python3 wget unzip pkg-config
python3 tools/generate-catalog.py
make USE_CCACHE=0
```

`catalog.json` est la source du catalogue ; `tools/generate-catalog.py` produit
`src/catalog.hpp`. Il n'y a aucune interrogation GitHub au démarrage du store.
Le téléchargement utilise les URLs fixes et empreintes du catalogue compilé.
La sortie est `dist/PPSA97631.zip`.

## Diagnostic de la version 0.3

- **Carré** : version SDK annoncée par le système, test d'accès aux fichiers et
  emplacement du rapport. La valeur SDK est indicative et peut être falsifiée
  par l'environnement homebrew ; elle ne sert pas de preuve de compatibilité.
- Rapport : `/data/emustore/compatibility.log` ; si `/data` est inaccessible,
  tentative d'écriture dans `/download0/emustore-compatibility.log`.
- La vérification HTTPS utilise en priorité les certificats inclus dans
  `/app0/assets/cacert.pem`, puis les emplacements système si le fichier manque.
  L'heure de la console doit être correcte. Aucun certificat invalide n'est accepté.
- Sockets non bloquantes : option native, puis ioctl FIONBIO si nécessaire.
  Si les deux méthodes échouent, le téléchargement refuse de démarrer.
- Espace libre : statvfs, puis fstatvfs sur PS5. Si les deux échouent, l'installation
  est refusée avec un message distinct d'un manque de place.
- L'environnement doit déjà fournir les services et permissions nécessaires.
  Le store ne modifie pas le firmware et n'ajoute pas de jailbreak.

## Crédits

- Projet et sélection du catalogue : **RomainJ.**
- Développement assisté par OpenAI Codex.
- Base native et renderer : BlackBearReloaded, sous GPL-3.0-or-later.
- Émulateurs : leurs auteurs respectifs, cités dans `catalog.json`.

Les mentions de licence et les crédits d’origine sont conservés.
