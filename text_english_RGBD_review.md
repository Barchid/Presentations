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


## Existing Benchmarks
Now let's see the major benchmarks used in the field.

**IMAGE** The useful information here is the year of publication, the number of images in the dataset, the usual class number and, of cours, the dimension of the images.

**IMAGE** The most popular (and oldest) one is NYUv2. It has been created quite long ago now, which explains the small number of images. The usual setting

## Depth Map Examples
On the other hand, the quality of depth sensors is another important feature to take into account. Compared to the current depth sensor’s performance, the depth maps collected by less recent datasets are not as accurate. As seen in the NYUv2 example, the early depth sensors provide non-smooth depth maps with many artifacts, as opposed to the more recent 2D-3D-S example. The perfectly-annotated example of SceneNet RGB-D is unreachable in practice because of the synthetic nature of the data. Therefore it can lead to poor feature extraction.

