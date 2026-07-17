# HRV Cross-Dataset Stress Detection

## Overview

This repository contains the implementation of an undergraduate thesis on cross-dataset stress detection using Heart Rate Variability (HRV) features and machine learning.

The study investigates the consistency and contribution of HRV features for classifying three conditions (normal, academic stress, and driving stress) using a cross-dataset evaluation framework based on Stratified Group K-Fold Cross Validation. Four machine learning algorithms were evaluated:

- Multi-Layer Perceptron (MLP)
- AdaBoost
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)

## Datasets

This project uses three publicly available datasets from PhysioNet:

- Wearable Exam Stress Dataset
- Driving Stress Database
- Normal Sinus Rhythm RR Interval Database

Please download the datasets from the official PhysioNet website:

- https://physionet.org/

## Project Structure

```
hrv-cross-dataset-stress-detection/
│
├── notebooks/
│   ├── 01_preprocessing.ipynb
│   ├── 02_feature_extraction.ipynb
│   ├── 03_training_evaluation.ipynb
│   ├── 04_permutation_importance.ipynb
│   └── 05_statistical_tests.ipynb
│
├── README.md
├── LICENSE
└── .gitignore
```

## Features

- HRV time-domain feature extraction
- Temporal feature extraction using TSFEL
- HRV feature engineering
- Cross-dataset evaluation
- Feature importance analysis using permutation importance
- Statistical significance testing

## License

This project is released under the MIT License.
