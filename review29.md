### Summary

The paper introduces a new event representation technique called "Compact SpatioTemporal Representation" (CSTR) that encodes spatial, temporal, and frequency information from an event stream into a frame-like representation. Compared to other methods (event frame, event count, recent timestamp, and recent timestamp + event count), CSTR provides a more comprehensive representation. It computes the average timestamps per polarity and the number of events per spatial index, resulting in a tensor of shape (3xHxW) that can be used directly by popular computer vision models like ResNets and MobileNets.

The study evaluates CSTR in the context of event-based object recognition. Experiments are conducted on popular datasets, including N-Cars, N-MNIST, N-Caltech101, and CIFAR10-DVS, where the proposed CSTR method is compared against the other formulated representations. The results indicate that CSTR outperforms the other techniques in terms of accuracy. Additionally, the impact of random data augmentation on training efficiency is investigated, and the positive effects on performance are observed. Ultimately, the reported results of CSTR are on par with or exceed those of previous state-of-the-art works.

### Strengths

1. The paper is well-written, very clear and is overall a pleasure to read. Figures and tables are well presented, and perfectly support the ideas expressed by the text.
2. The core idea of the paper (i.e., a new event representations approach) is an interesting topic, since new techniques that can encode various information about an event stream is always welcomed to assist future works on event-based vision systems. In addition, CSTR combines several information about .
3. Concerning the experiments, the choice of the authors to report accuracy scores of several CNN architectures using a given event representation is particularly appreciated, since previous works (e.g., [a]) tend to only use one model to validate their performance.

### Weaknesses

1. The experiments conducted on "Section 4.3 - Effects of random augmentations" are not interesting. What we learn from them is not very new: applying data augmentation during training improves the performance. As shown in Table 2, CSTR benefits more from these augmentations compared to other representations, and the difference is small but significant. However, there is no explanation or hypothesis to justify this fact.
2. The authors do not compare CSTR against similar event representation techniques from the state-of-the-art. I can mention DiST from [b] (ICCV 2021, so the paper is not recent and thus should be taken into account), an event representation technique very similar to CSTR since it incorporates recent timestamps and event counts in an image-like representation as well. While comparing against well-established event representations is a good thing, it feels not fair to exclude more recent works, especially when they are as relevant.
3. The limitations of the experiments should be acknowledged in the text about the comparison of event representations: the settings of the comparison are not fair for certain event representation techniques. For instance, event frames tend to "saturate" when integrating a lot of events (as illustrated in Figure 2). This means it works better when integrating less events. Let me tell an alternative story: event frames work better without needing a large number of events, and thus is more efficient. In my opinion, it should be clearly stated that the investigated representations are compared on their capacity to handle "long" event sequences (to some extent), which limits the impact of the scope of the experiments.
4. The paper only investigates event-based object recognition datasets, where there is no actual "temporal information" (i.e., the captured object does not change over time). Since the paper claims that "CSTR captures spatioTEMPORAL information" (in the Abstract, L21-23), I expect the method to be evaluated on datasets that expose such challenging spatiotemporal information (e.g. event-based action recognition datasets like DVSGesture [c] or HAR-DVS [d]).
5. Despite being well-written, the text contains important flaws that do not facilitate the reading experience. Some examples are given below:
   - Fundamental references are missing: in "Section 3.1 - Image-like representations", the event representations are not referenced, despite being described as "common and foundational" (in L353-354). Since they are fundamental in this work, they must be referenced.
   - Important claims are not supported by references: for instance, in L136-139, the authors state that "complex representations have been developed for specific frameworks, limiting their scalability and applicability in different applications". There is no reference to illustrate this strong statement. How can the reader be aware of the importance of this problem or whether it exist at all? I strongly recommend the authors to ensure that their statements are well referenced when they expose such information, especially about prior works.
   - Misleading statements: in L146-149, the authors say that "Our proposed representation is SCALABLE and can be easily integrated into existing frameworks, enabling more effective use in a VARIETY OF APPLICATIONS". Firstly, it is not shown in the paper that CSTR is particularly scalable (and the notion is quite obscure in the first place). Secondly, the paper does not demonstrate that CSTR is more effective in a variety of applications, since it is only evaluated on object recognition. The fact that CSTR representations can be directly fed into popular CNN architectures does not necessarily make CSTR effective on various applications. This information should be supported by experiments.
   - Misleading statements: in L686-689 (Section 4.3 - "Effects of random augmentations"), the authors say that the aim of the experiments on data augmentation is to "investigate whether introducing variations in the training data can help the fine-tuned models become MORE ROBUST to different variations ...". However, the paper does not investigates the robustness of the models, only their performance on the test set. More specifically, evaluating the robustness of a model refers to evaluating how the performance remains unchanged after applying corruptions on the data [e].

References:
[b]: Kim, Junho, et al. "N-imagenet: Towards robust, fine-grained object recognition with event cameras." Proceedings of the IEEE/CVF International Conference on Computer Vision. 2021. 
[c]: Amir, Arnon, et al. "A low power, fully event-based gesture recognition system." Proceedings of the IEEE conference on computer vision and pattern recognition. 2017.
[d]: Wang, Xiao, et al. "HARDVS: Revisiting Human Activity Recognition with Dynamic Vision Sensors." arXiv preprint arXiv:2211.09648 (2022).
[e]: Hendrycks, Dan, and Thomas Dietterich. "Benchmarking neural network robustness to common corruptions and perturbations." arXiv preprint arXiv:1903.12261 (2019).


### Rating and Justifications

Weak Reject

The paper is well-written, CSTR is a simple yet effective technique for event representation, and the results of the experiments are very competitive, showing the efficiency of the method. Overall, this is an interesting paper, but it lacks important investigations to completely support the claims made by the authors. Firstly, the authors claim that CSTR is effective at handling spatiotemporal information, yet the experiments only show performance on event-based object recognition datasets where there is no actual temporal information. Secondly, the conclusions drawn by the experiments on random augmentations are redundant: this is not surprising that data augmentations increase the performance. In addition, the superior improvements observed with CSTR are not explained in the paper. Thirdly, important prior works (e.g. DiST [b]) that are very similar to CSTR are not investigated in this work. Comparisons with well-established methods are good, but comparisons with relevant and more advanced representations should be expected. Finally, the text should contain important references when comparing fundamental works, or strong claims.

### conseils

Here are minor issues (typos, etc) that can help the authors:

- Equation 1: events are represented by their pixel location and polarity, but the timestamp (t_i) should be added.
- In L126, "learning based CONVECTIONAL neural network (CNN)" -> I think the authors meant "convolutional" instead of "convectional".
- In L372-373, the authors introduce the math variable "$EF_{bin}$", but this variable is not used anywhere. 
- In the "Training parameters", the employed frameworks (e.g. pytorch) are not mentioned. Similarly, the hardware setup is not mentioned (typically, the employed GPUs).
- In general, some titles of sections/subsections are not capitalized. E.g. Section 3.1.