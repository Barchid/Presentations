# Contrôle de bras robotique par approches neuromorphiques

Ce plan est destiné à guider le stagiaire tout au long de son stage en définissant des objectifs à suivre. Bien entendu, ces objectifs ne sont pas rigides et peuvent être modifiés/supprimés ou autre selon l'évolution du projet.

## Contexte et objectif du stage

![Bras robot Yahboom](http://sc04.alicdn.com/kf/Hb531628d5bfb47cea11004e489a8ac25T.jpg)

Nous utilisons un bras robotique de la marque Yahboom à 6 degrés de libertés (DoF, en abrégé anglais), tournant sur un combo Raspberry Pi 4 muni d'un accélérateur neuronal nommé "Intel Movidius", afin de faire tourner des réseaux de neurones profonds en temps réel.

Bien que ce bras ne soit pas taillé pour des applications industrielles (force et taille très limitées), il permet de réaliser plusieurs tâches intéressantes tel que:
- Tri de déchet
- Suivre un objet
- Exécuter une action après avoir reconnu un geste
- ...

De nombreuses implémentations et tutoriels sont disponibles à l'adresse suivante: http://www.yahboom.net/study/Dofbot-Pi .

L'objectif premier du stage est de reprendre des cas d'utilisation proposés par le bras robot et d'y remplacer petit à petit les briques logicielles (gérées par des réseaux de neurones artificiels) par des méthodes neuromorphiques inspirées de la biologie.

## 1. Prise en main

Le but de cette partie est de prendre en main et comprendre les technologies utilisées pendant le stage.

### 1.1. Prise en main du bras robot
- Suivre les tutoriels disponibles pour le bras robot : http://www.yahboom.net/study/Dofbot-Pi .

  - Tous les tutoriels ne sont pas forcément pertinents. Il ne faut pas hésiter à en éviter certains.
  - Noter les cas d'utilisation disponibles, notamment dans la rubrique "AI Vision Course".

### 1.2. Installation Intel Movidius
Un accélérateur neuronal "Intel Movidius Neural Compute Stick" est disponible pour accélérer l'inférence des réseaux de neurones utilisés (afin qu'il soit possible de faire du temps réel sur un Raspberry).

- Installer la Movidius sur le Raspberry en suivant le tutoriel sur le site de Intel https://www.intel.com/content/www/us/en/developer/articles/guide/raspberry-pi-4-and-intel-neural-compute-stick-2-setup.html
- Vérifier que cette installation fonctionne.
- Prendre un tutoriel du bras robot basé sur un réseau de neurones et y intégrer la Movidius.

### 1.3. Prise de contact : caméra DVS
- Suivre cette vidéo pour comprendre ce qu'est une caméra DVS et le domaine de l' "event-based computer vision" : https://www.youtube.com/watch?v=6Sn9-M7qXLk 


## Connexion bras robot
