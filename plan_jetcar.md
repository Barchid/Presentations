# Plan : Neuromomorphic Autonomous Driving

## 1. Introduction au projet

L'objectif de cette partie est de se familiariser avec la tâche de vision à réaliser nommée **Car Steering Prediction**, ainsi qu'avec les outils à prendre en main.

### 1.1. Théorie
**Ojectif :** comprendre l'aspect théorique du projet.

**Rendu :** répondre (très brièvement) aux questions posées dans l'énoncé.

#### Étapes
- **Si le Deep Learning n'est pas encore connu :**
  - Comprendre l'aspect théorique du Deep Learning. Vidéo conseillée: https://www.youtube.com/watch?v=VyWAvY2CF9c (en anglais). Faire une courte liste de ce que vous avez appris (sans grandes explications).
  - Suivre ces deux tutoriels pratiques avec PyTorch:
    - Définir un réseau de neurones https://pytorch.org/tutorials/beginner/blitz/neural_networks_tutorial.html#sphx-glr-beginner-blitz-neural-networks-tutorial-py
    - Entraîner un classifieur avec PyTorch https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html#sphx-glr-beginner-blitz-cifar10-tutorial-py
    - Faire une courte liste de ce que vous avez appris.
- [Lire le tutoriel suivant](https://medium.com/@pathak.kapil/self-driving-car-steering-angle-prediction-304517df69d0) et [celui-ci également](https://towardsdatascience.com/teaching-cars-to-drive-using-deep-learning-steering-angle-prediction-5773154608f2) pour comprendre davantage la tâche de vision à réaliser.
  - Regarder rapidement le CNN-type utilisé pour résoudre cette tâche de vision. Qu'est-ce qui diffère par rapport à un CNN utilisé en classification (répondre en une ou deux phrase(s)) ?
- [Regarder cette vidéo](https://www.youtube.com/watch?v=6Sn9-M7qXLk) expliquant ce qu'est une **caméra DVS**. Quelles sont ses particularités par rapport à une caméra RGB classique (spécificités, avantages, inconvénients, ...) ?
- Lire les tutoriels sur les **Spiking Neural Networks (SNN)**. Expliquez la différence entre un ANN standard et un SNN.

### 1.2. Installation du projet d'entraînement
**Objectif :** Installer et se familiariser avec les ressources fournies pour la suite du projet.

#### Étapes

- ***Préalablement :** choisir une personne responsable de ce point. L'autre binôme aura pour responsabilité le point 1.3.*
- Un code de base est disponible sous forme de git à [l'url suivante](https://TODO). Il s'agit d'un projet de base permettant de faire un entraînement sur une petite base de données d'images captées dans une voiture. Installer le projet et créer un repository sur le serveur GitLab de l'IMT. Ajouter les encadrants.
  - **Note :** Ce code présente un notebook que vous pouvez upload sur Google Colab pour réaliser des entraînements sur GPU.
- Implémenter le CNN classique décrit sur l'image suivante dans le fichier **TODO** :

![image_CNN_carpred](https://miro.medium.com/max/500/1*VB_OYZu4DDlNIT7mdSstcg.png)

- Entraîner le modèle implémenté sur Google Colab et rapporter les performances du CNN en training/validation.
- Communiquer avec l'autre binôme sur le travail réalisé (expliquer la structure du projet, ce qui a été fait, etc).

### 1.3. Installation de la JetRacer

**Objectif :** installer les ressources pour travailler avec la voiture JetRacer et suivre la documentation disponible. Cette documentation permet déjà de capter des images et d'entraîner un modèle CNN dessus, ainsi que de faire rouler la voiture avec ce modèle entraîné.

**Rendu :** une petite base de données d'images peut être captée. La JetRacer est capable de rouler de manière autonome en utilisant le modèle CNN fourni dans le tutoriel.

#### Étapes
- ***Préalablement :** choisir une personne responsable de ce point. L'autre binôme aura pour responsabilité le point 1.2.*
- [Prendre connaissance du wiki officiel pour la JetRacer et procéder à l'installation sur la Jetson Nano embarquée.](https://www.waveshare.com/wiki/JetRacer_AI_Kit)
- [Le projet disponible à l'url suivante](https://github.com/waveshare/jetracer) fournit une API/des notebooks pour commander la voiture JetRacer avec un ordinateur local, capter des images d'apprentissage, etc. Installer le projet et suivre les tutoriels.
  - [Documentation pour l'installation](https://github.com/waveshare/jetracer/blob/master/docs/software_setup.md)
  - [Exemples pour commencer à utiliser la JetRacer](https://github.com/waveshare/jetracer/blob/master/docs/examples.md)
- Communiquer avec l'autre binôme sur le travail réalisé (expliquer comment travailler avec la JetRacer, ce qui a été fait, comment capter des images, etc).

### 1.4. Installation de DV
DV est un logiciel permettant de faire l'interface entre la caméra DVS et un ordinateur. Ce logiciel va permettre de récupérer le flux DVS et de l'exploiter dans nos programmes python.

**Objectif :** Installer le logiciel DV dans les ordinateurs utilisés pendant le projet et lire un peu de documentation sur son utilisation. 

**Rendu :** un petit programme python permettant d'afficher un flux DVS filmé par la caméra DVS, afin de s'assurer que la liaison entre la caméra et un ordinateur se passe sans problème.

#### Étapes
- Installer le logiciel DV sur les machines que vous utilisez. [Suivre les instructions ici](https://inivation.gitlab.io/dv/dv-docs/docs/getting-started/).
- Explorer l'interface du logiciel DV. Faire une petite liste des features intéressantes du logiciel.
- [Installer le logiciel DV sur la Jetson Nano](https://inivation.gitlab.io/dv/dv-docs/docs/getting-started/#nvidia-jetson) de la JetRacer. Ensuite, [suivre le tutoriel suivant](https://inivation.gitlab.io/dv/dv-docs/docs/getting-started/#launching-dv-runtime-with-a-remote-gui) pour utiliser un remote GUI avec un runtime DV sur la Jetson NANO
- [Lire et installer le projet `dv-python`](https://gitlab.com/inivation/dv/dv-python) afin de pouvoir lier le logiciel DV à un programme python sur votre machine de travail.
  - Implémenter les scripts d'exemple disponibles dans le readme.
- Refaire l'installation de `dv-python` sur la Jetson Nano de la JetRacer pour vérifier que cela fonctionne également.


### 1.5. Récapitulatif
La première partie du projet est terminée. Arrivé à ce point, l'environnement technique est installé, fonctionne et est compris. Faites une courte liste des choses accomplies et des choses apprises durant cette première partie.

A partir de maintenant, le projet entre dans un contexte plus orienté R&D. C'est pourquoi les prochaines étapes du plan seront moins explicites.

## 2. Caméra RGB -> Caméra DVS

**Objectif :** remplacer la caméra RGB utilisée dans les notebooks [de la partie 1.3](#13-installation-de-la-jetracer) par des frames DVS récupérées grâce à DV et `dv-python` ([partie 1.5](#15-récapitulatif)). Puis de faire un entraînement sur ces nouvelles frames DVS, en adaptant les notebooks de [la partie 1.3](#13-installation-de-la-jetracer).

#### Suggestion d'étapes
- Connecter la caméra DVS à la JetRacer en utilisant un remote GUI sur votre machine de travail ([point 1.4](#14-installation-de-dv)).
- Modifier le notebook de captation d'images ([partie 1.3.](#13-installation-de-la-jetracer)) pour y inclure des frames DVS au lieu des frames RGB, afin d'avoir une nouvelle base d'entraînement.
- Adapter le reste des notebooks de [la partie 1.3](#13-installation-de-la-jetracer) pour faire des entraînements sur frame DVS.

## 3. Base de données vidéo DVS
Jusqu'ici, nous avons utilisé un CNN classique avec des frames (RGB ou DVS). Il faut maintenant passer de frames DVS à une **vidéo** DVS en fichier `.aedat` (format de fichier standard utilisé par DV). Un exemple de script avec dv-python pour lire un fichier .aedat [est donné ici](https://gitlab.com/inivation/dv/dv-python#open-a-recording-made-with-dv).

**Objectif :** réaliser une base de données de **vidéos** DVS avec DV, tout en récupérant les steering predictions. Pas d'entraînement de CNN ici, étant donné que nous ne traitons plus des images mais des vidéos.

#### Intuitions
- Connecter la caméra DVS à la JetRacer en utilisant un remote GUI sur votre machine de travail ([point 1.4](#14-installation-de-dv)).
- Modifier le notebook de captation d'images ([partie 1.3.](#13-installation-de-la-jetracer)) pour y inclure un flux DVS au lieu des frames RGB, afin d'avoir une nouvelle base d'entraînement.
  - **Difficulté :** lier la ground truth des angles de steering avec le flux DVS capté n'est pas aussi intuitif qu'avec des frames. Il va falloir réfléchir à une bonne méthode et en discuter avec les encadrants.


## 4. Spiking Neural Networks
**Objectif :** utiliser la base de données de vidéos DVS captée en [partie 3](#3-base-de-données-vidéo-dvs) pour entraîner un SNN.

#### Intuitions
