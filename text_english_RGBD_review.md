# Review on Indoor RGB-D Semantic Segmentation with Deep Convolutional Neural Networks ( DCNN )
Hello ! My name is Sami Barchid and in this video, I will present our short paper "Review on Indoor RGB-D Semantic Segmentation with Deep Convolutional Neural Networks" or DCNN for short.

## Objective
**FRAGMENT** The main objective in this review paper is to make a condensed introduction to RGB-D semantic segmentation so that the reader quickly understands the context of the field.

**FRAGMENT** I will present the current challenges encountered by state-of-the-art approaches and

**FRAGMENT** finally, we will talk about promising perspectives that may be interesting for future research works.


## Formulation
First and foremost, let's formulate the task of RGB-D semantic segmentation.

**IMAGE** Given an input RGB image I and its related depth map D

**IMAGE** the objective is to obtain an output semantic segmentation map S that provides a pixel-wise classification among C defined categories.

Because of the pixel-level accuracy of the predicted S, the semantic segmentation task requires to keep the spatial features in addition to the semantic information.

**IMAGE** To do so, the most popular approach currently is to use a fully convolutional neural network following the encoder-decoder paradigm.

**IMAGE** The first part of an encoder-decoder model is the encoder, which is a standard deep backbone network such as ResNet. It aims to extract features of high semantic values. However, during the process, the deep layers of the encoder reduce the feature maps resolution and, as a consequence, lose the spatial information required to peform an accurate prediction.

**IMAGE** That is why we need the decoder. It will progressively recover the lost spatial information and resolution by using skip connections with the low-layers of the encoder. These skip connection usually merge the feature maps of the encoder with the one of the decoder.

## Overview of Current Models
It has been shown in many works that depth provides a complementary geometric information that can benefit a standard RGB segmentation model.

**FRAGMENT** However, there is no established method to perfectly merge depth and RGB features together.

**FRAGMENT** State-of-the-art models vary depending on how depth features are incorporated.

**FRAGMENT** We identify three main strategies used in previous works.

## Depth as Input
The first and most popular one is Depth as Input. It is also the most intuitive. It basically uses the depth map as an additional input. Depth and RGB are fed into separated branches of the DCNN and the specific features are simply fused in a fusion part of the model. Consequently this strategy requires to duplicate several parts of the DCNN, leading to an increased computational and memory costs.

## Depth as Operation
The "Depth as Operation" strategy does not use depth as an additional input, but directly modify the operations performed in the CNN with respect to the depth. For example, the convolutional kernel is weighted according to a depth similarity term. This strategy does not need to duplicate some parts of the model, which reduces the computational complexity. Therefore it is quite intersting when the designed model has to run on low-cost devices.

## Depth as Prediction
As opposed to the two other strategies, "Depth as Prediction" only uses depth during training, because the objective of this strategy is to predict both the segmentation AND the depth maps. In this way, the model implicitly learns the geometric information from depth data by learning how to produce one. Because depth is not required during inference, a "Depth as Prediction" can run on cheaper RGB cameras.


## Existing Datasets
Now let's see the major datasets used in the field.

**IMAGE** We can divide the existing datasets on three different categories.

**IMAGE** The first one consists of NYUv2 and SUN RGBD.
**IMAGE** They are the oldest datasets in the list and are not perfectly suitable for data-hungry algorithms like deep learning.
**IMAGE** Indeed, NYUv2 and SUN-RGBD have a very small number of samples and 
**IMAGE** the images have a low resolution.

**IMAGE** The problems of this first category have been solved in 
**IMAGE** 2017 with the release of two more recent benchmarks, namely 2D-3D-S and Matterport3D.
**IMAGE** They are composed of a higher number of images with higher dimensions. Therefore these new datasets are much more adapted to current deep learning models.

**IMAGE** The last category contains SceneNet-RGBD and focus on synthetic data.

**IMAGE** In SceneNet RGB-D, 3D indoor scenes are generated automatically to create a huge quantity of annotated data. Using a synthetic dataset is a good option for pretraining in order to boost the performance. Thus this can be used in addition to the two other categories of datasets.

<!-- ## Depth Map Examples
On the other hand, the quality of depth sensors is another important feature to take into account.

**IMAGE** as you can see here, in old datasets like NYUv2, we observe many artifacts in non-smooth depth. These problems may lead to poor feature extraction by a deep learning model. 

**IMAGE** On the other hand, more recent datasets like 2D-3D-S were captured by recent depth sensors with better accuracy.

**IMAGE** However, the perfectly-annotated example of SceneNet RGB-D is unreachable in practice because of the synthetic nature of the data. -->

## Performance analysis
Now let's analyze the current state-of-the-art models by comparing the results reported in the litterature. Here, I will mainly focus on complexity comparison because it leads to the main challenges for future works but feel free to pause the video or read our paper to have the full analysis.

We evaluate the models using the following metrics :
**IMAGE** the mean intersection over union on NYUv2 and SUN-RGBD datasets.
**IMAGE** the inference speed in frame per second reported in the paper of ESANet.
**IMAGE** the backbone networks used in the encoder
**IMAGE** and finally we sort the models by the adopted strategy 
**IMAGE**
**IMAGE** Let's begin with depth as input, which composes the majority of current works.

**IMAGE** As said before, this strategy involves duplicated parts of a model, which can be seen here with the use of two heavy backbone networks.

**IMAGE**
**IMAGE** In comparison, depth as Operation models are much lighter, only needing one encoder part and still achieves competitive results.

**IMAGE** the least popular approach is depth as prediction, with only one model in state-of-the-art. We can notice an important improviement in term of performance but **IMAGE** this approach usually comes with the same drawbacks of heavy duplicated parts in the neural network's design.

An important observation here is that, in general, the backbone networks used are all deep ResNets, which leads to heavy models that require expensive hardware. 

## Challenges
So, now we know the main information about RGBD semantic segmentation, we can summarize the main challenges of the field ?

**FRAGMENT** firstly, we noticed the heaviness of the current models in State-of-the-art. These models use large and deep backbone encoders which make them unsuitable for use in edge devices.

**FRAGMENT** Secondly, despite the release of larger indoor RGBD datasets, current models are still evaluated on NYUv2 and SUN RGBD. We argue that these datasets limit the performance of modern RGBD semantic segmentation models due to the small number of samples.

**FRAGMENT** Nowadays, new models still adopt the Depth as Input strategy even if it comes with a high computational cost.

## Perspectives
These challenges create some interesting perspectives for future works.

**FRAGMENT** The most obvious improvement is to start evaluating future models on recent datasets like 2D-3D-S. We believe that the higher number of samples can increase the accuracy performance of future models.

**FRAGMENT** Working on Depth as Prediction and Depth as Operation strategies is an interesting direction to design innovative models and exploit the advantages of such strategies like reduced complexity.

**FRAGMENT** Finally, focusing on lightweight backbone networks would enable the creation of applications running on low-cost devices since existing models are still heavy.

## Thanks
This concludes my presentation. I hope it was interesting for you and I'll be glad to answer your questions. Thank your for listening.