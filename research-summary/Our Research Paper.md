
# TODO

- [ ] Abstract
- [ ] Introduction
- [ ] Relevant work
	- [ ] Few shot learning
	- [ ] Loss function
	- [ ] Embeding function
	- [ ] DNN 
	- [ ] CNN
- [ ] Implementation
	- [ ] Proposed Model
	- [ ] Dataset
	- [ ] Data preprocessing
	- [ ] Evaluation metrics
	- [ ] Experiments
- [ ] Results and Comparision
- [ ] Discussion
- [ ] Conclusion and future works
- [ ] References


# Introduction
Intrusion detection systems can be defined as a group of hardware and software
mechanisms that tries to prevent actions leading to compromise confidentiality,
integrity, and availability of network resources. [1] In other words, an Intrusion
Detection System (IDS) is a monitoring system that detects suspicious activities
and generates alerts when they are detected. IDS is a well-known term in the do-
main of Network and Information Security. It’s one of the important components
of the Network and Information Security infrastructure. IDS plays an important
role in securing IT infrastructure. Intrusion detection systems capture and ana-
lyze the network traffic to detect suspicious activity.

IDS mainly works on two different approaches. One is misuse/signature based intrusion detection system which is based on pattern-matching techniques to find a known attack; these are also known as Knowledge-based Detection or Misuse Detection. In other words, when an intrusion signature matches with the signature of a previous intrusion that already exists in the signature database, an alarm signal is triggered. [2] And another is anomaly based intrusion detection system which detects the abnormal behavior of system and alarm signal is triggered. In AIDS, a normal model of the behavior of a computer system is created using machine learning, statistical-based or knowledge-based methods. [2] Any significant deviation between the observed behavior and the model is regarded as an anomaly, which can be interpreted as an intrusion. AIDS can be classified into a number of categories based on the method used for training, for instance, statistical-based, knowledge-based and machine learning based. The main advantage of AIDS is the ability to identify zero-day attacks due to the fact that recognizing abnormal user activity do not rely on a signature database

> HIDS NIDS ???

Few-Shot Learning (FSL) is a novel Deep Learning method that aims to learn from a small amount of labeled data. FSL can rapidly generalize to new tasks containing only a few samples with supervised information. This technique is mostly utilized in the field of computer vision, where employing an object categorization model still gives appropriate results even without having several training samples. FSL can be an effective method to solve the problem of the small amount of network detection data. [3]

Prototypical Network, is a FSL method which is based on the idea that there exist an embedding in which samples from each class cluster around a single prototypical representation which is simply the mean of the individual samples. Here, Embeddings of both Query set and Support Set are calculated. Classification is then performed for an embedded query point by simply finding the nearest class prototype using distance functions. [4] 

Embeddings are dense numerical representations of real-world objects and relationships, expressed as a vector. The vector space quantifies the semantic similarity between categories. Embedding vectors that are close to each other are considered similar. Embeddings are passed to other models. 
The goal of embedding function is to extract essential features, reduce the dimension of data, and retain all the information of the original data to the maximum extent. Various embedding function/models can be used to extract features. Two of them are DNN and CNN.

The main contributions of this proposed method are as follows:
- [ ] TODO


# Implementation

### Training Procedure : Training algorithm
##### Requirement



# References
[1] Intrusion Detection Systems: Principles And Perspectives | Mohammed Jamal al-mansor, Kok Beng Gan | 2018
[2] Survey of intrusion detection systems: techniques, datasets and challenges | Ansam Khraisat, Iqbal Gondal, Peter Vamplew and Joarder Kamruzzaman | 2019
[3] An Intrusion Detection Method Using Few-Shot Learning | yingwei yu and naizheng bian | 2020
[4] Prototypical Networks for Few-shot Learning | Jake Snell, Kevin Swersky, Richard S. Zemel | 2017

