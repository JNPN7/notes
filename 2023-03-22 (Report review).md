### Abstract
- [ ] change accuracy and loss
- [ ] Remove info about auto-encoder
- [ ] Add that the conversion of linear data into image

### Introduction
- [ ] Remove info about IGTD??
- [ ] Remove DNN as embedding function ?
- [ ] Add scope and application section

### Literature Review
- [ ] Needs refactoring


### Requirement analysis
- [x] Change Software requirements to tools used
- [x] Change the language used in functional and non functional requirements

### Methodology
- [ ] Change size of image and add boldness to image
- [ ] Change order of images
- [x] Data pre-processing manage format
- [ ] Keep sample image of 2D generated
- [x] Add algorithm too
- [x] Change model architecture of auto-encoder
- [ ] Model training image (block diagram)

### Results
- [ ] Add updated results
- [ ] Add auto-encoder results

### Conclusion
- [ ] Add some results too in conclusion
- [ ] Can add future enhancement and problem faced at conclusion itself

### Appendix
- [ ] Maintain table



## Literature review

- CICIDS
The cicids2017 dataset was created by Canadian Institute for Cybersecurity (CIC), University of New Brunswick (UNB), Canada
Sharafaldin et al. [10] evaluated the performance of a comprehensive set of network  
traffic features and also indicated a set of features vital for various kinds of attacks  
like Flow Inter arrival time (IAT) related features such as Min, Mean, Max and  
also the Flow Duration are the best common features for DoS detection. For DDoS  
attacks, backward packet length, average packet size, and some inter-arrival time-  
related features were found to be more vital. Similarly, a comprehensive table  
has been asserted by Sharafaldin et al. with the types of attacks included in  
CICIDS2017 datasets and the most vital features for each attack.

- IDS
(NON AI) Ghafir et al, [13] developed an ids for detecting command and control traffic
detection. The modules used by authors is blacklist based detection modules.
Blacklist was automatically updated. [13]’s authors used four detection modules
which are malicious IP address detection module (MIPD), malicious SSL certifi-
cate detection module (MSSLD), Domain flux detection module (DFD) and Tor
connection detection module (TorD). The output of all these modules is fed to
correlation framework (CF) which find links between alerts to increase the confi-
dence of botnet traffic detection and decrease the rate of false alarm. Update of
blacklist is scheduled using corntab.

- Prototypical network
- IGTD algo
- Autoencoders
- Survey
[14] Similarly, Wang Z. et al. proposed a few-shot learning-based Siamese network and
capsule network hybrid to tackle the scarcity of abnormal network traffic training
data and enhance the detection of unknown attacks. Also, new sampling method
based on unsupervised machine learning techniques (clustering) to group training
samples of each network attack type into subtypes of data was done for balancing
the training data

- Fewshot
Few-shot classification is a task in which a classifier must be adapted to accommodate new classes not seen in training, given only a few examples of each of these classes. Fewshot has been used for multiple things. 

Jake Snell et al. [5], proposed a prototypical networks for the problem of few-shot classification, where a classifier must generalize the new classes not seen in training set, given only a small number of examples of each new class. This prototype network technique, according to this research, is significantly superior and simpler than other ways such as the Matching Network and the MAML method.  The authors evaluated the prototypical network on several known datasets such as Omniglot, miniImageNet, and CU-Birds, achieving state-of-the-art results on the CU-Birds datasets while extending the prototypical network to zero-shot learning.

YAQING WANG et al. starting from a formal definition of FSL, they distinguished FSL from several relevant machine learning problems. They generalized FSL methods from three perspectives: (i) data, which uses prior knowledge to augment the supervised experience; (ii) model, which uses prior knowledge to reduce the size of the hypothesis space; and (iii) algorithm, which uses prior knowledge to alter the search for the best hypothesis in the given hypothesis space. 

- Model used RNN
Multiple other models have been used for intrusion detection system. Some modules includes RNN, DNN, LSTM, etc.

Chuanlong Y. et al. [11], proposed a deep learning approach for intrusion detection using recurrent neural networks(RNN-IDS). The authors treated IDS as a classification problem, such as a binary or a multi-class classification problem. The authors studied the performance of proposed model in binary and multi-class classification and compared it with those of J48, artificial neural network, random forest, support vector machine, and other machine learning methods proposed by previous researchers

Punam Bedi et al. [15] developed a novel IDS named Siam-IDS using the
Siamese Neural Network to handle the class imbalance problem in NSL-KDD
dataset. They used the siamese network consisting of two identical DNNs com-
prising of an input layer, five hidden layers and four dropout layers to compute
the similarity score between the input pairs. If the similarity score has a high
value, the inputs belong to the same class and if the similarity score is low, the
inputs belong to different classes. In their experiment, they have compared the
performance of Siam-IDS with DNN and CNN based IDSs and found that there
was a significant increase in the recall values of minority classes.

- Autoencoder
Autoencoder is one of the method in which the anomaly in the data is detected.

Mirsky et al. [12], proposed a plug and play which can learn to detect attacks
on the local network, without supervision, and in efficient online manner. [12]
designed KitNET (kitsune Network) algorithm uses an ensemble of neural net-
works called autoencoder to collectively differentiate between normal and abnor-
mal traffic patterns. [12] proposed NIDS has five components, packet capture,
packet parser, feature extractor(FE), feature mapper (FM), and anomaly detector
(AD).In FE, window of packets from each channel was maintained and contin-
uously computation of statistics over those window. The author used damped
incremental statistics for creation of window. 5 time window was taken, 100ms,
500ms, 1.5sec, 10sec and 1min. Total features extracted was 115, 23 features from
each window. In FM, n features is mapped into k smaller sub-instances, one sub-
instances for each autoencoder. The AD has two layers, ensemble layer and output
layer. Ensemble layer is 3 layer autoencoder which is responsible for measuring
the independent abnormalities of each subspace(instance). And Output layer is
an ANN which is responsible for producing final score. The ensemble layer passes
the RMSE (root mean square error) to the output layer. The main problem with
KitNET is DDoS attack, the attack can consume the device’s memory.

