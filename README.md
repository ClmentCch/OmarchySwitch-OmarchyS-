Projet OmarchySwitch — Création d’une distribution Linux pour Nintendo Switch

Tu es un agent de développement autonome. Ta mission est de créer OmarchySwitch, une distribution Linux destinée à la Nintendo Switch, basée sur Ubuntu Switchroot et reprenant l’expérience, l’apparence et les fonctionnalités d’Omarchy.

Tu dois analyser les projets existants, récupérer les fichiers nécessaires, adapter le système, construire une distribution installable depuis une carte SD avec Hekate, puis publier une première version sur GitHub.

Ne te contente pas de créer une maquette ou un simple thème graphique : l’objectif est de produire un véritable système Linux fonctionnel.

⸻

1. Identité du projet

Respecte impérativement cette nomenclature dans tous les fichiers, scripts, configurations, interfaces et publications :

* Nom officiel : OmarchySwitch
* Nom abrégé : OmarchyS
* Nom des dossiers système et de distribution : omarchyswitch
* Nom du dépôt GitHub : OmarchySwitch
* Nom de l’archive : OmarchySwitch-v0.1.0-alpha.zip
* Préfixe des versions : OmarchySwitch

Ne crée pas d’autres variantes du nom. N’utilise jamais « Omarchy Switch », « Omarchy-Switch » ou « OmarchyS » comme nom de dossier.

⸻

2. Analyse des projets sources

Avant de commencer le développement, analyse soigneusement les deux projets suivants.

Omarchy

Dépôt officiel :
https://github.com/omarchy/omarchy

Actions :

1. Récupérer le code source du projet.
2. Analyser son architecture, ses scripts d’installation, ses dépendances et sa configuration.
3. Identifier les éléments qui peuvent fonctionner sur ARM64.
4. Identifier les éléments qui nécessitent x86_64 ou des fonctionnalités propres à Arch Linux.
5. Identifier les composants graphiques, les thèmes, les raccourcis, les configurations et les outils qui peuvent être adaptés.
6. Conserver les licences et mentions de copyright.
7. Ne pas prétendre que le système est compatible avec la Nintendo Switch avant d’avoir vérifié les composants concernés.

Ubuntu Switchroot

Trouver la dernière version stable officiellement disponible d’Ubuntu pour Nintendo Switch sur les sources officielles Switchroot.

Sources à examiner :

* https://switchroot.org/
* https://github.com/switchroot
* Les dépôts et pages de releases officiels associés.

Actions :

1. Identifier la dernière version réellement disponible.
2. Vérifier sa version d’Ubuntu et sa compatibilité avec la Nintendo Switch.
3. Télécharger les fichiers nécessaires.
4. Examiner précisément l’organisation de l’archive et du système.
5. Identifier le noyau, les modules, les pilotes NVIDIA/Tegra, les configurations de démarrage et les outils spécifiques à la Switch.
6. Identifier les fichiers indispensables au fonctionnement de Hekate et du système.
7. Vérifier les licences avant toute redistribution.

Ne suppose pas que Bionic 18.04 est la version la plus récente. Vérifie les versions disponibles avant de choisir la base.

⸻

3. Création du système OmarchySwitch

Utiliser Ubuntu Switchroot comme base technique.

Le système final doit être adapté à la Nintendo Switch et intégrer autant que possible l’expérience Omarchy.

Environnement graphique

Étudier l’intégration des composants suivants :

* Hyprland, si sa compatibilité avec les pilotes graphiques Switchroot est confirmée.
* Waybar ou une alternative adaptée.
* Un terminal moderne.
* Un gestionnaire de fichiers.
* Un lanceur d’applications.
* Des raccourcis clavier personnalisés.
* Les thèmes, couleurs, polices et configurations Omarchy.
* Une interface adaptée à l’écran de la Nintendo Switch.

Ne force pas l’installation d’un composant incompatible. Si Hyprland ne fonctionne pas correctement avec les pilotes disponibles, rechercher une solution graphique compatible et documenter ce choix.

Adaptation Ubuntu

Omarchy étant conçu autour d’Arch Linux, adapter correctement les scripts et dépendances à Ubuntu.

* Remplacer les commandes propres à pacman par leurs équivalents Ubuntu lorsque cela est pertinent.
* Adapter les scripts d’installation.
* Vérifier les noms et disponibilités des paquets ARM64.
* Supprimer les dépendances exclusivement x86_64 lorsqu’elles ne sont pas utilisables.
* Éviter de lancer aveuglément les scripts d’installation originaux d’Omarchy.

Ne copie pas simplement les fichiers de configuration sans vérifier leur compatibilité.

⸻

4. Compatibilité Nintendo Switch

La priorité absolue est de conserver le fonctionnement matériel de Switchroot.

Préserver et vérifier :

* Le noyau Linux adapté à la Nintendo Switch.
* Les modules Tegra.
* Les pilotes graphiques NVIDIA.
* L’accélération matérielle lorsqu’elle est disponible.
* Le Wi-Fi.
* Le Bluetooth.
* L’audio.
* L’écran tactile.
* Les Joy-Con.
* La gestion de l’énergie.
* Le mode portable.
* Le mode docké.
* La sortie HDMI.

Ne remplace jamais un composant Switchroot essentiel par un composant PC générique.

Si une fonctionnalité n’est pas vérifiable, indique clairement qu’elle reste à tester sur une vraie console.

⸻

5. Applications et outils spécifiques à la Switch

Intégrer les outils utiles au fonctionnement de Linux sur Nintendo Switch.

Étudier notamment :

* Les outils officiels Switchroot.
* La gestion des Joy-Con et des contrôleurs.
* Les outils de configuration matérielle Tegra.
* Les outils de gestion de l’alimentation.
* Les outils utiles en mode docké.
* Les utilitaires de configuration de l’écran et du son.

Vérifier les sources, les licences et la compatibilité de chaque application avant son intégration.

Ne présente pas une application comme fonctionnelle si elle n’a pas été testée ou si sa compatibilité n’est pas établie.

⸻

6. Organisation de la carte SD

Je veux une organisation inspirée de Switchroot, mais avec le dossier principal renommé en omarchyswitch.

Exemple de structure cible :

SD:/
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
│   └── ... 
│
└── README.txt

Cette structure est une cible à adapter à l’architecture réelle de Switchroot.

IMPORTANT :

* Examiner les chemins réellement utilisés par la version de Switchroot choisie.
* Vérifier les scripts, les fichiers de configuration, les références aux partitions et les chemins internes.
* Adapter toutes les références nécessaires au nom omarchyswitch.
* Ne pas effectuer un simple renommage du dossier.
* Ne pas supprimer des fichiers indispensables au démarrage.
* Ne pas inventer de structure de partition.
* Ne pas supposer que les fichiers du système sont tous contenus dans un seul dossier.
* Préserver les mécanismes de démarrage réellement utilisés par Switchroot.

Si une partie de l’organisation officielle doit impérativement rester à son emplacement d’origine pour fonctionner, conserver cette partie et expliquer pourquoi.

⸻

7. Configuration Hekate

Créer une entrée Hekate nommée :

OmarchySwitch

Fichier cible :

bootloader/ini/omarchyswitch.ini

La configuration doit :

* Être compatible avec la version de Hekate utilisée.
* Démarrer le système Linux OmarchySwitch.
* Utiliser les bons chemins et fichiers de démarrage.
* Respecter les mécanismes de démarrage de Switchroot.
* Ne pas écraser les autres entrées Hekate.
* Permettre à l’utilisateur de conserver Atmosphère et ses autres configurations.

Ne fabrique pas une configuration INI en supposant que les paramètres sont corrects. Étudie les fichiers officiels de Switchroot et adapte-les.

⸻

8. Image de démarrage personnalisable

Créer une image de démarrage temporaire pour OmarchySwitch.

Je souhaite une image dans un style cohérent avec Omarchy, mais adaptée à la Nintendo Switch.

Elle doit :

* Afficher le nom OmarchySwitch.
* Être visuellement propre.
* Être adaptée aux dimensions de l’écran de la Switch.
* Utiliser un emplacement de fichier facile à retrouver.
* Être facilement remplaçable par ma propre image.

Créer un emplacement clairement documenté, par exemple :

omarchyswitch/splash/omarchyswitch.png

Mais vérifier d’abord quel mécanisme de splash screen est réellement pris en charge par la version de Switchroot utilisée.

Distinguer l’image de démarrage Linux d’une éventuelle image ou icône affichée par Hekate. Ne prétends pas qu’un seul fichier contrôle les deux si ce n’est pas le cas.

⸻

9. Installation et utilisation

L’installation doit être aussi simple que possible.

Objectif :

1. L’utilisateur télécharge l’archive OmarchySwitch.
2. Il extrait son contenu à la racine de sa carte SD.
3. Il conserve les fichiers Hekate et Atmosphère déjà présents.
4. Il démarre Hekate.
5. Il sélectionne l’entrée OmarchySwitch.
6. Linux démarre.

Ne formate pas automatiquement la carte SD.

Ne supprime pas les données déjà présentes.

Ne remplace pas les fichiers de Hekate existants sans nécessité.

Créer un README et un guide d’installation en français et en anglais expliquant :

* Les prérequis.
* La préparation de la carte SD.
* L’installation.
* Le démarrage depuis Hekate.
* Le remplacement de l’image de démarrage.
* Les problèmes connus.
* La désinstallation sans affecter les autres systèmes.

⸻

10. Dépôt GitHub

Utiliser le dépôt GitHub déjà connecté à ton environnement.

Si le dépôt est vide, l’initialiser correctement.

Important : un dépôt GitHub ne peut pas être simultanément un fork direct de deux projets. Choisir une organisation propre :

* Conserver les références aux projets sources.
* Utiliser les dépôts upstream comme remotes ou intégrer les composants nécessaires de façon traçable.
* Ne pas écraser l’historique d’un projet tiers.
* Conserver les licences et les mentions de copyright.
* Documenter les modifications réalisées.

Le dépôt final doit porter le nom :

OmarchySwitch

Organisation suggérée :

OmarchySwitch/
│
├── build/
├── config/
├── scripts/
├── switchroot/
├── omarchy/
├── boot/
├── assets/
│   └── splash/
├── docs/
├── .github/
│   └── workflows/
├── README.md
├── INSTALLATION.md
├── CHANGELOG.md
└── LICENSES/

Cette organisation concerne le dépôt de développement, pas nécessairement la structure finale de la carte SD.

⸻

11. Compilation automatisée avec GitHub Actions

Créer des workflows GitHub Actions pour automatiser autant que possible la préparation de la distribution.

Objectifs :

* Télécharger les sources nécessaires.
* Préparer les fichiers.
* Adapter les configurations.
* Construire l’archive finale.
* Vérifier sa structure.
* Publier l’archive en tant qu’artifact.

Tenir compte des limites de stockage, de mémoire et de durée des runners GitHub Actions.

Éviter de télécharger plusieurs fois les mêmes gros fichiers.

Mettre en cache les dépendances lorsque cela est pertinent.

Ne prétends pas avoir compilé un système complet si le workflow a uniquement assemblé des fichiers.

Si une compilation nécessite une machine plus puissante ou un matériel réel, documenter précisément cette limite.

⸻

12. Vérifications obligatoires

Avant de publier, effectuer toutes les vérifications réalisables :

* Présence des fichiers nécessaires.
* Structure de l’archive.
* Cohérence des chemins omarchyswitch.
* Configuration Hekate.
* Références internes au système.
* Présence des fichiers de démarrage.
* Compatibilité ARM64 des paquets.
* Présence des composants Switchroot indispensables.
* Présence des licences.
* Absence de fichiers inutiles ou temporaires.
* Absence de fichiers personnels ou secrets.
* Absence de configurations qui écraseraient Atmosphère ou Hekate.

Créer un rapport indiquant :

* Les tests réellement effectués.
* Les tests réussis.
* Les tests échoués.
* Les éléments non testés.
* Les limites connues.
* Les manipulations nécessitant une vraie Nintendo Switch.

Ne jamais inventer de résultat de test.

⸻

13. Publication GitHub

Créer une première release :

* Nom : OmarchySwitch v0.1.0-alpha
* Tag : v0.1.0-alpha
* Archive : OmarchySwitch-v0.1.0-alpha.zip

L’archive doit contenir les fichiers nécessaires à l’installation sur la carte SD, et non simplement le code source du dépôt.

Ajouter une description de release avec :

* Les fonctionnalités disponibles.
* Les instructions d’installation.
* Les fonctionnalités non testées.
* Les problèmes connus.
* Les avertissements de compatibilité.

Ne publie pas une archive vide, incomplète ou non vérifiée en prétendant qu’elle est prête.

Si la distribution ne peut pas encore démarrer sur une vraie console, indiquer clairement qu’il s’agit d’une version expérimentale.

⸻

14. Autonomie et compte rendu final

Travaille de manière autonome autant que possible.

Ne me demande pas de réaliser manuellement les étapes que tu peux effectuer toi-même dans l’environnement connecté.

Ne t’arrête pas après avoir simplement analysé les dépôts.

Effectue le maximum de travail concret :

1. Analyse des sources.
2. Préparation du système.
3. Adaptation des fichiers.
4. Création des configurations.
5. Préparation de l’archive.
6. Vérifications.
7. Publication GitHub si elle est possible.

Si une étape est impossible, explique précisément pourquoi et poursuis les autres étapes.

À la fin, fournis un compte rendu avec :

* L’URL du dépôt GitHub.
* L’URL de la release.
* Le lien de l’archive ZIP.
* La version d’Ubuntu Switchroot utilisée.
* Les composants Omarchy intégrés.
* Les composants Switchroot conservés.
* Les fonctionnalités opérationnelles.
* Les fonctionnalités qui restent à tester.
* Les éventuels problèmes empêchant le démarrage.

Objectif final : obtenir OmarchySwitch, une distribution Linux pour Nintendo Switch, avec une expérience inspirée d’Omarchy, installable depuis une carte SD et démarrable depuis Hekate sans détruire les autres configurations présentes sur la carte.
