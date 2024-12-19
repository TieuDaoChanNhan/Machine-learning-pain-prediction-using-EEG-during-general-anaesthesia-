# Pain Prediction Using EEG Data During General Anesthesia

## 1. Introduction
This project focuses on developing an AI model to predict pain levels in patients under general anesthesia using EEG (Electroencephalogram) data. By analyzing EEG signals that reflect brain activity, the model aims to estimate pain scores with high accuracy. This repository provides the process for loading, preprocessing, analyzing, and modeling the EEG data to achieve these predictions.

---

## 2. Data Overview
The dataset consists of EEG recordings from 568 patients, each saved as a CSV file. Key characteristics include:
- **Sampling Rate**: 100 Hz (100 samples per second)
- **Input Data**: Single-channel raw EEG signals for each patient
- **Output**: Pain score predictions on a scale of 0 to 10
- **Challenges**:  
  - Noise and artifacts present extreme values (e.g., 100, -1000, 32670) that require filtering.  
  - Varying data lengths across patients.

---

## 3. Data Organization
- **Input Data**: EEG files are stored locally in the directory `D:\AI\EEG`, with 200 CSV files named `subject_(1-200).csv`, each containing raw EEG signals.
- **Output Data**: Predicted pain scores are stored in the `data/output` folder, with 568 CSV files named `subject_(1-200).csv`, containing a single predicted score column.

---

## 4. Task
The goal is to train and evaluate the model using existing datasets:
- **Training Data**: Records from the first 160 patients.
- **Validation Data**: Records from the remaining 40 patients.
- **Accuracy Metric**: Predicted pain scores are compared with those in the output data folder to measure performance.

---

## 5. Solution
### Data Loading
Input data is read directly from local storage for processing.

### Data Preprocessing
1. **Bandpass Filtering**: Removes noise and artifacts to clean the raw signals.
2. **Epoch Segmentation**:  
   - EEG signals are divided into 30-second epochs, discarding incomplete segments.  
   - For instance, a sequence structured as `1,1,1,1,1,1,1` will be segmented into `1,1; 1,1; 1,1`.

---

## 6. Model Choice
A **1D Convolutional Neural Network (CNN)** is used for time-series analysis. CNNs are effective at identifying spatial and local patterns in transformed EEG signals. The model is trained on preprocessed data to optimize feature extraction and pain level predictions.

---
