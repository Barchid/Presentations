# Text for video

## Title slide
Hello world. My name is Sami Barchid and in this video, I am going to present our paper at CBMI 2021 called : "Deep Spiking Convolutional Neural Network for Single Object Detection based on Deep Continuous Local Learning".

## Context"
First and foremost, let's discuss the context behind our work.

### Deep Learning
As you doubtless know, currently Deep Learning is kind of the go-to approach for almost every Computer Vision or Machine learning task, achieving impressive state-of-the-art results in most cases.

However, such approach require heavy computational and memory, leading to a high energy consumption. To the point that nowadays training state-of-the-art architectures can even emit as much carbon as five cars in their lifetime.  

### Spiking Neural Networks
To counter this problem, many works focus on Spiking Neural Networks (or SNN for short). 

It is well-known as the third generation of AI. SNNs consist of Spiking neurons, which are strongly inspired by the neurons of our brain. 

They can be implemented on neuromorphic hardware, which are extremely energy efficient.

Therefore SNNs can be a good candidate to solve the problem.

### Challenges
For now, SNNs performance are still far behind Artificial Neural Networks. This can be explained by the non-differentiablity of spiking neurons, which prevent the use of the standard backpropagation algorithm that unleashed the potential of ANNs.

## SNN for Computer Vision
Knowing this, we can recap the state of SNNs in computer vision.

### Overall Process

### Definition
TODO

### Image Neural Coding
Since SNNs work with spikes instead of numerical values, the first thing to do when working with static images is to convert the numerical values of pixels into spikes. 

This conversion is known as Neural Coding and there are several different methods.

Here, i'm showing you the frequecy coding (or rate-coding) where a pixel value is represented by a frequency of spikes. It means that a high value involves a high number of spikes and a low numerical value involves a low frequency.

Among popular neural coding there is also the temporal coding, where values are represented by a single spike that appear early for high values and late for low values.


### Running an SNN
To run an SNN, we can consider neuromorphic hardware that I talked about earlier. However, neuromorphic hardware are still limited in term of neuron capacity and they are not easily available.

That's why it is much more convenient to simulate SNNs on common synchronous architectures like CPU or GPU. This kind of simulation requires to discretize the continuous dynamics of spiking neurons into a certain number of T successive timesteps.

### Learning Approaches
To train an SNNs, there is basically three principal strategies :

The first and oldest approach is to use unsupervised bio-inspired learning rules observed in our brain such as STDP. These approaches are local, which means that it can be implemented on neuromorphic hardware and, of course, do not require any annotation.

The second one focus on converting a trained ANN into a functional SNN. This approach achieves the best performance and there already exist converted SNNs that can deal with modern computer vision tasks. However, the SNN is not trained directly and training the ANN remains energy intensive. I tend to consider this approach as an ANN optimization rather than an SNN training algorithm.

The third strategy is to adapt the original backpropagation to enable supervised learning on SNNs. This is a recent approach that promising results currently. That's why we focus on this approach for our contribution.

### State of SNN in Computer Vision
As we review the recent works on SNNs for Computer Vision, we notice that most papers still focus on simple recognition tasks such as digit recognition and mostly use shallow networks composed of 2 or 3 layers. Consequently we observe a lack of works towards complex vision tasks like object detection.

Our contribution aims at tackling these problems. Our objective is to exploit recent supervised learning approaches to perform complex vision tasks with SNNs and see if these approaches are currently relevant.

## Deep Continuous Local Learning
Now let's focus on the supervised learning model we employ. We use Deep Continuous Local Learning (or DECOLLE, for short). It is a state-of-the-art approach based on surrogate gradient learning for SNNs.

### Overview
We are not going to extensively describe the method here because it is not the scope of this paper. Instead we simply recap the specific properties.

So DECOLLE is an online surrogate gradient learning method, which means that synaptic weights are updated continuously after each timesteps. The learning rule is local, and we've seen that localality is an important feature to be implementable on neuromorphic hardware. Another significant advantage is the low memory complexity required to simulate DECOLLE on GPU, which enable the simulation of deep spiking networks.

### Illustration
The overall architecture of a DECOLLE SNN can be described like this. 

In DECOLLE, 