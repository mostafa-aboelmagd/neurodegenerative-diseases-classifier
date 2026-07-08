# Neurodegenerative Disease Classifier

## Description

- **Machine Learning Model** focused on **classifying** neurodegenerative diseases, specifically **Alzheimer's Disease (AD) and Parkinson's Disease (PD)**, from MRI brain images.

- **Provides An Automated Classification System** to assist medical professionals for faster and more accurate diagnosis, thereby potentially leading to **earlier treatment and improved patient outcomes**.

## Methodology

1. **Data Preprocessing Evaluation:** A systematic evaluation of **23 different preprocessing techniques** was conducted to optimize classification accuracy. **Standard Histogram Equalization** was identified as the **best preprocessing approach, achieving 80% classification accuracy**.

   ![Data before and after applying Histogram Equalization](https://github.com/user-attachments/assets/9ac614d5-5806-4f29-bf3e-d4f86d14c638)
   _Data before and after applying Histogram Equalization_

   ![Overall scores for different preprocessing techniques](https://github.com/user-attachments/assets/cd80f7c0-e14d-4bf1-be71-c16759ae9eba)
   _Overall scores for different preprocessing techniques_

2. **Feature Extraction:** A comprehensive set of features were extracted from the 2D MRI slices, including:
   - First-Order Statistical Features (mean, standard deviation, skewness, entropy, ...)
   - Gray Level Co-occurrence Matrix (GLCM) Features (e.g., contrast, dissimilarity, correlation, ...)
   - Local Binary Pattern (LBP) Features
   - Wavelet Features (from 2D Discrete Wavelet Transform using 'dbl' wavelet)
   - Edge and Gradient Features (using Sobel and Canny operators)
   - Gray Level Run Length Matrix (GLRLM) Features

   ![Distribution of Selected Features Across Diagnostic Classes](https://github.com/user-attachments/assets/615d9467-e126-40ca-a90d-ac5769849241)
   _Distribution of Selected Features Across Diagnostic Classes_

3. **Feature Selection:** Multiple feature selection methods (Fisher Score, Mutual Information, Random Forest Feature Importance, Correlation Coefficient, Lasso Regression, Recursive Feature Elimination (RFE), T-Test, Elastic Net, SVM, Gradient Boosting) were employed to identify the most informative features. **The T-Test emerged as the most effective method**, yielding the highest **cross-validation accuracy of 0.799 with 10 features**.

   | Method                              | Best Number of Features | Cross-Validation Score |
   | :---------------------------------- | :---------------------- | :--------------------- |
   | Fisher Score (fclassif)             | 30                      | 0.786                  |
   | Mutual Information                  | 15                      | 0.796                  |
   | Random Forest                       | 25                      | 0.792                  |
   | Correlation                         | 20                      | 0.794                  |
   | Lasso Regression                    | 25                      | 0.790                  |
   | Recursive Feature Elimination (RFE) | 10                      | 0.797                  |
   | T-Test                              | 10                      | 0.799                  |
   | Elastic Net                         | 20                      | 0.798                  |
   | Support Vector Machine (SVM)        | 30                      | 0.797                  |
   | Gradient Boosting                   | 30                      | 0.792                  |

   _Table I: Feature Selection Methods and Performance_

4. **Classification:** A **Support Vector Machine (SVM) model utilizing a One-Vs-Rest strategy** for multi-class classification was trained. The RBF kernel function was used to map non-linear data into a higher dimensional space where separation is easier. The SVM classifier achieved an **overall accuracy of 87.5%** in distinguishing between Alzheimer's, Parkinson's, and normal brain MRI images.

   ![Confusion Matrix](https://github.com/user-attachments/assets/8afccc99-c605-49ae-a0b9-a3e009f6a34c)

   ![ROC Curve](https://github.com/user-attachments/assets/bf94808a-a6df-4357-8b03-52057d51d7c3)

## Dataset

**MRI Brain Scans** categorized into three classes:

- Parkinson's disease: 2391 images
- Alzheimer's disease: 2500 images
- Normal controls: 2699 images

The dataset was divided using **stratified sampling** with an **80% training set and 20% testing set**. A balanced subset of **50 images per class was used** for the **preprocessing evaluation phase** to ensure fair comparison between techniques.

## Results

- **Optimal Preprocessing:** Standard Histogram Equalization.
- **Overall Classification Accuracy: 87.5%**.
- **Class-wise Accuracy:**
  - Alzheimer: 85.2%
  - Parkinson: 97.5%
  - Normal: 81%
- **AUC Scores:** Ranged from 0.93 to 1, indicating excellent separability between classes.

Further details on results and methodolgy used can be found in our [paper](https://drive.google.com/file/d/1pqs2T5OE2rDsWRbhKSZUdEtdz-fw9sT2/view?usp=sharing).

## Contributors

| Name             | GitHub                                                                                                                            |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Mostafa Ayman    | [![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/mostafa-aboelmagd)  |
| Rawan Ahmed      | [![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/RawanAhmed444)      |
| Kareem Abdelnabi | [![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/karreemm)           |
| Youssef Aboelela | [![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/Youssef-Abo-El-Ela) |
