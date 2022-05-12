# Major-Project
An Ensemble based Machine Learning Approach for Network Intrusion Detection

## Motivation
Security failures and intrusion has been a major problem since the commercialization of the internet. It's a more valid issue now more than ever due to the ever-increasing number of devices being linked to networks. While this has indeed led to big possibilities for online storage and others, it also has led to huge security risks which need to be sufficiently countered. Network Intrusion Detection Systems have been around for decades now but traditional detection was more reliant on static analysis of the packets and extraction of simple attributes of data packets like header length, body size, flags used, etc, have been replaced by more robust and efficient IDS systems that have the capability of deep packet inspection and uses Machine Learning algorithms to find correlations and extrapolate new attributes and relations out of the given data to predict the result. But most of these solutions suffer from high false positivity rate problems or extensive consumption of computational power problems.

Our approach tries to redress this weakness by using an ensemble of machine learning algorithms that can learn the nature of attacks from the data flow statistics of some channel and gauge whether it is malicious in nature or not. The implemented approach has a very low false positivity rate and a very high true positivity rate.

## Dataset Used 
The datasets we chose for the task of training an ML model were the CSE-CIC-IDS-2018 and CIC-IDS-2017. These datasets have been constructed such that they effectively capture a real-world network attack. The data creators in their paper described in their seminal paper the notion of profiles to generate cybersecurity datasets. In their paper, they describe the use of M profiles in an attempt to make the attack setting simple. A straightforward way to accomplish this is by having humans interpret and act it out. In a more ideal setting, we would have an independent agent with compilers to carry them out. Some examples of the attacks carried out include Heartleech, Botnet, DDos, Dos, Infiltration. On the other hand B profile can be understood as having ML and Statistical models capture the behaviour of the malicious user and have it perform attacks.

<!-- table image , Distribution of different types of attacks in both datasets. image-->

## Approach
The dataset provides two columns as targets one with normal-not normal values and one with attack type values. We found that classifying by attack type and aggregating the results to normal and abnormal traffic gave us better results than classifying on normal/abnormal traffic. Thus, our problem is categorized as a supervised multiclass classification problem. supported the papers we mentioned we selected the utilization of three algorithms to specialize in the issue:
<ul>
<li>Decision Tree Classifier</li>
<li>Random Forest Classifier</li>
<li>Support Vector Machine.</li> 
<li>Logistic Regression.</li>
<li>XGBoost Classifier.</li>
</ul>

Stacked Generalization (also known as Stacking ) is a type of ensemble ML algorithm. It involves combining the predictions from multiple machine learning models on the same dataset, like bagging and boosting.
Unlike bagging, the models we make use of are typically different but fit on the same dataset. Unlike boosting, a single model has been used to fit over the predictions from the base models 
The architecture of a stacking model generally has two and above base models, known as level-0 models, and a meta-model that fits over the predictions of the base models, known as a level-1 model.

<ul>
<li>Level-0 Models (Base-Models): Models fit on the train set and predictions are made into a dataset for the meta-model.</li>
<li>Level-1 Model (Meta-Model): Model that fits on predictions of the base models.</li>
</ul>

## Overview of results
Training both binary and multi-class classifiers on the training set, it could be observed that the hypothesis of stacking weaker learners into a strong learner is true. Although the stacked ensemble is not vastly different from that of the strongest level 0 base learner, it still outperforms it by an appreciable margin. Considering that this stacked ensemble model did not look at the training data at all and identifies the cases in which our strongest base learner gets the predictions wrong and gives some weightage to other weaker learners to improve the strongest prediction even further. 

We present the different metrics commonly used for classification. Proposing accuracy is perhaps not the best measure although not completely ignoring it, we look at ROC score which signifies to some degree how confidently the model identifies what it does.  It tells how much the model is capable of distinguishing between classes. We also look at the individual confusion matrices for binary classification and the final confusion matrix of the stacked ensemble for multi-class classification as well.

<!-- Add images -->

