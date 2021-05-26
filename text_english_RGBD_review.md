# Review on Indoor RGB-D Semantic Segmentation with Deep Convolutional Neural Networks ( DCNN )
Hello ! My name is Sami Barchid and in this video, I will present our short paper "Review on Indoor RGB-D Semantic Segmentation with Deep Convolutional Neural Networks" or DCNN for short.

## Objective
**FRAGMENT** The main objective in this review paper is to give the reader a condensed introduction to RGB-D semantic segmentation.

**FRAGMENT** I will present the current challenges encountered by state-of-the-art approaches and

**FRAGMENT** finally, we will talk about promising perspectives that may be interesting for future research works.


## Formulation
First and foremost, let's formulate the task of RGB-D semantic segmentation.

**IMAGE** Given an input RGB image and its related depth map

**IMAGE** the objective is to obtain a semantic segmentation map that provides a pixel-wise classification among a defined number of categories.

**IMAGE** To do so, the most popular approach currently is to use an encoder-decoder network.

**IMAGE** It is composed of the encoder, which is a standard deep backbone network such as ResNet. An encoder extracts feature maps but progressively lose spatial information during the process. 

**IMAGE** To solve this problem, the decoder recovers low-level features information by merging the encoder's feature maps **IMAGE** using skip connections.

## Overview of Current Models
It has been shown in many works that depth provides a complementary geometric information that can benefit a standard RGB segmentation model.

**FRAGMENT** However, there is no established method to perfectly merge depth and RGB features together.

**FRAGMENT** State-of-the-art models vary depending on how depth features are incorporated.

**FRAGMENT** We identify three main strategies used in previous works.

## Depth as Input
The most popular one is Depth as Input. It basically uses the depth map as an additional input, and processes both modalities in separated parts before a fusion step. Consequently this strategy requires to duplicate several parts of the DCNN, leading to an increased computational and memory costs.

## Depth as Operation
The "Depth as Operation" strategy directly modifies the operations performed in the CNN with respect to the depth. Without duplicated parts, this strategy reduces the computational complexity. Therefore it is quite intersting when the designed model has to run on low-cost devices.

## Depth as Prediction
"Depth as Prediction" only uses depth during training, because the objective of this strategy is to predict both segmentation AND depth maps. In this way, the model implicitly learns the geometric information from depth data. Consequently, "Depth as Prediction" can run on cheaper RGB cameras.


## Existing Datasets
Now let's see the major datasets used in the field.

**IMAGE** We can divide the existing datasets on three different categories.

**IMAGE** The first one consists of NYUv2 and SUN RGBD.
**IMAGE** They are the oldest datasets in the list and are not perfectly suitable for data-hungry algorithms like deep learning.
**IMAGE** Indeed, NYUv2 and SUN-RGBD have a very small number of samples and 
**IMAGE** the images have a low resolution.

**IMAGE** The problems of this first category have been solved in 
**IMAGE** 2017 with the release of two more recent benchmarks, namely 2D-3D-S and Matterport3D.
**IMAGE** They are composed of a higher number of high resolution images, making them more adapted to current deep learning models.

**IMAGE** The last category focus on synthetic data.

**IMAGE** In SceneNet RGB-D, 3D indoor scenes are generated automatically to create a huge quantity of annotated data. Using a synthetic dataset is a good option for pretraining in order to boost the performance. It is a good choice to pretrain a model on SceneNet instead of the usual ImageNet.

<!-- ## Depth Map Examples
On the other hand, the quality of depth sensors is another important feature to take into account.

**IMAGE** as you can see here, in old datasets like NYUv2, we observe many artifacts in non-smooth depth. These problems may lead to poor feature extraction by a deep learning model. 

**IMAGE** On the other hand, more recent datasets like 2D-3D-S were captured by recent depth sensors with better accuracy.

**IMAGE** However, the perfectly-annotated example of SceneNet RGB-D is unreachable in practice because of the synthetic nature of the data. -->

## Performance analysis
Now let's analyze the state-of-the-art models. Here, I will mainly focus on complexity comparison because it leads to the main challenges for future works but feel free to read our paper to have the full analysis.

We evaluate the models using 
**IMAGE** the mean intersection over union on NYUv2 and SUN-RGBD datasets,
**IMAGE** a frame per second metric, 
**IMAGE** the backbone network used
**IMAGE** and we sort them by the adopted strategy.
**IMAGE**
**IMAGE** DaI strategy is by far the most popular strategy,
**IMAGE** but is a heavy approach due to duplicated parts of the model, notably the encoder part.

**IMAGE**
**IMAGE** In comparison, depth as Operation models are much lighter, only needing one encoder part and still achieves competitive results.

**IMAGE** the least popular approach is depth as prediction, but is promising according to the accuracy results.
**IMAGE** However, this approach usually comes with the same drawbacks of heavy duplicated parts in the neural network's design.

**IMAGE** An important observation here is that the backbone networks used are all deep ResNets, which leads to heavy models that require expensive hardware. 

## Challenges
So let's summarize the main challenges of the field

**FRAGMENT** firstly, we noticed the heaviness of the current models in State-of-the-art. These models use large and deep backbone encoders which make them unsuitable for use in edge devices.

**FRAGMENT** Despite the release of larger indoor RGBD datasets, current models are still evaluated on NYUv2 and SUN RGBD. We argue that these datasets limit the performance of modern RGBD semantic segmentation models due to the small number of samples.

**FRAGMENT** Nowadays, new models still adopt the Depth as Input strategy even if it comes with a high computational cost.

## Perspectives
These challenges create some interesting perspectives for future works.

**FRAGMENT** starting to evaluate future models on recent datasets can increase the performance of future models, due to the higher number of samples.

**FRAGMENT** Working on DaP and DaO strategies is an interesting direction to exploit the advantages of such strategies like reduced complexity.

**FRAGMENT** Finally, focusing on lightweight backbone networks would enable the creation of applications running on low-cost devices since existing models are still heavy.

## Thanks
This concludes my presentation. I hope it was interesting for you and I'll be glad to answer your questions. Thank your for listening.