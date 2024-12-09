# Business Understanding
Road accidents are the leading cause of death for individuals under the age of 30. Therefore, it is in the interest of all parties to attempt to reduce this figure. This project aims to design a model that will predict the primary contributory cause of car accidents based on available data such as vehicle information, occupant details, road conditions, and environmental factors.

## Business Objectives
### Problem Statement
Road accidents are the leading cause of death for people under the age of 30. Understanding the primary contributory causes of accidents is essential for stakeholders such as city planners, law enforcement, and vehicle safety boards to develop effective interventions.

The goal is to build a predictive model that accurately identifies the primary contributory cause of accidents using available data on vehicles, drivers, road conditions, and environmental factors. By addressing class imbalances and identifying meaningful patterns, the model will support stakeholders in:
- Reducing accident rates through targeted interventions,
- Allocating resources more effectively to address high-risk causes,
- Informing policies and infrastructure improvements to enhance road safety.

### Expected Benefits
Through the success of the project, the Transportation Safety Board will be able to understand what factors lead to accidents and help inform policy creation to make the roads safer.

### Business Success Criteria
Success of the project will be evaluated through the creation of a model which can predict the primary cause of an accident where one has occurred.

---

## Assessment
The data available consists of information about accidents that happened in Chicago.  
The most prominent risk of this project is the existence of an unbalanced dataset. The causes of accidents may not be evenly spread, hence, some factors may be more likely than others, leading to issues in the modeling process.

---

## Project Goals
- Clean the data
- Perform Exploratory Data Analysis
- Develop a decision tree and iterate upon it to improve metrics
- Evaluate the model

### Project Success Criteria
The project will be considered a success following the completion and evaluation of a decision tree classifier to predict the main reason for accidents.

---

## Data Understanding
The data has been collected by the Chicago Police Department and dates between 2015 and December 2024. It has:
- **Records**: 899,000
- **Columns**: 48  

---

## Data Preparation
- All columns with more than 50% missing values are dropped.
- The remaining columns with rows containing missing values are dropped.
- Categorical columns are encoded using pandas’ `get_dummies` function with `drop_first` set to `True` to avoid data leakage.

---

## Modelling
- **Train-Test Split**: 75/25 split with `random_state` set to `42`.

### Iterative Modeling Process:
1. **Baseline Model**:
   - A decision tree classifier with `random_state=42`.
   - Scores: 
     - **Train Accuracy**: 100% 
     - **Test Accuracy**: 83.3% (indicating overfitting).

2. **Second Model**:
   - Set `criterion="entropy"` and `max_features=5` to perform feature selection on the high-dimensional dataset (130+ columns due to encoding).
   - **Test Accuracy**: 83.5% (minimal improvement).

3. **Third Model**:
   - To address class imbalance (89% of values in one class), training data is balanced using **SMOTE**.
   - The model adds `max_depth=30` to reduce overfitting.
   - Scores:
     - **Test Accuracy**: 81.9% (slightly lower than earlier models due to balanced classes).
     - **F1 Score**: 82.8% (a good score considering class imbalance).

---

## Recommendations
1. **Address Human Error**:
   - As human error, particularly **failing to yield**, is the leading cause of accidents in the dataset:
     - Improve signage to clearly indicate yield points.
     - Provide better driver training to reduce accidents caused by human error.

2. **Enhance Modeling Techniques**:
   - Use more advanced models based on decision trees, such as **Random Forests**, to improve predictive performance.

---

## Next Steps
1. **Advanced Machine Learning Techniques**:
   - Apply techniques like **Principal Component Analysis (PCA)** to reduce dimensionality and improve model efficiency.

2. **Model Comparisons**:
   - Experiment with different classification models (e.g., Random Forest, Gradient Boosting) and compare results.
