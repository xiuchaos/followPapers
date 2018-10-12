# Speed/accuracy trade-offs for modern convolutional object detectors

[CVPR 2017 paper](http://openaccess.thecvf.com/content_cvpr_2017/papers/Huang_SpeedAccuracy_Trade-Offs_for_CVPR_2017_paper.pdf)

Main contributions:

* Fewer proposals for Faster R-CNN can speed it up significantly without a big loss in accuracy, making it competitive with its
faster cousins, SSD and RFCN.
	+  Inception Resnet, which has 35.4% mAP with 300 proposals can still have surprisingly high accuracy (29% mAP) with only 10 proposals. The sweet spot is probably at 50 proposals, where we are able to obtain 96% of the accuracy of using 300 proposals while reducing running time by a factor of 3. 

* SSD’s performance is less sensitive to the quality of the feature extractor than Faster R-CNN and R-FCN. 
	+ SSD is apparently unable to fully leverage the power of the ResNet and Inception ResNet feature extractors, it also suggests that using cheaper feature extractors does not hurt SSD too much.
	+  SSD models typically have (very) poor performance on small objects, they are competitive with Faster RCNN and R-FCN on large objects, even outperforming these meta-architectures for the faster and more lightweight feature extractors.


Resolution, Stride

* For Faster R-CNN and R-FCN, in addition to the default stride of 16, we also experiment with a (more expensive) **stride 8 Resnet-101** in which the conv4 1 block is additionally modified to have stride 1. 
Likewise, stride 16 and **stride 8 Inception Resnet network**. 

* Using stride 8 instead of 16 **improves the mAP by 5%**, but increased running time by a factor of 63%.

* Comparing detector performance on large objects against that on small objects, confirms that **high resolution models lead to significantly better mAP results on small objects (by a factor of 2 in many cases)** and somewhat better mAP results on large objects as well. 

*  Most notably,our model achieves a relative improvement of nearly 60%
on small object recall over the previous best result. 
