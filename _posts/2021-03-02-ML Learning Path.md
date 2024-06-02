---
title: "Hands-on Machine Learning Log"
excerpt: "A learning log for learning the key concepts of ML"
categories:
  - portfolio
tags:
  - data science
  - python
  - machine learning
---
# Hands-on Machine Learning
### What is Machine Learning?
Machine Learning (ML) is a subfield of artificial intelligence (AI) that focuses on the development of algorithms and statistical models that enable computers to learn from and make predictions or decisions based on data. Unlike traditional programming, where explicit instructions are given to perform a task, machine learning algorithms use patterns and inference to improve their performance on a given task.

### Key Machine Learning methods
Machine learning methods can be broadly categorized into several types based on their learning paradigm and application. Here are some of the most common machine learning methods:

### 1. Supervised Learning

**Description**: Supervised learning involves training a model on a labeled dataset, which means that each training example is paired with an output label. The model learns to map inputs to outputs.

**Common Algorithms**:
- **Linear Regression**: Used for predicting continuous values.  
- **Logistic Regression**: Used for binary classification problems.  
See [post]({% post_url 2024-04-01-Regression-Analysis %}) for some example codes.

- **Support Vector Machines (SVM)**: Can be used for both classification and regression.
- **Decision Trees**: Used for both classification and regression tasks.
- **Random Forests**: An ensemble method that combines multiple decision trees.
- **K-Nearest Neighbors (KNN)**: A non-parametric method used for classification and regression.
- **Gradient Boosting Machines (GBM)**: An ensemble technique that builds models sequentially.
- **Neural Networks**: Models inspired by the human brain, used for complex tasks like image and speech recognition.

### 2. Unsupervised Learning

**Description**: Unsupervised learning involves training a model on data that does not have labeled responses. The goal is to infer the natural structure present within a set of data points.

**Common Algorithms**:
- **K-Means Clustering**: Partitions data into k clusters.
- **Hierarchical Clustering**: Builds a hierarchy of clusters.
- **Principal Component Analysis (PCA)**: Reduces the dimensionality of data while preserving variance.
- **Independent Component Analysis (ICA)**: A computational method for separating a multivariate signal into additive, independent components.
- **Association Rules**: Used for discovering interesting relationships between variables in large databases (e.g., Market Basket Analysis).

### 3. Semi-Supervised Learning

**Description**: Semi-supervised learning falls between supervised and unsupervised learning. It uses a small amount of labeled data and a large amount of unlabeled data for training.

**Common Algorithms**:
- **Self-training**: Uses a supervised learning algorithm iteratively.
- **Co-training**: Trains two classifiers on two different views of the data.
- **Transductive Support Vector Machines (TSVM)**: Extends SVM to handle both labeled and unlabeled data.

### 4. Reinforcement Learning

**Description**: Reinforcement learning involves training an agent to make a sequence of decisions by rewarding it for good decisions and punishing it for bad ones. It is often used for robotics, game playing, and navigation.

**Common Algorithms**:
- **Q-Learning**: A value-based method of learning the value of an action in a particular state.
- **Deep Q-Networks (DQN)**: Combines Q-learning with deep neural networks.
- **Policy Gradient Methods**: Directly learn the policy that maps states to actions.
- **Actor-Critic Methods**: Combine value-based and policy-based approaches.

### 5. Ensemble Learning

**Description**: Ensemble learning involves combining multiple models to improve the overall performance. The models (often referred to as "weak learners") are combined to produce a stronger model.

**Common Algorithms**:
- **Bagging (Bootstrap Aggregating)**: Reduces variance by training multiple models on different subsets of the data and averaging their predictions.
- **Boosting**: Reduces bias by training models sequentially, each trying to correct the errors of the previous one.
- **Stacking**: Combines multiple models using a meta-model that learns how to best combine the base models' predictions.

### 6. Neural Networks and Deep Learning

**Description**: Neural networks are a subset of machine learning models inspired by the human brain. Deep learning refers to neural networks with many layers (deep neural networks), which are particularly powerful for tasks like image and speech recognition.

**Common Algorithms**:
- **Convolutional Neural Networks (CNNs)**: Primarily used for image data.
- **Recurrent Neural Networks (RNNs)**: Primarily used for sequence data.
- **Long Short-Term Memory Networks (LSTMs)**: A type of RNN that can learn long-term dependencies.
- **Autoencoders**: Used for unsupervised learning tasks like dimensionality reduction and feature learning.
- **Generative Adversarial Networks (GANs)**: Used for generating new data samples.

These categories cover a wide range of machine learning methods, each suited to different types of tasks and data. The choice of method depends on the specific problem, the nature of the data, and the desired outcome.
