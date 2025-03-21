# Step Detection Competition

This repository contains the code and resources for the Step Detection Competition. The goal of the competition is to predict the start and end of human steps using sensor signals recorded from accelerometers and gyroscopes. These sensors were held in the hand during various activities, such as simple walking, walking up and down stairs, and standing still.

## Competition Overview

Participants are provided with both training and testing datasets. The challenge is to develop a model that processes these sensor signals and outputs, for each time point, the probability that it marks the start and the end of a step.

### Task Description

- **Objective:**  
  Predict the start and end of human steps from six sensor signals.

- **Data Source:**  
  The data consists of accelerometer and gyroscope readings captured during four different activities.

## Data Description

### Training Data

Each training folder includes:
- **Signal File (`xxxx.csv`):**  
  Contains seven columns:
  - **Activity ID:** The first column indicating the type of activity.
  - **Accelerometer Data:** Three columns for x, y, and z axes.
  - **Gyroscope Data:** Three columns for x, y, and z axes.
  
- **Step Label Files (`xxxx.csv.stepMixed`):**  
  Contains labels indicating the start and end indexes for each complete step. Multiple step label files might be present per folder, representing different chunks of the recorded signals.

### Testing Data

- **Test Data File (`testData.csv`):**  
  Has the same structure as the training signal files, except it does not include the activity column. The model is expected to predict the probability of a step start and end for each time point in this file.

### Expected Output Format

For each time point in the test data, your model should output a probability for the start and a probability for the end of a step. The output should be a CSV file formatted as follows:

index,start,end 0,0.01,0.2 1,0.9,0.1 2,1.0,0.0 3,0.05,0.95 ... 102090,0.0,1.0

Each row represents a time point, where:
- `index` is the time point index.
- `start` is the probability that the time point marks the beginning of a step.
- `end` is the probability that the time point marks the end of a step.

## Evaluation Metric

The competition uses the **Mean Columnwise Accuracy Precision (MCAP)** metric, as described in the [scikit-learn average_precision_score documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score). Your predictions will be evaluated against this metric when submitted on Kaggle.
