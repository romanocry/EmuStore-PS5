# Validation EmuStore 0.3

Effectuée sur Linux, pas sur console :

- 15 entrées générées depuis un catalogue fixe ; archives prises chez leurs auteurs.
- Vérification des SHA-256 annoncés pour les nouveaux téléchargements.
- Extraction réelle des 13 ZIP avec le même code que le store, dont RetroArch
  (plus de 13 000 entrées et 1,3 Go extraits), Castation et les cinq pEMU.
- Vérification des fichiers attendus selon le format natif ou Homebrew Launcher.
- Refus d'une installation déjà présente pour chacune des 15 entrées.
- Transfert exact des deux ELF officiels Snes9x et Genesis Plus GX vers un
  récepteur simulé sur la boucle locale : taille et SHA-256 reçus conformes.
- Test du chargeur absent et du refus d'envoyer un ELF si le titre existe déjà.
- Tests C++ avec AddressSanitizer et UndefinedBehaviorSanitizer. LeakSanitizer
  désactivé car l'environnement ne permet pas son inspection de /proc.
- Contrôles de chemins conservés depuis la v0.1 (traversée, liens symboliques).
- Compilation PS5 avec Clang/LLVM 18.1.3, SDK public v0.42 ; conversion
  ELF/FSELF et vérification statique d'intégrité réussies.

Les ELF n'ont pas été exécutés sur ordinateur : leur réception a été simulée.
Aucun test réel de l'installation, des permissions, de l'interface, du réseau,
des helpers ou du lancement des émulateurs sur PS5 11.60 n'a été réalisé.

Contrôles ajoutés en 0.3 :
- Test de lecture/écriture réel d'un fichier temporaire dans un dossier de test,
  suppression après contrôle, refus des liens et des chemins absents.
- Détection d'espace disponible et distinction d'une erreur de mesure.
- Régression des transferts ELF avec le module de diagnostic lié.
- Compilation des chemins PS5 ioctl/fstatvfs/sysctl, non exécutés sur console.
- Les certificats intégrés sont chargés depuis le bundle Mozilla fourni par curl.
Aucune compatibilité matérielle 4.xx à 13.60 n'a été confirmée par ces tests.

Contrôles 0.3.1 : ajout du crédit RomainJ. dans l’interface et la documentation ;
compilation PS5 et intégrité FSELF validées. Présence du texte dans le binaire
vérifiée. Aucun changement à la logique d’installation, aucun nouvel essai PS5.
