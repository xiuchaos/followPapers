# Deep learning for generic object detection: a survey

[Deep learning for generic object detection: a survey](https://arxiv.org/pdf/1809.02165v1.pdf)

## Resources - Tutorial
[CVPR17 Tutorial: Deep Learning for Objects and Scenes ](http://deeplearning.csail.mit.edu/)

+ [Part 1](https://www.youtube.com/watch?v=jHv37mKAhV4)
+ [Part 2](https://www.youtube.com/watch?v=pK6XAk95kUY)

[CVPR18 Tutorial: Visual Recognition and Beyond](http://cvpr2018.thecvf.com/program/tutorials)
+ [Part 1](https://www.youtube.com/watch?v=m60uJVIE4Ys)


## 4. Fundamental subproblems

### 4.1 DCNN based Object Representation

#### Popular CNN Architectures
Pretrained CNNs without finetuning were explored for object classification and detection.
features performance is a function of the extracted layer for AlexNet pretrained on ImageNet, FC6 / FC7 / Pool5 are in descending order of detection accuracy
+ [DeCAF: A Deep Convolutional Activation Feature for Generic Visual Recognition](https://arxiv.org/pdf/1310.1531.pdf)

The relationship or similarity between the source and target datasets plays a critical role, for example that ImageNet based CNN features show better performance on object related image datasets.
+ [Learning Deep Features for Discriminative Localization])http://cnnlocalization.csail.mit.edu/Zhou_Learning_Deep_Features_CVPR_2016_paper.pdf)

#### Methods For Improving Object Representation
So if a target object is small it requires fine detail information in earlier layers and may very well disappear at later layers, in principle make small object detection very challenging, for which tricks such
as dilated convolutions [229] or atrous convolution [40, 27] have been proposed.

multiscale object detection:
* Detecting with combined features of multiple CNN layers [75,103, 10];
* Detecting at multiple CNN layers;
* Combinations of the above two methods [58, 130, 190, 104,246, 239].
* Model Geometric Transformations [118].

**Hands On**
1. FPN shows significant improvement as a generic feature extractor in several applications including object detection[130, 131] and instance segmentation [80], e.g. using FPN in a basic Faster RCNN detector.

2. STDN [246] used DenseNet [94] to combine features of different layers and designed a scale transfer module to obtain feature maps with different resolutions. The scale transfer module can be directly embedded into DenseNet with little additional cost.


### 4.2 Context Modeling
There is strong psychological evidence [13, 9] that context plays an essential role in human object recognition. proper modeling of context helps object detection and recognition [203,155, 27, 26, 47, 59], especially when object appearance features are insufficient because of small object size, occlusion, or poor image quality. Many different types of context have been discussed,in particular see surveys [47, 59]

#### Global context
Global context refers to **image or scene level context**, can serve as cues for object detection (e.g., a bedroom will predict the presence of a bed). 

* DeepIDNet [160]
	+ the image classification scores were used as contextual features, and concatenated with the object detection scores to improve detection results.

* ION [10]
	+ use spatial Recurrent Neural Networks (RNNs) to explore contextual information across the entire image. 
 
* SegDeepM [250]
	+ proposed a MRF model that scores appearance as well as context for each detection, and allows each candidate box to select a segment and score the agreement between them. 

* In [188], semantic segmentation was used as a form of contextual priming.


#### Local context 
Local context[240, 59, 171] considers **local surroundings** in object relations, the interactions between an object and its surrounding area.  In general, modeling object relations is challenging, requiring reasoning about bounding boxes of different classes,locations, scales etc. In the deep learning era, research that explicitly models object relations is quite limited.

* Spatial Memory Network (SMN) [29]
	[ICCV 2017](http://openaccess.thecvf.com/content_ICCV_2017/papers/Chen_Spatial_Memory_for_ICCV_2017_paper.pdf) [read note](https://www.cnblogs.com/daihengchen/p/6869452.html)

	+ In SMN, spatial memory essentially **assembles object instances back into a pseudo image representation** that is easy to be fed into another CNN for object relations reasoning, leading to a new sequential reasoning architecture where image and memory are processed in parallel to obtain detections which further update memory. 

* Object Relation Network [90]
	+ Inspired by the recent success of attention modules in natural language processing field [211], Hu et al. [90] proposed a lightweight ORN, which processes a set of objects simultaneously through interaction between their appearance feature and geometry. It does not require additional supervision and is easy to embed in existing networks. It has been shown to be effective in improving object recognition and duplicate removal steps in modern object detection pipelines, giving rise to the first fully end-to-end object detector. 

* Structure Inference Network (SIN) [137].
	+ SIN [137] considered two kinds of context including scene contextual information and object relationships within a single image. It formulates object detection as a problem of **graph structure inference**, where given an image the objects are treated as nodes in a graph and relationships between objects are modeled as edges in such graph.
	[CVPR2018 -SIN](http://openaccess.thecvf.com/content_cvpr_2018/CameraReady/2114.pdf)



### 4.3 Detection Proposal Methods
We refer interested readers to the recent surveys [86, 23] which provides an in-depth analysis of many classical **object proposal algorithms and their impact on detection performance**. 

[ICCV 2017 - Soft Proposal Networks for Weakly Supervised Object Localization](http://openaccess.thecvf.com/content_ICCV_2017/papers/Zhu_Soft_Proposal_Networks_ICCV_2017_paper.pdf)

#### Bounding Box Proposal Methods
* Adjacency and Zoom Network (AZNet)
	+ Instead of **fixing a priori a set of anchors** as MultiBox and RPN, [141] proposed to generate anchor locations by using a recursive search strategy which can **adaptively guide computational resources to focus on** subregions likely to contain objects. 

	+ Starting with the whole image, all regions visited during the search process serve as anchors. For any anchor region encountered during the search procedure, a scalar zoom indicator is used to decide whether to further partition the region, and a set of bounding boxes with objectness scores are computed with a deep network called Adjacency and Zoom Network (AZNet). AZNet extends RPN by adding a branch to compute the scalar zoom indicator in parallel with the existing branch.

* DeepProposal[61] 
	+ generates object proposals by using a cascade of multiple convolutional features, building an inverse cascade to select the most promising object locations and to refine boxes in a coarse to fine manner. 

* HyperNet 
	+ An improved variant of RPN, HyperNet[103] designs Hyper Features which aggregate multilayer convolutional features and shares them both in generating proposals and detecting objects via an end to end joint training strategy. 

* Deepbox [111]
	+ proposed a light weight CNN to learn to rerank proposals generated by EdgeBox,

* DeNet [208] 
	introduces a bounding box corner estimation to predict object proposals efficiently to replace RPN in a Faster RCNN style two stage detector.

#### Object Segment Proposal Methods
segment proposals are likely to correspond to objects and are more informative than bounding box proposals, and take a step further towards object instance segmentation [74, 39, 126]. 

* DeepMask
	+ A pioneering work[167], segment proposals are learned directly from raw image data with a deep network. Sharing similarities with RPN, after a number of shared convolutional layers DeepMask splits the network into two branches to predict a class agnostic mask and an associated objectness score.

* SharpMask [168]
	+ augmenting the DeepMask architecture with a refinement module. With the feedforward network with a top-down refinement process, SharpMask can efficiently integrate the spatially rich information from early features with the strong semantic information encoded in later layers to generate high fidelity object masks.

* InstanceFCN [38] 
	+ the two branches are fully convolutional, where one branch generates a small set of instance sensitive score maps, followed by an assembling module that outputs instances, and the other branch for predicting the objectness score

* FastMask [89]
	+ efficiently generate instance segment proposals in a oneshot manner similar to SSD [136]. Sliding windows extracted densely from multiscale convolutional feature maps were input to a scale-tolerant attentional head module to predict segmen-tation masks and objectness scores. 
	+ FastMask is claimed to run at 13 FPS on a 800 × 600 resolution image with a slight trade off in average recall.

* ScaleNet [170 -ICCV 17] 
	+  extend by explicitly adding a scale prediction phase. That is, ScaleNet estimates the distribution of object scales for an input image, upon which SharpMask searches the input image at the scales predicted by ScaleNet and outputs instance segment proposals. 
	+  outperformed the previous state of the art on super-market datasets by a large margin.

### 4.4 other issues
* image resolution
	+ It has been shown [96, 136] that image resolution has a considerable impact on detection accuracy[96-Speed/accuracy trade-offs for modern convolutional object detectors](http://openaccess.thecvf.com/content_cvpr_2017/papers/Huang_SpeedAccuracy_Trade-Offs_for_CVPR_2017_paper.pdf)

* scale invariance problem
	+ advanced and efficient data argumentation methods SNIP [192] and SNIPER [193] to illustrate the scale invariance problem
	+ SNIPER [193] is an approach proposed for efficient multiscale training. It only processes context regions around ground truth objects at the appropriate scale instead of processing a whole image pyramid. 

* class imbalance problem
	+ [189] explored approaches to handle the extreme foreground-background class imbalance issue [131].
	+ [216] proposed to train an adversarial network to generate examples with occlusions and deformations that are difficult for the object detector to recognize. There are some works focusing on developing better methods for nonmaximum suppression[16, 87, 207].


## Future work - directions 

### Compact and Efficient Deep-CNN Features
* growing interest in designing compact and lightweight networks
	+ Learning the number of neurons in deep networks. *NIPS 2016*
	+ Towards accurate binary convolutional neural network. *NIPS 2017*
	+ NISP: Pruning networks using neuron importance score propagation. *CVPR 2018*

* network compression and acceleration
	+ Binarized neural networks. *NIPS 2016*
	+ Pruning filters for efficient convnets. *ICLR 2017*
	+ Mimicking very efficient network for object detection. *CVPR 2017*

* network interpretation and understanding
	+ Visualizing deep convolutional neural networks using natural preimages *2016*
	+ Methods for interpreting and understanding deep neural networks. *2018*


### Context Reasoning 
> How to efficiently and effectively **incorporate contextual information** remains to be explored, ideally guided by how humans are quickly able to guide their attention to objects of interest in natural scenes.

* very limited progress in exploiting contextual information
	+ Spatial memory for context reasoning in object detection *ICCV 2017*
	+ [Object detection via a multiregion and semantic segmentation aware CNN model *ICCV 2015*](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Gidaris_Object_Detection_via_ICCV_2015_paper.pdf)
	+ [Relation networks for object detection *CVPR 2018*](https://github.com/msracver/Relation-Networks-for-Object-Detection)



### Weakly Superised or Unsupervised learning
Fully supervised learning has serious limitations: **not scalable in the absence of fully labelled training data**, therefore it is valuable to study how the power of CNNs can be leveraged in weakly supervised or unsupervised detection

+ Weakly supervised deep detection networks. *CVPR 2016*
+ [Weakly supervised cascaded convolutional networks *CVPR 2017*](https://www.csee.umbc.edu/~hpirsiav/papers/cascade_cvpr17.pdf)
+ Weakly supervised image annotation and segmentation with objects and attributes *TPAMI 2017*


### 3D Object Detection
The depth modality can be employed to help object detection and recognition, however there is only limited work in this direction 

+ 3d object proposals for accurate object class detection. *NIPS 2015*
+ Beyond PASCAL: A benchmark for 3D object detection in the wild.




