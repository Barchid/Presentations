# Slide 1
Hello! My name is Sami Barchid, and welcome to the presentation video of our paper Bina Rep Event Frames: a simple and effective representation for event-based cameras

# Slide 2
Let's get started by introducing our context.

# Slide 3
Firstly let's talk about the specific type of sensor we use in this work, which is called Event Cameras.
TODO

# Slide 4
Event-based sensors have a lot of advantages over conventional cameras.
--
Events are emitted only when there is movement in the scene, so there is no redundant data, which results in a sparser representation of the scene.
--
In addition, event cameras have very low latency, which 
--
prevents them from motion blur effects.
--
They also have a higher dynamic range.
--
And last but not least, these cameras are highly energy-efficient, which makes them perfect for edge devices.

# Slide 5
One challenge about event cameras is that conventional computer vision algorithms cannot be applied directly. Mostly because of the nature of the output, which is
--
1) composed of asynchronous events and no 2D frames, and
2) these events are binary changes and not intensity values of pixels.

# Slide 6
To deal with this problem, specific methods were designed, which we can define as "Event Representation" methods. We define them as follows:
An Event Representation method is a method 
--
that takes asynchronous events as input, and transforms them
--
into an alternative representation, such as a binary event frame in this example.

# Slide 9
This leads us to our objective. Our main goel in this work is to propose a new event representation method that produces 2D frames, in order to apply conventional vision algorithms with event sensors.

# Slide 10
To summarize, we propose two contributions:
--
Firstly, we propose bina-rep, an efficient, and simple approach to create frames from events. The created frames are sparse and more expressive than other popular methods.
--
Secondly, we propose a comparative study on event-based recognition against other state-of-the-art event representation methods. With this study, we report competitive results in pure accuracy as well as robustness against common corruptions.


# Slide 11 - Event Representation Methods
So what are the existing event representation methods in the state-of-the-art.

# Slide 12
We can divide most of these into three strategies: individual events, time surfaces and event frames.

# Slide 13
Individual events are basically methods that apply little to no transformations to the output events, and directly process them to make predictions. A typical example is spiking neural networks. This strategy is highly efficient and integrates perfectly with event sensors. However, such methods are sometimes limited in terms of performance due to their novelty

# Slide 14
Time surfaces focus on processing the temporal information of a stream of events, in order to expose it as a frame-like representation, so that conventional vision algorithms can be applied directly. These methods are known to be robust to noisy events.

# Slide 15
Finally, Event Frames is a strategy that works directly with events, by accumulating them to reconstruct 2D frames. This method is popular thanks to its intuitive use with standard algorithms.
--
However, they tend to lose the temporal information contained in an event sequence. But it does not prevent them from achieving top performance in general.

# Slide 16
As for our proposed approach, Bina-Rep, we can place it the event frame strategy. However, it is important to mention that it is capable of expressing temporal information without intensive addition computations.

# Slide 17 - Bina-Rep Event Frames
Now that we know about the existing works, let's talk about how to create Bina-Rep event frames.

# Slide 18
To create a bina-rep event frame, we need binary event frames, so let's talk about it first. 

An event cameras of resolution H times W
--
produces a stream of events e_i, that contains a pixel location (x,y), a timestamp and the sign of the polarity change (positive of negative).
--
--
by accumulating events during a certain time interval, a binary frame can easily be obtained.
--
--

# Slide 19
From a certain number N of consecutive binary frames, we can produce a bina-rep frame.
--
For each pixel location (x,y), we can see the N consecutive frames as a sequence of N consecutive binary digits.
--
We have 8 bits in this example
--
The simple intuition in Bina-Rep is that these N bits can be interpreted as an N-bit number instead of a sequence of bits.
--
In our example, this series of bits gives 108 as an unsigned int number.
--
With this change, a single bina-rep event frame is produced, where each pixel value depends on the order of arrival of the events in the sequence.

# Slide 20
Similarly to binary event frames, it is also possible to produce a sequence of T bina-rep frames. As a result, this representation method is sparser than standard event frames, since processing T bina-rep frames of N-bit numbers with a vision algorithm is the same as processing T \times N event frames.

# Slide 21
We can also discuss the specificities of bina-rep compared to similar representations. To do so, let's look at which information is represented for each one:
--
For binary event frame, the frame simply represent the presence or absence of events for each pixel.
--
For event histograms, the frame additionally represents the number of events that occured during the time interval.
-- 
For a bina-rep frame, these two information are also represented. In addition, the value of a pixel is influenced by the order of arrival of these events, which indirectly encodes temporal information.

# Slide 22
To conduct our experiments, a simple baseline for event-based object recogition has been designed.
--
It takes one or more 2D representations of events as input,
--
and processes them using a convolutional neural network
--
to predict the right category.

This model allows us to evaluate bina-rep and other event representation approaches.

# Slide 23 Experiments
Now let's discuss our experiments.

# Slide 24 
We use well-known datasets for event-based recognition, such as N-MNIST or DVS-Gesture. Naturally, all experiments are evaluated using the top-1 accuracy.

# Slide 25
Here are the implementation details of our experiments. 
--
Notably, every sequence are resized to a resolution of 224 \times 224. 
--
We use a ResNet-18 as the convolutional neural network used in our baseline.
--
As for our experiments using our bina-rep method, we use an 8-bit representation, which means that the hyper-parameter N = 8.

# Slide 26
Our first experiment aims to compare our bina-rep frames with similar event representation methods from the state-of-the-art. 
In addition to event binary frames and event histograms that were shown previously, Voxel-Grid was also studied. 
--
As for Bina-Rep, we tested two scenarios, which are one single frame and a sequence of 3 consecutive frames

# Slide 27
In general, we observe that Bina-Rep performs on par with other methods.
--
More precisely, it outperforms other methods on N-MNIST and shows the second-best performance on N-Cars and DVS-Gesture.
--
Bina-Rep also shows better performance on the multiple frames settings in general, which can be explained by a more precise decomposition of the original event sequence.
--
DVS-Gesture is an interesting case to analyze, because it has been shown in previous works that it can be considered as truly exposing temporal information contrary to the others. so It allows us to investigate the capacity of an event representation method to handle temporal information.

--
The reported results vary importantly across the compared approaches, which shows a significant difference in the capacity to handle temporal information.
--
Our Bina-Rep event frames with 3 frames achieves second-best accuracy, which highlights its efficiency to deal with temporal information.
--
It also achieves better performance than 10 Binary Event images, confirming the better expressivity and sparser representation.
--
Interestingly, Event Histogram outperforms other methods, suggesting that it can effectively deal with temporal information without specifically leveraging temporal information. 
--
Our single frame setting achieves poor performance. It can be explained by the fact that a single Bina-Rep event frame cannot integrate a high quantity of events from longer temporal sequences because it would quickly saturate the N -bit representation of pixels.

# Slide 28
We alo compare our CNN-based model coupled with bina-rep frames to results from state-of-the-art algorithms. Our model achieves competitive or even better performance, which shows the efficacy of our approach. However, it is important to mention that the models can differ importantly in complexity.
--
For instance, DiST use a ResNet-34 CNN, while HATS is based on a linear SVM.

# Slide 29
Our study also investigates the capacity of Bina-Rep to be robust against common corruptions in event cameras. We evaluate two simulated corruptions.
--
The first one is the Background Activity Noise, which occurs due to thermal noise and junction leakage current in event cameras. It results in additional events produced without any light change in the scene.
--
The second corruption is Occlusion. It simulates the presence of an object occluding the scene. To do so, events are dropped in an occlusion box area placed at the center of the scene.

# Slide 30
We design 5 levels of severity for each corruption, which gradually increases the strength of the corruption.

# Slide 31
We evaluate the robustness using the relative accuracy drop, on all severity levels. 
--
Basically, it gives a percentage on how much the accuracy score drops when testing our model on corrupted data compared to its performance on clean data.

# Slide 32
We report the results for all event representation methods, including ours. 
--
In general, we report the same evolution for all methods when the severity level increases,
--
aside from Voxel-Grid, that is more robust to background activity noise.
--
Our bina-rep frames are still competitive against other approaches. 
--
Bina-Rep also shows higher robustness on Background Activity, when increasing the number of frames. It can be explained by the fact that a single Bina-Rep frame saturates too much due to background events, showing that it needs more frames, or a higher value for the parameter N.

# Slide 33 - Conclusion
This finally leads us to the conclusion.

# Slide 34
In this work,
--
we propose Bina-Rep, a novel approach to represent events as 2D event frames. Bina-Rep frames express 3 information:
--
The presence/absence of events, the number of events that occured at the pixel level, and the order of arrival of these events.
--
Bina-Rep performs on par with state-of-the-art event representation, or even outperforms them. 
--
We also report competitive robustness against common corruptions of event cameras.

# Slide 35
You want to try Bina-Rep in future works or look at the code? You can, by using the Tonic Library! Tonic is a python library that is really useful when working on event-based vision, and integrates perfectly with other machine learning frameworks, like PyTorch.
--
A simple call to the transform function and you can evaluate Bina-Rep in your own work.

# Slide 36
That's it for this presentation. Thank you for watching this video and I wish you a good day.

# Slide 37
