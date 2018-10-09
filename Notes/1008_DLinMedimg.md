
# A Survey on Deep Learning in Medical Image Analysis

[MIA2017, review paper](https://arxiv.org/pdf/1702.05747.pdf)
The last update to the included papers was on Feb 1,2017.

## Deep Learning methods
As images in computer vision tend to be 2D natural images, networks developed in those scenarios do not directly leverage 3D information.

convolutional sparse auto-encoders(CSAE) (Kallenberg 2016). The major difference between CSAE and a classic CNN is the usage of unsupervised pre-training with sparse auto-encoders.

Chen 2015a, employed LSTM models to incorporate temporal information of consecutive sequence in US videos for fetal standard plane detection. Kong 2016 combined an LSTM-RNN with a CNN to detect the end-diastole and end-systole frames in cine-MRI of the heart.


## Deep Learning Uses in Medical Imaging
Table 1: overview of papers using DL for brain imaging analysis.
* disorder classification
* tissue segmentation
* lesion detection
* development prediction
* image construction
* others (p15)

Table 4: overview of papers using DL for chest CT image analysis. 
* nodule detection (p17)

### 1.classification
Three papers used an architecture leveraging the unique attributes of medical data: 
* 3D convolutions (*Hosseini 2016; Payan 2015*) to classify patients as having Alzheimer Disease.

* *Kawahara 2016b* applied a CNN-like architecture to a brain connectivity graph derived from DTI. 
	> developed several new layers which formed the basis of network, so-called edge-to-edge, edge-to-node, and node-to-graph layers. They predicted brain development and showed that they outperformed existing methods in assessing cognitive scores.


### 2.detection
object detection and object classification are mostly similar

still need to address issues specific to object detection: 
* **class imbalance/hard-negative mining** 
	+ to add insult to injury, usually the majority of the non-object samples are easy to discriminate, preventing the deep learning method to focus on the challenging samples. 
	+ *vanGrinsven 2016* proposed a selective data sampling: wrongly classified samples were fed back to the network more often to focus on challenging areas in retinal images. 
* **efficient pixel/voxel-wise processing** of images. 


### 3. segmentation
Challenges:
class imbalance,as most voxels/pixels in an image are from the non-diseased class.
	> challenge that lesion segmentation shares with object detection
	* 1. combat this by **adapting the loss function**: *Brosch 2016* defined it to be a weighted combination of the sensitivity and the specificity, with a larger weight for the specificity to make it less sensitive to the data imbalance. 
	* 2. balance the data set by performing **data augmentation on positive samples** *Kamnitsas 2017; Litjens 2016; Pereira 2016*.

annoted training data:
	* as the an notation burden to generate training data, **weakly-supervised deep learning** has been explored by *Hwang and Kim 2016*, who adopted such a strategy for the detection of nodules in chest radiographs and lesions in mammography.

appliations:
	* Dou 2016c used a 3D CNN to find micro-bleeds in brain MRI. 



### 4. registration
Registration (spatial alignment) of medical images is a common image analysis task in which a coordinate transform is calculated from one medical image to another. Often this is performed in an iterative framework where a specific type of (non-)parametric transformation is assumed and a predetermined metric is optimized. 

Broadly speaking, two strategies are prevalent in current literature: 
* using deep-learning networks to estimate a similarity measure for two images to drive an iterative optimization strategy
* directly predict transformation parameters using deep regression networks.
	+ Simonovsky 2016 used a similar strategy, albeit with CNNs, to estimate a similarity cost between two patches from differing modalities. 


### 5. image generation and enhancement

* *Li 2014* even showed that one can use these generated images in computer-aided diagnosis systems for Alzheimer’s disease when the original data is missing or not acquired.

* With multi-stream CNNs super-resolution images can be generated from multiple low-resolution inputs In *Oktay 2016*, multi-stream networks reconstructed high-resolution cardiac MRI from one or more low-resolution input MRI volumes.

* Not only can this strategy be used to infer missing spatial information, but can also be leveraged in other domains;for example, inferring advanced MRI diffusion parameters from limited data *Golkov 2016*. 


### 6. Combining Image Data with Reports
The combination of text reports and medical imagedata has led to two avenues of research: 
* (1) leveraging reports to improve image classification accuracy *Schlegl et al., 2015*
* (2) generating text reports from images *Kisilev 2016; Shin2015,2016a; Wang2016e*

	+ the first step towards leveraging reports was taken by *Schlegl 2015*, who argued that large amounts of annotated data may be difficult to acquire and proposed to add semantic descriptions from reports as labels. The system was trained on sets of images along with their textual descriptions and was taught to predict semantic class labels during test time. They showed that semantic information increases classification accuracy for a variety of pathologies in OCT images.

	+ *Shin 2015 and Wang 2016e* mined semantic interactions between radiology reports and images from a large data set. They employed latent Dirichlet allocation (LDA),a type of stochastic model that generates a distribution over a vocabulary of topics based on words in a document.  *Shin 2016a* proposed a system to generate descriptions from chest X-rays.



## Discussion

### key aspects of successful deep learning methods.
Groups and researchers that obtain good performance when applying deep learning algorithms often differentiate themselves in aspects outside of the deep network, like novel data preprocessing or augmentation techniques. 

1. the best performing method in the CAMELYON16-challenge improved significantly (AUC from 0.92 to 0.99) by adding a **stain normalization preprocessing** step to improve generalization without changing the CNN. 

2. **data augmentation strategies** make networks more robust, are essential to obtain good performance. An example is the elastic deformations that were applied in the original U-Net paper (Ronneberger 2015).

3. designing architectures **incorporating unique task-specific properties** can obtain better results than straightforward CNNs.

4. other, often underestimated,parts of network design are the network input size and receptive field. **Input sizes** should be selected considering for example the *required resolution and context to solve a problem*.

5. model hyperparameter optimization (e.g. learning rate, dropout rate), which can help squeeze out extra performance from a network.


### key aspects of successful deep learning methods. 
1. The main challenge is thus not the availability of image data itself, but the acquisition of relevant annotations/labeling for these images. Turning reports into accurate annotations or structured labels in an automated manner requires sophisticated text-mining methods.  With the introduction of **structured reporting** into several areas of medicine, extracting labels to data is expected to become easier in the future. 
	* leverage BI-RADS categorizations by radiologist to train deep networks *Kisilev 2016* or semantic descriptions in analyzing OCT *Schlegl 2015*. 
	* We expect the amount of research in optimally **leveraging free-text and structured reports for network training** to increase in the near future.
	
2. Even when data is annotated by domain expert, label noise can be a significant limiting factor in developing algorithms, whereas in computer vision the noise in the labeling of images is typically relatively low. 
	* To give an example, a widely used dataset for evaluating image analysis algorithms to detect nodules in lung CT is the LIDC-IDRI dataset (Armato 2011). In this dataset pulmonary nodules were annotated by four radiologists independently. Subsequently the readers reviewed each others annotations but no consensus was forced. 
	* It turned out that the number of nodules they did not **unanimously agreed** on to be a nodule, was three times larger than the number they did **fully agree on**.
	* Training a deep learning system on such data requires careful consideration of how to deal with noise and uncertainty in the reference standard. 

3.  Some researchers have specifically looked into tackling this imbalance by incorporating intelligence in the training process itself, by applying selective sampling *van Grinsven 2016* or hard negative mining *Wang 2016b*.

4. *Pereira 2016* performed a thorough evaluation of data augmentation strategies for brain lesion segmentation to combat class imbalance.

5. In medical image analysis useful information is not just contained within the images themselves. Physicians often leverage a wealth of data on patient history, age, demographics and others to arrive at better decisions.One of the challenges is to balance the number of imaging features in the deep learning network (typically thousands) with the number of clinical features (typically only a handful) to prevent the clinical features from being drowned out. 

6. One aspect to consider is that both *Esteva 2017* and *Gulshan 2016* focus on small 2D color image classification, which is relatively similar to the tasks that have been tackled in computer vision (ImageNet). This allows them to take advantage of well-explored network architectures like ResNet and VGG-Net which have shown to have excellent results in these tasks. 
	* However,there is no guarantee that these architectures are optimal in for example regressions/detection tasks. 


### Outlook 

**Unsupervised methods** are attractive and will still have a significant role to play as they 
	+ allow network training with the wealth of unlabeled data available in the world.  
	+ it is the analogue to human learning, which seems to be much more data efficient and also happens to some extent in an unsupervised manner; we can learn to recognize objects and structures without knowing the specific label. We only need very limited supervision to categorize these recognized objects into classes. 

Two novel unsupervised strategies that we expect to have an impact in medical imaging are variational auto-encoders (VAEs), introduced by Kingma 2013 and generative adversarial networks GAN, Goodfellow 2014

+ The former **merges variational Bayesian graphical models with neural networks** as encoders/decoders.
	> some groups have tried to **combine Bayesian statistics with deep networks to obtain true network uncertainty estimates**, *Kendall 2017*. This would allow physicians to assess when the network is giving unreliable predictions.

+ The latter uses two competing convolutional neural networks where one is generating artificial data samples and the other is discriminating artificial from real samples. 
	> Both have stochastic components and are generative networks. 

