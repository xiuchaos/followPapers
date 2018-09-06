

## AdaBN for domain adaptation

[Sep-05]
[Rrevisiting batch normalization for practical domain adaptation](https://openreview.net/pdf?id=BJuysoFeg) 

**Issues**

1. not well written, how to improve, especially abstract.

2. Fig 1, a clear illustration?

3. Fig 2, tSNE visualization of features, how to plot?


**Experiments**

1. Office-31 - standard benchmark for domain adaption
	> 4652 images in 31 classes from three domains: A, D, W

	* Table 1 - single source domain adaption results
	* Table 2 - multi-source domian adaption results

2. Caltech-Bing - larger domain adaption dataset
	> 30607 and 121730 images from two domains: C and B

	* Table 3 - single source domain adaption results

3. Analysis of feature divergence
	\begin{equation*}
	D(F_i /|| F_j) = KL(F_i || F_j) + KL(F_j || F_i) 
	KL(F_i || F_j) = log\frac\{sigma_j}{sigma_i} + \frac{(/sigma_i)^2 + (/mu_i - mu_j)^2}{2(/sigma_j)^2} - 1frac\2
	\end{equation*\

	* Fig 3 - how to compute distribution of the symmetric KL divergence

4. Sensitivity to target domain size
	
	* Fig 4 - accuracy vs. varing number of mini-batches for calculating the statistics of BN layers

5. Cloud detection in remote sensing images
	
	* Fig 5-6, Table 5 (baseline vs. AdaBN)


**think more ...**

For MICCAI, how to contribute more?

challengs:

* vgg, resNet, denseNet -> pretraind using ImageNet, need fine tune, huge data

* domain adaption -> small-dateset, light weight, easy to train

* key idea

* answer two questions: 

	+ Whether adaBN can improve DNN performance? how largely?
	+ how many samples were needed to get acceptable results? 


Experiments:

1. tSNE visualization: CT scans, MRI scans ...

2. performance 
              CNN  AlexNet ResNet DenseNet
	baseline  []
	adaBN     []

3. sample size vs. accuracy (baseline  vs. adaBN, respectively)






### How to type equations in jupyter

[tutorial](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Typesetting%20Equations.html)








