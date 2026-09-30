<div align="center">

# HRV Cross-Dataset Stress Detection

**Can heart rate variability tell us when someone is stressed, across different settings?**

Implementation of an undergraduate thesis on cross-dataset stress detection using Heart Rate Variability (HRV) features and machine learning.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)

</div>

---

## Overview

Most stress detection studies train and test on a single dataset, which can make results look better than they would be in real life. This project takes a stricter approach by evaluating models **across datasets** with different stress conditions.

The study investigates the **consistency and contribution of HRV features** for classifying three conditions:

* Normal
* Academic stress
* Driving stress

Evaluation uses **Stratified Group K-Fold Cross Validation**, so recordings from the same subject never appear in both training and test sets.

## Models Evaluated

* Multi-Layer Perceptron (MLP)
* AdaBoost
* K-Nearest Neighbors (KNN)
* Support Vector Machine (SVM)

## Results

Performance of each model under cross-dataset evaluation with Stratified Group K-Fold Cross Validation:

| Model    | Accuracy (%) | F1-score (%) |
| -------- | ------------ | ------------ |
| MLP      | 80.99        | 79.11        |
| AdaBoost | 79.67        | 77.99        |
| KNN      | 78.91        | 76.03        |
| SVM      | 83.12        | 83.05        |

### Key Findings

* **All four algorithms classified the three conditions well** (normal, academic stress, and driving stress) in the cross-dataset setting.
* **No model clearly outperformed the others.** SVM achieved the highest F1-score, but statistical tests showed that the performance differences between models are not significant, so the four algorithms can be considered comparable.
* **Academic stress is the easiest condition to separate.** The dominant misclassifications occurred between normal and driving stress, while AUC was consistently higher for academic stress.
* **No single HRV feature was consistently the most important or the most stable** across all models, stressor types, and datasets. Feature contribution and consistency depend on the combination of classifier, stressor type, and dataset.
* **Engineered features often mattered more than conventional HRV features.** In particular, features based on pNN50 and RMSSD tended to play an important role more frequently.

### Takeaway

Successful HRV-based stress detection in a cross-dataset setting depends on the interaction between the model, the type of stressor, and the data source. No single combination of features and model performs best universally, so feature and algorithm selection should be adapted to the characteristics of the data.

## Features

| Feature | Description |
| ------- | ----------- |
| HRV time-domain features | Standard time-domain measures computed from RR intervals |
| Temporal features | Extracted with the TSFEL library |
| Feature engineering | Additional HRV-based features built on top of the base set |
| Cross-dataset evaluation | Models tested across different datasets and conditions |
| Permutation importance | Identifies which features contribute most to classification |
| Statistical testing | Checks whether differences between models are significant |

## Workflow

```text
Raw RR data -> Preprocessing -> Feature extraction -> Training and evaluation -> Feature importance -> Statistical tests
```

| Notebook | Purpose |
| -------- | ------- |
| `01_preprocessing.ipynb` | Clean and prepare the raw datasets |
| `02_feature_extraction.ipynb` | Extract HRV and temporal features |
| `03_training_evaluation.ipynb` | Train and evaluate MLP, AdaBoost, KNN, and SVM |
| `04_permutation_importance.ipynb` | Analyze feature importance |
| `05_statistical_tests.ipynb` | Run statistical significance tests |

## Datasets

The datasets are **not included** in this repository. This project uses three publicly available datasets from PhysioNet:

* Wearable Exam Stress Dataset
* Driving Stress Database
* Normal Sinus Rhythm RR Interval Database

Please download them from the official PhysioNet website: [https://physionet.org/](https://physionet.org/)

After downloading, place the files in the appropriate project directory before running the notebooks.

## Project Structure

```text
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

## How to Run

**Step 1: Get the data**

Download the three datasets from PhysioNet and place them in the project directory.

**Step 2: Install the requirements**

```bash
pip install numpy pandas scikit-learn tsfel scipy matplotlib
```

**Step 3: Run the notebooks in order**

Open the notebooks in Jupyter or Google Colab and run them from `01` to `05`. Each notebook builds on the output of the previous one.

## Tools

* Python
* Jupyter Notebook
* scikit-learn
* TSFEL

## Citation

If you use this code or build on this work, please credit this repository and the original PhysioNet datasets.

## Author

Made by **AURELIA ARDHANISA PUTRI** as part of an undergraduate thesis.


## License

Copyright (c) 2026 Aurelia Ardhanisa Putri. All rights reserved.

This repository is shared for viewing and academic reference only. If you would like to use, adapt, or build on this work, please contact me first at aureliaardhanisap@gmail.com
