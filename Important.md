Projet OmarchySwitch — Création d’une distribution Linux pour Nintendo Switch

Tu es un agent de développement autonome. Ta mission est de créer OmarchySwitch, une distribution Linux destinée à la Nintendo Switch, basée sur Ubuntu Switchroot et reprenant l’expérience, l’apparence et les fonctionnalités d’Omarchy.

Ton objectif est de préparer intégralement le projet dans le dépôt GitHub déjà connecté à ton environnement.

IMPORTANT : TU NE DOIS EFFECTUER AUCUN BUILD, AUCUNE COMPILATION ET AUCUNE CRÉATION D’IMAGE SYSTÈME.

Tu dois uniquement :

* Analyser les projets existants.
* Récupérer les sources et fichiers nécessaires.
* Adapter les configurations.
* Créer les scripts et fichiers du projet.
* Organiser correctement le dépôt GitHub.
* Préparer tous les fichiers nécessaires à une future archive ZIP.
* Vérifier la cohérence des fichiers et des chemins.
* Publier les modifications sur GitHub.

Le résultat attendu est un dépôt GitHub organisé contenant le projet de développement et un dossier séparé contenant l’intégralité des fichiers destinés à la carte SD.

⸻

1. Identité du projet

Respecte impérativement cette nomenclature partout :

* Nom officiel : OmarchySwitch
* Nom abrégé : OmarchyS
* Nom des dossiers système : omarchyswitch
* Nom du dépôt GitHub : OmarchySwitch
* Nom de la future archive : OmarchySwitch-v0.1.0-alpha.zip
* Préfixe des versions : OmarchySwitch

N’utilise jamais :

* Omarchy Switch
* Omarchy-Switch
* Un autre nom de distribution.

Le dossier système doit toujours s’appeler omarchyswitch.

⸻

2. Analyse des projets sources

Avant de commencer, analyse les deux projets suivants.

Omarchy

Dépôt officiel :

https://github.com/omarchy/omarchy

Actions :

1. Récupérer le code source.
2. Analyser son architecture.
3. Examiner les scripts d’installation.
4. Identifier les dépendances.
5. Identifier les configurations graphiques.
6. Identifier les composants compatibles ARM64.
7. Identifier les composants nécessitant x86_64.
8. Identifier les éléments propres à Arch Linux.
9. Identifier les thèmes, raccourcis, polices et applications réutilisables.
10. Conserver les licences et mentions de copyright.

Ne copie pas aveuglément les scripts d’installation originaux.

Ubuntu Switchroot

Sources officielles :

* https://switchroot.org/
* https://github.com/switchroot

Actions :

1. Identifier la dernière version stable réellement disponible.
2. Vérifier la version d’Ubuntu.
3. Identifier les fichiers nécessaires.
4. Examiner l’organisation des fichiers.
5. Identifier les composants spécifiques à la Nintendo Switch.
6. Identifier le noyau et les modules Tegra.
7. Identifier les pilotes NVIDIA.
8. Identifier les configurations de démarrage.
9. Examiner les fichiers Hekate.
10. Conserver les licences.

Ne suppose pas que Bionic 18.04 est la dernière version disponible.

Ne lance aucune compilation et ne construis aucune image.

⸻

3. Organisation obligatoire du dépôt GitHub

C’est une partie particulièrement importante du projet.

Le dépôt GitHub doit contenir DEUX DOSSIERS PRINCIPAUX DISTINCTS.

Le premier contient les fichiers de développement.

Le deuxième contient les fichiers destinés à être copiés sur la carte SD.

Structure obligatoire :

OmarchySwitch/
│
├── OmarchySwitch/
│   │
│   ├── build/
│   ├── config/
│   ├── scripts/
│   ├── switchroot/
│   ├── omarchy/
│   ├── boot/
│   ├── assets/
│   │   └── splash/
│   ├── docs/
│   ├── .github/
│   │   └── workflows/
│   │
│   ├── README.md
│   ├── INSTALLATION.md
│   ├── CHANGELOG.md
│   └── LICENSES/
│
├── SD/
│   │
│   ├── bootloader/
│   │   └── ini/
│   │       └── omarchyswitch.ini
│   │
│   ├── omarchyswitch/
│   │   ├── boot/
│   │   ├── etc/
│   │   ├── home/
│   │   ├── usr/
│   │   ├── var/
│   │   ├── lib/
│   │   ├── splash/
│   │   │   └── omarchyswitch.png
│   │   └── ...
│   │
│   └── README.txt
│
├── README.md
├── LICENSE
└── .gitignore

Cette structure est une organisation cible.

Tu dois l’adapter à la structure réellement utilisée par Switchroot.

Ne crée pas de faux fichiers système simplement pour remplir les dossiers.

Ne crée pas de répertoires vides inutiles.

Si certains composants doivent rester à leur emplacement officiel pour fonctionner, respecte leur organisation réelle.

Rôle du dossier OmarchySwitch/

Ce dossier est exclusivement destiné au développement du projet.

Il doit contenir :

* Les sources nécessaires.
* Les configurations.
* Les scripts d’adaptation.
* Les scripts d’installation.
* Les références aux composants Switchroot.
* Les ressources graphiques.
* Les documents techniques.
* Les workflows GitHub Actions.
* Les informations de licences.

Il doit permettre de comprendre, modifier et faire évoluer OmarchySwitch.

Rôle du dossier SD/

Ce dossier représente directement la racine de la carte SD.

Il doit contenir les fichiers nécessaires à l’installation de la distribution.

Exemple :

SD/
├── bootloader/
│   └── ini/
│       └── omarchyswitch.ini
│
├── omarchyswitch/
│   ├── boot/
│   ├── etc/
│   ├── home/
│   ├── usr/
│   ├── var/
│   └── lib/
│
└── README.txt

L’utilisateur doit pouvoir prendre le contenu de ce dossier et le copier à la racine de sa carte SD.

Il ne doit pas avoir à déplacer manuellement les fichiers dans différents dossiers.

Ne crée pas un dossier SD contenant un deuxième dossier SD.

Ne place pas les fichiers d’installation dans OmarchySwitch/.

Les deux dossiers doivent rester indépendants et clairement identifiables.

⸻

4. Création du système OmarchySwitch

Utiliser Ubuntu Switchroot comme base technique.

Adapter les composants Omarchy à Ubuntu ARM64.

Étudier notamment :

* Hyprland, si compatible.
* Waybar ou une alternative.
* Un terminal moderne.
* Un gestionnaire de fichiers.
* Un lanceur d’applications.
* Les raccourcis clavier.
* Les thèmes Omarchy.
* Les polices.
* Les couleurs.
* Les configurations graphiques.

Si Hyprland est incompatible avec les pilotes graphiques disponibles, choisir une alternative adaptée.

Ne force jamais l’installation d’un composant incompatible.

Adapter les commandes Arch Linux vers Ubuntu lorsque cela est pertinent.

Vérifier les dépendances ARM64.

Ne pas conserver de dépendances exclusivement x86_64 inutilisables sur la Switch.

⸻

5. Compatibilité Nintendo Switch

La priorité absolue est de préserver la compatibilité Switchroot.

Préserver les composants nécessaires :

* Noyau Linux adapté à la Switch.
* Modules Tegra.
* Pilotes NVIDIA.
* Accélération graphique.
* Wi-Fi.
* Bluetooth.
* Audio.
* Écran tactile.
* Joy-Con.
* Gestion de l’énergie.
* Mode portable.
* Mode docké.
* Sortie HDMI.

Ne remplace jamais les composants matériels Switchroot par des composants PC génériques.

Ne déclare pas une fonctionnalité opérationnelle sans preuve.

⸻

6. Applications spécifiques à la Switch

Étudier les outils Switchroot disponibles :

* Gestion des Joy-Con.
* Gestion des contrôleurs.
* Configuration Tegra.
* Gestion de l’énergie.
* Gestion du mode docké.
* Configuration de l’écran.
* Configuration audio.

Intégrer uniquement les composants dont les sources, licences et compatibilités sont suffisamment établies.

⸻

7. Configuration Hekate

Créer une entrée Hekate nommée :

OmarchySwitch

Fichier :

SD/bootloader/ini/omarchyswitch.ini

La configuration doit :

* Être compatible avec Hekate.
* Utiliser les bons fichiers de démarrage Switchroot.
* Utiliser les bons chemins.
* Démarrer OmarchySwitch.
* Ne pas écraser les configurations existantes.
* Préserver Atmosphère et les autres entrées.

Étudier les configurations officielles avant de créer ce fichier.

Ne fabrique pas de paramètres Hekate au hasard.

⸻

8. Image de démarrage

Préparer une image de démarrage personnalisable.

Emplacement souhaité :

SD/omarchyswitch/splash/omarchyswitch.png

Elle doit :

* Afficher OmarchySwitch.
* Avoir un style inspiré d’Omarchy.
* Être adaptée à l’écran de la Switch.
* Être facilement remplaçable.

Vérifier le mécanisme de splash screen réellement utilisé par Switchroot.

Distinguer le splash screen Linux de l’image éventuellement utilisée par Hekate.

⸻

9. Préparation de l’installation sur carte SD

Le dossier SD/ doit être organisé pour une installation simple.

L’utilisateur doit pouvoir :

1. Télécharger ultérieurement l’archive ZIP.
2. Extraire son contenu.
3. Ouvrir le dossier SD de l’archive.
4. Copier son contenu à la racine de sa carte SD.
5. Conserver ses fichiers Hekate et Atmosphère.
6. Démarrer Hekate.
7. Sélectionner OmarchySwitch.

Ne formate jamais la carte SD.

Ne supprime aucun fichier existant.

Ne remplace pas les fichiers de démarrage existants sans nécessité.

Créer les guides en français et en anglais.

⸻

10. Préparation de la future archive ZIP

IMPORTANT : TU NE DOIS PAS CRÉER L’ARCHIVE ZIP MAINTENANT.

Tu dois uniquement préparer son contenu dans le dépôt GitHub.

Le contenu de la future archive devra correspondre exactement au contenu du dossier SD/.

Nom prévu :

OmarchySwitch-v0.1.0-alpha.zip

La future archive devra avoir cette structure à sa racine :

OmarchySwitch-v0.1.0-alpha.zip
│
├── bootloader/
│   └── ini/
│       └── omarchyswitch.ini
│
├── omarchyswitch/
│   ├── boot/
│   ├── etc/
│   ├── home/
│   ├── usr/
│   ├── var/
│   ├── lib/
│   └── splash/
│
└── README.txt

Il ne doit pas y avoir de dossier SD supplémentaire à l’intérieur de cette archive.

Le dossier SD/ du dépôt est simplement le répertoire source qui servira ultérieurement à fabriquer le ZIP.

Ne crée pas de ZIP vide ou fictif.

⸻

11. GitHub Actions

Préparer éventuellement des workflows GitHub Actions pour les opérations futures.

Ils pourront notamment :

* Vérifier les fichiers.
* Contrôler les chemins.
* Vérifier la structure du dossier SD.
* Contrôler les configurations.
* Vérifier les licences.
* Détecter les fichiers manquants.
* Préparer une future archive ZIP lorsqu’une demande explicite de build ou de packaging sera faite.

Cependant, pour cette mission :

Ne lance aucun workflow de build.

Ne compile aucun système.

Ne génère aucune image système.

Ne fabrique aucune archive ZIP.

Les workflows doivent uniquement être préparés et enregistrés dans le dépôt.

⸻

12. Vérifications obligatoires

Avant de terminer, vérifier :

* La présence des deux dossiers principaux.
* La séparation entre développement et installation SD.
* La cohérence des chemins.
* Le nom exact omarchyswitch.
* La configuration Hekate.
* Les références aux fichiers Switchroot.
* Les composants ARM64.
* Les licences.
* Les fichiers nécessaires au démarrage.
* L’absence de fichiers personnels.
* L’absence de secrets.
* L’absence de configurations écrasant Atmosphère.

Créer un rapport de vérification.

Indiquer clairement :

* Les vérifications effectuées.
* Les fichiers créés.
* Les fichiers adaptés.
* Les fichiers manquants.
* Les composants incompatibles.
* Les fonctionnalités non vérifiées.
* Les tests nécessitant une vraie Nintendo Switch.

Ne prétends jamais qu’un système a été compilé ou démarré.

⸻

13. GitHub

Utiliser le dépôt GitHub déjà connecté.

Si le dépôt est vide, l’initialiser.

Le nom du dépôt doit être :

OmarchySwitch

Effectuer les modifications directement dans le dépôt.

Créer des commits cohérents.

Ne supprime pas l’historique existant.

Conserver les références upstream vers :

* Omarchy.
* Switchroot.

Ne prétends pas créer un fork direct de deux dépôts différents.

Ne publie pas de release pour le moment.

La publication de la première release sera une étape ultérieure.

⸻

14. Interdictions absolues

Pendant cette mission, tu ne dois jamais :

* Compiler Ubuntu.
* Compiler un noyau.
* Compiler Hyprland.
* Compiler une ROM ou une image système.
* Créer une image disque.
* Créer un fichier ZIP.
* Lancer une procédure de build complète.
* Prétendre avoir testé le démarrage sur une Switch si ce n’est pas le cas.
* Remplacer les fichiers système Switchroot sans vérification.
* Supprimer les configurations Hekate ou Atmosphère existantes.

Ton travail consiste exclusivement à préparer les fichiers et les dossiers du projet dans GitHub.

⸻

15. Compte rendu final

Lorsque tu as terminé, fournis :

1. L’URL du dépôt GitHub.
2. La liste des fichiers créés.
3. La liste des fichiers adaptés.
4. La version Ubuntu Switchroot sélectionnée.
5. Les composants Omarchy intégrés.
6. Les composants Switchroot conservés.
7. La structure finale du dossier OmarchySwitch/.
8. La structure finale du dossier SD/.
9. Les éventuels fichiers manquants.
10. Les problèmes de compatibilité identifiés.
11. Les vérifications réellement effectuées.
12. Les éléments qui nécessiteront une future compilation.
13. Les éléments qui nécessiteront des tests sur une vraie Nintendo Switch.

RAPPEL FINAL : AUCUN BUILD, AUCUNE COMPILATION, AUCUN ZIP ET AUCUNE RELEASE.

Le résultat attendu est un dépôt GitHub correctement préparé, avec :

* OmarchySwitch/ : le projet complet de développement.
* SD/ : tous les fichiers organisés pour l’installation future sur la carte SD.

L’objectif est de pouvoir poursuivre ultérieurement le développement, puis fabriquer l’archive ZIP à partir du dossier SD/, sans devoir réorganiser manuellement le projet.
