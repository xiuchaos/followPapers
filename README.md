## Papers

	> Sep 03, after one month's hands-on training (pytorch, kaggle lungCT), it is time to keep up with research trends.

#### MICCAI 2017
https://link.springer.com/content/pdf/bfm%3A978-3-319-66182-7%2F1.pdf


#### CVPR 2017
http://openaccess.thecvf.com/CVPR2017.py

http://www.cvpapers.com/cvpr2017.html



### Human-like Concept and Task Learning

**Aim** to develop AI capcities that can learn concept and tasks, as well as understand physical environments through instruction and interaction with human co-workers. 

	> the developed AI system can learn concepts and new physical models implicitly by grounding language/vocabulary to visual representation through human instruction and demenstration. Furthermore, the algorithm can be generalised to a large category of tasks, and human feedback will also be used to further improve the learning efficientcy and task execution speed during the human-robot callaboration.

* Generalize the learning outcome to similar tasks

* Implicitly learn the new tasks

* Efficiently execute the tasks in new or uncertain scenarios and environments.


[Sep-03]
[AAAI2017 - implicit learning, concept grounding](http://www.aaai.org/Conferences/AAAI/2017/PreliminaryPapers/22-Alomari-14913.pdf) 

**how to ground language to concepts in vision?**

Ground words to visual features given raw linguistic and visual inputs.

> the recorded videos and commands are used as input data to the system to learn two key components (i) the world's visual representation(actions, spatial-relations, object properties) (ii) the probabilistic grammer rules.

*previous*:they assumed the shapes, sptial-relations and actions representations are known to the robot beforehand, also they rely on a mannually constructed parse to extract the verbs and nouns from natural language.

*now* we extract visual representations automatically by clustering features from video clips, and we learn grammer rules from the raw natural language data.
	> each linguistic description is represented as a sequence of tokens(words), and each video as a sequence of spatial-temporal acyclic graphs(STDAG). The principle for learning is to seek frequent co-occurence of n-grams and sub-grpahs or consective sequences derived from the corresponding video clips.  To relate n-grams to fragments of the visual representation of the world. 

*key* The spatio-temporal graphs (STDAG) representation is also a key contribution of the paper acting as an intermediary representation between the continuous perceptual space, and the purely symbolic lingusitic structures.


Sep-04
[learn concepts by grounding language/vocabulary to visual representation](https://papers.nips.cc/paper/7017-deep-reinforcement-learning-from-human-preferences.pdf)







