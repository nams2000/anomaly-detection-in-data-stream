# Benchmarking data stream outlier detection methods

### Main Contributions
Data stream datasets have characteristics depending on the underlying domain and context. From their proximity to time series (mmmmmmmmmm citer le papier), we can characterize a data stream by the presence of  seasonality, trend, and cycle; due to the way data are arriving, we can add concept drift which is a non-negligible phenomenon which currently occurs in data stream context. 

This work: 

:white_check_mark: Compare some data stream anomaly detection methods on their latences and performances 

:white_check_mark: Focus on caracteristics presents on the datasets (seasonality, trend, cycle, concept drift) 

### Interested in my work?

Feel free to contact me at: anne.ngobibinbe@gmail.com

*The final version of our paper (in French) on the benchmark of data stream outlier detection methods is being submitted to the 2022 French Speaking Conference on the Extraction and Management of Knowledge (EGC).*

### README Structure
1. [Methods compared](#Methods-compared): Presentation of methods we compared
2. [Datasets and their caracteristics](#Emotional-Models): Brief Description of datasets and caracteristics identified 
3. [Description of the experimental protocol](#Emotional-Models): Description of the experimental protocol
5. [Results](#Emotional-Models): Presentation of results obtained
6. [Reproducibility](#Emotional-Models): How to reproduce our tests
7. [Referencies](#Emotional-Models)


## Methods compared
As it's the case for most of the anomaly detection methods, the following methods produce an anomaly score for each incoming instance showing how well the instance could be an anomaly, finally a threshold fixed by the user permits to say that instances with anomaly scores higher than the threshold are anomalies. In the literature, data stream anomaly detection methods are mostly separated into statistical based, tree based, proximity based and deep learning based approaches. We have chosen highly used and recommended approaches in each of those categories. 

Methods:
1. Online ARIMA : Statistic based methods which provide the anomaly score by computing the distance between the value of the instance forecasted from past instances and the real value of the instance. (mmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmm rajouter son lien et ceux des autres, mettre aussi le lien directe vers le github)
2. HStree : Tree based approach, providing the anomaly score according to how well an instance is isolated from other instances in an ensemble of pre-constructed trees
3. IforestASD : Similar to HStree
4. KitNet : Deep learning based methods  providing the anomaly score as the reconstruction error of an instance (Autoencoder)
5. MILOF : Proximity based approach, providing the anomaly score according to how locally reachable is an instance compared to its nearest neighbours. 

## Datasets and their caracteristics
We selected datasets mostly from IOT domain and whose anomalies causes are known to avoid errors due to human or tools labeling. In the boards, **no** trend means the dataset has a constant trend. Those characteristics have been identified by visualizing the datasets and are support by STL decompositions for trends and seasonalities.

:link: Anchor Links:
1. [Univariate datasets](#Univariate-datasets)
2. [Multivariate datasets](#Multivariate-datasets)

### Univariate datasets
We used here the Real known cause group of datasets of the NAB Benchmark (mmmmmmmmmmmmmmmmmmmmciter nab, mettre aussi le lien directe vers le github)

Dataset | Domain | Dataset length | number of anomalies | Concept Drift | Seasonality | Trend | Cylce 
-----|-------------|------------|------------|---------|-----------------------|------------ |------------
ambiant temperature system failure|  |7267 | 2| yes | yes | yes| no
cpu utilization asg misconfiguration|  |18050 | 1| yes | yes | yes| yes
ec2 request latency system failure|  |4032 | 3| no | no | yes| no
machine temperature system failure|  |22695 | 4| no | no | no| no
new york taxi|  |10320 | 5| no | yes | yes| yes
rogue agent keyhold|  |1882 | 2| yes | no | yes| no
rogue agent key up down|  |5315 | 2| yes | no | no| no

 
### Multivariate datasets
We selected some datasets showing a great number of our specified characteristics from the SKAB benchmark (mmmmmmmmmmciter SKAB). All those datasets have 7 dimensions.


Dataset | Domain | Dataset length | number of anomalies | Concept Drift | Seasonality | Trend | Cylce 
-----|-------------|------------|------------|---------|-----------------------|------------ |------------
other 9: Closing the valve at the flow inlet to the pump| IOT |751 | 2| no | no | yes| yes
other 11: Closing the valve at the flow inlet to the pump|  |665 | 4| no | yes | no| no
other 13: Sharply behavior of rotor imbalance|  |7267 | 2| yes | yes | yes| no
other 14: Linear behavior of rotor imbalance|  |1153 | 2| yes | yes | yes| yes
other 15: Step behavior of rotor imabalance |  |1147 | 2| yes | yes | yes| no
other 17: Exponential behavior of rotor imbalance|  |1147 | 4| no | yes | no| yes
other 20: Draining water from the tank until cavation |  |1191 | 4| yes | yes | yes| no
other 22: Water supply of increased temperature |  |1079 | 4| yes | yes | yes| yes

7. [Discrete Model](#Discrete-Model): Description of discrete emotions and the main representations
8. [Continuous Model](#Continuous-Model): Description of continuous emotions and the main representations




## How to reproduce our tests 
### Install dependencies:
Make sure you have at least python 3.6 
to install requirement type: pip install -r requirements.txt

### To test methods:
On univariate dataset:
python test_univariate.py name-of-the-method-to-test

On multivariate datasets: 
python test_multivariate.py name-of-the-method-to-test

The name of methods are the following:
  MILOF for MILOF,  ARIMAFD for online ARIMA,  HS-tree for Hs-tree, iforestASD for iForestASD, KitNet for KitNet,

The results of the test will be in the folder result. for each dataset, the result file contains:
-the time execution

-the f1-score

-the best hyperparameters of each method

# Notices: 
It is possible to change the score used for the experiment by default the MERLIN score (1% around the anomaly )is used.

Details on characteristics of the datasets and hyperparameters we found are summarized in the file: summary_of_the_experiment.pdf. 


# referencies:
- 
