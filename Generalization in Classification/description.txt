### Problem Statement

The project aims to build and enhance a ResNet model for image classification using the SVHN (Street View House Numbers) and MNIST datasets. The objective is to achieve high accuracy on these datasets and explore various techniques to improve model generalization and performance.

### Solution Overview

1. **Train the Base Model**:
    - **Model Architecture**: Implement a ResNet architecture using BasicBlock.
    - **Datasets**: Load and normalize the SVHN and MNIST datasets.
    - **Training**: Train the ResNet model on the SVHN dataset.
    - **Evaluation**: Evaluate the model performance on both SVHN and MNIST test sets.

2. **Enhance Generalization**:
    - **Model Architecture Modification**: Remove batch normalization from the ResNet architecture to observe its impact on performance.
    - **Loss Function**: Implement Label Smoothing Cross-Entropy Loss to improve model robustness.
    - **Data Augmentation**: Apply various augmentation techniques to the training data to improve generalization.
    - **Transfer Learning**: Utilize a pre-trained ResNet18 model and fine-tune it for the SVHN dataset.
    - **Optimizer**: Experiment with different optimizers like Adam to find the best performing one.

3. **Reverse Training**:
    - **Train on MNIST**: Retrain the model on the MNIST dataset using the best settings from previous steps.
    - **Fine-Tune**: Fine-tune the model using a subset of the SVHN dataset to enhance performance on SVHN after training on MNIST.

### Key Features and Methods

- **ResNet Architecture**: Implemented using BasicBlock for the base model and without Batch Normalization for testing.
- **Datasets**: SVHN and MNIST datasets with appropriate transformations and augmentations.
- **Training Loop**: Custom training loop with loss tracking and visualization.
- **Evaluation**: Function to evaluate model performance on test datasets.
- **Data Augmentation**: Random rotations, affine transformations, resized crops, color jitter, and perspective transformations to improve generalization.
- **Label Smoothing**: Cross-entropy loss with label smoothing to prevent overconfidence in predictions.
- **Transfer Learning**: Fine-tuning a pre-trained ResNet18 model on SVHN.
- **Optimizer**: Comparison between SGD and Adam optimizers to find the most effective one.
- **Reverse Training**: Train on MNIST and fine-tune on SVHN to test cross-dataset generalization.

### Results and Observations

- **Base Model**: Achieved 90.31% accuracy on SVHN and 62.89% on MNIST using the ResNet18 model.
- **Batch Normalization Removal**: Accuracy dropped on SVHN (84.00%) and MNIST (56.11%) without batch normalization.
- **Label Smoothing**: Improved accuracy on SVHN to 91.30% and MNIST to 63.53%.
- **Data Augmentation**: Further enhanced accuracy on SVHN to 93.83% and MNIST to 68.01%.
- **Transfer Learning**: Using a pre-trained ResNet18, achieved 92.09% on SVHN and 69.00% on MNIST.
- **Optimizer**: Adam optimizer improved SVHN accuracy to 91.74% and MNIST to 75.99%.
- **Reverse Training**: Training on MNIST first resulted in 27.95% on SVHN and 99.01% on MNIST. Fine-tuning on SVHN improved SVHN accuracy to 31.89%.

### How to Use

1. **Setup**: Ensure all required libraries are installed (`torch`, `torchvision`, `matplotlib`, `numpy`).
2. **Run Training**: Execute the training scripts provided for each section to replicate the results.
3. **Evaluate Models**: Use the evaluation functions to test model accuracy on SVHN and MNIST datasets.
4. **Experiment**: Modify parameters, try different augmentations, or use other datasets to explore further improvements.

By following these steps and using the provided methods, you can train a robust ResNet model for image classification and explore various techniques to enhance model performance and generalization.
