# Ad Clicks Prediction Project
It's a classification model that predict advertisement click behaviour based on various user and ad-related features.

## Overview
This project aims to predict whether a user will click on an advertisement based on various user and ad-related features. The goal is to build a robust classification model that can assist in optimizing ad placement and targeting strategies. We explore several machine learning models and evaluate their performance to identify the most effective solution.

## Dataset
The dataset `advertising.csv` contains information about users, their internet usage, demographics, and whether they clicked on an ad. Key features include:
- `Daily Time Spent on Site`
- `Age`
- `Area Income`
- `Daily Internet Usage`
- `Ad Topic Line`
- `City`
- `Male` (binary: 0 for female, 1 for male)
- `Country`
- `Timestamp`
- `Clicked on Ad` (target variable: 0 for no click, 1 for click)

## Data Preprocessing and Feature Engineering
1.  **Missing Values**: No missing values were found in the dataset.
2.  **Timestamp Features**: The `Timestamp` column was converted to datetime objects, and new features `Hour`, `Day_of_Week`, and `Month` were extracted.
3.  **Outlier Handling**: Outliers in numerical features were identified and capped using the IQR method.
4.  **Categorical Feature Removal**: High-cardinality categorical features such as `Ad Topic Line`, `City`, `Country`, and the original `Timestamp` were dropped to simplify the model and avoid issues with one-hot encoding a large number of unique values. The remaining features were all numerical.

## Exploratory Data Analysis (EDA) - Key Insights
Correlation analysis revealed strong relationships between certain features and ad clicks:
-   **`Daily Internet Usage` (-0.79)**: Strong negative correlation. Users with higher daily internet usage are less likely to click on ads.
-   **`Daily Time Spent on Site` (-0.75)**: Strong negative correlation. Users spending more time on the site are less likely to click on ads.
-   **`Area Income` (-0.47)**: Moderate negative correlation. Higher area income is associated with a lower likelihood of clicking on ads.
-   **`Age` (0.49)**: Moderate positive correlation. Older users show a higher propensity to click on ads.
-   `Male`, `Hour`, `Day_of_Week`, and `Month` showed weaker correlations, suggesting less influence on ad click behavior compared to the other features.

## Model Development and Evaluation
We trained and evaluated five different classification models. All models were built using `scikit-learn` pipelines, incorporating `StandardScaler` for feature scaling and the respective classification algorithm.

### Models Implemented:
1.  **Logistic Regression**
2.  **Decision Tree Classifier**
3.  **Random Forest Classifier**
4.  **K-Nearest Neighbors (KNN)**
5.  **Support Vector Machine (SVM)**

### Model Performance Summary:
| Model                       | Accuracy (Test Set) |
| :-------------------------- | :------------------ |
| Logistic Regression         | 0.9749              |
| Decision Tree Classifier    | 0.9648              |
| Random Forest Classifier (Initial) | 0.9749              |
| K-Nearest Neighbors (KNN)   | 0.9598              |
| Support Vector Machine (SVM)| 0.9698              |


## Conclusion
All implemented models achieved high accuracy, consistently performing in the 96-97% range on the test set. Logistic Regression and the initial Random Forest model showed slightly superior performance. The strong predictive power of the models, combined with the insights from EDA, suggests that features like `Daily Internet Usage`, `Daily Time Spent on Site`, `Area Income`, and `Age` are crucial in determining ad click likelihood.

This project provides a solid foundation for understanding and predicting ad click behavior, which can be further leveraged for targeted advertising campaigns and improved user engagement strategies.
