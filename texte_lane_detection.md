# Projet étudiant : méthodes bio-inspirées pour la navigation robotique embarquée

## Résumé
Ce projet est destiné aux étudiants intéressés par l'IA et la vision artificielle dans le cadre de la navigation de robots et de voitures autonomes. L'objectif est de réaliser un algorithme de suivi de route pour un robot JetRacer AI en utilisant des méthodes bio-inspirées, plus efficaces en termes de consommation énergétique que les méthodes de Deep Learning communément utilisées. L'intérêt du projet est d'aider à valider l'utilisation de réseaux de neurones impulsionnels (basés sur le fonctionnement du cerveau) dans des applications de navigation robotique.

## Description détaillée

### Contexte
L'apparition et la popularisation des réseaux de neurones artificiels (deep learning) ont conduit à d'immenses progrès dans quasiment toutes les tâches d'intelligence artificielle (IA) et de vision par ordinateur. Si bien que, de nos jours, l'usage de ces méthodes est systématique.

Cependant, le deep learning implique un important coût en capacité de calcul/mémoire et, par conséquent, consomme beaucoup d'énergie. Pour illustrer, on peut mentionner l'entraînement d'une architecture de deep learning actuelle dont l'empreinte carbone est 5 fois plus élevée que celle d'une voiture américaine durant toute sa vie [1].

L'autre problème du deep learning est la nécessité de disposer d'une grande quantité de données annotées par un expert humain afin de pouvoir l'entraîner à faire de la reconnaissance. C'est pourquoi, la création de cette base de données d'apprentissage est un processus coûteux en temps et en argent.

Pour répondre à ces problèmes, une piste de solution envisagée est de s'inspirer du fonctionnement de notre cerveau, notamment grâce à l'utilisation de **réseaux de neurones impulsionnels** (ou "**SNN**", pour "Spiking Neural Network") [2]. Ils ne sont pas à confondre avec les populaires neurones artificiels. A l'instar de notre cerveau, les SNNs sont ultra-basse consommation [3] et peuvent apprendre des motifs sans avoir besoin d'annotations préalables [4]. Ces neurones impulsionnels restent, en IA et en vision artificielle, un domaine exploratoire dont les performances sont encore en-dessous de celles des méthodes populaires de deep learning [5]. 

Afin de développer ce domaine encore balbutiant, ce projet a pour but d'entraîner et de déployer un SNN pour réaliser une tâche de suivi de route par une voiture autonome. Cette tâche sera réalisée en "miniature" à l'aide d'un robot et d'une route installée en laboratoire (exemple de la tâche à réaliser ci-dessous).

[![JetRacer AI Example](http://img.youtube.com/vi/FcH7D-mSKU0/0.jpg)](http://www.youtube.com/watch?v=FcH7D-mSKU0 "Waveshare Jetracer Pro")

### Travail de l'étudiant
L'étudiant sera muni d'un robot JetRacer AI et d'une caméra DVS (fonctionnant à la manière d'une rétine biologique). Son travail comprendra les tâches suivantes :
1. Acquérir une base de données de navigation autonome à l'aide du robot JetRacer et de la caméra DVS sur la route en laboratoire.
2. Entraîner un SNN sur la base de données créée précédemment.
3. Évaluer les performances du SNN par rapport à celles d'un modèle standard de Deep Learning la tâche de navigation robotique définie.

## Contacts
- **José MENNESSON :** <jose.mennesson@univ-lille.fr>
- **Sami BARCHID :** <sami.barchid@univ-lille.fr>

## References
1. **Training a single AI model can emit as much carbon as five cars in their lifetimes**. Lien : https://www.technologyreview.com/2019/06/06/239031/training-a-single-ai-model-can-emit-as-much-carbon-as-five-cars-in-their-lifetimes/

2. W. Maass, “Networks of spiking neurons: the third generation of neural
network models,” Neural networks, vol. 10, no. 9, pp. 1659–1671, 1997.

3. M. Davies et al., "Loihi: A Neuromorphic Manycore Processor with On-Chip Learning," in IEEE Micro, vol. 38, no. 1, pp. 82-99, January/February 2018, doi: 10.1109/MM.2018.112130359.

4. P. Falez, P. Tirilly, I. M. Bilasco, P. Devienne, and P. Boulet, “Multi-
layered spiking neural network with target timestamp threshold adap-
tation and stdp,” in 2019 International Joint Conference on Neural
Networks (IJCNN). IEEE, 2019, pp. 1–8.

5. Taherkhani, Aboozar, et al. "A review of learning in biologically plausible spiking neural networks." Neural Networks 122 (2020): 253-272.