# Projet étudiant en vision artificielle : améliorer les performances des réseaux de neurones impulsionnels par la simulation des saccades occulaires

## Contexte
Ce projet est destiné aux étudiants en informatique de L3, intéressés par l'IA, et la vision artificielle. Nous cherchons un étudiant dans le but de travailler au sein de l'équipe FoX du laboratoire CRIStAL (Université de Lille). Ce travail s'inscrit dans la direction de recherche de FoX consacrée aux approches bio-inspirées pour la reconnaissance de forme.

## Objectif du projet

L'apparition et la popularisation des réseaux de neurones artificiels (deep learning) ont conduit à d'immenses progrès dans quasiment toutes les tâches d'intelligence artificielle (IA) et de vision par ordinateur. Si bien que, de nos jours, l'usage de ces méthodes est systématique.

Cependant, le deep learning implique un important coût en capacité de calcul/mémoire et, par conséquent, consomme beaucoup d'énergie. Pour illustrer, on peut mentionner l'entraînement d'une architecture de deep learning actuelle dont l'empreinte carbone est 5 fois plus élevée que celle d'une voiture américaine durant toute sa vie [1].

L'autre problème du deep learning est la nécessité de disposer d'une grande quantité de données annotées par un expert humain afin de pouvoir l'entraîner à faire de la reconnaissance. C'est pourquoi, la création de cette base de données d'apprentissage est un processus coûteux en temps et en argent.

Pour répondre à ces problèmes, une piste de solution envisagée est de s'inspirer du fonctionnement de notre cerveau, notamment grâce à l'utilisation de **réseaux de neurones impulsionnels** (ou "**SNN**", pour "Spiking Neural Network") [2]. Ils ne sont pas à confondre avec les populaires neurones artificiels. A l'instar de notre cerveau, les SNNs sont ultra-basse consommation [3] et peuvent apprendre des motifs sans avoir besoin d'annotations préalables [4]. Ces neurones impulsionnels restent, en IA et en vision artificielle, un domaine exploratoire dont les performances sont encore en-dessous de celles des méthodes populaires de deep learning [5].

On constate plusieurs verrous scientifiques limitant l'apprentissage des SNNs. On peut notamment citer : la perte d'activité neuronale dans les réseaux profonds [6], l'encodage neuronal des images numériques [7], ...

L'objectif de ce projet est de collaborer avec les membres de l'équipe dans le développement des réseaux de neurones impulsionnels pour la vision par ordinateur afin de lever ces verrous scientifiques.

## Description du projet

Le projet s'inspire du système des saccades occulaires que nous retrouvons habituellement dans le système visuel d'une grande partie des êtres-vivant. Il s'agit de rapides mouvements inconscients de l'oeil qui pourraient jouer un rôle important dans les systèmes visuels biologiques [8]. L'idée est de simuler ces mouvements de saccades occulaires afin d'encoder les informations visuelles fournies à un SNN, permettant à celui-ci d'améliorer grandement son apprentissage.

Le travail de l'étudiant sera d'étudier et d'implémenter ce mouvement de saccade occulaire pour qu'il puisse être exploité dans les modèles de SNN développés par au sein de FoX. Après développement de ce système de saccade, il est également possible de participer aux expériences de ces saccades employées avec les neurones impulsionnels.

## Profil du candidat
Le candidat est un étudiant en 3ème année de licence informatique, intéressé par la recherche et désireux de travailler dans un projet au sein d'un laboratoire.

Concernant les compétences techniques, il est impératif que le candidat ait une bonne maîtrise en programmation orienté objet avec le langage Python. Des notions en traitement d'image et machine learning sont un plus.


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

6. Falez, Pierre. Improving spiking neural networks trained with spike timing dependent plasticity for image recognition. Diss. Université de Lille, 2019.

7. Rufin Van Rullen, Simon J. Thorpe; Rate Coding Versus Temporal Order Coding: What the Retinal Ganglion Cells Tell the Visual Cortex. Neural Comput 2001; 13 (6): 1255–1283.

8. Masquelier, T., Portelli, G. & Kornprobst, P. Microsaccades enable efficient synchrony-based coding in the retina: a simulation study. Sci Rep 6, 24086 (2016).