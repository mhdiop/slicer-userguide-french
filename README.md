
# Démarrer avec *3D Slicer*

Bienvenue dans la communauté 3D Slicer. Cette page contient les informations dont vous avez besoin pour démarrer avec 3D Slicer, notamment comment l'installer et utiliser ses fonctionnalités de base et où trouver plus d'informations.

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

## Installing 3D Slicer

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

## Glossary

Terms used in various fields of medical and biomedical image computing and clinical images are not always consistent. This section defines terms that are commonly used in 3D Slicer, especially those that may have different meaning in other contexts.

- **Annotation**: Simple geometric objects and measurements that the user can place in viewers. Annotations module can be used to create such objects, but it is deprecated - being replaced by Markups module.
- **Bounds**: Describes bounding box of a spatial object along 3 axes. Defined in VTK by 6 floating-point values: `X_min`, `X_max`, `Y_min`, `Y_max`, `Z_min`, `Z_max`.
-** Brightness/contras**t: Specifies linear mapping of voxel values to brightness of a displayed pixel. Brightness is the linear offset, contrast is the multiplier. In medical imaging, this linear mapping is more commonly specified by window/level values.
- **Cell**: Data cells are simple topological elements of meshes, such as lines, polygons, tetrahedra, etc.
- **Color legend** (or color bar, scalar bar): a widget overlaid on slice or 3D views that displays a color legend, indicating meaning of colors.
- **Coordinate system** (or coordinate frame, reference frame, space): Specified by position of origin, axis directions, and distance unit. All coordinate systems in 3D Slicer are right-handed.
- **Extension** (or Slicer extension): A collection of modules that is not bundled with the core application but can be downloaded and installed using the Extensions manager.
- [**Extensions manager**](extensions_manager): A software component of Slicer that allows browsing, installing, uninstalling extensions in the [Extensions catalog (also known as the Slicer app store)](https://extensions.slicer.org) directly from the application.
- [**Extensions index**](https://github.com/Slicer/ExtensionsIndex): A repository that contains description of each extension that the Extension catalog is built from.
- **Extent**: Range of integer coordinates along 3 axes. Defined in VTK by 6 values, for IJK axes: `I_min`, `I_max`, `J_min`, `J_max`, `K_min`, `K_max`. Both minimum and maximum values are inclusive, therefore size of an array is `(I_max - I_min + 1)` x `(J_max - J_min + 1)` x `(K_max - K_min + 1)`.
- **Fiducial**: Represents a point in 3D space. The term originates from image-guided surgery, where "fiducial markers" are used to mark point positions.
- **Frame**: One time point in a time sequence. To avoid ambiguity, this term is not used to refer to a slice of a volume.
- **Geometry**: Specify location and shape of an object in 3D space. See "Volume" term for definition of image geometry.
- **Image intensity**: Typically refers to the value of a voxel. Displayed pixel brightness and color is computed from this value based on the chosen window/level and color lookup table.
- **IJK**: Voxel coordinate system axes. Integer coordinate values correspond to voxel center positions. IJK values are often used as coordinate location within a 3D array. By VTK convention, and I indexes the column, J indexes the row, K indexes the slice. Note that numpy uses the opposite ordering convention, where `a[K][J][I]`. Sometimes this memory layout is described as I being the fastest moving index and K being the slowest moving.
- **ITK**: [Insight Toolkit](https://itk.org/). Software library that Slicer uses for most image processing operations.
- **Labelmap** (or labelmap volume, labelmap volume node): Volume node that has discrete (integer) voxel values. Typically each value corresponds to a specific structure or region. This allows compact representation of non-overlapping regions in a single 3D array. Most software use a single labelmap to store an image segmentation, but Slicer uses a dedicated segmentation node, which can contain multiple representations (multiple labelmaps to allow storing overlapping segments; closed surface representation for quick 3D visualization, etc.).
- **LPS**: Left-posterior-superior anatomical coordinate system. Most commonly used coordinate system in medical image computing. Slicer stores all data in LPS coordinate system on disk (and converts to/from RAS when writing to or reading from disk).
- **Markups**: Simple geometric objects and measurements that the user can place in viewers. [Markups module](modules/markups.md) can be used to create such objects. There are several types, such as point list, line, curve, plane, ROI.
- **Source volume**: Voxel values of this volume is used during segmentation by those effects that rely on intensity of an underlying volume.
- **MRML**: [Medical Reality Markup Language](https://en.wikipedia.org/wiki/Medical_Reality_Markup_Language): Software library for storage, visualization, and processing of information objects that may be used in medical applications. The library is designed to be reusable in various software applications, but 3D Slicer is the only major application that is known to use it.
- **Model** (or model node): MRML node storing surface mesh (consists of triangle, polygon, or other 2D cells) or volumetric mesh (consists of tetrahedral, wedge, or other 3D cells)
- **Module** (or Slicer module): A Slicer module is a software component consisting of a graphical user interface (that is displayed in the module panel when the module is selected), a logic (that implements algorithms that operate on MRML nodes), and may provide new MRML node types, displayable managers (that are responsible for displaying those nodes in views), input/output plugins (that are responsible for load/save MRML nodes in files), and various other plugins. Modules are typically independent and only communicate with each other via modifying MRML nodes, but sometimes a module use features provided by other modules by calling methods in its logic.
- **Node** (or MRML node): One data object in the scene. A node can represent data (such as an image or a mesh), describe how it is displayed (color, opacity, etc.), stored on disk, spatial transformations applied on them, etc. There is a C++ class hierarchy to define the common behaviors of nodes, such as the property of being storable on disk or being geometrically transformable. The structure of this class hierarchy can be inspected in the code or in the [API documentation](https://apidocs.slicer.org/main/classvtkMRMLStorableNode.html).
- **Orientation marker**: Arrow, box, or human shaped marker to show axis directions in slice views and 3D views.
- **RAS**: Right-anterior-superior anatomical coordinate system. Coordinate system used internally in Slicer. It can be converted to/from LPS coordinate system by inverting the direction of the first two axes.
- **Reference**: Has no specific meaning, but typically refers to a secondary input (data object, coordinate frame, geometry, etc.) for an operation.
- **Region of interest (ROI)**: Specifies a box-shaped region in 3D. Can be used for cropping volumes, clipping models, etc.
- **Registration**: The process of aligning objects in space. Result of the registration is a transform, which transforms the "moving" object to the "fixed" object.
- **Resolution**: Voxel size of a volume, typically specified in mm/pixel. It is rarely used in the user interface because its meaning is slightly misleading: high resolution value means large spacing, which means coarse (low) image resolution.
- **Ruler**: It may refer to: 1. View ruler: The line that is displayed as an overlay in viewers to serve as a size reference. 2. Annotation ruler: deprecated distance measurement tool (use "Markups line" instead).
- **Scalar component**: One element of a vector. Number of scalar components means the length of the vector.
- **Scalar value**: A simple number. Typically floating-point.
- **Scene** (or MRML scene): This is the data structure that contains all the data that is currently loaded into the application and additional information about how they should be displayed or used. The term originates [computer graphics](https://en.wikipedia.org/wiki/Rendering_(computer_graphics)).
- **Segment**: Corresponds to single structure in a segmentation. See more information in [Image segmentation](image_segmentation.md) section.
- **Segmentation** (also known as contouring, annotation; region of interest, structure set, mask): Process of delineating 3D structures in images. Segmentation can also refer to the MRML node that is the result of the segmentation process. A segmentation node typically contains multiple segments (each segment corresponds to one 3D structure). Segmentation nodes are not labelmap nodes or model nodes but they can store multiple representations (binary labelmap, closed surface, etc.). See more information in [Image segmentation](image_segmentation) section.
- **Slice**: Intersection of a 3D object with a plane.
- **Slice view annotations**: text in corner of slice views displaying name, and selected DICOM tags of the displayed volumes
- **Spacing**: Voxel size of a volume, typically specified in mm/pixel.
- **Transform** (or transformation): Can transform any 3D object from one coordinate system to another. Most common type is rigid transform, which can change position and orientation of an object. Linear transforms can scale, mirror, shear objects. Non-linear transforms can arbitrarily warp the 3D space. To display a volume in the world coordinate system, the volume has to be resampled, therefore transform *from* the world coordinate system to the volume is needed (it is called the resampling transform). To transform all other node types to the world coordinate system, all points must be transformed *to* the world coordinate system (modeling transform). Since a transform node must be applicable to any nodes, transform nodes can provide both *from* and *to* the parent (store one and compute the other on-the-fly).
- **Volume** (or volume node, scalar volume, image): MRML node storing 3D array of voxels. Indices of the array are typically referred to as IJK. Range of IJK coordinates are called extents. Geometry of the volume is specified by its origin (position of the IJK=(0,0,0) point), spacing (size of a voxel along I, J, K axes), axis directions (direction of I, J, K axes in the reference coordinate system) with respect to a frame of reference. 2D images are single-slice 3D volumes, with their position and orientation specified in 3D space.
- [**Voxel**](https://en.wikipedia.org/wiki/Voxel): One element of a 3D volume. It has a rectangular prism shape. Coordinates of a voxel correspond to the position of its center point. Value of a voxel may be a simple scalar value or a vector.
- **VR**: Abbreviation that can refer to volume rendering or virtual reality. To avoid ambiguity it is generally recommended to use the full term instead (or explicitly define the meaning of the abbreviation in the given context).
- **VTK**: [Visualization Toolkit](https://vtk.org/). Software library that Slicer uses for to data representation and visualization. Since most Slicer classes are derived from VTK classes and they heavily use other VTK classes, Slicer adopted many conventions of VTK style and application programming interface.
- **Window/level** (or window width/window level): Specifies linear mapping of voxel values to brightness of a displayed pixel. Window is the size of the intensity range that is mapped to the full displayable intensity range. Level is the voxel value that is mapped to the center of the full displayable intensity range.
