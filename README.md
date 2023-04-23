# Network-Intrusion-Detection
Analysis for Model Selection for Network Intrusion Detection through Machine Learning

# About:

In this mini-project for our SC1015 Module, we look at a Network Intrusion Detection Dataset consisting of a wide variety of intrusions simulated in a military network environment. 

Mini-Project By:
* Yashver Shori
* Josiah Yong
* Anish Gholap

# Background:

In the modern era, technology plays a crucial role in simplifying our daily routines. Despite the numerous advantages that digital devices and networks offer, they also make us susceptible to cyber attacks. Therefore, it is imperative that we prioritize maintaining the security of our digital networks by ensuring they are up-to-date and resilient to potential threats.

Network Intrusion Detection Systems (NIDS) are critical tools for maintaining the security of digital networks. Their primary function is to monitor network traffic for suspicious activity and identify potential security breaches in real-time. NIDS can help detect attacks that may have gone unnoticed, such as unauthorized access attempts, malicious network scans, and other suspicious network activity.

NIDS use machine learning algorithms to detect and classify network attacks. These algorithms are trained on large datasets of network traffic, including both normal and malicious traffic, to learn patterns and identify anomalies in the data.

# Objective:

Our objective is to use the network detection dataset together with various machine learning models for anomaly detection to find out which one is the best to build a network intrusion detection model.

# What's Included:

1. Network Intrusion Datasets
2. Presentation Slides
3. SC1015 Miniproject Notebook
   * Data Cleaning and Preparation
   * Exploratory Data Analysis
   * Machine Learning:
        - K-Nearest Neighbours
        - Random Forest Classifier
        - Logistics Regression
   * Analysis
   * Conclusion


# Notebook Walkthrough:

## Data Cleaning and Preparation

* Our dataset has 2 individual files for Train and Test but we chose to use the Train Set only which we will split later on
* We first checked for missing values to ensure that the dataset is complete and accurate as it may lead to biased or innacurate results and errors
* Next, we checked for duplicate rows as it may also create bias

## Exploratory Data Analysis

Our dataset consists of 41 features (independent var) and a class label (dependant var). The 41 features can be grouped into:
   - Basic(9): Derived from header information of network packets. Eg: duration, protocol_type, service, etc.
   - Content(13): Derived from packet payload. Eg: hot, num_failed_logins, logged_in, etc
   - Traffic(9): Capture the behaviour of connecttions between  **same source** and destination hosts. Eg: count, serror_rate, rerro_rate, etc.
   - Traffic between different hosts(10):  capture the behavior of connections between **different source** and destination hosts. Eg: dst_host_count, dst_host_srv_count, etc.

As such for our EDA, we decided to do the following:
   - Exploring the Categorical Features to analyse the distribution of values within each feature and observe any patterns
   - **Correlation Analysis** through a heatmap
   - Exploring the Numerical Features using **Univariate Analysis** to visualize their distributions
   - Exploring through **Bivariate Analysis** but before that we found the **Statistical Dispersion and Variation** as some features behaved like constant features
   - Lastly, we look at the problem of **GroundTruth** to see if there is a problem of Class Imbalance.
 
## Machine Learning
   - Before we started the machine learning, we first standardised the dataset as they might behave badly if the individual features do not more or less look like the standard normally distributed data, eg. for K-Nearest-Neighbours
   - Next, we encode the categorical attributes to make it compatible with numeric data when using models
   - Then, we performed feature importance using Random Forests and Recursive Feature Elimination to rank the importance of features to identify the most relevant ones for the anomaly detection 
   - After that we split the dataset and use the features identified by RFE

   * Baseline: We will be using Decision Tree to compare our models to. We chose Decision Tree as our baseline because of its versatility and that it doesnt require a lot of assumptions that need to be fulfilled for the model to work efficiently. It is also easily interpretable.

   1. Optimised Decision Tree:
        - Chosen for the reasons mentioned earlier however, it is now optimised.
        - We performed Hyperparemeter tuning to find the set of hyperparameters that maximizes the accuracy of the Decision Tree classifier on the test data.
       
   2. K-Nearest-Neighbours:
        - KNN is a non-parametric algorithm, meaning it does not make any assumptions about the underlying distribution of the data. Instead, it relies on the distances between data points to make predictions. It is supervised machine learning algorithm that can be used to solve both classification and regression problems using feature similarity making it popular for anomaly detection.
   
   3. Logistics Regression 
        - Logistic regression is a fast and accurate algorithm. It's a process of modelling the probability of a discrete outcome which is applicable in our scenario as Logistic Regression models a binary outcome of Normal or Anomalous.

   *all models were optimised*

## Analysis
    
  - Decision Tree is most acccurate
  - K Nearest Neighbours is the fastest
  - SRC_bytes most important feature
  - However, we need to take into account the optimization time, which is more than three times that of KNN since time taken for the whole model is important as intrusion detection is done in real-time.

## Conclusion

  -  All models perform similarly with each with its own strengths as mentioned before in our analysis
  -  We believe that the next best steps for companies would be to use multiple models together and leverage their strenghts to improve speed and accuracy which are key for a detection system

# What We Learnt 

  1. High Max Proportions and Low Variance
  2. Checking Class Imbalance
  3. K Nearest Neighbours and Logistics Regression
  4. Optimisation of a Model's Hyperparameters
  5. Importance of Feature Selection

# Contributions
  
  * Josiah: Problem Statement, Data Preparation and Slides
  * Yash: Machine Learning Models and Presentation
  * Anish: Exploratory Data Analysis, Github Repository and Presentation

# References

  1. https://www.analyticsvidhya.com/blog/2021/04/beginners-guide-to-low-variance-filter-and-its-implementation/
  2. https://www.dominodatalab.com/data-science-dictionary/ground-truth
  3. https://www.analytixlabs.co.in/blog/decision-tree-algorithm/#:~:text=Decision%20Trees%20can%20create%20complex,is%20that%20it%20offers%20interpretability.
  4. https://www.sciencedirect.com/topics/computer-science/logistic-regression
  5. https://optuna.readthedocs.io/en/stable/tutorial/index.html
  6. https://towardsdatascience.com/how-to-tune-a-decision-tree-f03721801680
  7. https://www.ibm.com/topics/logistic-regression
  8. https://towardsdatascience.com/two-is-better-than-one-ensembling-models-611ee4fa9bd8
