

# Multi-Armed Bandit to select training set from big medical data

**Paper**
[MICCAI2017 MABS to select training set](https://arxiv.org/abs/1705.08111)


**Author**
[Benjamin Gutierrez Becker](http://wachinger.devweb.mwn.de/people/benjamin-gutierrez-becker/), [Christian Wachinger](http://people.csail.mit.edu/wachinger/), [Artificial Intelligence in Medical Imaging Lab](http://wachinger.devweb.mwn.de/)

**Related**
[Neuroimage 2018 - Gaussian Process Uncertainty in Age Estimation as a Measure of Brain Abnormality](https://arxiv.org/pdf/1804.01296.pdf)


## Notes: ML language

#### Training data
Select a subset of the data for training that is most relevant for a specific task.
>an adequte training set is becoming more important to address the heterogeneity of datesets. Simply including all the data does not only *incur* high processing costs but can even harm the prediction.We hypothesize that given this partitioning, where exist clusters that contain more relevant samples than others for a specific task. Intuitively, we would like to draw samples h from clusters with a higher probability of returning a relevant sample.

We formulate the smart and efficient selection of a training dataset from a big medical image data as a multi-armed bandit problem.
>related to **Active learning** which aims to select samples to be labled out of a pool of unlabeled data.


#### Testing scenarios
1. create a testing dataset by randomly selecting subsets from all the datasets. 
> acapable of selecting samples that will create a model that can *generalize well to a heterogeneous population*.

2. the testing dataset correponds to a single dataset.
> show that the sample selection permits tailoring the training dataset to specific target dataset. our method can be deployed when samples have to be selected according to a specific population and prediction task.

3. we demonstrated that our technique can either be used to build a general model or to adapt to a specific target dataset, depending on the compostion of the test dataset.


#### Reinforcement learning

We formulate the selection of the samples to be included in a training set as reinformcement learning, *where a trade-off must be reached between the **exploration** of new sources of data and the **exploitation** of sources that have been shown to lead to informative data points in the past*.

We model this as a multi-armed bandit problem solved with Thompson sampling, where each arm of the bandit corresponds to a cluster of samples generated using meta information.



## Techicial Notes - Thompson Sampling

#### Bernoulli distribution and conjugate distribution

[Bernoulli distribution](https://en.wikipedia.org/wiki/Bernoulli_distribution)
> the discrete probability distribution of a random variable which takes the value 1 with probability p and the value 0 with probability

Bernoulli distribution:
* the probability distribution of any single experiment that asks a yes–no question

* a special case of **binomial distribution** where a single experiment/trial is conducted (n=1). 
> If $$ X_{1},\dots ,X_{n}$$ are independent, identically distributed (i.i.d.) random variables, all Bernoulli distributed with success probability p, then
$$ Y=\sum_{k=1}^{n}X_k \sim \mathrm{B}(n,p) $$ (binomial distribution).The Bernoulli distribution is simply $$ \mathrm {B}(1,p) $$

* a special case of **two-point distribution**, for which the outcome need not be a bit, i.e., the two possible outcomes need not be 0 and 1.

* **Beta distribution** is the conjugate prior of the Bernoulli distribution.


[Beta distribution](https://en.wikipedia.org/wiki/Beta_distribution)
* In Bayesian inference, the beta distribution is the **conjugate prior** probability distribution for the Bernoulli, binomial, negative binomial and geometric distributions. 

>  For example, the beta distribution can be used in Bayesian analysis to describe initial knowledge concerning probability of success $$p$$ such as the probability that a space vehicle will successfully complete a specified mission. The beta distribution is a suitable model for the random behavior of percentages and proportions.

**Probability density function**
The probability density function (pdf) of the beta distribution, for 0 ≤ x ≤ 1, and shape parameters α, β > 0, is a power function of the variable x and of its reflection (1 − x) as follows.

*x is a realization* an observed value, that actually occurred,of a random process X.

In the following, a random variable X beta-distributed with parameters α and β will be denoted by: $$ X \sim \operatorname {Beta} (\alpha ,\beta )} $$ w


## Think More





##### **Related**
[Neuroimage 2018 - Gaussian Process Uncertainty in Age Estimation as a Measure of Brain Abnormality](https://arxiv.org/pdf/1804.01296.pdf)

* Multivariate regression models for age estimation are a powerful tool for assessing abnormal brain morphology associated to neuropathology. Age prediction models are built on cohorts of healthy subjects and are built to reflect normal aging patterns. The application of these multivariate models to diseased subjects usually results in high prediction errors, under the hypothesis that neuropathology presents a similar degenerative pattern as that of accelerated aging.

* In this work, we propose an alternative to the idea that pathology follows a similar trajectory than normal aging. Instead, we propose the use of metrics which measure deviations from the mean aging trajectory.

* Our approach assumes that pathologic brain patterns are different to those of normal aging. We present results for subjects with autism, mild cognitive impairment and Alzheimer’s disease to highlight the versatility of the approach to different diseases and age ranges. We evaluate volume, thickness, and VBM features for quantifying brain morphology.