# Network-Intrusion-Detection
Analysis for Model Selection for Network Intrusion Detection

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
   - Correlation Analysis throigh a heatmap
   - Exploring the Numerical Features using **Univariate Analysis** to visualize their distributions
   - Exploring through **Bivariate Analysis** but before that we found the **Statistical Dispersion and Variation** as some features behaved like constant features
   - Lastly, we look at the problem of **GroundTruth** to see if there is a problem of Class Imbalance.
 
## Machine Learning
   - Before we started the machine learning, we first standardised the dataset as they might behave badly if the individual features do not more or less look like the standard normally distributed data, eg. for K-Nearest-Neighbours
   - Next, we performed feature importance using Random Forests and Recursive Feature Elimination to rank the importance of features to identify the most relevant ones for the anomaly detection 
   - After that we split the dataset and use the features identified by RFE

   1. Decision Tree:
        - We chose decision tree as they are able to handle catgorical and numerical data and can be combined with other algorithms to improve accuracy
        - We performed Hyperparemeter tuning to find the set of hyperparameters that maximizes the accuracy of the Decision Tree classifier on the test data.
       
   2. K-Nearest-Neighbours:
        - KNN is a non-parametric algorithm, meaning it does not make any assumptions about the underlying distribution of the data. Instead, it relies on the distances between data points to make predictions.
   
   3. Logistics Regression 
        - Logistic regression is a fast and accurate algorithm, making it suitable for real-time network anomaly detection.
   
# Conclusion:

# What We Learnt:

# References:
