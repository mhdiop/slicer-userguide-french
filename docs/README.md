
# Démarrer avec 3D Slicer

Bienvenue dans la communauté 3D Slicer. Cette page contient les informations dont vous avez besoin pour démarrer avec 3D Slicer, notamment comment l'installer et utiliser ses fonctionnalités de base et où trouver plus d'informations.
> **_NOTE :_**  Cette page est une traduction d'une [partie](https://slicer.readthedocs.io/en/latest/user_guide/getting_started.html) de la [documentation officielle de *3D Slicer*](https://slicer.readthedocs.io/en/latest/).
## Configurations requises

3D Slicer fonctionne sur tout ordinateur Windows, Mac ou Linux sorti au cours des cinq dernières années. Les ordinateurs plus anciens peuvent également le supporter (dépend principalement des capacités graphiques).

Slicer peut également fonctionner sur des machines virtuelles et des conteneurs docker. Par exemple, [*3D Slicer + Jupyter Notebook* dans un navigateur web](https://mybinder.org/v2/gh/Slicer/SlicerNotebooks/master?filepath=SlicerWeb.ipynb) est disponible gratuitement via le service Binder (aucune installation nécessaire, l'application peut fonctionner dans n'importe quel navigateur web).

### Versions des systèmes d'exploitation

- Windows : Windows 10 ou 11, avec toutes les mises à jour recommandées installées. La version 1903 de Windows 10 (mise à jour de mai 2019) ou une version ultérieure est requise pour la prise en charge des caractères internationaux (UTF-8) dans les noms de fichiers et le texte. Microsoft ne prend plus en charge Windows 8.1 et Windows 7. Slicer n'est donc pas testé sur ces anciennes versions du système d'exploitation, mais pourrait malgré tout y fonctionner.
- MacOS : MacOS High Sierra (10.13) ou version ultérieure (systèmes basés sur Intel et ARM). La dernière version publique est recommandée.
- Linux : Ubuntu 18.04 ou version ultérieure<br>CentOS 7 ou version ultérieure. La dernière version LTS (Long-term-support) est recommandée.

### Configuration matérielle recommandée

- Mémoire : plus de 4 Go (8 ou plus sont recommandés). En règle générale, ayez 10 fois plus de mémoire que la quantité de données que vous chargez.
- Affichage : une résolution minimale de 1024 par 768 (1280 par 1024 ou plus est recommandé).
- Graphique : Une mémoire dédiée au matériel graphique (GPU discret) est recommandée pour un rendu rapide des volumes.
GPU : Le matériel graphique doit supporter au minimum OpenGL 3.2. Une carte graphique intégrée est suffisante pour une visualisation de base. Une carte graphique discrète (telle qu'un GPU NVidia) est recommandée pour le rendu interactif de volumes 3D et le rendu rapide de scènes complexes. La mémoire de texture du GPU (VRAM) doit être supérieure à votre plus grand jeu de données (par exemple, si vous travaillez avec des données de 2 Go, utilisez une VRAM > 4 Go) et vérifiez que vos images tiennent dans les dimensions maximales de texture de votre matériel GPU. À l'exception du rendu, la plupart des calculs sont effectués par le CPU. Par conséquent, un GPU plus rapide n'aura généralement pas d'impact sur la vitesse globale de l'application.
- Certains calculs de 3D Slicer sont multithreadés et bénéficieront de configurations multi-cœurs et multi-processeurs.
- Dispositif d'interface : une souris à trois boutons avec molette de défilement est recommandée. Le stylet, l'écran tactile multipoint, le pavé tactile et la tablette graphique sont pris en charge. Tous les casques de réalité virtuelle compatibles avec OpenVR sont pris en charge pour l'affichage de la réalité virtuelle.
- Connexion Internet pour accéder aux extensions, aux paquets Python, à la documentation en ligne, aux jeux de données d'exemple et aux tutoriels.

## Installation de 3D Slicer

Pour télécharger Slicer, cliquez [ici](https://download.slicer.org/).

![](https://github.com/Slicer/Slicer/releases/download/docs-resources/getting_started_download.png)

**Notes:**
- La "Preview Release" de 3D Slicer est mise à jour quotidiennement (le processus commence à 23 heures heure de l'Est et prend quelques heures) et représente le dernier développement incluant les nouvelles fonctionnalités et les corrections.
- La "Stable Release" est habituellement mise à jour plusieurs fois par an et fait l'objet de tests plus rigoureux.
- Slicer est généralement simple à installer sur toutes les plateformes. Il est possible d'installer plusieurs versions de l'application sur le même compte utilisateur et elles n'interféreront pas entre elles. Si vous rencontrez des problèmes mystérieux lors de votre installation, vous pouvez essayer de supprimer les [fichiers de paramètres de l'application](settings.md#settings-file-location).
- Seuls les installateurs 64 bits de Slicer sont disponibles au téléchargement. Les développeurs peuvent essayer de construire eux-mêmes des versions 32 bits s'ils ont besoin d'exécuter Slicer sur un système d'exploitation 32 bits. Cela dit, il convient d'y réfléchir attentivement, car de nombreuses tâches de recherche clinique, telles que le traitement de grands ensembles de données volumétriques de tomodensitométrie ou d'IRM, nécessitent plus de mémoire qu'un programme 32 bits.

Une fois téléchargé, suivez les instructions ci-dessous pour terminer l'installation :

### Windows

- Exécutez le programme d'installation.
  - Limitation actuelle : Le chemin d'installation ne doit contenir que des caractères anglais ([ASCII imprimable](https://en.wikipedia.org/wiki/ASCII#Printable_characters)), sinon certains paquets Python risquent de ne pas se charger correctement (voir cette [question](https://github.com/Slicer/Slicer/issues/5383) pour plus de détails).
- Lancez Slicer à partir du menu de démarrage de Windows.
- Utilisez "Programmes et fonctionnalités" dans les paramètres de Windows pour supprimer l'application.

### Mac

- Ouvrez le paquet d'installation (fichier .dmg).
- Faites glisser l'application Slicer (Slicer.app) vers votre dossier Applications (ou tout autre emplacement de votre choix).
  - Cette étape est nécessaire car le contenu d'un fichier .dmg est ouvert en tant que volume en lecture seule, et vous ne pouvez pas installer d'extensions ou de paquets Python dans un volume en lecture seule.
- Supprimez le dossier Slicer.app pour le désinstaller.

Remarque concernant l'installation d'une Preview Release : Actuellement, les paquets de la Preview Release ne sont pas signés. Par conséquent, lorsque l'application est lancée la première fois, le message suivant s'affiche : "Slicer... ne peut pas être ouvert car il provient d'un développeur non identifié". Pour résoudre cette erreur, localisez l'application dans le Finder, faites un clic droit (deux doigts) et cliquez sur "Ouvrir". Lorsque le message "Cette application ne peut pas être ouverte" apparaît, cliquez sur "Annuler". Faites à nouveau un clic droit et dites "Ouvrir" (oui, vous devez répéter la même chose que la fois précédente - le résultat sera différent de celui de la première fois). Cliquez sur le bouton "Ouvrir" (ou "Ouvrir quand même") pour lancer l'application. Vous trouverez plus d'explications et des techniques alternatives [ici](https://support.apple.com/en-my/guide/mac-help/mh40616/mac).

#### Installer avec Homebrew

Slicer peut être installé à l'aide d'une seule commande dans un terminal en utilisant le gestionnaire de paquets [Homebrew](https://brew.sh/) :

```shell
brew install --cask slicer  # pour installer
brew upgrade slicer         # pour mettre à jour
brew uninstall slicer       # pour désinstaller
```

Cette démarche permet d'éviter le processus habituel consistant à rechercher sur Google, puis de télécharger, de monter et de glisser pour installer les applications macOS.

Les "Preview releases" peuvent être installées en utilisant [`homebrew-cask-versions`](https://github.com/Homebrew/homebrew-cask-versions) :

```shell
brew tap homebrew/cask-versions     # doit être exécuté une fois
brew install --cask slicer-preview  # pour installer
brew upgrade slicer-preview         # pour mettre à jour
brew uninstall slicer-preview       # pour désinstaller
```

### Linux

- Ouvrez l'archive tar.gz et copiez le répertoire à l'emplacement de votre choix.
- L'installation de paquets supplémentaires peut être nécessaire selon la distribution et la version de Linux, comme décrit dans les sous-sections ci-dessous.
- Lancez l'exécutable `Slicer`.
- Supprimez le répertoire pour désinstaller.

**Notes:**
- Slicer est censé fonctionner sur la grande majorité des distributions Linux de bureau et de serveur. Le système doit fournir au moins GLIBC 2.17 et GLIBCCC 3.4.19. Pour plus de détails, lisez [ici](https://www.python.org/dev/peps/pep-0599/#the-manylinux2014-policy).
- Le gestionnaire d'extensions utilise QtWebengine pour afficher la liste des extensions. Si votre noyau linux ne répond pas aux [exigences de sandboxing](https://doc.qt.io/Qt-5/qtwebengine-platform-notes.html#sandboxing-support) alors vous pouvez désactiver le sandboxing par cette commande : `export QTWEBENGINE_DISABLE_SANDBOX=1`
- Pour obtenir des arguments de ligne de commande et des résultats de processus contenant des caractères non ASCII, le système doit utiliser une variable locale UTF-8. Si le système utilise une autre  variable locale, la commande `export LANG="C.UTF-8"` peut être utilisée avant de lancer l'application pour passer à une variable locale acceptable.

#### Debian / Ubuntu
Les éléments suivants peuvent être nécessaires sur un debian ou un ubuntu récent :

    sudo apt-get install libpulse-dev libnss3 libglu1-mesa
    sudo apt-get install --reinstall libxcb-xinerama0

:::{note} Avertissement
:class : warning

Les utilisateurs de Debian 10.12 peuvent rencontrer une erreur lors du lancement de Slicer :

   Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
    qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
    This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

   Available platform plugins are: xcb.

[La solution](https://forum.qt.io/topic/93247/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/81) consiste à créer un lien symbolique :

    sudo ln -s /usr/lib/x86_64-linux-gnu/libxcb-util.so /usr/lib/x86_64-linux-gnu/libxcb-util.so.1

:::

#### ArchLinux
ArchLinux exécute l'utilitaire `strip` par défaut ; il doit être désactivé afin d'exécuter les binaires Slicer.  Pour plus d'informations, voir [cette discussion sur le forum Slicer](https://discourse.slicer.org/t/could-not-load-dicom-data/14211/5).

#### Fedora
Installez les dépendances :

    sudo dnf install mesa-libGLU libnsl

La libcrypto.so.1.1 incluse dans l'installation de Slicer est incompatible avec les bibliothèques système utilisées par Fedora 35. La solution, jusqu'à ce qu'elle soit mise à jour, est de déplacer/supprimer les fichiers libcrypto inclus :

    $SLICER_ROOT/lib/Slicer-4.xx/libcrypto.*

## Utiliser Slicer

3D Slicer propose de nombreuses fonctionnalités et offre aux utilisateurs une grande flexibilité dans la manière de les utiliser. Par conséquent, les nouveaux utilisateurs peuvent être submergés par le nombre d'options et avoir des difficultés à comprendre comment effectuer même des opérations simples. C'est normal et de nombreux utilisateurs ont réussi à franchir cette étape difficile en investissant un peu de temps pour apprendre à utiliser ce logiciel.

Comment apprendre Slicer ?

### Démarrage rapide

Vous pouvez essayer de comprendre le fonctionnement de l'application en chargeant des jeux de données et explorer ce que vous pouvez faire.

#### Charger des données

Ouvrez 3D Slicer et, à l'aide du panneau de bienvenue, chargez vos propres données ou téléchargez des échantillons de données à explorer. Les échantillons de données sont souvent utiles pour essayer les fonctionnalités de 3D Slicer si vous ne disposez pas de vos propres données.

![](https://github.com/Slicer/Slicer/releases/download/docs-resources/getting_started_load_data.png)

![](https://github.com/Slicer/Slicer/releases/download/docs-resources/getting_started_sample_data.png)

#### Visualiser des données

L'onglet "Hiérarchie des sujets" du module "Data" affiche tous les jeux de données de la scène. Cliquez sur l'icône "œil" pour afficher/masquer un élément dans toutes les vues.

Vous pouvez personnaliser les vues (afficher le marqueur d'orientation, la règle, changer l'orientation, la transparence) en cliquant sur la punaise dans le coin supérieur gauche du visualiseur. Dans les visionneuses de coupes, la barre horizontale peut être utilisée pour faire défiler les coupes ou sélectionner une coupe.

![](https://github.com/Slicer/Slicer/releases/download/docs-resources/getting_started_view_controllers.png)

#### Traiter des données

3D Slicer est construit sur une architecture modulaire. Choisissez un module pour traiter ou analyser vos données. Les modules les plus importants sont les suivants (la liste complète est disponible dans la section [Modules](modules/index.md)) :

- *Bienvenue* : Le module par défaut lorsque 3D Slicer est lancé. Il présente des options pour le chargement des données et la personnalisation de 3D Slicer. Sous ces options, des boîtes déroulantes contiennent des informations essentielles à l'utilisation de 3D Slicer.
- [Data](modules/data.md) : agit comme un centre d'organisation des données. Il répertorie toutes les données actuellement présentes dans la scène et permet des opérations de base telles que rechercher, renommer, supprimer et déplacer.
- [DICOM](modules/dicom.md) : Importez et exportez des objets DICOM, tels que des images, des segmentations, des ensembles de structures, des objets de radiothérapie, etc.
- [Volumes](modules/volumes.md) : Utilisé pour changer l'apparence de divers types de volumes.
- [Volume Rendering](modules/volumerendering.md) : Fournit une visualisation interactive des données d'imagerie 3D.
- [Segmentations](modules/segmentations.md) : Modifier les propriétés d'affichage et importer/exporter des segmentations.
- [Segment Editor](modules/segmenteditor.md) : Segmentez des volumes 3D en utilisant divers outils manuels, semi-automatiques et automatiques.
- [Markups](modules/markups.md) : Permet la création et l'édition des markups (annotations) associés à une scène.
- [ Models ](modules/models.md) : Charge et ajuste les paramètres d'affichage des modèles. Permet à l'utilisateur de modifier l'apparence des modèles de surface 3D et de les organiser.
- [Transforms](modules/transforms.md) : Ce module est utilisé pour créer et éditer des matrices de transformation. Vous pouvez établir ces relations en déplaçant les nœuds de la liste Transformable vers la liste Transformé ou en faisant glisser les nœuds sous les nœuds Transformation du module Data.

#### Sauvegarder des données

Les jeux de données chargés dans l'application peuvent être enregistrés à l'aide de la boîte de dialogue Enregistrer les données, ou exportés au format DICOM à l'aide du module DICOM. Les détails sont décrits dans la section [Chargement et sauvegarde des données](data_loading_and_saving.md).

#### Les extensions

3D Slicer prend en charge des plug-ins appelés extensions. Une extension peut être considérée comme un paquet de distribution regroupant un ou plusieurs modules Slicer. Après avoir installé une extension, les modules associés seront présentés à l'utilisateur comme des modules intégrés. Les extensions peuvent être téléchargées à partir du gestionnaire d'extensions pour installer de manière sélective les fonctionnalités utiles à l'utilisateur final.

![](https://github.com/Slicer/Slicer/releases/download/docs-resources/getting_started_module_list.png)

![](https://github.com/Slicer/Slicer/releases/download/docs-resources/getting_started_extensions_manager.png)

Pour plus de détails sur le téléchargement des extensions, voir la [documentation du gestionnaire d'extensions](extensions_manager.md).
Cliquez [ici](https://www.slicer.org/wiki/Documentation/Nightly/ModuleExtensionListing/Extensions_by_category) pour obtenir une liste complète des extensions. Les liens sur la page fourniront la documentation pour chaque extension.

Slicer est extensible. Si vous souhaitez personnaliser ou ajouter des fonctionnalités à Slicer, cliquez [ici](https://www.slicer.org/wiki/Documentation/Nightly/Training#Tutorials_for_software_developers).

### Tutoriels

Vous apprenez aussi bien les concepts de base que les flux de travail hautement spécialisés grâce aux nombreux tutoriels vidéo et étape par étape disponibles.

Essayez le [Tutoriel de bienvenue](https://www.slicer.org/wiki/Documentation/Nightly/Training#Slicer_Welcome_Tutorial) et le [Tutoriel sur le chargement des données et la visualisation 3D](https://www.slicer.org/wiki/Documentation/Nightly/Training#Slicer4_Data_Loading_and_3D_Visualization) pour apprendre les bases.

Pour plus de tutoriels, visitez la [page des tutoriels](https://www.slicer.org/wiki/Documentation/Nightly/Training).

### Manuel utilisateur

Parcourez la section [Interface utilisateur](user_interface.md) pour obtenir un aperçu rapide de l'interface utilisateur de l'application ou la section [Modules](modules/index.md) pour obtenir une description détaillée de chaque module.

### Obtenir de l'aide

3D Slicer existe depuis de nombreuses années et de nombreuses questions ont déjà été posées et répondues à son sujet. Si vous avez des questions, vous pouvez commencer par une recherche sur le web, par exemple en tapant sur Google `slicer charger jpg` pour savoir comment importer une pile d'images jpg.

L'application dispose d'une grande communauté d'utilisateurs très sympathiques et serviables. Nous avons des personnes qui seront heureuses de vous aider pour des questions simples, comme la façon d'effectuer une tâche spécifique dans Slicer, et nous avons un grand nombre d'experts en ingénierie et en médecine qui peuvent vous donner des conseils pour résoudre des problèmes complexes.

**Si vous avez des questions, rendez-vous sur le [forum Slicer](https://discourse.slicer.org) et posez-les nous!**

