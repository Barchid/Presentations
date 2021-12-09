# Plan : Neuromomorphic Autonomous Driving

## 1. Introduction au projet

L'objectif de ce chapitre est de se familiariser avec la tâche de vision à réaliser nommée **Car Steering Prediction**, ainsi qu'avec les outils à prendre en main.

### 1.1. Lecture
**Ojectif :** comprendre l'aspect théorique du projet.

**Rendu :** répondre (très brièvement) aux questions posées dans l'énoncé.

#### Étapes
- **Si le Deep Learning n'est pas encore connu :**
  - Comprendre l'aspect théorique du Deep Learning. Vidéo conseillée: https://www.youtube.com/watch?v=VyWAvY2CF9c (en anglais). Faire une courte liste de ce que vous avez appris (sans grandes explications).
  - Suivre ces deux tutoriels pratiques avec PyTorch:
    - Définir un réseau de neurones https://pytorch.org/tutorials/beginner/blitz/neural_networks_tutorial.html#sphx-glr-beginner-blitz-neural-networks-tutorial-py
    - Entraîner un classifieur avec PyTorch https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html#sphx-glr-beginner-blitz-cifar10-tutorial-py
    - Faire une courte liste de ce que vous avez appris.
- [Lire le tutoriel suivant](https://medium.com/@pathak.kapil/self-driving-car-steering-angle-prediction-304517df69d0) pour comprendre davantage la tâche de vision à réaliser.
  - Regarder rapidement le CNN-type utilisé pour résoudre cette tâche de vision. Qu'est-ce qui diffère par rapport à un CNN utilisé en classification (répondre en une ou deux phrase(s)) ?
- [Regarder cette vidéo](https://www.youtube.com/watch?v=6Sn9-M7qXLk) expliquant ce qu'est une **caméra DVS**. Quelles sont ses particularités par rapport à une caméra RGB classique (spécificités, avantages, inconvénients, ...) ?
- Lire les tutoriels sur les **Spiking Neural Networks (SNN)**. Expliquez la différence entre un ANN standard et un SNN.

### 1.2. Installation du projet d'entraînement
**Objectif :** Installer et se familiariser avec les ressources fournies pour la suite du projet.

#### Étapes

- *Préalablement :* choisir une personne responsable de ce point. L'autre binôme aura pour responsabilité le point 1.3.
- Un code de base est disponible sous forme de git à [l'url suivante](https://TODO). Il s'agit d'un projet de base permettant de faire un entraînement sur une petite base de données d'images de voitures. Installer le projet et créer un repository sur le serveur GitLab de l'IMT. Ajouter les encadrants.
  - **Note :** Ce code présente un notebook que vous pouvez upload sur Google Colab pour réaliser des entraînements sur GPU.
- Implémenter le CNN classique décrit sur l'image suivante dans le fichier **TODO** :

![image_CNN_carpred](https://miro.medium.com/max/500/1*VB_OYZu4DDlNIT7mdSstcg.png)

- Entraîner le modèle implémenté sur Google Colab et rapporter les performances du CNN en training/validation.
- Communiquer avec l'autre binôme sur le travail réalisé (expliquer la structure du projet, ce qui a été fait, etc).

### 1.3. Installation de la JetRacer

**Objectif :** installer les ressources pour travailler avec la voiture JetRacer et suivre la documentation disponible.

#### Étapes
- *Préalablement :* choisir une personne responsable de ce point. L'autre binôme aura pour responsabilité le point 1.2.
- [Le projet disponible à l'url suivante](https://github.com/NVIDIA-AI-IOT/jetracer) fournit une API/des notebooks pour commander la voiture JetRacer avec un ordinateur local, capter des images d'apprentissage, etc. Installer le projet et suivre les tutoriels.
  - [Documentation pour l'installation](https://github.com/NVIDIA-AI-IOT/jetracer/blob/master/docs/software_setup.md)
  - [Exemples pour commencer à utiliser la JetRacer](https://github.com/NVIDIA-AI-IOT/jetracer/blob/master/docs/examples.md)
- Communiquer avec l'autre binôme sur le travail réalisé (expliquer comment travailler avec la JetRacer, ce qui a été fait, comment capter des images, etc).

