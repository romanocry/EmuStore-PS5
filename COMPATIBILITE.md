# Compatibilité d'EmuStore 0.3

## Ce qui est établi

- Compilation PS5 réussie, intégrité ELF/FSELF contrôlée.
- Le titre ne déclare pas de firmware minimal artificiel dans ses métadonnées
  (`requiredSystemSoftwareVersion` reste à zéro). Cela ne suffit pas à rendre
  les fonctions système ou le runtime compatibles avec toutes les versions.
- Le code ne contient aucun offset noyau dépendant d'un firmware.
- Affichage CPU / VideoOut : aucune dépendance Vulkan ou OpenGL pour le store.
- TLS et crypto liés avec libcurl/OpenSSL ; racines Mozilla incluses, validation
  des certificats et noms de domaine active.
- Le SDK et le runtime publics de la base restent inchangés.

## Matrice honnête

| Firmware | Cible du store | Essai réel EmuStore |
| --- | --- | --- |
| 4.xx | Oui, selon environnement homebrew disponible | Non réalisé |
| 5.xx | Oui, selon environnement homebrew disponible | Non réalisé |
| 6.xx | Oui | Non réalisé |
| 7.xx–10.xx | Oui | Non réalisé |
| 11.xx, dont 11.60 | Oui | Non réalisé |
| 12.xx | Oui | Non réalisé |
| 13.00–13.60 | Oui | Non réalisé |

La base de développement annonce des tests de son squelette sur 6.02 et 12.70.
Ce ne sont ni des tests d'EmuStore, ni une validation des autres versions.
Source : https://github.com/blackbearreloaded/ps5-native-app-boilerplate

ShadowMountPlus annonce la prise en charge des firmwares jailbreakés avec
kstuff-lite v1.07 ou supérieur ; cela concerne son propre fonctionnement, pas
une certification d'EmuStore. La chaîne de chargement et ses versions exactes
sont à vérifier pour chaque console.
Source : https://github.com/drakmor/ShadowMountPlus

## Validation nécessaire pour confirmer un firmware

Pour chaque version exacte, consigner modèle PS5, firmware réel (Paramètres),
version d'etaHEN/kstuff/ShadowMountPlus, puis :

1. Apparition de la tuile et ouverture du store.
2. Affichage stable, DualSense, navigation, fermeture normale.
3. Carré : vérifier le test de lecture/écriture et récupérer le rapport.
4. Installation d'un titre absent : HTTPS, vérification, extraction et apparition.
5. Refus de remplacer un titre existant ; conservation des sauvegardes.
6. Si concerné : installateur ELF sur port 9021 et Homebrew Launcher.

Le premier essai peut être réalisé sur la PS5 11.60 de l'utilisateur.
Un essai réussi en 11.60 ne prouve pas 4.xx ou 13.60.

## Émulateurs

La compatibilité du store porte sur son menu et son mécanisme d'installation.
Chaque release d'émulateur a son propre runtime, ses helpers, ses exigences
mémoire et éventuellement ses pilotes graphiques. Aucun binaire d'émulateur
n'est modifié ou rétroporté. Il peut être installable sans être exécutable sur
un ancien firmware. X360PS5 reste un diagnostic, sans prise en charge des jeux.
