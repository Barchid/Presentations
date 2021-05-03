# Text for video

## Title slide
Hello. My name is Sami Barchid and in this video, I am going to present our paper at CBMI 2021 called : "Deep Spiking Convolutional Neural Network for Single Object Localization based on Deep Continuous Local Learning".

## Context"
First and foremost, let's discuss the context behind our work.

### Deep Learning
As you doubtless know, currently Deep Learning is kind of the go-to approach for almost every Computer Vision or Machine learning task, achieving impressive state-of-the-art results in most cases.

However, such approach require heavy computational and memory capacity, leading to a high energy consumption. To the point that nowadays training state-of-the-art architectures can even emit as much carbon as five cars in their lifetime.  

### Spiking Neural Networks
To counter this problem, many works focus on Spiking Neural Networks (or SNN for short). 

It is well-known as the third generation of AI. SNNs consist of Spiking neurons, which are strongly inspired by the neurons of our brain. 

They can be implemented on neuromorphic hardware, which are extremely energy efficient.

Therefore SNNs can be a good candidate to solve the problem.

### Challenges
For now, SNNs performance are still far behind Artificial Neural Networks. This can be explained by the non-differentiablity of spiking neurons, which prevent the use of the standard backpropagation algorithm that unleashed the potential of ANNs.

## SNN for Computer Vision
Knowing this, we can recap the state of SNNs in computer vision.

### Definition
An SNN is composed of spiking neurons. These neurons communicate asynchronously through discrete events known as spikes. There are numerous models to design the behaviour of spiking neurons, but one of the most popular and simplest model is the Leaky Integrate-and-Fire model, or LIF for short.

A LIF neuron has a membrane potential V that is excited when it receives input spikes from the presynaptic neurons. When the membrane is not excited, it slowly returns to its resting potential, which is equal to 0 here.

Once the membrane potential exceeds a defined threshold theta, the LIF neuron emits a spike to its post-synaptic neurons and the membrane potential is reset to its resting potential.

Similarly to ANNs, the presynaptic neurons are weighted by synaptic weights and training an SNN essentially means to change their values to produce a desired prediction.

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

So DECOLLE is an online surrogate gradient learning method, which means that synaptic weights are updated continuously after each timesteps. The learning rule is local, and we've seen that locality is an important feature to be implementable on neuromorphic hardware. Another significant advantage is the low memory complexity required to simulate DECOLLE on GPU, which enables the simulation of deep spiking networks.

### Illustration
The overall architecture of a DECOLLE SNN can be described like this. 

Similarly to ANNs, an SNN consists of successive layers like fully connected or convolutional layers for example. And, like ANNs, these successive layers create deep hierarchical representations that increase the expressivity of the model. 

In DECOLLE, a readout layer initialized with fixed random weights is attached to each layer of spiking neurons. At each timestep, a readout layer multiplies the neural activation of its related LIF layer with its fixed random weights. The output of a readout layer is a prediction that is used to solve the targeted task and compute a local error. Consequently, each layer minimizes its own local error function. LIF layers build on the features of the previous layers trained with their own local error function. The layers indirectly learn features that are useful for their successors.

## Contributions
Now, let's see how we can deal with computer vision problems with SNNs on DECOLLE.

### Formulation
The vision task is formulated as follows : given a grayscale image I that contains stricly one object, the objective is to predict the bounding box B that surrounds this object. To do so, we first encode the image I using rate coding. The resulting input spikes are fed in s(I), a deep convolutional spiking neural network (or DCSNN for short).

### Readout Layers
As said previously, in DECOLLE, a readout layer is attached to each spiking layer. In our model, these readout layers are used to predict the targeted bounding box. Which means that a DCSNN s(I) composed of L layers outputs L bounding box predictions. 

### Architecture
The architecture of our proposed DCSNN follows the encoder-decoder paradigm, which is quite common in the deep learning community. It consists of an encoder composed of 3 convolutional LIF layers. The role of the encoder is to increase the semantic information of the extracted spiking feature maps while decreasing the spatial information. The lost spatial information is then recovered in a 3-layered decoder, where the output spikes from the encoder’s layers are passed to the decoder through residual connections. The residual connections are essentially addition operations between two spiking feature maps.

Note that, for readability, the readout layers are not shown in this illustration.

### Output Conversion Strategy
A major issue in our model is to obtain the final bounding box prediction. Indeed, an output prediction is produced for each of the T timesteps. in addition, each readout layer produces a prediction. To summarize, it means that we have T predictions for each of the L layers in our model. So, the problem is : which prediction should we choose ?

### Output Conversion Strategy
Firstly, we know that the neural coding used is the rate coding. which means the rate-coded image delivers its total information after all the T timesteps. Consequently, a bounding box prediction produced in the last timestep may contain the maximal information.

Secondly, because of the hierarchical representation of succesive layers in a deep neural network, we assume that the last layer contains the best prediction of our model.

Consequently, the final prediction of our model is the prediction of the last readout layer obtained at the last timestep.


## Experiments
To validate our model and, more generally, to validate the use of SNNs for modern computer vision tasks, we conducted an experimental proof-of-concept.

### OXFORD-IIIT-PET dataset
We used the OXFORD-IIIT-Pet dataset, which is composed of color images containing stricly one cat or one dog and an associated segmentation mask.

For our experiment, we modified the dataset to obtain grayscale images and used the segmentation mask to obtain the bounding box coordinates.

### Results
In the end, our model achieves promising results, with 63.2% in mean intersection over Union (which is a standard metric to evaluate the performance in object localization).

We also analyzed the results qualitatively. Here, I show you representative samples. In most cases, objects are well localized with 55 to 75% mIoU. However, we observed that small objects are poorly localized, with less than 15% mIoU.

### Hypotheses
To explain these poor performance with small objects, we have two hypotheses :

The first one is a data imabalance problem, which is unfortunately common in machine learning. Indeed, most images in OXFORD-IIIT-PET are close-up pictures of cats and dogs. Consequently, our model does not generalize to the rare, small objects.

The second one is related to the output conversion strategy. Even if taking the last prediction of the last layer is justified, we suspect a loss of information with this strategy.


## Conclusion and perspectives
So, let's recap and dicuss the presented work.

### Conclusion
We designed a single object localization model using Deep spiking neural network.

The promising proof-of-concept results show the applicability of supervised learning SNN for more complex vision tasks. To the best of our knowledge, this is the first work on supervised SNNs for complex vision task. Finally, we think that this work can be a first step towards modern computer vision solutions using SNNs.

### Perspectives
As a first step, this work can pave the way to many perspectives. Even though our DCSNN is used for static images, it can be intersting to exploit event-based cameras instead of static images. Switching to this sensor would lead to a sparser and fully spike-based computer vision solution.

Another interesting perspective is simply to increase the complexity of the vision task, with a multiple object localization. Or, more generally, diversify our future works towards other popular vision tasks such as semantic segmentation or object detection. 

## Thanks
This concludes my presentation. I hope it was interesting for you and I'll be glad to answer your questions. Thank your for listening.