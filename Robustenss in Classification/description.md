## Problem Statement

The project aims to train a ResNet model on the CIFAR10 dataset using different training techniques to improve its robustness against adversarial attacks. Specifically, it involves using traditional cross-entropy loss, incorporating data augmentation, and experimenting with circle loss to enhance the model's generalization and adversarial resistance.

## Solution Overview

1. **Setup and Installation**:
    - Install the necessary libraries including `pytorch_metric_learning` for advanced loss functions.

2. **Data Preparation**:
    - Load and preprocess the CIFAR10 dataset, splitting it into training, validation, and test sets.
    - Compute class weights to handle class imbalance using a weighted random sampler.

3. **Model Training and Evaluation**:
    - Train a ResNet18 model on the CIFAR10 dataset using different loss functions and data augmentation techniques.
    - Evaluate the model's performance on original and adversarial test sets using K-Nearest Neighbors (KNN) classifier and UMAP for feature visualization.

## Key Steps and Methods

1. **Original Data with Cross-Entropy Loss**:
    - **Training**: Train the ResNet18 model on the original CIFAR10 dataset using cross-entropy loss.
    - **Evaluation**: Evaluate the trained model on both original and adversarial test sets using KNN.

2. **Data Augmentation with Cross-Entropy Loss**:
    - **Training with FGSM**: Incorporate Fast Gradient Sign Method (FGSM) during training with a 50% probability to generate adversarial examples on-the-fly.
    - **Evaluation**: Evaluate the robustness of the model trained with augmented data on both original and adversarial test sets using KNN.

3. **Circle Loss**:
    - **Greedy Search**: Perform a greedy search to find the optimal parameters (m and gamma) for the circle loss.
    - **Training**: Train a modified ResNet18 model with the optimal circle loss parameters.
    - **Evaluation**: Evaluate the performance of the circle loss-trained model on original and adversarial test sets using KNN.

## Results and Observations

1. **Original Data with Cross-Entropy Loss**:
    - Training and validation loss decreased over epochs.
    - Accuracy on original test data: 80.72%
    - Accuracy on adversarial test data: 11.12%
    - Feature visualization using UMAP showed class separations but with overlaps.

2. **Data Augmentation with Cross-Entropy Loss**:
    - Training with FGSM led to a robust model with better generalization.
    - Accuracy on original test data: 75.27%
    - Accuracy on adversarial test data: 25.85%
    - Improved class separation in UMAP visualization compared to the original training.

3. **Circle Loss**:
    - Greedy search identified optimal values of m and gamma.
    - Training with circle loss exhibited steady loss reduction.
    - Accuracy on original test data: 27.79%
    - Accuracy on adversarial test data: 14.04%
    - UMAP visualization indicated dense clustering but less distinct class separations.

## How to Use

1. **Setup**:
    - Install the required libraries using `pip install pytorch_metric_learning`.
    - Ensure other dependencies like `torch`, `torchvision`, and `umap-learn` are installed.

2. **Run Training**:
    - Execute the training scripts provided for each section (Original, Augmented, Circle Loss) to replicate the results.
    - Modify parameters such as `num_epochs`, `batch_size`, and `learning_rate` to explore further improvements.

3. **Evaluate Models**:
    - Use the provided functions to evaluate the model performance on CIFAR10 test sets (both original and adversarial).
    - Visualize the feature embeddings using UMAP to understand the model's class separation capabilities.

4. **Experiment**:
    - Try different data augmentation techniques, loss functions, and optimizers to enhance model performance.
    - Test the model on different datasets to explore its generalization capabilities.

By following these steps and using the provided methods, you can train robust image classification models that are resilient to adversarial attacks and explore various techniques to enhance their performance and generalization.
