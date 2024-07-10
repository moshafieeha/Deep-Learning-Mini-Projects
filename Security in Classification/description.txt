## Problem Statement

This project addresses the detection and mitigation of backdoor attacks in neural networks, specifically targeting a poisoned ConvNet model trained on the MNIST dataset. Backdoor attacks insert malicious triggers into training data, causing the model to misclassify inputs when the trigger is present. The solution involves identifying the trigger, determining the attacked label, and then unlearning the trigger to restore the model's performance.

## Solution Overview

The solution is divided into two main parts: Trigger Finding and Unlearning.

### 1. Trigger Finding

**1.1 Trigger Reconstruction**

- **Model Setup**: A poisoned ConvNet model is loaded.
- **Trigger Visualization**: The model is optimized to visualize potential triggers for each class. This involves updating a pattern and mask using gradient descent.
- **Loss Tracking**: The loss for each class during the optimization process is tracked and visualized.
- **Results**: Triggers for each class are visualized, and the optimization process is monitored through loss curves.

**1.2 Attacked Label Detection**

- **Data Preparation**: The MNIST test data is loaded.
- **Mean Absolute Deviation (MAD) Calculation**: For each class, the MAD is calculated based on predictions made by the poisoned model when triggers are added to clean data.
- **Attacked Label Identification**: The label with the minimum MAD value is identified as the attacked label.
- **Visualization**: The MAD values and prediction distributions are visualized to confirm the attacked label.

### 2. Unlearning

**2.1 Building a New Dataset**

- **Poisoned Subset Creation**: A subset of the MNIST test data is poisoned with the trigger of the attacked label, but using true labels.

**2.2 Model Training with New Data**

- **Training**: The poisoned model is retrained using the poisoned subset to unlearn the backdoor trigger.
  
**2.3 Evaluation**

- **Evaluation Metrics**: The model's accuracy, precision, and the number of successful and unsuccessful attacks are measured before and after unlearning.
- **Results**: The poisoned model is evaluated on clean test data before and after the unlearning process, demonstrating significant improvements in accuracy and precision post-unlearning.

## How to Use

1. **Setup**:
    - Ensure that the necessary libraries are installed (`torch`, `torchvision`, `numpy`, `matplotlib`, `scipy`, `sklearn`).

2. **Run the Trigger Finding**:
    - Execute the provided code for trigger reconstruction to identify and visualize the triggers for each class.
    - Determine the attacked label by calculating the MAD values and examining the prediction distributions.

3. **Perform Unlearning**:
    - Create a poisoned subset using the identified trigger.
    - Retrain the poisoned model with the poisoned subset to mitigate the backdoor attack.
    - Evaluate the model on clean test data before and after the unlearning process to assess the effectiveness of the mitigation.

4. **Visualize Results**:
    - Use the provided visualization functions to plot triggers, loss curves, MAD values, and prediction distributions.

By following these steps, you can detect and mitigate backdoor attacks in neural networks, restoring the model's performance and robustness.
