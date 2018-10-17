
# concept grounding

Oct.13, google "concept grounding   ICML NIPS"

## Papers
[CVPR 2018- Unsupervised Textual Grounding: Linking Words to Image Concepts](https://arxiv.org/pdf/1803.11185.pdf)

[CVPR 2018- Finding “It”: Weakly-Supervised Reference-Aware Visual Grounding in
Instructional Videos](http://vision.stanford.edu/pdf/huang-buch-2018cvpr.pdf)

[CVPR 2018- Finding beans in burgers:Deep semantic-visual embedding with localization](http://openaccess.thecvf.com/content_cvpr_2018/papers/Engilberge_Finding_Beans_in_CVPR_2018_paper.pdf)

[NIPS 2017- Interpretable and Globally Optimal Prediction for Textual Grounding using Image Concepts](https://papers.nips.cc/paper/6787-interpretable-and-globally-optimal-prediction-for-textual-grounding-using-image-concepts.pdf)

[ICML 2018- Interpretability Beyond Feature Attribution:Quantitative Testing with Concept Activation Vectors (TCAV)](https://arxiv.org/pdf/1711.11279.pdf)

[ICML 2012 - A Joint Model of Language and Perception for Grounded Attribute Learning](https://homes.cs.washington.edu/~lsz/papers/mfzbf-icml12.pdf)

[2018 Multimodal Grounding for Language Processing](http://aclweb.org/anthology/C18-1197)

## NIPS Workshops
* [Visually Grounded Interaction and Language 2017](https://nips2017vigil.github.io/)
* [Visually Grounded Interaction and Language 2018](https://nips2018vigil.github.io/)

## ICML 2018 Notes
https://david-abel.github.io/blog/posts/misc/icml_2018.pdf

## Blogs 
Felix Hill@deepmind https://fh295.github.io/
David Abel@brown    https://david-abel.github.io/
Devi Parikh@FAIR    https://www.cc.gatech.edu/~parikh/
Douwe Kiela@FAIR    https://douwekiela.github.io/
ChenYu @Indiana 

## The grounding problem
**The dominant paradigm** learning models from text-only corpora/ image-only data. 
Meaningless symbols (i.e. words) cannot be grounded in anything but other meaningless symbols.
This approach is founded on a distributional notion of semantics, i.e. that the "meaning" of a word is based only on its relationship to other words.

Humans, on the other hand, acquire and learn language by communicating about and interacting with the visual environment. This behavior provides the necessary grounding of physical concepts in words. 
To this end, several recent works study **grounded language-learning tasks**, e.g. 

* grounding in natural images 
	+ ReferIt[1] GuessWhat?![2] 
	+ Visual Question Answering[3,4] Visual Dialog[5] 
	+ Captioning[6]

* embodied agents performing interactive tasks 
	+ [18,22,23,24,26]

* grounding in a physically-simulated environment 
	+ DeepMind Lab [7], Baidu XWorld [8], OpenAI Universe [9]
	+ House3D [20], Matterport3D [21], GIBSON [24], MINOS [25], AI2-THOR [19], StreetLearn [17]
	+ We believe this line of research is more suited for **human-machine collaboration** than unimodal approaches that ignore the grounding aspect.

* grounding use deep learning 
	+ DL capable of learning high-level semantics from low-level sensory data in CV and language. 
	+ DL as an efficient tool for **fusing different modalities into a single representation** [3,4]. 

* grounding scenerios: interact with an external environment in goal-oriented tasks
	+ As grounded language acquisition requires to interact with an external environment, reinforcement learning provides an elegant framework to cover the planning aspect of visually grounded dialogue as well as other goal-oriented tasks. 
	+ recent effort on combining DL and RL in various grounding scenarios [10,11,12].

* grounded language-learning
> Research in understanding human behavior provides yet another perspective in building models capable of grounded language-learning. 
	+ In neuroscience, recent progress in fMRI enables us to create a semantic atlas of the cerebral cortex [13] or to learn to decode semantic information from visual input [14]. 

	+ fMRI has enabled to better understand the interleave between language, vision and other modalities [15,16] suggesting that the **brains shares neural representation of concepts across vision and language**. Differently, developmental cognitive scientists have also argued that children acquiring various words is closely linked to them learning the underlying concept in the real world [12].

	+ In one study, psychologists followed blind children and show that they are not linguistically deficient. Despite the lack of visual stimuli, blind children manage to use visual concepts such as colors or visual verbs ("see" or "look") [15] and circumvent their visual impairment through unique strategies [17].


This workshop aims to gather people from backgrounds in machine learning, computer vision, natural language, neuroscience, and psychology, who are excited about this space of **grounding and interaction**, and are willing to share ideas from their work and perspectives on future directions.

### References
#### grounding in natural images 
1. Kazemzadeh "ReferIt Game: Referring to Objects in Photographs of Natural Scenes". EMNLP. 2014.
2. de Vries   "GuessWhat?! Visual Object Discovery through Multi-modal Dialogue". CVPR. 2017.
3. Antol "VQA: Visual Question Answering". ICCV. 2015.
4. Malinowski,"Ask Your Neurons: A Neural-based Approach to Answering Questions about Images". ICCV 2015.
5. Das  "Visual Dialog". CVPR. 2017.
6. Rohrbach "Generating Descriptions with Grounded and Co-Referenced People". CVPR. 2017.

#### grounding in a physically-simulated environment 
7. Beattie, Charles, et. al. "DeepMind Lab". 2016.
8. Yu "A Deep Compositional Framework for Human-like Language Acquisition in Virtual Environment". 2017.
9. OpenAI. "Universe". 2016.

19. E Kolve "AI2-THOR: An Interactive 3D Environment for Visual AI." arXiv, 2017.
20. Yi Wu   "House3D: A Rich and Realistic 3D Environment." arXiv, 2017.
21. Angel Chang "Matterport3D: Learning from RGB-D Data in Indoor Environments." arXiv, 2017.
25. Manolis "MINOS: Multimodal indoor simulator for navigation in complex environments." arXiv, 2017.


#### grounding scenerios and RL 
10. Strub "End-to-end Optimization of Goal-driven and Visually Grounded Dialogue Systems". IJCAI. 2017.
11. Das "Learning Cooperative Visual Dialog Agents with Deep Reinforcement Learning". ICCV. 2017.
12. Hermann  "Grounded Language Learning in a Simulated 3D World". arXiv 2017.

#### embodied agents performing interactive tasks 
18. Piotr Mirowski "Learning to Navigate in Cities Without a Map." arXiv 2018.
22. Abhishek Das "Embodied Question Answering." CVPR 2018.
23. Peter Anderson "Vision-and-Language Navigation: Interpreting visually-grounded navigation instructions in real environments." CVPR, 2018.
24. Fei Xia  "Gibson Env: Real-World Perception for Embodied Agents." CVPR, 2018.
26. Daniel  "IQA: Visual Question Answering in Interactive Environments." CVPR, 2018.


#### progress in cognitive neuroscience and psychology
13. Huth "Natural Speech Reveals the Semantic Maps that Tile Human Cerebral Cortex". Nature 2016.
14. Huth "Decoding the Semantic Content of Natural Movies from Human Brain Activity". Frontiers in systems neuroscience 10. 2016.

15. Landau "Language and Experience: Evidence from the Blind Child". 2009.
16. Harnad "The Symbol Grounding Problem". Physica D. 1990.
17. Perez-Pereira  "Language Development and Social Interaction in Blind Children". Psychology 2013.

Huth Nature 16 paper - https://www.youtube.com/watch?v=x3kWmmPvDf4

