
# TODO

- [ ] Abstract
- [ ] Introduction
- [ ] Relevant work
	- [x] Few shot learning
	- [ ] Loss function
	- [ ] Embeding function
	- [ ] DNN 
	- [ ] CNN
- [ ] Implementation
	- [ ] Proposed Model
		- [x] Algorithm
	- [x] Dataset
	- [ ] Data preprocessing
		- [x] IGTD
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
##### Requirement / Input:
Training set $D={(x_1, y_1), (x_2, y_2), ... , (x_N, y_N)}$ where $y \in {1, 2, ... k}$ and x is images which is obtained from pre-processing i.e. convering 1D into 2D image
##### Ensure / Output:
The loss $J$ calculation for a training episode.
- for $i$ in $(1, 2, ..., k)$ do
	- $s\ <-\ RandomSample(D, N_s)\ where\ y = i,\ and\ N_s\ is\ number\ of\ samples(shot)$ {Select support set}
	- $q\ <-\ RandomSample(D\\S_k, N_q) where y=i,\ and\ N_q\ is\ number of\ query$ {Select query set}
	- $S_k\ <-\ append(s)$ {Append all support set into one variable}
	- $Q_k\ <-\ append(q)$ {Append all query set into one variable}
 - end for
 - $J\ <-\ 0$ {Initialize loss}
 - for $i$ in $(1, 2, ..., k)$ do
	 - for $(x_s, x_q)$ in ($S_k, Q_k$) where $y=i$
		 - $x'_s = encoder(x_s)$ {Calculate embeding of support set}
		 - $x'_q = encoder(x_q)$ {Calculate embeding of query set}
		 - $J\ <-\ J + dist(x'_s, x'_q)$ {Update loss}
	 - end for
 - end for
 Where,
 dist is ecludian or manhattan [Need to write mathematical expression]

## Few shot learning
Few-Shot Learning (FSL) is a novel Deep Learning method that aims to learn from
a small amount of labeled data. FSL can rapidly generalize to new tasks containing
only a few samples with supervised information. This technique is mostly utilized
in the field of computer vision, where employing an object categorization model
still gives appropriate results even without having several training samples.

The critical idea of the FSL model is based on prior knowledge to constrain the complexity of hypothesis space $H$ and reduce its sample complexity $S$ [3]. Here, the hypothesis space $H$ is the embedding. The learned embeddings is mapped to each class embeddings which is taken from the support set. The simillarity between those two embeddings are calculated.

Typlically in Fewshot learning N-way K-shot learning scheme is used. “N-way” indicates
that there are “N” numbers of novel categories on which a pre-trained model needs to generalize over. “K-shot” defines the number of labeled samples available in the the support set for each of the “N” novel classes. The support set consists of a few labeled samples per novel category of data, which a pre-trained model will use to generalize on the new classes. The set of provided examples for comparing the metric is called the support set $S$. This support set includes KN labeled samples.
$$ S = (x_1 , y_1 ), (x_2 , y_2 ), .....(x_N , y_N )\  where\ y_i \in {1, 2, ... k} $$
The query set consists of the samples from the new and old categories of data on which the model needs to generalize using previous knowledge and information gained from the support set.


## Evaluation Metrices
Do binary??
How multiclass

## Datasets
1. CICIDS-2017 dataset
CICIDS2017 dataset contains benign and the most common attacks, which resembles the true-real world data. The dataset was collected by Canadian Institute of Cybersecurity (CIC), University of Brunswick (UNB). The dataset was created using CICFlowMeter with labeled flow based on the time stamp, source and destination IPs, source and destination ports, protocols and attack. The implemented attacks include Brute Force FTP, Brute Force SSH, DoS, Heartbleed, Web Attack, Infiltration, Botnet and DDoS.

The dataset consistes of abstract behavior of 25 users based on the HTTP, HTTPS, FTP, SSH, and email protocols. The dataset consists of 77 features and a label. Table below presents a summary of overall traffic features of each network connection vector within the dataset.

Furthermore, the dataset contains 14 attacks and normal traffic making 15 categories. Following are the categories and the number of each categories:
| Label             | Number of instance   | Percentage |
|-------------------|----------------------|------------|
| Benign            | 2273097              | 80.3004%   |
| DoS Hulk          | 161185               | 6.0532%    |
| Port Scan         | 111128               | 4.1733%    |
| DDoS              | 89792                | 3.3720%    |
| DoS Golden Eye    | 7192                 | 0.2700%    |
| FTP-Patator       | 5496                 | 0.2064%    |
| SSH-Patator       | 4051                 | 0.1521%    |
| DoS Slowloris     | 4031                 | 0.1513%    |
| DoS SlowHttpTest  | 3901                 | 0.1465%    |
| Bot               | 1358                 | 0.0510%    |
| Brute Force       | 1066                 | 0.0400%    |
| XSS               | 456                  | 0.0171%    |
| Infiltration      | 22                   | 0.0008%    |
| SQL Injection     | 14                   | 0.0005%    |
| Heartbleed        | 7                    | 0.0002%    |


# References
[1] Intrusion Detection Systems: Principles And Perspectives | Mohammed Jamal al-mansor, Kok Beng Gan | 2018
[2] Survey of intrusion detection systems: techniques, datasets and challenges | Ansam Khraisat, Iqbal Gondal, Peter Vamplew and Joarder Kamruzzaman | 2019
[3] An Intrusion Detection Method Using Few-Shot Learning | yingwei yu and naizheng bian | 2020
[4] Prototypical Networks for Few-shot Learning | Jake Snell, Kevin Swersky, Richard S. Zemel | 2017

